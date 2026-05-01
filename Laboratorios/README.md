# Laboratorio N.º 4: Adquisición y análisis de señales ECG en distintas condiciones fisiológicas

## 1. Introducción

En este laboratorio se realizó la adquisición de señales electrocardiográficas (ECG) utilizando el sistema BITalino y electrodos superficiales colocados según las derivaciones bipolares de Einthoven I, II y III. El objetivo principal fue observar cómo varía la señal ECG bajo diferentes condiciones fisiológicas: reposo, hiperventilación, actividad física y contención voluntaria de la respiración.

El ECG permite registrar la actividad eléctrica del corazón desde la superficie corporal. A partir de esta señal es posible identificar componentes característicos como la onda P, el complejo QRS y la onda T. Además, mediante la detección de los picos R se puede estimar la frecuencia cardíaca y analizar la variabilidad de los intervalos R-R.

Durante el laboratorio se buscó comparar la señal ECG basal con señales obtenidas en condiciones que modifican la respuesta cardiorrespiratoria. Asimismo, se evaluó cómo la posición de los electrodos, el cambio de derivación y la presencia de movimiento pueden afectar la amplitud, morfología y calidad de la señal registrada.

---

## 2. Objetivos

### Objetivo general

Adquirir y analizar señales ECG en diferentes condiciones fisiológicas, comparando los cambios observados entre reposo, hiperventilación, post-ejercicio y apnea voluntaria.

### Objetivos específicos

- Registrar señales ECG utilizando las derivaciones I, II y III.
- Comparar la señal basal con señales adquiridas después de hiperventilación, actividad física y contención de la respiración.
- Identificar cambios en la frecuencia cardíaca, intervalos R-R, amplitud y calidad visual de la señal.
- Reconocer posibles artefactos asociados al movimiento, respiración, sudoración o contacto electrodo-piel.
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
| Alcohol y material de limpieza | Utilizados para preparar la piel antes de colocar los electrodos |

Antes de colocar los electrodos, se limpió la zona de contacto con alcohol con el fin de reducir la impedancia piel-electrodo y mejorar la calidad de la señal. Además, se procuró evitar movimientos bruscos durante la adquisición, ya que estos pueden introducir artefactos en la señal ECG.

---

### 3.2. Consideraciones de privacidad

Las fotos y videos incluidos en este repositorio deben evitar mostrar el rostro del participante. Por ello, las imágenes utilizadas para documentar la metodología se enfocan únicamente en la colocación de electrodos, el sistema de adquisición y el procedimiento experimental.

Ejemplo de imagen de colocación:

```markdown
![Colocación de electrodos sin rostro](media/colocacion_electrodos.jpg)
```

Ejemplo de video corto o GIF:

```markdown
![Registro experimental sin rostro](media/registro_ecg.gif)
```

---

### 3.3. Colocación de electrodos

Se trabajó con configuraciones basadas en las derivaciones de Einthoven:

| Derivación | Configuración general | Descripción |
|---|---|---|
| Derivación I | RA (-) a LA (+) | Mide la diferencia de potencial entre el lado derecho e izquierdo superior del cuerpo |
| Derivación II | RA (-) a LL (+) | Mide la actividad eléctrica desde el lado superior derecho hacia la región inferior izquierda |
| Derivación III | LA (-) a LL (+) | Mide la actividad eléctrica desde el lado superior izquierdo hacia la región inferior izquierda |

En la primera configuración, los electrodos se colocaron en una disposición tipo **clavícula-clavícula-cadera**, usando la cadera o cresta ilíaca como referencia. Esta configuración permite aproximar las derivaciones de Einthoven y, al colocar los electrodos cerca de zonas óseas, ayuda a reducir parte del ruido asociado a actividad muscular.

Agregar imagen:

```markdown
![Esquema de derivaciones ECG](media/derivaciones_einthoven.jpg)
```

---

### 3.4. Actividades realizadas

El laboratorio se dividió en tres actividades principales.

---

#### Actividad 1: Señal basal e hiperventilación

Primero se adquirió una señal ECG basal durante **30 segundos** con el usuario en reposo y con los electrodos colocados en la primera derivación.

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

Para el análisis de las señales adquiridas se consideró el siguiente flujo general de procesamiento:

1. Importación de los datos exportados desde OpenSignals.
2. Selección del canal correspondiente al ECG.
3. Conversión o normalización de la señal, si corresponde.
4. Filtrado de la señal para reducir ruido de baja frecuencia, interferencia eléctrica o artefactos.
5. Detección de picos R.
6. Cálculo de intervalos R-R.
7. Estimación de frecuencia cardíaca.
8. Generación de gráficas comparativas por condición y derivación.

Espacio para colocar el código utilizado:

```python
# ============================================================
# Código de procesamiento de señal ECG
# Laboratorio N.º 4 - Señales Biomédicas
# ============================================================

# 1. Importar librerías
# import numpy as np
# import pandas as pd
# import matplotlib.pyplot as plt
# from scipy.signal import butter, filtfilt, find_peaks

# 2. Cargar señal ECG
# Reemplazar con la ruta del archivo exportado desde OpenSignals
# file_path = "data/ecg_basal.txt"

# 3. Leer datos
# data = ...

# 4. Seleccionar canal ECG
# ecg_signal = ...

# 5. Definir frecuencia de muestreo
# fs = ...

# 6. Filtrado de la señal
# Ejemplo:
# def bandpass_filter(signal, lowcut, highcut, fs, order=4):
#     nyq = 0.5 * fs
#     low = lowcut / nyq
#     high = highcut / nyq
#     b, a = butter(order, [low, high], btype="band")
#     return filtfilt(b, a, signal)

# filtered_ecg = bandpass_filter(ecg_signal, lowcut=0.5, highcut=40, fs=fs)

# 7. Detección de picos R
# peaks, properties = find_peaks(filtered_ecg, distance=0.4*fs, prominence=...)

# 8. Cálculo de intervalos R-R
# rr_intervals = np.diff(peaks) / fs

# 9. Cálculo de frecuencia cardíaca
# heart_rate = 60 / np.mean(rr_intervals)

# 10. Gráfica de la señal
# time = np.arange(len(filtered_ecg)) / fs
# plt.figure(figsize=(12, 4))
# plt.plot(time, filtered_ecg, label="ECG filtrado")
# plt.plot(time[peaks], filtered_ecg[peaks], "x", label="Picos R")
# plt.xlabel("Tiempo (s)")
# plt.ylabel("Amplitud")
# plt.title("Señal ECG procesada")
# plt.legend()
# plt.grid(True)
# plt.show()
```

---

## 4. Resultados

### 4.1. Variables analizadas

| Variable | Descripción | Unidad |
|---|---|---|
| Tiempo | Duración del registro ECG | s |
| Amplitud ECG | Valor de la señal registrada | mV o unidades del sistema |
| Picos R | Máximos asociados al complejo QRS | - |
| Intervalo R-R | Tiempo entre picos R consecutivos | s |
| Frecuencia cardíaca | Frecuencia estimada a partir de los intervalos R-R | bpm |
| Calidad de señal | Evaluación visual de ruido, artefactos y estabilidad | Cualitativa |

La frecuencia cardíaca se puede estimar mediante:

```text
FC = 60 / promedio(RR)
```

donde `RR` corresponde al intervalo promedio entre picos R consecutivos.

---

### 4.2. Resultados de la señal basal

Agregar gráfica:

```markdown
![ECG basal](figures/ecg_basal.png)
```

Descripción:

En la señal basal se espera observar una señal ECG más estable, debido a que el usuario se encontraba en reposo y con menor movimiento corporal. Esta condición sirve como referencia para comparar los cambios fisiológicos observados en las actividades posteriores.

Completar con resultados obtenidos:

| Parámetro | Valor |
|---|---:|
| Duración del registro | 30 s |
| Frecuencia cardíaca estimada | Pendiente |
| Intervalo R-R promedio | Pendiente |
| Calidad visual de la señal | Pendiente |

---

### 4.3. Resultados durante/post hiperventilación

Agregar gráfica:

```markdown
![ECG hiperventilación](figures/ecg_hiperventilacion.png)
```

Descripción:

Durante o después de la hiperventilación pueden observarse cambios en la frecuencia cardíaca y en la variabilidad de los intervalos R-R. Además, la respiración rápida puede introducir artefactos asociados al movimiento del tórax, los cables o los electrodos.

Completar con resultados obtenidos:

| Derivación | Frecuencia cardíaca estimada | Observaciones |
|---|---:|---|
| I | Pendiente | Pendiente |
| II | Pendiente | Pendiente |
| III | Pendiente | Pendiente |

---

### 4.4. Resultados post-ejercicio

Agregar gráfica:

```markdown
![ECG post ejercicio](figures/ecg_post_ejercicio.png)
```

Descripción:

Después de la actividad física se espera observar un aumento de la frecuencia cardíaca, reflejado en intervalos R-R más cortos. También puede presentarse mayor ruido debido a respiración agitada, sudoración, movimiento residual o cambios en el contacto electrodo-piel.

Completar con resultados obtenidos:

| Derivación | Frecuencia cardíaca estimada | Observaciones |
|---|---:|---|
| I | Pendiente | Pendiente |
| II | Pendiente | Pendiente |
| III | Pendiente | Pendiente |

---

### 4.5. Resultados durante apnea voluntaria

Agregar gráfica:

```markdown
![ECG apnea voluntaria](figures/ecg_apnea.png)
```

Descripción:

Durante la contención de la respiración pueden observarse cambios en el ritmo cardíaco y en la variabilidad de los intervalos R-R. La ausencia de movimiento respiratorio puede reducir algunos artefactos torácicos, aunque la incomodidad durante la apnea también puede generar tensión muscular o pequeños movimientos.

Completar con resultados obtenidos:

| Derivación | Frecuencia cardíaca estimada | Observaciones |
|---|---:|---|
| I | Pendiente | Pendiente |
| II | Pendiente | Pendiente |
| III | Pendiente | Pendiente |

---

### 4.6. Comparación general de condiciones

Completar con los valores obtenidos luego del procesamiento:

| Condición | Derivación | FC estimada | Calidad de señal | Observación principal |
|---|---|---:|---|---|
| Basal | I | Pendiente | Pendiente | Señal de referencia |
| Hiperventilación | I | Pendiente | Pendiente | Pendiente |
| Hiperventilación | II | Pendiente | Pendiente | Pendiente |
| Hiperventilación | III | Pendiente | Pendiente | Pendiente |
| Post-ejercicio | I | Pendiente | Pendiente | Pendiente |
| Post-ejercicio | II | Pendiente | Pendiente | Pendiente |
| Post-ejercicio | III | Pendiente | Pendiente | Pendiente |
| Apnea | I | Pendiente | Pendiente | Pendiente |
| Apnea | II | Pendiente | Pendiente | Pendiente |
| Apnea | III | Pendiente | Pendiente | Pendiente |

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

1. PLUX Wireless Biosignals. (2021). *BITalino (r)evolution Home Guide #2: Electrocardiography (ECG)*. PLUX – Wireless Biosignals, S.A.

2. Kim, J. W., Seok, H. S., & Shin, H. (2021). Is ultra-short-term heart rate variability valid in non-static conditions? *Frontiers in Physiology, 12*, 596060. https://doi.org/10.3389/fphys.2021.596060

3. Sokas, D., Rapalis, A., Petrenas, A., Daukantas, S., & Marozas, V. (2021). Evaluation of stair climbing as an approach for estimating heart rate recovery in daily activities. *Proceedings of the 14th International Joint Conference on Biomedical Engineering Systems and Technologies - BIOSIGNALS*, 21–25. https://doi.org/10.5220/0010184500002865

4. Castaño Usuga, F. A., Gissel, C., & Hernández, A. M. (2022). Motion artifact reduction in electrocardiogram signals through a redundant denoising independent component analysis method for wearable health care monitoring systems: Algorithm development and validation. *JMIR Medical Informatics, 10*(11), e40826. https://doi.org/10.2196/40826

5. Sanjo, K., Hebiguchi, K., Tang, C., Rashed, E. A., Kodera, S., Togo, H., & Hirata, A. (2024). Sensitivity of electrocardiogram on electrode-pair locations for wearable devices: Computational analysis of amplitude and waveform distortion. *Biosensors, 14*(3), 153. https://doi.org/10.3390/bios14030153

6. Bouten, J., Bourgois, J. G., Boone, J., & others. (2021). Heart rate and muscle oxygenation kinetics during dynamic apneas in breath-hold divers. *Frontiers in Physiology, 12*, 712629. https://doi.org/10.3389/fphys.2021.712629

7. Sinha, M., Sinha, R., Ghate, J., & Sarnik, G. (2020). Impact of altered breathing patterns on interaction of EEG and heart rate variability. *Annals of Neurosciences, 27*(2), 67–74. https://doi.org/10.1177/0972753120950075
