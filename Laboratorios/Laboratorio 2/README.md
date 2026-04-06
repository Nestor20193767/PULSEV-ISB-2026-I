# PULSEV-ISB-2026-I
## Introducción a Señales Biomédicas

> **Informe N°1** | Universidad Peruana Cayetano Heredia — Ingeniería Biomédica | 2026-I

---

## 👥 Integrantes — Grupo N°3

| Nombre | DNI |
|--------|-----|
| Milagros Natalie Sante Huaynates | 73610573 |
| Ana Cristina Angulo Chavez | 70199532 |
| Nestor Manuel Allende Heredia | 74124434 |
| Nataly Marcela Deledesma Romero | 71865405 |
| Luis Bryan Loayza Arroyo | 72483504 |

---

## 📌 Introducción

En los últimos años, el estrés académico ha cobrado mayor relevancia como problema de salud en estudiantes universitarios, debido a la alta exigencia académica, la sobrecarga de actividades y la constante presión por el rendimiento. Todas estas condiciones generan un impacto negativo en los estudiantes: afectan su bienestar psicológico y también las respuestas fisiológicas del organismo.

Desde una perspectiva fisiológica, el estrés académico activa el sistema nervioso autónomo, promoviendo el incremento de la actividad del sistema nervioso simpático y una disminución del parasimpático [1]. Esta desregulación se manifiesta principalmente en el sistema cardiovascular, produciendo variaciones en la frecuencia cardíaca y el ritmo cardíaco [2].

La variabilidad de la frecuencia cardíaca (**HRV**) se ha convertido en un biomarcador no invasivo utilizado para evaluar el balance autonómico y la capacidad del organismo para adaptarse al estrés [3]. El electrocardiograma (**ECG**) permite registrar la actividad eléctrica del corazón y obtener los intervalos RR, a partir de los cuales se calcula la HRV [4].

---

## ⚠️ Problemática

Los periodos de evaluación académica se asocian con cambios significativos en la HRV, evaluada mediante:

**Dominio temporal:**
- **SDNN** — Desviación estándar de los intervalos NN
- **RMSSD** — Raíz cuadrática media de las diferencias sucesivas entre intervalos RR
- **pNN50** — Porcentaje de intervalos sucesivos que difieren en más de 50 ms

**Dominio frecuencial:**
- **LF** — Baja frecuencia
- **HF** — Alta frecuencia
- **LF/HF** — Razón entre ambas bandas [5]

La confiabilidad de estas métricas depende directamente de la correcta estimación de los intervalos RR. Incluso un solo latido mal detectado puede alterar considerablemente los resultados, especialmente en registros cortos [6].

En entornos académicos reales (escribir, teclear, cambiar de postura), pueden aparecer:
- Artefactos de movimiento
- Ruido muscular
- Variaciones en la línea base

Estos factores modifican la morfología del ECG y dificultan la localización precisa de los complejos QRS [7][8]. Los dispositivos wearables también requieren **baja complejidad computacional** por sus restricciones de memoria y energía [7].

> 📖 Una revisión reciente encontró que una parte considerable de los estudios depende de bases de datos obtenidas en condiciones controladas, limitando la generalización a escenarios reales [9].

---

## 💡 Propuesta de Solución

### Motor Algorítmico: Pan-Tompkins + Machine Learning Tradicional

Se propone un **pipeline algorítmico en tres fases** para extraer HRV de manera confiable en entornos académicos:

```
Señal ECG cruda
      │
      ▼
┌──────────────────────────┐
│  FASE 1                  │
│  Filtrado +              │
│  Algoritmo Pan-Tompkins  │  ──► Detección precisa de picos R
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│  FASE 2                  │
│  Extracción de HRV       │  ──► Intervalos RR → SDNN, RMSSD, pNN50, LF, HF
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│  FASE 3                  │
│  Clasificación ML        │  ──► SVM / k-NN / Árbol de Decisión
└──────────────────────────┘
```

### 🔧 Fase 1 — Filtrado y Detección de Picos R (Pan-Tompkins)

El algoritmo de **Pan-Tompkins** es un estándar eficiente para la detección de complejos QRS y la extracción de intervalos RR [11][12]. Atenúa artefactos de movimiento, ruido muscular y variaciones de línea base propios de la actividad del usuario [13], garantizando una localización temporal precisa con costo computacional mínimo.

### 📊 Fase 2 — Extracción de Características (HRV)

A partir de los intervalos RR se calcularán dinámicamente:

| Dominio | Métricas |
|---------|----------|
| Temporal | SDNN, RMSSD, pNN50 |
| Frecuencial | LF, HF, LF/HF (periodograma de Welch) |

### 🤖 Fase 3 — Clasificación con Machine Learning

| Modelo | Ventaja principal |
|--------|-------------------|
| **SVM** | Alta precisión en espacios de alta dimensión |
| **k-NN** | Simple, interpretable y sin entrenamiento costoso |
| **Árbol de Decisión** | Visualizable y explicable |

La literatura avala la combinación **Pan-Tompkins + SVM/k-NN** para clasificación cardiovascular con alta precisión y bajo costo computacional [11][13][14].

---

## 📅 Plan de Actividades (15 semanas)

| Fase | Actividad | Semanas |
|:----:|-----------|:-------:|
| 1 | Revisión de literatura y preparación | 1 – 3 |
| 2 | Procesamiento de señal ECG (Pan-Tompkins) | 3 – 6 |
| 3 | Extracción de métricas HRV | 6 – 8 |
| 4 | Entrenamiento de modelos ML | 8 – 11 |
| 5 | Integración y pruebas end-to-end | 11 – 13 |
| 6 | Documentación y entrega final | 13 – 15 |

### Descripción de Fases

**🔹 Fase 1 — Revisión y Preparación (Sem. 1–3)**
Revisión sistemática de literatura sobre HRV, procesamiento de ECG y Pan-Tompkins. Definición de métricas de evaluación (sensibilidad, especificidad, F1-score, DER). Selección de bases de datos: **MIT-BIH Arrhythmia Database** y **MIT-BIH Noise Stress Test Database**.

**🔹 Fase 2 — Procesamiento de Señal ECG (Sem. 3–6)**
Implementación del pipeline de filtrado y programación del algoritmo Pan-Tompkins. Comparación de estrategias: Butterworth, Notch, filtro de derivada. Validación sobre bases de datos con métricas de la Fase 1.

**🔹 Fase 3 — Extracción de HRV (Sem. 6–8)**
Cálculo de métricas temporales (SDNN, RMSSD, pNN50) y frecuenciales (LF, HF, LF/HF) mediante periodograma de Welch. Módulo de detección y corrección de artefactos en intervalos RR (regla de Malik, interpolación cúbica).

**🔹 Fase 4 — Machine Learning (Sem. 8–11)**
Construcción del dataset de características HRV. Entrenamiento de SVM, k-NN y Árbol de Decisión. Validación cruzada k-fold (k=5 o 10). Ajuste de hiperparámetros y comparación mediante curvas ROC y F1-score.

**🔹 Fase 5 — Integración y Pruebas (Sem. 11–13)**
Integración del pipeline completo (Filtrado → Detección R → HRV → Clasificación) y pruebas end-to-end con señales que simulen estrés académico. Medición de eficiencia computacional (tiempo por segmento, uso de memoria).

**🔹 Fase 6 — Documentación y Cierre (Sem. 13–15)**
Redacción del informe técnico completo con resultados, discusión y conclusiones. Elaboración de figuras, tablas y visualizaciones finales. Preparación y entrega de la presentación final.

---

## 📚 Referencias

[1] Top Doctors, "Fisioterapia y sistema nervioso autónomo: el papel clave de la variabilidad cardiaca (HRV)," 2025. Disponible: https://www.topdoctors.es/articulos-medicos/fisioterapia-y-sistema-nervioso-autonomo-el-papel-clave-de-la-variabilidad-cardiaca-hrv/

[2] Revista Colombiana de Cardiología, "Variabilidad de la frecuencia cardiaca como factor predictor de enfermedad cardiovascular," Elsevier, 2019. Disponible: https://www.sciencedirect.com/science/article/pii/S0120563319300683

[3] SciELO Colombia, "Variabilidad de la frecuencia cardiaca como factor predictor," 2019. Disponible: https://www.scielo.org.co/scielo.php?pid=S0120-56332019000400205&script=sci_arttext

[4] Metaciclista, "Variabilidad de la frecuencia cardiaca (HRV)," 2024. Disponible: https://www.metaciclista.cl/conceptos/variabilidad-frecuencia-cardiaca-hrv

[5] S. Hammoud et al., "Stress and Heart Rate Variability during University Final Examination among Lebanese Students," *Behavioral Sciences*, vol. 9, no. 1, 2019, doi: 10.3390/bs9010003.

[6] F. Shaffer, Z. M. Meehan, and C. L. Zerr, "A Critical Review of Ultra-Short-Term Heart Rate Variability Norms Research," *Frontiers in Neuroscience*, vol. 14, 2020, doi: 10.3389/fnins.2020.594880.

[7] R. A. Félix et al., "Fast Parabolic Fitting: An R-Peak Detection Algorithm for Wearable ECG Devices," *Sensors*, vol. 23, no. 21, 2023, doi: 10.3390/s23218796.

[8] M. Khalili et al., "Motion Artifacts in Capacitive ECG Monitoring Systems," *Medical & Biological Engineering & Computing*, vol. 62, pp. 3599–3622, 2024, doi: 10.1007/s11517-024-03165-1.

[9] A. Sathyanarayana et al., "Examining the Use of Consumer Wearable Devices for Stress Measurement in College Students," *JMIR mHealth and uHealth*, vol. 14, 2026, doi: 10.2196/64144.

[11] I. N. Martínez, "Clasificador SVM usando Pan-Tompkins para detección de arritmias," UNAD. Disponible: https://repository.unad.edu.co/jspui/bitstream/10596/56472/1/inmartinezt.pdf

[12] "Clasificación automática de latidos de ECG," UdeC. Disponible: https://repositorio.udec.cl/bitstreams/b4d63579-6925-48cd-8f21-2d3d6755b371/download

[13] "Extracción de características y clasificación de latidos ECG," UPV. Disponible: https://riunet.upv.es/bitstream/handle/10251/159880/DNI_TFG-M_15948934222327436714347389687137.pdf

[14] "Sistemas de monitoreo portátil cardíaco con ML," Dialnet. Disponible: https://dialnet.unirioja.es/descarga/articulo/6846301.pdf
