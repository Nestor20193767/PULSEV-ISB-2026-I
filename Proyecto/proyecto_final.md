# 🧠 Detección de Estrés Académico mediante Análisis de HRV en Señales ECG

> Procesamiento de señal ECG · Algoritmo Pan-Tompkins · HRV · Machine Learning

[![Licencia: MIT](https://img.shields.io/badge/Licencia-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Estado del proyecto](https://img.shields.io/badge/Estado-En%20desarrollo-brightgreen)]()

## 📖 Introducción

En los últimos años, el estrés académico ha cobrado mayor relevancia como problema de salud en estudiantes universitarios, debido a la alta exigencia académica, la sobrecarga de actividades y la constante presión por el rendimiento. Todas estas condiciones generan un impacto negativo en los estudiantes: además de afectar su bienestar psicológico, también afectan las respuestas fisiológicas del organismo.

Desde una perspectiva fisiológica, el estrés académico activa el sistema nervioso autónomo, promoviendo un incremento de la actividad del sistema nervioso simpático y una disminución del sistema nervioso parasimpático [1]. Esto se traduce en una desregulación que se manifiesta principalmente en el sistema cardiovascular, produciendo variaciones en la frecuencia cardíaca y en el ritmo cardíaco [2].

Por lo tanto, en este contexto, la **variabilidad de la frecuencia cardíaca (HRV)** se ha convertido en un biomarcador no invasivo utilizado para evaluar el balance autonómico y la capacidad del organismo para adaptarse a situaciones de estrés [3]. Por otro lado, el **electrocardiograma (ECG)** es una herramienta fundamental en el análisis de señales biomédicas porque permite registrar la actividad eléctrica del corazón y obtener parámetros importantes para nuestro proyecto, como los intervalos **RR**, a partir de los cuales se calcula la HRV [4].

## 🎯 Problemática a Abordar

En el contexto universitario, se ha observado que los periodos de evaluación académica se asocian con cambios significativos en la HRV, lo que respalda su utilidad como indicador fisiológico del estrés académico. Para este análisis, la HRV suele evaluarse mediante métricas del dominio temporal y frecuencial, como se detalla en la siguiente tabla:

| Dominio     | Métrica | Descripción breve                              | Unidad | Relevancia clínica           |
|-------------|---------|------------------------------------------------|--------|------------------------------|
| **Temporal**  | SDNN    | Desv. estándar de intervalos NN                | ms     | Actividad autonómica global  |
| **Temporal**  | RMSSD   | Raíz cuadrática media de diferencias sucesivas | ms     | Actividad parasimpática      |
| **Temporal**  | pNN50   | % de intervalos que difieren >50 ms            | %      | Tono vagal                   |
| **Frecuencial** | LF      | Potencia de baja frecuencia (0.04–0.15 Hz)     | ms²    | Balance simpático-vagal      |
| **Frecuencial** | HF      | Potencia de alta frecuencia (0.15–0.40 Hz)     | ms²    | Actividad parasimpática      |
| **Frecuencial** | LF/HF   | Razón entre bandas                             | —      | Indicador de estrés autonómico |

*Tabla 1. Métricas estándar de HRV empleadas en la evaluación del estrés académico [5].*

Sin embargo, la confiabilidad de estas métricas depende directamente de la correcta estimación de los intervalos RR. Esto es especialmente importante porque incluso un solo latido mal detectado puede alterar de manera considerable los resultados de HRV, sobre todo en registros cortos, por lo que el control de artefactos y la calidad del procesamiento de la señal son aspectos fundamentales [6].

Aunque existen algoritmos de detección de picos R con buen desempeño en señales limpias o en bases de datos controladas, su rendimiento puede disminuir cuando la señal ECG presenta perturbaciones propias de entornos no controlados. En actividades académicas reales (escribir, teclear, cambiar de postura) pueden aparecer artefactos de movimiento, ruido muscular y variaciones en la línea base que modifican la morfología del ECG y dificultan la localización precisa de los complejos QRS [7], [8]. Además, en dispositivos vestibles no solo se requiere robustez frente al ruido, sino también baja complejidad computacional [7].

Asimismo, un filtrado insuficiente o una detección poco robusta puede generar falsos positivos, falsos negativos o errores en la localización temporal de los picos R, afectando directamente la estimación de los intervalos RR y, en consecuencia, la validez de las métricas de HRV. Finalmente, la literatura reciente muestra limitaciones metodológicas importantes en estudios con wearables en población universitaria [9], existiendo una brecha en el desarrollo de estrategias de procesamiento para entornos académicos cotidianos.

## 🚀 Propuesta de Solución

**Motor Algorítmico basado en Pan-Tompkins y Machine Learning Tradicional**

Para abordar la necesidad de extraer la HRV de manera confiable en entornos académicos, se propone el desarrollo de un pipeline algorítmico centrado en el procesamiento de señales y Machine Learning clásico. El flujo se divide en cuatro fases fundamentales:

| Fase | Componente | Descripción |
|------|------------|-------------|
| ① **Filtrado** | Pan-Tompkins (pre-procesado) | Filtro pasa-banda (5–15 Hz), diferenciación, cuadrado, integración ventana móvil |
| ② **Detección R** | Umbralización adaptativa | Localización precisa de picos R con umbral dinámico y lógica de refractividad |
| ③ **Extracción HRV** | Métricas temporales y espectrales | SDNN, RMSSD, pNN50 + LF, HF, LF/HF mediante Welch |
| ④ **Clasificación** | SVM / k-NN / Árbol de Decisión | Modelos ML clásicos entrenados con vector de características HRV para clasificar estado de estrés |

*Tabla 2. Pipeline algorítmico propuesto para la detección de estrés académico mediante HRV.*

### Fase 1: Filtrado y Detección de Picos R (Algoritmo de Pan-Tompkins)

El primer paso computacional utilizará el **algoritmo de Pan-Tompkins**, consolidado como un estándar eficiente para la detección de complejos QRS y base para extraer intervalos RR [11], [12]. Este método es altamente efectivo para atenuar artefactos de movimiento, ruido muscular y variaciones de línea base, asegurando una localización temporal precisa de los picos R con bajo costo computacional [13]. Se evaluarán también distintas estrategias de filtrado previo (Butterworth pasa-banda, Notch 60 Hz, filtros adaptativos) para optimizar el balance entre atenuación de ruido y preservación del QRS.

### Fase 2: Extracción de Características (HRV)

A partir de la detección exacta de los picos R, se extraerán los intervalos RR [11] y se calcularán dinámicamente las métricas estándar de HRV en dominio temporal (SDNN, RMSSD, pNN50) y espectral (LF, HF, LF/HF mediante método de Welch) [12], [13]. Se incluirá una etapa de corrección de artefactos para tratar latidos ectópicos y outliers.

### Fase 3: Clasificación de Estados mediante Machine Learning

Las características extraídas alimentarán modelos de **Machine Learning tradicional** (SVM, k-NN, Árbol de Decisión), evitando redes neuronales profundas costosas. La literatura respalda la robustez de combinar Pan-Tompkins con estos clasificadores para categorización de señales cardiovasculares [11], [13], [14], logrando alta precisión, modelos interpretables y rápida inferencia, viables para despliegue en wearables.

## 📅 Plan de Actividades

El desarrollo del proyecto se organiza en **seis fases secuenciales** a lo largo de **15 semanas**, asegurando un avance estructurado desde la revisión teórica hasta la entrega del informe final.

### Diagrama de Gantt

![*Figura 1. Diagrama de Gantt del plan de actividades (15 semanas).*](https://github.com/Nestor20193767/PULSEV-ISB-2026-I/blob/main/Proyecto/imagenes/plan_actividades_gantt.png)
*Figura 1. Diagrama de Gantt del plan de actividades (15 semanas).*

### Descripción de Fases

- **Fase 1 — Revisión y Preparación (Semanas 1–3)**: Revisión sistemática de literatura, definición de métricas (sensibilidad, especificidad, F1-score, DER) y selección de bases de datos públicas (MIT-BIH Arrhythmia Database, MIT-BIH Noise Stress Test Database).

- **Fase 2 — Procesamiento de Señal ECG (Semanas 3–6)**: Implementación del pipeline de filtrado y algoritmo Pan-Tompkins. Evaluación de estrategias de filtrado y validación de detección de picos R.

- **Fase 3 — Extracción de HRV (Semanas 6–8)**: Cálculo de intervalos RR, métricas temporales (SDNN, RMSSD, pNN50) y frecuenciales (LF, HF, LF/HF) mediante periodograma de Welch. Implementación de corrección de artefactos (regla de Malik, interpolación cúbica).

- **Fase 4 — Machine Learning (Semanas 8–11)**: Construcción del dataset de características HRV, entrenamiento de SVM, k-NN y Árbol de Decisión, validación cruzada k-fold (k=5/10), ajuste de hiperparámetros y comparación mediante curvas ROC y F1-score.

- **Fase 5 — Integración y Pruebas (Semanas 11–13)**: Integración del pipeline completo (Filtrado → Detección R → HRV → Clasificación), pruebas end-to-end con señales simulando estrés académico, medición de eficiencia computacional (tiempo, memoria).

- **Fase 6 — Documentación y Cierre (Semanas 13–15)**: Redacción del informe técnico, elaboración de figuras/tablas, preparación de la presentación final y entrega de todos los entregables.

## 📚 Referencias

[1] Top Doctors, *Fisioterapia y sistema nervioso autónomo: el papel clave de la variabilidad cardiaca (HRV)*, 2025. [En línea]. Disponible: https://www.topdoctors.es/articulos-medicos/fisioterapia-y-sistema-nervioso-autonomo-el-papel-clave-de-la-variabilidad-cardiaca-hrv/

[2] Revista Colombiana de Cardiología, *Variabilidad de la frecuencia cardiaca como factor predictor de enfermedad cardiovascular*, Elsevier, 2019. [En línea]. Disponible: https://www.sciencedirect.com/science/article/pii/S0120563319300683

[3] SciELO Colombia, *Variabilidad de la frecuencia cardiaca como factor predictor*, 2019. [En línea]. Disponible: https://www.scielo.org.co/scielo.php?pid=S0120-56332019000400205&script=sci_arttext

[4] Metaciclista, *Variabilidad de la frecuencia cardiaca (HRV)*, 2024. [En línea]. Disponible: https://www.metaciclista.cl/conceptos/variabilidad-frecuencia-cardiaca-hrv

[5] S. Hammoud et al., *Stress and Heart Rate Variability during University Final Examination among Lebanese Students*, Behavioral Sciences, vol. 9, no. 1, Art. no. 3, 2019. doi: 10.3390/bs9010003

[6] F. Shaffer, Z. M. Meehan, and C. L. Zerr, *A Critical Review of Ultra-Short-Term Heart Rate Variability Norms Research*, Frontiers in Neuroscience, vol. 14, Art. no. 594880, 2020. doi: 10.3389/fnins.2020.594880

[7] R. A. Felix et al., *Fast Parabolic Fitting: An R-Peak Detection Algorithm for Wearable ECG Devices*, Sensors, vol. 23, no. 21, Art. no. 8796, 2023. doi: 10.3390/s23218796

[8] M. Khalili et al., *Motion Artifacts in Capacitive ECG Monitoring Systems: A Review of Existing Models and Reduction Techniques*, Medical & Biological Engineering & Computing, vol. 62, pp. 3599-3622, 2024. doi: 10.1007/s11517-024-03165-1

[9] A. Sathyanarayana et al., *Examining the Use of Consumer Wearable Devices and Digital Tools for Stress Measurement in College Students: Scoping Review of Methods*, JMIR mHealth and uHealth, vol. 14, Art. no. e64144, 2026. doi: 10.2196/64144

[11] I. N. Martinez, *Clasificador SVM usando Pan-Tompkins para detección de arritmias*, Repositorio Institucional UNAD, Colombia. [En línea]. Disponible: https://repository.unad.edu.co/jspui/bitstream/10596/56472/1/inmartinezt.pdf

[12] Autor del estudio (Pendiente), *Clasificación automática de latidos de ECG*, Repositorio Institucional UdeC, Chile.

[13] Autor del TFG (Pendiente), *Extracción de características y clasificación de latidos ECG*, Trabajo de Fin de Grado, RiuNet, UPV, España.

[14] Autor del estudio (Pendiente), *Sistemas de monitoreo portátil cardiaco con métodos de aprendizaje automático*, Dialnet, Universidad de La Rioja.

---


