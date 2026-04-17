# Informe de Obra Civil — EDAR
**Construcción e Instalaciones Industriales · MII · Curso 2025-2026**

---

## Parámetros del grupo

| Variable | Valor | Derivado de |
|---|---|---|
| **X** | 4 | 1ª cifra de la media de los 6 DNIs |
| **Y** | 3 | 2ª cifra de la media de los 6 DNIs |
| Desnivel muro | 7,3 m | (X+3, Y) |
| Arqueta (L × B × H) | 4 × 3 × 3,5 m | X × Y × (X+Y)/2 |

> DNIs (números): 30248832 / 49505322 / 77936142 / 01647207 / 49275542 / 53965819  
> Suma = 262.578.864 → Media = 43.763.144 → X=4, Y=3

---

## Estructura del proyecto

```
construcciones/
├── main.tex                          ← Punto de entrada principal
├── preamble.tex                      ← Paquetes, comandos y parámetros
├── referencias.bib                   ← Bibliografía (formato BibTeX)
│
├── chapters/
│   ├── 00_portada.tex
│   ├── 01_introduccion.tex           ← Contexto, datos del sondeo, condicionantes
│   ├── 02_muro/
│   │   ├── 00_intro_muro.tex
│   │   ├── 01_descripcion_opciones.tex   ← Muro ménsula vs. pantalla
│   │   ├── 02_calculos_geotecnicos.tex   ← Empujes, hundimiento, asientos
│   │   ├── 03_predimensionamiento.tex    ← Geometría, armado, materiales
│   │   ├── 04_calculos_estructurales.tex ← ELU, ELS
│   │   ├── 05_proceso_constructivo.tex   ← Medios humanos y maquinaria
│   │   ├── 06_presupuesto.tex
│   │   └── 07_gantt.tex
│   └── 03_arqueta/
│       ├── 00_intro_arqueta.tex
│       ├── 01_calculos_geotecnicos.tex
│       └── 02_cimentacion.tex
│
├── figures/
│   ├── muro/                         ← Imágenes y figuras del muro
│   └── arqueta/                      ← Imágenes y figuras de la arqueta
│
├── planos/                           ← Planos en TikZ o PDFs importados
├── tablas/                           ← Tablas externas (CSV, etc.)
└── anexos/
    ├── A_sondeo.tex                  ← Sondeo 1 completo
    ├── B_calculos_manuales.tex       ← Cálculos manuales y tanteos
    └── calculos_manuales/            ← Escaneos de hojas manuscritas
```

---

## Cómo compilar

### Opción A: `latexmk` (recomendado)
```bash
latexmk -pdf main.tex
```
Este comando ejecuta automáticamente todas las pasadas necesarias
(pdflatex → biber → pdflatex → pdflatex).

### Opción B: manual
```bash
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```

### Opción C: VS Code con LaTeX Workshop
1. Instalar la extensión **LaTeX Workshop** (`James-Yu.latex-workshop`).
2. Abrir `main.tex` y pulsar el botón **Build LaTeX project** (▶) o `Ctrl+Alt+B`.
3. Para ver el PDF: `Ctrl+Alt+V`.

---

## Sistema de contexto compartido para Claude Code

> **Para compañeros que usen Claude Code (CLI de Anthropic)**

Este repositorio usa un fichero **`CLAUDE.md`** en la raíz (`construcciones/CLAUDE.md`) que Claude Code carga automáticamente al arrancar cualquier sesión dentro de este directorio. Gracias a esto, **no es necesario re-leer ni re-analizar el proyecto desde cero** cada vez que alguien del equipo abre una sesión nueva.

### ¿Qué contiene `CLAUDE.md`?

| Sección | Contenido |
|---|---|
| Resumen del proyecto | Descripción y dimensiones (muro H=7,3 m / arqueta 4×3×3,5 m) |
| Parámetros del grupo | X=4, Y=3 y todas las dimensiones derivadas |
| Estratigrafía completa | Tabla de cotas, γ, φ, c, E, ν por estrato |
| Resultados geotécnicos | σ'v, Ka/Kp, todos los FS, decisiones de cimentación |
| Estado del trabajo | Checklist ✅/⬜ con ruta de cada archivo |
| Mapa de ficheros | Qué calcula cada `.tex` |
| Metodología | Fórmulas y referencias metodológicas usadas |
| Materiales | HA-30, B500S, exposición Q-c |
| Comandos LaTeX | `\resultado`, `\kNm`, `\alturaDesnivelMuro`, etc. |
| Protocolo de actualización | Reglas para mantener el fichero al día |

### Cómo usarlo

1. **Al empezar una sesión** — Claude Code leerá `CLAUDE.md` automáticamente. Puedes pedir directamente: *"continúa con `04_calculos_estructurales.tex`"* sin contexto adicional.
2. **Al terminar una sección** — Actualiza la sección **"Estado del trabajo"** de `CLAUDE.md` marcando la tarea como ✅ y añade los resultados clave nuevos si los hay.
3. **Tras cambios significativos** (nuevos resultados, cambio de hipótesis) — Actualiza también la sección correspondiente de `CLAUDE.md` antes de hacer push.
4. **Commit sugerido** tras actualizar:
   ```
   docs: actualizar CLAUDE.md con resultados de [sección]
   ```

### Regla de oro

> `CLAUDE.md` = **fuente de verdad del estado del proyecto**.  
> El código LaTeX = **fuente de verdad de los cálculos detallados**.  
> Si hay conflicto entre ambos, prevalece el `.tex`.

---

## Flujo de trabajo en equipo

### Ramas Git recomendadas
```
main          ← versión estable (solo merge cuando algo está revisado)
develop       ← integración continua del equipo
feat/muro     ← trabajo en la parte del muro
feat/arqueta  ← trabajo en la parte de la arqueta
```

### Convención de commits
```
feat: añadir cálculo de empuje activo (muro)
fix: corregir tabla de presupuesto
wip: borrador predimensionamiento zapata
```

### Recomendaciones
- **Cada miembro trabaja en su rama** y hace merge a `develop` cuando termina una sección.
- **No editar `main.tex` ni `preamble.tex`** sin consenso del equipo.
- **Compilar antes de hacer push** para asegurarse de que no hay errores LaTeX.
- Los **planos se incluyen como PDF** (exportados desde AutoCAD/Revit) o como **figuras TikZ**.
- Los **cálculos manuales escaneados** van en `anexos/calculos_manuales/` como imágenes PNG/PDF.

---

## Contenido pendiente (TODO)

Busca en el código los comentarios `% TODO:` para ver exactamente qué falta rellenar
en cada sección.

### Parte I — Muro
- [x] Descripción técnica de opciones (muro ménsula vs. pantalla) → `02_muro/01_descripcion_opciones.tex`
- [x] Cálculos geotécnicos: empujes, hundimiento, asientos → `02_muro/02_calculos_geotecnicos.tex`
- [ ] Predimensionamiento: geometría definitiva + planos → `02_muro/03_predimensionamiento.tex`
- [ ] Cálculos estructurales: ELU fuste y zapata → `02_muro/04_calculos_estructurales.tex`
- [ ] Despiece de acero y peso total
- [ ] Proceso constructivo con croquis → `02_muro/05_proceso_constructivo.tex`
- [ ] Presupuesto (completar mediciones) → `02_muro/06_presupuesto.tex`
- [ ] Gantt (completar duraciones reales) → `02_muro/07_gantt.tex`

### Parte II — Arqueta
- [x] Cargas transmitidas al terreno → `03_arqueta/01_calculos_geotecnicos.tex`
- [x] Comprobación de flotación → `03_arqueta/01_calculos_geotecnicos.tex`
- [x] Capacidad portante y asientos → `03_arqueta/01_calculos_geotecnicos.tex`
- [ ] Plano acotado con perfil del sondeo → `03_arqueta/02_cimentacion.tex`
- [ ] Detalle de impermeabilización → `03_arqueta/02_cimentacion.tex`

---

## Recursos de consulta

| Carpeta | Contenido |
|---|---|
| `Cimentaciones superficiales/` | Zapatas, losas, capacidad portante |
| `Cimentaciones profundas/Pilotes/` | Cálculo de pilotes, DBSE-C |
| `Materiales y medios auxiliares/` | Hormigón, acero, encofrados, topografía |
| `Mecánica del suelo/` | Muros pantalla, empujes, consolidación |
