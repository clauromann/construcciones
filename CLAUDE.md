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
- **Empuje activo total:** ET = **25,78 Tn/ml** (Rankine, por estratos; incluye agua + sobrecarga q=1 Tn/m²)
  - Descomposición: E1=1,97 (arena ns) + E2=1,75 (arena sat) + Ew=15,68 (agua) + E3=3,64 (arcilla) + Eq1=1,21 + Eq2=1,53
  - Momento total: MT = **74,77 Tn·m/ml**; altura de aplicación dT = 2,90 m
- **Fuerzas verticales (B=4,00 m, primer tanteo):** ΣN = 57,22 Tn/ml; ΣMs = 131,76 Tn·m/ml → FS_vuelco = 1,76 < 1,80 → NO CUMPLE
- **Redimensionamiento → B=5,60 m** (Btalón=4,05 m) — **con subpresión triangular incluida:**
  - Subpresión: N_{s,w} = −15,68 Tn/ml (↑) a x=3,73 m; M_{s,w} = −58,54 Tn·m/ml
  - ΣN = **68,83 Tn/ml**; ΣMs = **204,04 Tn·m/ml**
  - FS_vuelco = **2,73** ≥ 1,80 ✅
  - FS_deslizamiento = **1,88** ≥ 1,50 ✅ (μ=0,30, c'A=26,32 Tn, Ep=0,97, Ep,w=0,5)
  - Hundimiento: x_R=1,88 m ≥ B/3=1,87 m (núcleo central ✅); σ1=3,71 kg/cm²; σ_med=1,23 kg/cm² ≤ 2,00 ✅
- **Capacidad portante** (est. 2, Brinch-Hansen, B₀=2,60 m predim): qh = **147,1 Tn/m²**, Fs = **10,9** ✅
  - Con B=5,60 m, Fs sólo mejora.
- **Asiento total estimado (B=5,60 m, estrato 4 arcillas margosas):** Si=2,97 cm + Sc=4,54 cm = **s=7,51 cm > 5 cm → PILOTAR**
  - Método edométrico (verificación): subcapa A (7,6 cm) + subcapa B (4,9 cm) = 12,5 cm → confirma necesidad de pilotes
- **Decisión cimentación muro:** cimentación mixta **zapata + pilotes CPI D=0,45 m** (L≈8 m hasta arcillas margosas)
  - Rcd=74,5 Tn > NT=68,80 Tn/ml ✅ · Asiento grupo Sg=0,66 cm (despreciable) ✅

### 4.4 Muro en ménsula — Estabilidad (B=5,60 m definitivo, con subpresión)
| Comprobación | Valor | Límite | Estado |
|---|---|---|---|
| Vuelco FS (B=4 m) | 1,76 | ≥ 1,80 | ❌ NO CUMPLE → ampliar |
| Vuelco FS (B=5,60 m) | **2,73** | ≥ 1,80 | ✅ |
| Deslizamiento FS | **1,88** | ≥ 1,50 | ✅ |
| Núcleo central x_R | 1,88 m | ≥ B/3=1,87 m | ✅ |
| Hundimiento σ_med | 1,23 kg/cm² | ≤ 2,00 | ✅ |

Geometría adoptada: e1=0,60 m (coronación), e2=0,75 m (base), **B=5,60 m**, hz=0,80 m, Bpunta=0,80 m, **Btalón=4,05 m**.

### 4.5 Cálculos estructurales ELU — Valores definitivos (de PDF Muro_pantalla.pdf)
- **Fuste — presiones activas (h_fuste=4,80 m sobre NF):** ET=20,64 Tn/ml; MT=58,16 Tn·m/ml; h_ef=2,82 m
  - Md = 1,50 × 58,16 = **87,24 Tn·m/ml** · Vd = 1,50 × 20,64 = **30,96 Tn = 303,72 kN/m**
- **Fuste armadura:** As_calc < As,min=10,44 cm²/m → **6φ16 c/16,7 cm** (As=12,06 cm²/m)
- **Cortante fuste:** VEd=303,72 kN > VRd,c=184,5 kN → **estribos 3 ramas φ10 c/195 mm** ✅
- **Zapata — presiones de contacto:** σ_max=14,45 Tn/m² (talón); σ_min=10,13 Tn/m² (puntera); sin despegue
- **Talón y puntera:** ambas rigen mínimo → **6φ16 c/16,7 cm** (As=12,06 cm²/m)
- **Total acero:** actualizar (cambio significativo respecto al cálculo anterior con estribos)

### 4.6 Pantalla (descartada — solo referencia)
- Longitud total: **24,92 m** (t=14,68 m empotramiento, D=17,62 m), e=0,75 m (10%×H)
  - Modelo 3 estratos con Ka3=0,390, Kp3=2,561
  - Sifonamiento: ic=0,92, i_real=0,272, FS=3,38 > 3 ✅; L_min=15,65 m
- **Motivo descarte:** lodos bentoníticos incompatibles con zona protegida + coste ~61% mayor (~849 kEUR vs ~334 kEUR)

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
- [x] **Predimensionamiento completo** — `03_predimensionamiento.tex` — 100%
  - Geometría definitiva (e1=0,60; e2=0,75; hz=0,80; B=4,40; Btalón=2,85; Bpunta=0,80)
  - Plano TikZ acotado con NF, empujes y dimensiones
  - Tabla de acero actualizada con valores definitivos del cálculo estructural
- [x] **Cálculos estructurales ELU** — `04_calculos_estructurales.tex` — 100% (reescrito según PDF)
  - Fuste: ET=20,64 Tn, MT=58,16 Tn·m, Md=87,24 Tn·m → **6φ16 c/16,7 cm** (As,min rige)
  - Cortante: VEd=303,72 kN > VRd,c=184,5 kN → **estribos 3 ramas φ10 c/195 mm**
  - Zapata: σ_max=14,45 Tn/m²; σ_min=10,13 Tn/m²; sin despegue
  - Talón y puntera: rigen mínimos → **6φ16 c/16,7 cm** ambas
- [x] Detalle impermeabilización arqueta (`02_cimentacion.tex` — parcial)
- [x] **Proceso constructivo** — `05_proceso_constructivo.tex` — 100%
  - 15 pasos detallados (replanteo → acabados), con 2 notabox
  - Tablas de cuadrillas y maquinaria completas
  - Volúmenes calculados: HM-15=66 m³, HA-30=1.187 m³ (zapata+fuste), encofrado=1.950 m²
- [x] **Presupuesto** — `06_presupuesto.tex` — 100% (actualizado con pilotes)
  - 11 partidas: exc=1596 m³, HA-30=1187 m³, enc fuste=1950 m², enc zap=240 m², imp=975 m², rell=2779 m³, pilotes=1200 m
  - **PEM = 473.094 €** · PEC (con IVA) = **681.208 €** · Coste unitario ≈ 3.154 €/ml
- [x] **Gantt** — `07_gantt.tex` — 100% (actualizado con pilotes como actividad D)
  - 14 actividades (A–N): pilotaje D=3 sem. insertado entre HM-15 y ferrallado zapata
  - Plazo total = **32 semanas** (≈8 meses); ruta crítica A-B-C-D-E-F-G-H-I-J-K-L-M-N
  - Diagrama TikZ pendiente de actualización manual por el usuario (columnas 1-30 → 1-32)

- [x] **Cimentación arqueta** — `03_arqueta/02_cimentacion.tex` — 100%
  - Sección transversal TikZ acotada (dimensiones, estratigrafía, N.F.)
  - Justificación cota −1,80 m (seco, Fs_flot=1,87, portante ok)
  - Tabla resumen cimentación + sistema impermeabilización HDPE + drenante

- [x] **Anexo A — Sondeo** — `anexos/A_sondeo.tex` — 100%
  - Columna estratigráfica TikZ (4 estratos + NF + profundidades + parámetros)
  - Leyenda tabular con cotas, γ, φ', c', E, ν
- [x] **Anexo B — Cálculos manuales** — `anexos/B_calculos_manuales.tex` — 100%
  - Predimensionamiento muro (reglas proporcionalidad)
  - Ka/Kp Rankine, diagrama de empujes, bloques 1-6
  - FS vuelco (1,97 ✅), FS deslizamiento (2,26 ✅)
  - Tanteo armadura fuste (As≈17,6 cm²/m vs. 16,08 cm²/m del cálculo detallado)
  - Arqueta: cargas, flotación (Fs=1,87 ✅), capacidad portante Terzaghi (Fs≈13,7 ✅)
  - Comparativa asientos Timoshenko vs. Steinbrenner

### Pendiente ⬜
- (ningún elemento pendiente — TFA completo)

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
│   │   ├── 03_predimensionamiento.tex   ← ✅ completo (B=5,60 m, TikZ acotado)
│   │   ├── 04_calculos_estructurales.tex← ✅ completo (reescrito según PDF)
│   │   ├── 05_proceso_constructivo.tex  ← ✅ completo
│   │   ├── 06_presupuesto.tex           ← ✅ completo (con pilotes, PEM=473k€)
│   │   └── 07_gantt.tex                 ← ✅ texto/tabla completo (TikZ pendiente manual)
│   └── 03_arqueta/
│       ├── 00_intro_arqueta.tex         ← datos dimensionales
│       ├── 01_calculos_geotecnicos.tex  ← ✅ cargas+flotación+cap.portante (FASE 1)
│       └── 02_cimentacion.tex           ← ✅ completo (TikZ sección + tabla cimentación)
└── anexos/
    ├── A_sondeo.tex                     ← ✅ completo (TikZ columna estratigráfica)
    └── B_calculos_manuales.tex          ← ✅ completo (tanteos muro + arqueta)
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
*Última actualización: 2026-05-12 — Revisión completa basada en Calculos_manuales/Muro_pantalla.pdf:*
*(1) Asientos corregidos: s=7,51 cm > 5 cm → PILOTAR (antes s=3,5 cm con B=2,60 m predim, incorrecto);*
*(2) Pilotes CPI D=0,45 m añadidos: Rcd=74,5 Tn, Sg=0,66 cm; sección nueva en 01_descripcion_opciones.tex;*
*(3) 02_calculos_geotecnicos.tex actualizado: asientos con B=5,60 m (E3=2527,8 Tn/m²) y decisión cimentación mixta;*
*(4) 04_calculos_estructurales.tex reescrito: ET=20,64 Tn, Md=87,24 Tn·m, estribos φ10 c/195 mm (antes sin estribos);*
*(5) Pantalla corregida: L=24,92 m (3 estratos, antes 14,71 m), sifonamiento verificado FS=3,38;*
*(6) 06_presupuesto.tex: pilotes añadidos (1200 m × 85 €/m), PEM=473k€, PEC=681k€;*
*(7) 07_gantt.tex: actividad D=Pilotaje (3 sem.) añadida, plazo total=32 sem., actividades renombradas E-N.*

*Entrada anterior: 2026-05-07 — Reorganización y corrección de cálculos basada en PDFs manuales:*
*(1) Empujes activos corregidos: ET=25,78 Tn/ml (antes 21,4) con desglose por estratos según cálculo manual;*
*(2) Secuencia redactada: N₄m → Empujes → Vuelco→NO CUMPLE → B=5m → N₅m → Vuelco → Desliz → Hundimiento;*
*(3) B definitivo cambia de 4,40 m a 5,00 m; Btalón de 2,85 m a 3,45 m;*
*(4) FS_vuelco 2,40→2,98; FS_desliz usa μ=tg(2φ'/3)=0,30; hundimiento con σadm=2 kg/cm²;*
*(5) Pantalla: longitud 11,8→14,71 m con ecuación cúbica de equilibrio de momentos;*
*(6) `01_descripcion_opciones.tex` reescrito completamente; `02_calculos_geotecnicos.tex` elimina sección de empujes; `03_predimensionamiento.tex` actualizado a B=5 m.*

*Entrada anterior: 2026-04-19 — Recálculo completo con B=4,40 m definitivo:*
*(1) tabla `tab:fuerzas_verticales` reescalada: ΣV 57,45→64,31; ΣMs 133,24→162,11 Tn·m/ml;*
*(2) FS vuelco 1,97→**2,40**; FS deslizamiento 2,26→**2,50**;*
*(3) excentricidad recalc e=0,73 m ≤ B/6=0,733 m (distribución trapezoidal sin despegue);*
*(4) asientos definitivos recalculados con q=14,62 Tn/m² → s_tot=**5,4 cm** (Steinbrenner neto 5,0 + consolidación 0,4);*
*(5) notabox "Excentricidad" reescrita para reflejar el cumplimiento con B=4,40;*
*(6) `tab:comparativa_opciones` y `supuestobox` de justificación actualizados con nuevos FS;*
*(7) nota de coherencia en CLAUDE.md sobre las presiones usadas en `04_calculos_estructurales.tex` (queda documentada para revisión posterior si se desea ajustar el armado del talón).*
*Pendiente: log de compilación del usuario para cerrar la revisión completa.*

*Entrada anterior (2026-04-18):*
*(a) label `subsec:tensiones_verticales` añadida en 02_calculos_geotecnicos.tex;*
*(b) ref rota `sec:calculos_geotecnicos_muro` corregida a `sec:muro_geotecnia` en Anexo B;*
*(c) error lógico `e ≤ B/6` → `e > B/6` corregido en 01_descripcion_opciones.tex;*
*(d) inconsistencia B=2,60 vs 4,40 resuelta con notabox aclaratoria y supuestobox actualizado;*
*(e) tabla de predimensionamiento con columna "Inicial / Definitivo".*
