# CLAUDE.md — Contexto del proyecto TFA (Obra Civil EDAR)
> **Propósito:** Este fichero es cargado automáticamente por Claude Code al inicio de cada sesión.
> Contiene todo el contexto necesario para continuar el trabajo sin releer el proyecto desde cero.
> **REGLA DE EQUIPO: actualizar este fichero al final de cada sesión de trabajo.**

---

## 1. Resumen del proyecto

TFA de la asignatura *Construcción e Instalaciones Industriales* (MII, Loyola, 2025-2026).
Se proyecta la obra civil de una EDAR con dos elementos:
- **Muro de contención en ménsula** (H = 7,3 m, L = 150 ml) para planta fotovoltaica.
- **Arqueta de fangos mezcla** (4 × 3 × 3,5 m interior) como nuevo depósito.

El documento LaTeX está en `TFA/`. Compilar con `pdflatex main.tex` desde esa carpeta.

---

## 2. Parámetros del grupo (NO cambiar)

| Parámetro | Valor | Origen |
|---|---|---|
| X | 4 | 1ª cifra media DNIs |
| Y | 3 | 2ª cifra media DNIs |
| Desnivel muro H | **7,3 m** | (X+3, Y) |
| Longitud muro | **150 ml** | enunciado |
| Arqueta L × B × H | **4 × 3 × 3,5 m** | interior |
| Espesor paredes/losa arqueta | **0,30 m** | adoptado |
| Sobrecarga tráfico | **q = 1 Tn/m²** | enunciado |
| γ_fango | **1,1 Tn/m³** | enunciado |
| Sulfatos suelo | **3 500 mg SO₄²⁻/kg** | condicionante |
| Zona protegida | **Sí** | condicionante medioambiental |

---

## 3. Datos geotécnicos — Sondeo 1 (usar siempre estos valores)

**Nivel freático (N.F.): −2,50 m** (profundidad absoluta desde trasdós/rasante).

| Estrato | Cotas (m) | γ (Tn/m³) | φ' (°) | c' (kg/cm²) | Cu (kg/cm²) | E (MPa) | ν |
|---|---|---|---|---|---|---|---|
| Arena limosa (no sat.) | 0,00 → −2,50 | 1,82 | 29 | 0 | 0 | 6,894 | 0,25 |
| Arena limosa (sat.) | −2,50 → −3,50 | 1,98 | 29 | 0 | 0 | 6,894 | 0,25 |
| Arcillas versicolores | −3,50 → −8,00 | 1,78 | 25,2 | 0,47 | 1,00 | 12,000 | 0,30 |
| Arcillas margosas | −8,00 → −25,00 | 1,92 | 26 | 0,78 | 1,52 | 25,278 | 0,25 |

Densidades sumergidas: γ_sum = γ_sat − 1,00 Tn/m³ → 0,98 / 0,78 / 0,92 Tn/m³ respectivamente.

---

## 4. Resultados calculados — NO recalcular, solo referenciar

### 4.1 Tensiones verticales efectivas (Sondeo 1)
| Cota (m) | σ_v (Tn/m²) | u (Tn/m²) | σ'_v (Tn/m²) |
|---|---|---|---|
| 0,00 | 0,00 | 0,00 | **0,00** |
| −2,50 | 4,55 | 0,00 | **4,55** |
| −3,50 | 6,53 | 1,00 | **5,53** |
| −8,00 | 14,54 | 5,50 | **9,04** |
| −25,00 | 47,30 | 22,50 | **24,80** |

### 4.2 Coeficientes Rankine
| Estrato | φ' | Ka | Kp |
|---|---|---|---|
| Arena limosa (est. 1) | 29° | **0,347** | **2,886** |
| Arcillas versicolores (est. 2) | 25,2° | **0,402** | **2,490** |

### 4.3 Muro de contención — Resultados clave
- **Empuje activo total:** Ea = **21,4 Tn/ml** (incluye agua + sobrecarga q=1 Tn/m²)
- **Empuje pasivo** (Df=1,0 m): Ep = 2,63 Tn/ml
- **Capacidad portante** (est. 2, Brinch-Hansen, B=2,60 m): qh = **147,1 Tn/m²**, Fs = **10,9** ✅
- **Asiento total estimado:** s ≈ **3,5 cm** (Steinbrenner + consolidación) ✅
- **Decisión cimentación muro:** zapata corrida superficial, B=4,00 m, hz=0,80 m

### 4.4 Muro en ménsula — Estabilidad (Fase 2)
| Comprobación | Valor | Límite | Estado |
|---|---|---|---|
| Vuelco (FS) | **1,97** | ≥ 1,50 | ✅ |
| Deslizamiento (FS) | **2,26** | ≥ 1,50 | ✅ |
| Hundimiento (FS) | **10,9** | ≥ 3,00 | ✅ |
| Excentricidad | corregida con B=4,40 m | e < B/6 | ✅ |

Geometría adoptada: e1=0,60 m (coronación), e2=0,75 m (base), B=4,40 m, hz=0,80 m, Bpunta=0,80 m, Btalón=2,85 m.

### 4.5 Pantalla (descartada — solo referencia)
- Longitud necesaria (anclada): **11,8 m** (d=4,5 m clava en est. 2-3)
- Fuerza de anclaje: T = 4,9 Tn/ml
- **Motivo descarte:** lodos bentoníticos incompatibles con zona protegida + coste 38% mayor

### 4.6 Arqueta — Resultados clave
- **Carga total:** P = 101,95 Tn → q = **6,16 Tn/m²** sobre losa
- **Flotación** (NF en rasante, arqueta vacía): Fs_flot = **1,87 > 1,05** ✅
- **Capacidad portante** (est. 1a, Brinch-Hansen): qh = **91,05 Tn/m²**, Fs = **14,8** ✅
- **Asiento total:** s ≈ **7,7 cm** (algo alto → discusión en sección 3.1)
- **Decisión cimentación arqueta:** losa de cimentación 4,60×3,60 m, e=0,30 m, cota −1,80 m

---

## 5. Estado actual del trabajo

### Completado ✅
- [x] **Fase 1 — Geotecnia completa** (tensiones, Rankine, cap. portante, asientos, decisión cimentación)
  - `TFA/chapters/02_muro/02_calculos_geotecnicos.tex` — 100% completo
  - `TFA/chapters/03_arqueta/01_calculos_geotecnicos.tex` — 100% completo
- [x] **Fase 2 — Comparativa muro ménsula vs. pantalla + justificación**
  - `TFA/chapters/02_muro/01_descripcion_opciones.tex` — 100% completo
- [x] Portada, Introducción, datos del sondeo (`01_introduccion.tex`)
- [x] Intro muro (`00_intro_muro.tex`), intro arqueta (`00_intro_arqueta.tex`)
- [x] Predimensionamiento materiales y clase exposición (`03_predimensionamiento.tex` — parcial)
- [x] Detalle impermeabilización arqueta (`02_cimentacion.tex` — parcial)

### Pendiente ⬜
- [ ] **`02_muro/03_predimensionamiento.tex`** — Completar geometría definitiva + plano TikZ
- [ ] **`02_muro/04_calculos_estructurales.tex`** — ELU fuste (flexión + cortante) y zapata (punzonamiento, flexión)
- [ ] **`02_muro/05_proceso_constructivo.tex`** — Descripción + medios humanos/maquinaria
- [ ] **`02_muro/06_presupuesto.tex`** — Mediciones y precios unitarios
- [ ] **`02_muro/07_gantt.tex`** — Diagrama Gantt con pgfgantt
- [ ] **`03_arqueta/02_cimentacion.tex`** — Completar plano acotado TikZ + cota cimentación
- [ ] **`anexos/A_sondeo.tex`** — Insertar figura escaneada/TikZ del sondeo
- [ ] **`anexos/B_calculos_manuales.tex`** — Desarrollar tanteos manuales

---

## 6. Mapa de ficheros LaTeX

```
TFA/
├── main.tex                  ← entrada; compila pdflatex main.tex
├── preamble.tex              ← paquetes + \paramX=4, \paramY=3
├── referencias.bib
├── chapters/
│   ├── 00_portada.tex
│   ├── 01_introduccion.tex   ← sondeo + tabla estratigráfica (tab:sondeo1)
│   ├── 02_muro/
│   │   ├── 00_intro_muro.tex            ← descripción encargo
│   │   ├── 01_descripcion_opciones.tex  ← ✅ ménsula vs pantalla (FASE 2)
│   │   ├── 02_calculos_geotecnicos.tex  ← ✅ empujes+cap.portante+asientos (FASE 1)
│   │   ├── 03_predimensionamiento.tex   ← ⬜ pendiente
│   │   ├── 04_calculos_estructurales.tex← ⬜ pendiente
│   │   ├── 05_proceso_constructivo.tex  ← ⬜ pendiente
│   │   ├── 06_presupuesto.tex           ← ⬜ pendiente
│   │   └── 07_gantt.tex                 ← ⬜ pendiente
│   └── 03_arqueta/
│       ├── 00_intro_arqueta.tex         ← datos dimensionales
│       ├── 01_calculos_geotecnicos.tex  ← ✅ cargas+flotación+cap.portante (FASE 1)
│       └── 02_cimentacion.tex           ← ⬜ completar plano TikZ
└── anexos/
    ├── A_sondeo.tex                     ← ⬜ pendiente figura
    └── B_calculos_manuales.tex          ← ⬜ pendiente tanteos
```

---

## 7. Metodología de cálculo adoptada (no cambiar sin consenso)

| Cálculo | Método | Referencia |
|---|---|---|
| Tensiones verticales efectivas | Terzaghi: σ'v = σv − u | Apuntes Mecánica Suelos II |
| Empuje activo/pasivo | Rankine (Ka, Kp) + separación efectiva/agua | Apuntes Mecánica Suelos II |
| Capacidad portante | Brinch-Hansen (drenada, LP) | Apuntes Cim. Superficiales |
| γk con NF bajo zapata | Peso ponderado (Caso II, Sec. 136) | Apuntes Cim. Superficiales |
| Asiento inmediato | Steinbrenner (ROM fig. 3.5.6) | Casos prácticos clase |
| Asiento consolidación | Módulo edométrico Eed de E y ν | Apuntes Cim. Superficiales |
| Vuelco/deslizamiento muro | Momentos respecto a punta zapata | Apuntes Mecánica Suelos |
| Flotación arqueta | Peso_HA / F_Arquímedes ≥ 1,05 | Clase |

**FS mínimos usados:** hundimiento ≥ 3,0 · vuelco ≥ 1,5 · deslizamiento ≥ 1,5 · flotación ≥ 1,05

---

## 8. Materiales y clase de exposición (ya definidos)

| Elemento | Hormigón | Cemento | Recub. nominal |
|---|---|---|---|
| Muro fuste + zapata | HA-30/B/20/IIb+QA | SR (CEM I 42,5 SR) | 45 mm |
| Hormigón limpieza | HM-15 | — | — |
| Losa arqueta + paredes | HA-30/B/20/IIb+QA | SR | 45 mm |
| Acero pasivo | B 500 SD | — | — |

---

## 9. Comandos LaTeX personalizados (preamble.tex)

```latex
\alturaDesnivelMuro  → 7,3
\largoArqueta        → 4
\anchoArqueta        → 3
\alturaArqueta       → 3,5
\kNm  \kNmm  \MPa    → unidades SI
\resultado{x}        → \boxed{x}  (resaltar resultado final)
% Entornos: notabox / supuestobox / resultadobox
```

---

## 10. Cómo actualizar este fichero (protocolo de equipo)

Al terminar cada sesión de trabajo, actualizar las secciones 5 (estado) con:
- Mover ítems de ⬜ a ✅ según lo completado.
- Añadir resultados nuevos en la sección 4.
- Si se cambia geometría o parámetros, actualizar sección 4.

**Hacer commit del CLAUDE.md junto con los ficheros .tex modificados:**
```bash
git add TFA/chapters/... CLAUDE.md
git commit -m "feat: descripción del cambio"
git push
```

---
*Última actualización: 2026-04-17 — Fases 1 y 2 completas (geotecnia + comparativa estructural)*
