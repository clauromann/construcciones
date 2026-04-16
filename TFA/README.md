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
- [ ] Descripción técnica de opciones (muro ménsula vs. pantalla)
- [ ] Cálculos geotécnicos: empujes, hundimiento, asientos
- [ ] Predimensionamiento: geometría definitiva + planos
- [ ] Cálculos estructurales: ELU fuste y zapata
- [ ] Despiece de acero y peso total
- [ ] Proceso constructivo con croquis
- [ ] Presupuesto (completar mediciones)
- [ ] Gantt (completar duraciones reales)

### Parte II — Arqueta
- [ ] Cargas transmitidas al terreno
- [ ] Comprobación de flotación
- [ ] Capacidad portante y asientos
- [ ] Plano acotado con perfil del sondeo
- [ ] Detalle de impermeabilización

---

## Recursos de consulta

| Carpeta | Contenido |
|---|---|
| `Cimentaciones superficiales/` | Zapatas, losas, capacidad portante |
| `Cimentaciones profundas/Pilotes/` | Cálculo de pilotes, DBSE-C |
| `Materiales y medios auxiliares/` | Hormigón, acero, encofrados, topografía |
| `Mecánica del suelo/` | Muros pantalla, empujes, consolidación |
