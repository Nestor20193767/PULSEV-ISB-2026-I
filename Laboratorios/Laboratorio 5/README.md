# Laboratorio N.º 5: Adquisición y análisis de señales ECG en distintas condiciones fisiológicas

## 1. Introducción

El electrocardiograma (ECG) es una técnica no invasiva utilizada para registrar la actividad eléctrica del corazón desde la superficie corporal. Debido a su carácter rápido, accesible y de bajo costo, continúa siendo una herramienta fundamental en la evaluación clínica, permitiendo detectar diversas patologías cardiovasculares [1]. Esta señal se origina por la propagación de potenciales de acción a través del tejido cardíaco, lo que da lugar a componentes característicos como la onda P, el complejo QRS y la onda T, asociados a los procesos de despolarización y repolarización del ciclo cardíaco [2].

Para la adquisición del ECG se emplean sistemas de derivaciones que permiten observar la actividad eléctrica desde distintas direcciones. Entre estos, destacan las derivaciones bipolares propuestas por Willem Einthoven (I, II y III). La orientación de estas derivaciones influye en la morfología y amplitud de la señal registrada, así como en su interpretación [3].

En este laboratorio se adquirieron señales ECG utilizando el sistema BITalino y electrodos superficiales, con el objetivo de analizar la variación de la señal bajo distintas condiciones fisiológicas: reposo, hiperventilación, actividad física y contención de la respiración. Asimismo, se evaluó el efecto de factores experimentales como la ubicación de los electrodos, el tipo de derivación y la presencia de artefactos por movimiento, los cuales afectan la calidad y características de la señal adquirida.

---

## 2. Objetivos

### Objetivo general

Adquirir y analizar señales ECG en diferentes condiciones fisiológicas, comparando los cambios observados entre reposo, hiperventilación, post-ejercicio y apnea voluntaria.

### Objetivos específicos

- Registrar señales ECG utilizando las derivaciones I, II y III.
- Comparar la señal basal con señales adquiridas después de hiperventilación, actividad física y contención de la respiración.
- Identificar cambios en la frecuencia cardíaca, intervalos R-R, amplitud y calidad visual de la señal.
- Discutir la coherencia fisiológica de los resultados obtenidos con base en literatura científica reciente.

---

## 3. Metodología

### 3.1. Componentes utilizados

| Componente | Descripción |
|---|---|
| BITalino (r)evolution | Sistema de adquisición de señales biomédicas |
| Sensor ECG BITalino | Módulo utilizado para adquirir la señal electrocardiográfica |
| Electrodos Ag/AgCl desechables | Electrodos superficiales pregelificados |
| Computadora | Equipo utilizado para visualizar, registrar y almacenar las señales |
| OpenSignals | Software empleado para la adquisición de datos |
| Cables de conexión | Conexión entre electrodos, sensor ECG y BITalino |

---

### 3.2. Colocación de electrodos

Se trabajó con configuraciones basadas en las derivaciones de Einthoven:

| Derivación | Configuración general | Descripción |
|---|---|---|
| Derivación I | RA (-) a LA (+) | Mide la diferencia de potencial entre el lado derecho e izquierdo superior del cuerpo |
| Derivación II | RA (-) a LL (+) | Mide la actividad eléctrica desde el lado superior derecho hacia la región inferior izquierda |
| Derivación III | LA (-) a LL (+) | Mide la actividad eléctrica desde el lado superior izquierdo hacia la región inferior izquierda |

Los electrodos se colocaron en una disposición tipo **clavícula-clavícula-cadera**, usando la cadera o cresta ilíaca como referencia. Esta configuración permite aproximar las derivaciones de Einthoven y, al colocar los electrodos cerca de zonas óseas, ayuda a reducir parte del ruido asociado a actividad muscular.

Agregar imagen:

```markdown
![Esquema de derivaciones ECG](media/derivaciones_einthoven.jpg)
```

---

### 3.3. Actividades realizadas

El laboratorio se dividió en tres actividades principales.

---

#### Actividad 1: Señal basal e hiperventilación

Primero se adquirió una señal ECG basal durante **30 segundos** con el usuario en reposo y con los electrodos colocados en las tres derivaciones.

Luego, el usuario realizó una fase breve de **hiperventilación**. Inmediatamente después se registró la señal ECG durante **30 segundos** en cada una de las tres derivaciones:

1. Derivación I  
2. Derivación II  
3. Derivación III  

Este procedimiento se repitió **dos veces**, con el objetivo de comparar la variabilidad entre repeticiones y entre derivaciones.

| Condición | Derivación | Duración | Repeticiones |
|---|---|---:|---:|
| Basal | I | 30 s | 1 |
| Hiperventilación | I | 30 s | 2 |
| Hiperventilación | II | 30 s | 2 |
| Hiperventilación | III | 30 s | 2 |

Agregar evidencia:

```markdown
![Actividad de hiperventilación sin rostro](media/hiperventilacion.jpg)
```

---

#### Actividad 2: Señal basal y ejercicio físico

En la segunda actividad se adquirió primero una señal basal del usuario en reposo. Luego, el usuario realizó **10 minutos de actividad física**, subiendo y bajando escaleras.

Al finalizar el ejercicio, se registró la señal ECG durante **30 segundos** en cada derivación, de forma consecutiva:

1. Derivación I  
2. Derivación II  
3. Derivación III  

| Condición | Derivación | Duración |
|---|---|---:|
| Basal | I | 30 s |
| Post-ejercicio | I | 30 s |
| Post-ejercicio | II | 30 s |
| Post-ejercicio | III | 30 s |

Agregar evidencia:

```markdown
![Actividad física en escaleras sin rostro](media/escaleras.gif)
```

---

#### Actividad 3: Contención de la respiración

En la tercera actividad, el usuario realizó una contención voluntaria de la respiración durante aproximadamente **20 segundos**. Durante esta condición se adquirió la señal ECG en las tres derivaciones.

| Condición | Derivación | Duración aproximada |
|---|---|---:|
| Apnea voluntaria | I | 20-30 s |
| Apnea voluntaria | II | 20-30 s |
| Apnea voluntaria | III | 20-30 s |

Agregar evidencia:

```markdown
![Registro durante apnea voluntaria sin rostro](media/apnea.jpg)
```

---

### 3.5. Procesamiento de la señal ECG

Las señales fueron exportadas desde OpenSignals en formato `.txt` y procesadas en Python mediante Google Colab. 
El flujo general de procesamiento fue el siguiente:

1. Carga de archivos `.txt` exportados desde OpenSignals.
2. Lectura de la señal mediante `opensignalsreader`.
3. Detección automática del canal válido.
4. Centrado de la señal mediante resta de la media.
5. Aplicación de filtro notch a 60 Hz para reducir interferencia eléctrica.
6. Aplicación de filtro pasa banda de 0.5 a 40 Hz para conservar los componentes principales del ECG.
7. Detección de picos R con `find_peaks`.
8. Corrección automática de polaridad en señales invertidas.
9. Cálculo de intervalos R-R.
10. Estimación de frecuencia cardíaca media y mediana.
11. Cálculo descriptivo de métricas HRV: SDNN, RMSSD y pNN50.
12. Generación de gráficas por registro: señal cruda, señal filtrada con picos R, FFT y espectrograma.

La frecuencia de muestreo utilizada en el procesamiento fue:

```python
fs = 1000  # Hz
```

El filtro aplicado fue:

```python
LOWCUT = 0.5      # Hz
HIGHCUT = 40      # Hz
NOTCH_FREQ = 60   # Hz
```

Las métricas principales se calcularon a partir de los picos R detectados:
```python
RR = diferencia temporal entre picos R consecutivos

FC = 60 / RR_promedio
```

Donde `RR` corresponde al intervalo entre dos picos R consecutivos.

---

Debido a que el código de procesamiento es extenso, se decidió colocarlo en un archivo independiente dentro del repositorio. Esto permite mantener el README más ordenado y facilita la revisión del flujo completo de análisis.

El procesamiento completo de las señales ECG se encuentra disponible en el siguiente archivo:

[Ver notebook de procesamiento ECG](./Lab5_bitalino.ipynb)

### 3.6. Variables analizadas

| Variable | Descripción | Unidad |
|---|---|---|
| Duración | Tiempo total del registro | s |
| Número de picos R | Cantidad de complejos QRS detectados | - |
| Intervalo R-R promedio | Tiempo promedio entre picos R consecutivos | s |
| Frecuencia cardíaca media | Frecuencia estimada a partir de los intervalos R-R | bpm |
| Frecuencia cardíaca mediana | Mediana de la frecuencia cardíaca instantánea | bpm |
| SDNN | Desviación estándar de los intervalos R-R | ms |
| RMSSD | Raíz cuadrática media de diferencias sucesivas entre intervalos R-R | ms |
| pNN50 | Porcentaje de diferencias sucesivas mayores a 50 ms | % |
| Polaridad | Orientación detectada de la señal ECG | normal/invertida |

Las métricas SDNN, RMSSD y pNN50 se interpretaron únicamente de manera descriptiva, ya que varias señales tuvieron duraciones cortas de aproximadamente 20 a 30 segundos.

---

## 4. Resultados

### 4.1. Gráficas obtenidas

Para cada señal se generó una figura con cuatro paneles:

1. Señal ECG cruda centrada.
2. Señal ECG filtrada con picos R detectados.
3. Espectro de frecuencia mediante FFT.
4. Espectrograma mediante STFT.

A continuación, se muestran ejemplos representativos por condición.

---

### 4.2. Señal basal

![ECG basal derivación I](Fotos/Basal_Der1.png)
![ECG basal derivación II](Fotos/Basal_Der2.png)
![ECG basal derivación III](Fotos/Basal_Der3.png)

En la condición basal se espera una señal más estable, debido a que el usuario se encontraba en reposo. Esta condición se utilizó como referencia para comparar los cambios observados en las demás actividades.

---

### 4.3. Señal durante hiperventilación

![ECG hiperventilación I](Fotos/Hyper1_Der1.png)
![ECG hiperventilación II](Fotos/Hyper1_Der2.png)
![ECG hiperventilación III](Fotos/Hyper1_Der3.png)
![ECG hiperventilación I](Fotos/Hyper2_Der1.png)
![ECG hiperventilación II](Fotos/Hyper2_Der2.png)
![ECG hiperventilación III](Fotos/Hyper2_Der3.png)
Durante la hiperventilación pueden aparecer cambios en la frecuencia cardíaca y en los intervalos R-R. Además, la respiración rápida puede introducir movimiento torácico y alterar la estabilidad de la línea base.

---

### 4.4. Señal post-ejercicio

![ECG post-ejercicio I](Fotos/Post_Exer_Der1.png)
![ECG post-ejercicio II](Fotos/Post_Exer_Der2.png)
![ECG post-ejercicio III](Fotos/Post_Exer_Der3.png)


En la condición post-ejercicio se observó un aumento evidente de la frecuencia cardíaca. Esto se refleja en una mayor cantidad de picos R por unidad de tiempo y en intervalos R-R más cortos.

---

### 4.5. Señal durante apnea voluntaria

![ECG apnea voluntaria I](Fotos/Apnea_Der1.png)
![ECG apnea voluntaria II](Fotos/Apnea_Der2.png)
![ECG apnea voluntaria III](Fotos/Apnea_Der3.png)

Durante la apnea voluntaria se observaron frecuencias cardíacas elevadas respecto a la condición basal. Esto puede asociarse tanto a cambios autonómicos como a incomodidad, tensión muscular o recuperación incompleta entre actividades.

---

### 4.6. Tabla resumen de resultados

| Condición | Derivación | Duración (s) | Picos R | FC media (bpm) | RR promedio (s) | Observación |
|---|---:|---:|---:|---:|---:|---|
| Basal | I | 31.20 | 43 | 84.51 | 0.727 | Señal invertida detectada |
| Basal | II | 31.05 | 44 | 85.37 | 0.704 | Señal normal |
| Basal | III | 37.20 | 52 | 87.61 | 0.720 | Señal normal |
| Hiperventilación rep. 1 | I | 38.25 | 58 | 91.55 | 0.660 | Aumento leve de FC |
| Hiperventilación rep. 1 | II | 30.60 | 43 | 85.33 | 0.708 | Similar a basal |
| Hiperventilación rep. 1 | III | 31.35 | 44 | 83.56 | 0.723 | Similar a basal |
| Hiperventilación rep. 2 | I | 30.30 | 44 | 89.92 | 0.684 | Señal invertida detectada |
| Hiperventilación rep. 2 | II | 32.10 | 47 | 88.40 | 0.683 | Aumento leve de FC |
| Hiperventilación rep. 2 | III | 36.00 | 53 | 88.71 | 0.684 | Aumento leve de FC |
| Post-ejercicio | I | 30.75 | 80 | 157.01 | 0.383 | Mayor FC registrada |
| Post-ejercicio | II | 31.65 | 72 | 137.21 | 0.438 | FC elevada |
| Post-ejercicio | III | 60.60 | 126 | 124.83 | 0.481 | FC elevada, registro más largo |
| Apnea | I | 21.45 | 49 | 136.36 | 0.440 | FC elevada |
| Apnea | II | 21.90 | 46 | 127.12 | 0.472 | FC elevada |
| Apnea | III | 28.80 | 62 | 129.02 | 0.465 | FC elevada |

---

### 4.7. Comparación global de frecuencia cardíaca

![Comparación global de frecuencia cardíaca](Fotos/Comp_Global.png)

La frecuencia cardíaca media en condición basal se mantuvo aproximadamente entre 84 y 88 bpm. Durante la hiperventilación, los valores se mantuvieron cercanos a la condición basal, con aumentos leves en algunos registros. En la condición post-ejercicio se observaron los valores más altos, especialmente en la derivación I, donde la frecuencia cardíaca media fue aproximadamente 157 bpm. Durante la apnea también se registraron valores elevados, entre 127 y 136 bpm.

---

### 4.8. Comparación respecto al promedio basal

El promedio de frecuencia cardíaca basal de la Actividad 1 fue utilizado como referencia descriptiva. Esta comparación debe interpretarse con cautela, ya que no se registró una señal basal inmediatamente antes de las actividades de ejercicio y apnea.

| Condición | Derivación | FC media (bpm) | Diferencia vs basal (bpm) |
|---|---:|---:|---:|
| Hiperventilación rep. 1 | I | 91.55 | +5.72 |
| Hiperventilación rep. 1 | II | 85.33 | -0.50 |
| Hiperventilación rep. 1 | III | 83.56 | -2.27 |
| Hiperventilación rep. 2 | I | 89.92 | +4.09 |
| Hiperventilación rep. 2 | II | 88.40 | +2.57 |
| Hiperventilación rep. 2 | III | 88.71 | +2.88 |
| Post-ejercicio | I | 157.01 | +71.18 |
| Post-ejercicio | II | 137.21 | +51.38 |
| Post-ejercicio | III | 124.83 | +39.00 |
| Apnea | I | 136.36 | +50.53 |
| Apnea | II | 127.12 | +41.29 |
| Apnea | III | 129.02 | +43.19 |

![Diferencia de FC vs basal](Fotos/Comp_Basal_Hyper.png)
![Diferencia de FC vs basal](Fotos/Comp_Post_Exer.png)
![Diferencia de FC vs basal](Fotos/Comp_Apnea.png)
---

## 5. Discusión

### 5.1. Coherencia fisiológica de los resultados

La señal basal representa la condición de referencia del laboratorio. En esta etapa, el usuario se encontraba en reposo, por lo que se esperaba una frecuencia cardíaca relativamente estable, intervalos R-R más regulares y una menor cantidad de artefactos. Esta condición es importante porque permite comparar los cambios observados en las demás actividades.

Durante la hiperventilación, los cambios en la respiración pueden modificar la interacción entre el sistema respiratorio y cardiovascular. En este tipo de condición, es posible observar variaciones en la frecuencia cardíaca y en los intervalos R-R, debido a la modulación autonómica asociada a la respiración. Además, la respiración rápida puede generar desplazamientos del tórax, movimiento de cables o variaciones en el contacto de los electrodos, lo que puede afectar la amplitud y estabilidad de la señal ECG.

En la actividad post-ejercicio, se esperaba un aumento de la frecuencia cardíaca como respuesta fisiológica al esfuerzo físico. Al subir y bajar escaleras durante 10 minutos, aumenta la demanda metabólica del cuerpo y se activa la respuesta cardiovascular para incrementar el aporte de oxígeno a los tejidos. Esto debería reflejarse en intervalos R-R más cortos y una mayor frecuencia cardíaca inmediatamente después del ejercicio. Sin embargo, debido a que las tres derivaciones se registraron de forma consecutiva y no simultánea, la frecuencia cardíaca pudo disminuir progresivamente durante la recuperación, generando diferencias entre derivaciones que no necesariamente se deben solo a la posición de los electrodos.

Durante la apnea voluntaria, la contención de la respiración puede modificar la regulación autonómica del corazón. Dependiendo de la duración y tolerancia del usuario, pueden aparecer cambios en la frecuencia cardíaca y en la variabilidad de los intervalos R-R. Aunque la ausencia de respiración puede reducir el movimiento torácico, también puede generar incomodidad, tensión muscular o pequeños movimientos involuntarios, los cuales pueden introducir ruido en la señal.

---

### 5.2. Comparación entre derivaciones

Las diferencias observadas entre las derivaciones I, II y III se explican porque cada derivación registra la actividad eléctrica cardíaca desde un eje distinto. Por ello, la amplitud del complejo QRS, la polaridad de algunas ondas y la claridad de los picos R pueden variar entre derivaciones.

En general, una derivación puede mostrar picos R más notorios si su eje de medición está más alineado con el vector eléctrico predominante del corazón. Por el contrario, si la orientación de la derivación no coincide adecuadamente con dicho vector, la amplitud puede disminuir o la morfología puede cambiar.

También es importante considerar que pequeñas diferencias en la colocación de electrodos, presión de contacto, adhesión, impedancia de la piel o movimiento de los cables pueden afectar la señal registrada. Por esta razón, no todas las diferencias entre derivaciones deben interpretarse únicamente como cambios fisiológicos.

---

### 5.3. Artefactos y problemas identificados

Durante la adquisición de señales ECG pueden aparecer distintos tipos de artefactos. En este laboratorio, los más probables fueron:

- **Artefactos por movimiento:** generados por cambios de postura, respiración intensa, recuperación post-ejercicio o movimiento de cables.
- **Ruido por contacto electrodo-piel:** asociado a mala adhesión, sudoración o limpieza insuficiente de la piel.
- **Inestabilidad de la línea base:** relacionada con respiración, desplazamiento del tórax o variaciones mecánicas en los electrodos.
- **Ruido muscular:** producido por tensión muscular, especialmente durante apnea o después del ejercicio.
- **Diferencias por adquisición secuencial:** las derivaciones se tomaron una después de otra, por lo que el estado fisiológico del usuario pudo cambiar entre registros.

Estos factores son importantes porque pueden modificar la amplitud, forma y estabilidad de la señal ECG. Por ello, el análisis debe diferenciar entre cambios fisiológicos reales y alteraciones producidas por el procedimiento experimental.

---

### 5.4. Limitaciones del laboratorio

Una primera limitación fue que las mediciones se realizaron en un solo usuario. Esto impide generalizar los resultados a una población más amplia, ya que la respuesta cardíaca y respiratoria puede variar según condición física, edad, estrés, postura, hidratación, respiración y otros factores individuales.

Una segunda limitación fue la duración de los registros. Las ventanas de 20 a 30 segundos son útiles para observar la morfología del ECG y estimar la frecuencia cardíaca de manera aproximada, pero son limitadas para un análisis completo de variabilidad de la frecuencia cardíaca. En condiciones dinámicas, como post-ejercicio o recuperación, se requieren ventanas más largas para obtener métricas HRV más estables.

Otra limitación importante fue que las derivaciones I, II y III no se registraron simultáneamente. Esto afecta especialmente a la condición post-ejercicio, ya que la frecuencia cardíaca disminuye progresivamente durante la recuperación. Por tanto, una diferencia entre derivaciones podría deberse tanto al eje eléctrico de medición como al cambio temporal del estado fisiológico.

Finalmente, las condiciones de hiperventilación y apnea no fueron controladas con instrumentos respiratorios. No se midió volumen corriente, frecuencia respiratoria exacta ni saturación de oxígeno, por lo que la interpretación debe mantenerse como descriptiva y no clínica.

---

### 5.5. Relación con la evidencia científica

La literatura reciente respalda que el análisis de HRV en ventanas ultracortas puede ser útil, pero su validez depende mucho de la condición experimental. En condiciones no estáticas, como ejercicio o recuperación post-ejercicio, se necesita mayor duración de registro para obtener métricas más confiables. Esto es relevante para este laboratorio, ya que varias adquisiciones fueron de 20 a 30 segundos.

En relación con el ejercicio físico, estudios sobre recuperación de frecuencia cardíaca indican que actividades cotidianas como subir escaleras pueden generar una respuesta cardiovascular suficiente para analizar la recuperación post-ejercicio. Esto coincide con lo esperado en este laboratorio, donde la actividad de escaleras debía elevar la frecuencia cardíaca y reducir los intervalos R-R.

Respecto a los artefactos, los estudios en sistemas ECG portátiles y wearables muestran que el movimiento y el contacto electrodo-piel son factores críticos en la calidad de la señal. Esto permite explicar posibles distorsiones observadas durante hiperventilación, post-ejercicio o cambios rápidos de derivación.

Finalmente, investigaciones recientes sobre la ubicación de electrodos muestran que la amplitud y morfología del ECG pueden cambiar según la posición del par de electrodos. Esto respalda la comparación realizada entre las derivaciones I, II y III, así como la necesidad de interpretar cuidadosamente las diferencias entre señales.

---

## 6. Conclusiones

- Se logró adquirir señales ECG en condiciones de reposo, hiperventilación, post-ejercicio y apnea voluntaria.
- La señal basal funcionó como referencia para comparar los cambios observados en las demás condiciones.
- Después del ejercicio se esperaba una mayor frecuencia cardíaca y una reducción de los intervalos R-R, debido al aumento de la demanda cardiovascular.
- La hiperventilación y la apnea pueden modificar la señal ECG por la interacción entre respiración, sistema nervioso autónomo y actividad cardíaca.
- Las diferencias entre derivaciones se explican por la orientación del eje de medición respecto al vector eléctrico cardíaco.
- La calidad de la señal ECG depende fuertemente de la correcta colocación de electrodos, el contacto piel-electrodo y la reducción de movimientos.
- Las ventanas de adquisición de 20 a 30 segundos permiten una descripción inicial de la señal, pero son limitadas para un análisis robusto de HRV.
- Para futuros laboratorios se recomienda registrar las derivaciones de forma simultánea, aumentar la duración de las mediciones y controlar mejor las condiciones respiratorias y de movimiento.

---

## 7. Referencias

1.  N. Rafie, A. H. Kashou, and P. A. Noseworthy, “ECG Interpretation: Clinical Relevance, Challenges, and Advances,” Hearts, vol. 2, no. 4, pp. 505–513, 2021.
2.  Fundamentals of the electrocardiogram and common cardiac arrhythmias, 2024. https://doi.org/10.1016/j.mpaic.2023.11.014
3.  PLUX Wireless Biosignals, BITalino (r)evolution Home Guide #2: Electrocardiography (ECG), 2021.

