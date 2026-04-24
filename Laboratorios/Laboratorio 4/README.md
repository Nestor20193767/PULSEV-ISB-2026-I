# 🧠 Laboratorio N°4 de Señales Biomédicas — Home Guide #1
## Electromiografía (EMG) — BITalino (r)evolution


> **Fecha:** Abril 2026  

---

## 📋 Tabla de Contenidos

1. [Introducción](#introducción)
2. [Materiales y Conexiones](#materiales-y-conexiones)
3. [Protocolo de Adquisición](#protocolo-de-adquisición)
4. [Resultados](#resultados)
   - [Silencio Eléctrico / Reposo](#silencio-eléctrico--reposo)
   - [Señal en OpenSignals](#señal-en-opensignals)
   - [Análisis de la Señal](#análisis-de-la-señal)
5. [Ploteo en Python](#ploteo-en-python)
6. [Archivos](#archivos)
7. [Discusión y Conclusiones](#discusión-y-conclusiones)
8. [Referencias](#referencias)
9. [Preguntas de la Guia](#Preguntas-de-la-Guia)

---

## Introducción

La Electromiografía (EMG) es una técnica que permite registrar la actividad eléctrica producida por los músculos esqueléticos. Cuando el sistema nervioso envía una señal a través de las motoneuronas superiores e inferiores, se genera un potencial de acción que produce una contracción muscular visible y medible eléctricamente.

En esta práctica se utilizó el sistema **BITalino (r)evolution** con el sensor EMG ensamblado para adquirir señales musculares en diferentes grupos musculares, explorando la variación de amplitud y frecuencia de las señales según la intensidad de contracción y la ubicación corporal.

---

## Materiales y Conexiones

### Equipos utilizados

| Componente | Descripción |
|---|---|
| BITalino (r)evolution Core BT | Placa de adquisición de señales biomédicas |
| Sensor EMG ensamblado | Sensor de electromiografía de superficie |
| Electrodos Ag/AgCl | Electrodos desechables auto-adhesivos con gel |
| Cable de referencia (1 lead) | Para electrodo de referencia en zona neutra |
| Dongle Bluetooth | Para comunicación inalámbrica con PC |
| OpenSignals (r)evolution | Software de visualización y adquisición |

### Conexión Electrodos–Cuerpo

Los electrodos se posicionaron siguiendo la configuración bipolar estándar:

- **IN+ e IN−**: sobre el vientre muscular, alineados con la fibra muscular, con separación de ~2 cm.
- **REF (referencia)**: sobre una zona neutra ósea.


#### 📸 Foto de conexiones — Electrodos en cuerpo

<table>
  <thead>
    <tr>
      <th>#</th>
      <th>Mano</th>
      <th>Brazo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td align="center">
        <img src="./Videos%20y%20Fotos/electrodos_mano.jpg" width="300"><br>
        <sub>Posicionamiento de los electrodos IN+ e IN− sobre los músculos abductores del pulgar y electrodo de referencia en el hueso pisiforme.</sub>
      </td>
      <td align="center">
        <img src="./Videos%20y%20Fotos/electrodos_brazo.PNG" width="300"><br>
        <sub>Posicionamiento de los electrodos en el brazo.</sub>
      </td>
    </tr>
  </tbody>
</table>
#### 📸 Foto de conexiones — BITalino y cables

<img src="./Videos%20y%20Fotos/bitalino.jpeg" width="350">

> *Descripción: Vista del sensor EMG ensamblado conectado al BITalino (r)evolution Core BT mediante el cable de referencia en el puerto analógico correspondiente.*

---

## Protocolo de Adquisición

Se siguió el protocolo indicado en el **Home-Guide #1**, sección 6.2:

1. Conexión y configuración del BITalino mediante Bluetooth.
2. Verificación del setup y revisión de la calidad de señal.
3. **Baseline inicial (30 s):** Registro en reposo sin activación muscular.
4. **Ciclos de contracción (×5):** CONTRACCIÓN (2 s) → RELAJACIÓN (2 s) → REPOSO (2 s), incrementando la intensidad progresivamente hasta la contracción voluntaria máxima.
5. **Baseline final (30 s):** Nuevo registro en reposo.
6. **Activaciones cortas consecutivas (×varios, 1 s c/u)** seguidas de una contracción sostenida (10 s).
7. Guardado del archivo de señal.

### Grupos musculares explorados

| # | Músculo | Zona | Acción para activar |
|---|---|---|---|
| 1 | Abductor pollicis brevis | Pulgar | Abducción del pulgar |
| 2 | Biceps | Brazo| Contracción del bicep |

---

## Resultados

### Silencio Eléctrico / Reposo

Durante la fase de reposo, la señal EMG mostró una línea base cercana a **0 mV**, característica del silencio eléctrico muscular. Esto confirma que, en ausencia de activación voluntaria, no se generan potenciales de acción significativos en el músculo.

#### 🎥 Videos — Silencio eléctrico y conexiones

<table>
  <thead>
    <tr>
      <th>#</th>
      <th>Mano</th>
      <th>Brazo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td align="center">
        <a href="https://drive.google.com/file/d/1lu_aLHdgQIbCsKkL5fag_nHpBS-1xgAm/view?usp=sharing" target="_blank">
          <img src="./Videos%20y%20Fotos/electrodos_mano.jpg" width="300"><br>
          <sub>▶ Ver video en Drive</sub>
        </a>
      </td>
      <td align="center">
        <a href="https://drive.google.com/file/d/1tug-7IPiYGpyVxjVVvpaHIj_opvMvUmk/view?usp=sharing" target="_blank">
          <img src="./Videos%20y%20Fotos/electrodos_brazo.PNG" width="300"><br>
          <sub>▶ Ver video en Drive</sub>
        </a>
      </td>
    </tr>
  </tbody>
</table>

### Señal en OpenSignals

A continuación se presenta el ploteo de la señal EMG adquirida con OpenSignals (r)evolution durante el protocolo completo:

#### 📊 Ploteo — OpenSignals (r)evolution

<table>
  <thead>
    <tr>
      <th>#</th>
      <th>Mano</th>
      <th>Brazo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td align="center">
        <img src="./Videos%20y%20Fotos/ploteo_mano.PNG" width="400" height="250"><br>
        <sub>Señal EMG del músculo abductor del pulgar adquirida con BITalino. Se observan las fases de reposo (línea base ~0 mV) y las fases de contracción (picos de amplitud creciente). El eje X representa el tiempo [s] y el eje Y la amplitud de la señal [mV].</sub>
      </td>
      <td align="center">
        <img src="./Videos%20y%20Fotos/ploteo_brazo.PNG" width="400" height="250"><br>
        <sub>Señal EMG del músculo del brazo adquirida con BITalino.</sub>
      </td>
    </tr>
  </tbody>
</table>


### Análisis de la Señal

#### Descripción general

La señal EMG adquirida presentó un comportamiento coherente con una señal de electromiografía superficial. Durante el reposo muscular, tanto en la mano como en el bíceps, se observó una señal de baja amplitud, asociada al silencio eléctrico o mínima activación voluntaria. En cambio, durante las contracciones se evidenciaron ráfagas de mayor amplitud, correspondientes al reclutamiento de unidades motoras.

**En reposo:**
- La señal presentó menor amplitud y pequeñas fluctuaciones alrededor de la línea base.
- Estas variaciones pueden asociarse a ruido instrumental, movimiento leve, contacto piel-electrodo o actividad muscular residual.
- La baja amplitud observada es coherente con una condición de reposo muscular.

**Durante la contracción muscular:**
- Se observó un incremento claro de la amplitud de la señal EMG.
- Las ráfagas de activación fueron más evidentes durante los momentos de contracción voluntaria.
- La señal presentó un comportamiento irregular o estocástico, debido a que la EMG superficial representa la suma de potenciales de acción provenientes de múltiples unidades motoras.

**Frecuencias de interés:**
- En el procesamiento de señales EMG superficiales suele emplearse un filtro pasabanda dentro de un rango aproximado de 20–450 Hz, ya que esta banda conserva gran parte de la información muscular y reduce componentes de baja frecuencia asociadas al movimiento, así como ruido de alta frecuencia.
- En este laboratorio se visualizaron la señal temporal, la Transformada Rápida de Fourier (FFT) y el espectrograma (STFT), con el fin de observar el comportamiento de la señal en tiempo, frecuencia y tiempo-frecuencia.

**Comparación entre músculos evaluados:**

| Músculo evaluado | Zona | Acción realizada | Comportamiento observado |
|---|---|---|---|
| Abductor pollicis brevis | Mano / pulgar | Abducción del pulgar o movimiento de pinza | Señal de menor amplitud relativa, asociada a un músculo pequeño y a un movimiento fino |
| Bíceps braquial | Brazo | Contracción voluntaria del bíceps | Señal de mayor amplitud relativa y ráfagas más evidentes durante la contracción |

La diferencia entre ambas señales puede explicarse por el tamaño muscular, la cantidad de unidades motoras reclutadas y la facilidad de ubicación de los electrodos sobre el vientre muscular. El bíceps, al ser un músculo de mayor tamaño, tiende a generar una señal superficial más evidente que el músculo evaluado en la mano.

---

## Ploteo en Python

La señal fue procesada y visualizada utilizando Python con las librerías `numpy`, `matplotlib` y `pandas`.

### Código utilizado

```python

!pip install opensignalsreader

from google.colab import drive
drive.mount('/content/drive')

baseline_brazo = "/content/drive/MyDrive/senalesBitalino/BASELINEBRAZO.txt"
baseline_mano = "/content/drive/MyDrive/senalesBitalino/BASELINEMANO.txt"

emg_mano = "/content/drive/MyDrive/senalesBitalino/PRUEBAMANO3.txt"
emg_brazo ="/content/drive/MyDrive/senalesBitalino/PRUEBABRAZO1.txt"

import opensignalsreader as osr
from opensignalsreader import OpenSignalsReader
import matplotlib.pyplot as plt
import numpy as np
from scipy.signal import butter, lfilter, welch

# Read OpenSignals file and plot all signals for baseline (hand and arm) and EMG (hand and arm)

# Lista de todas las rutas de los archivos de señales
signal_files = [
    baseline_mano,
    baseline_brazo,
    emg_mano,
    emg_brazo
]

# Iterar sobre cada archivo y plotear todas sus señales
for file_path in signal_files:
    print(f"Plotting signals from: {file_path}")
    acq = OpenSignalsReader(file_path, show=True)

# Definimos la frecuencia de muestreo (fs).
fs = 1000

for file_path in signal_files:
    # Extraemos el nombre del archivo
    nombre_archivo = file_path.split('/')[-1].replace('.txt', '')
    print(f"--- Procesando y graficando: {nombre_archivo} ---")

    # Leer el archivo
    acq = osr.OpenSignalsReader(file_path)

    # Buscamos automáticamente en qué canal de Bitalino hay datos
    senial = None
    canal_encontrado = ""

    for ch in range(1, 7):
        try:
            senial = acq.signal(ch)
            canal_encontrado = f"Canal {ch}"
            break
        except:
            continue

    if senial is None:
        print(f"No se encontraron canales válidos (1-6) en {file_path}")
        continue

    # Restamos la media para centrar la señal
    senial = senial - np.mean(senial)

    # -------------------------------------------------
    # REDUCIMOS EL TAMAÑO AQUÍ: figsize=(ancho, alto)
    # -------------------------------------------------
    fig, axs = plt.subplots(3, 1, figsize=(8, 7))

    # Título principal (le bajé un poquito el tamaño de la letra a 16)
    fig.suptitle(f'Análisis de Señal: {nombre_archivo} ({canal_encontrado})',
                 fontsize=16, fontweight='bold', color='darkblue')

    # Ajustamos el espaciado (pad más pequeño) para este nuevo tamaño
    fig.tight_layout(pad=3.0, rect=[0, 0, 1, 0.95])

    # -------------------------------------------------
    # 1. SEÑAL EN EL TIEMPO (RAW)
    # -------------------------------------------------
    tiempo = np.arange(len(senial)) / fs
    axs[0].plot(tiempo, senial, color='royalblue', linewidth=0.8)
    axs[0].set_title('Señal en el Dominio del Tiempo', fontsize=12, fontweight='bold')
    axs[0].set_xlabel('Tiempo [s]', fontsize=10)
    axs[0].set_ylabel('Amplitud [mV]', fontsize=10)
    axs[0].grid(True, linestyle='--', alpha=0.7)

    # -------------------------------------------------
    # 2. TRANSFORMADA RÁPIDA DE FOURIER (FFT)
    # -------------------------------------------------
    N = len(senial)
    fft_vals = np.fft.fft(senial)
    fft_freqs = np.fft.fftfreq(N, 1/fs)

    half_N = N // 2
    axs[1].plot(fft_freqs[:half_N], np.abs(fft_vals)[:half_N], color='crimson', linewidth=0.8)
    axs[1].set_title('Espectro de Frecuencia (FFT)', fontsize=12, fontweight='bold')
    axs[1].set_xlabel('Frecuencia [Hz]', fontsize=10)
    axs[1].set_ylabel('Magnitud', fontsize=10)
    axs[1].set_xlim(0, fs/2)
    axs[1].grid(True, linestyle='--', alpha=0.7)

    # -------------------------------------------------
    # 3. ESPECTROGRAMA (STFT)
    # -------------------------------------------------
    Pxx, freqs, bins, im = axs[2].specgram(senial, NFFT=256, Fs=fs, noverlap=128, cmap='viridis')
    axs[2].set_title('Espectrograma (STFT)', fontsize=12, fontweight='bold')
    axs[2].set_xlabel('Tiempo [s]', fontsize=10)
    axs[2].set_ylabel('Frecuencia [Hz]', fontsize=10)

    cbar = fig.colorbar(im, ax=axs[2])
    cbar.set_label('Densidad de Potencia (dB)', rotation=270, labelpad=15)

    plt.show()
```

### 📊 Resultado del ploteo en Python

#### Baseline de Brazo
<img src="https://raw.githubusercontent.com/Nestor20193767/PULSEV-ISB-2026-I/main/Laboratorios/Laboratorio%204/Videos%20y%20Fotos/Ploteo%20de%20Se%C3%B1ales/BASELINE_BRAZO.jpeg" width="600" alt="Baseline Brazo">

#### Baseline de Mano
<img src="https://raw.githubusercontent.com/Nestor20193767/PULSEV-ISB-2026-I/main/Laboratorios/Laboratorio%204/Videos%20y%20Fotos/Ploteo%20de%20Se%C3%B1ales/BASELINE_MANO.jpeg" width="600" alt="Baseline Mano">

#### EMG del Brazo
<img src="https://raw.githubusercontent.com/Nestor20193767/PULSEV-ISB-2026-I/main/Laboratorios/Laboratorio%204/Videos%20y%20Fotos/Ploteo%20de%20Se%C3%B1ales/EMG_BRAZO.jpeg" width="600" alt="EMG Brazo">

#### EMG de la Mano
<img src="https://raw.githubusercontent.com/Nestor20193767/PULSEV-ISB-2026-I/main/Laboratorios/Laboratorio%204/Videos%20y%20Fotos/Ploteo%20de%20Se%C3%B1ales/EMG_MANO.jpeg" width="600" alt="EMG Mano">

---

## Archivos

| Archivo | Descripción |
|---|---|
| [`señal_EMG.txt`](./Señal%20y%20Script) | Archivo raw exportado desde OpenSignals (r)evolution |
| [`ploteo_EMG.py`](./Señal%20y%20Script/Script) | Script de Python para procesamiento y visualización |
| `Videos y Fotos/` | Carpeta con capturas de fotos y videos del laboratorio |
| `Ploteo de Señales/` | Carpeta con capturas de las señales con su fft y sft|


---

## Discusión y Conclusiones

- La señal EMG adquirida con BITalino permitió diferenciar claramente el estado de **reposo** de las **fases de contracción muscular**. En las señales de baseline de mano y bíceps se observó una actividad de menor amplitud, mientras que durante las contracciones aparecieron ráfagas de mayor amplitud asociadas a la activación muscular.

- Este comportamiento es coherente con la fisiología de la señal EMG superficial, ya que durante una contracción voluntaria aumenta el reclutamiento de unidades motoras y, por tanto, la actividad eléctrica registrada en la superficie de la piel.

- Al comparar los músculos evaluados, la señal del **bíceps** presentó una activación más evidente que la señal de la **mano**. Esto puede explicarse porque el bíceps braquial es un músculo de mayor tamaño y participa en una contracción más global, mientras que el abductor pollicis brevis está asociado a movimientos finos del pulgar y puede generar señales de menor amplitud relativa.

- El análisis en el dominio de la frecuencia mediante **FFT** y el análisis tiempo-frecuencia mediante **espectrograma (STFT)** permitieron observar el contenido frecuencial de la señal EMG durante reposo y contracción. Esto es coherente con estudios recientes que analizan la sEMG en rangos aproximados de 20–450 Hz para conservar la información muscular relevante y reducir componentes asociadas a artefactos de movimiento o ruido.

- La amplitud del EMG **no equivale directamente a la fuerza muscular generada**. Aunque una mayor contracción suele producir mayor amplitud EMG, esta relación depende del procesamiento de la señal, la posición de los electrodos, el tejido subcutáneo, el contacto piel-electrodo y el posible crosstalk de músculos cercanos.

- Entre las principales limitaciones del laboratorio se identifican la ausencia de una medición directa de fuerza, la posible variabilidad en la colocación de los electrodos y la presencia de ruido o artefactos por movimiento. Por ello, los resultados permiten interpretar la activación muscular, pero no cuantificar directamente la fuerza producida.
  
- Estos resultados coinciden con lo reportado por Lim et al. (2024), quienes describen el uso de señales sEMG para evaluar activación muscular y resaltan la importancia del análisis frecuencial y la calidad de señal. Asimismo, Ranaldi et al. (2022) indican que la relación entre amplitud sEMG y fuerza no es directa ni universal, sino que depende del procesamiento y de las condiciones experimentales.

---
## Referencias

1. BITalino (r)evolution Home Guide #1 — Electromyography (EMG). PLUX – Wireless Biosignals, S.A. (2021).
2. Malmivuo, J. & Plonsey, R. *Bioelectromagnetism*. Oxford University Press, 1995.
3. Basmajian, J.V. & De Luca, C.J. *Muscles Alive: Their Functions Revealed by Electromyography*, 5th ed. Williams & Wilkins, 1985.
4. Criswell, E. *Cram's Introduction to Surface Electromyography*. Jones & Bartlett Publishers, 2010.
5. SENIAM — Recommended sensor placements: http://www.seniam.org/
6. Lim, J., Lu, L., Goonewardena, K., Liu, J. Z., & Tan, Y. *Assessment of Self-report, Palpation, and Surface Electromyography Dataset During Isometric Muscle Contraction*. Scientific Data, 11, 208, 2024. https://doi.org/10.1038/s41597-024-03030-8
7. Ranaldi, S., Corvini, G., De Marchis, C., & Conforto, S. *The Influence of the sEMG Amplitude Estimation Technique on the EMG–Force Relationship*. Sensors, 22(11), 3972, 2022. https://doi.org/10.3390/s22113972

---

## Preguntas de la Guia

**Q1. ¿Cuáles son las frecuencias significativas para las adquisiciones de EMG? ¿Son las mismas en todas las áreas del cuerpo, como el área facial?**

Para las señales de electromiografía de superficie (sEMG), la banda de frecuencia típica que contiene la información de la actividad muscular se encuentra entre los 20 y los 450 Hz. Esta banda estándar se aplica para la evaluación de músculos esqueléticos voluntarios en general. Sin embargo, la distribución espectral exacta puede variar sutilmente dependiendo del área del cuerpo, ya que está ligada al tamaño del músculo y a la cantidad de fibras musculares. Por ejemplo, los músculos grandes de las extremidades superiores difieren de los músculos finos del rostro (controlados por menos unidades motoras). En el caso escogido del pulgar, al realizar el movimiento de pinza (_pitching_), estamos evaluando fibras diseñadas para la motricidad fina y precisión, pero su señal eléctrica superficial sigue siendo procesada óptimamente dentro de este mismo filtro pasabanda de 20-450 Hz. [1]

**Q2. ¿Qué tipo de filtro es esencial al trabajar con señales EMG? ¿Por qué necesitamos aplicar dicho filtro?** 

El filtro más esencial es el filtro pasabanda, ajustado habitualmente entre 20 y 450 Hz. Necesitamos aplicarlo porque las señales mioeléctricas captadas desde la superficie de la piel poseen amplitudes sumamente bajas, en el rango de los milivoltios o microvoltios. Debido a esta baja amplitud, la señal es altamente vulnerable a fuentes de ruido y artefactos mecánicos generados por el movimiento. Al filtrar la señal, eliminamos estas frecuencias indeseadas y nos aseguramos de que los datos limitados entregados por el sensor correspondan genuinamente a despolarizaciones musculares. [2]

**Q3. ¿Cómo difiere la amplitud en cada contracción muscular? ¿Existe diferencia según la ubicación en el cuerpo?**

La amplitud difiere directamente con la intensidad de la activación neuromuscular; en un estado de reposo, la línea base se mantiene cercana a 0 mV, mientras que al contraerse se evidencian ráfagas de mayor amplitud (por ejemplo, ±0.5 mV). Definitivamente existe una gran diferencia dependiendo de la ubicación anatómica. Músculos más grandes generarán voltajes superficiales mayores simplemente por la mayor cantidad de fibras musculares involucradas en la contracción, a diferencia de los músculos periféricos más pequeños. [3]

**Q4. Muestra una captura de pantalla de una porción relevante de los datos de EMG (Sección D) de un músculo facial de interés. ¿Corresponde esta señal a lo que esperabas? ¿Por qué? ¿Qué emoción y acción realizaste? ¿Qué músculo activaste?**

Debido a que escogimos el ejercicio del _pitching_ para este análisis enfoqué los electrodos a lo largo de la fibra del _abductor pollicis brevis_, situado en la base del pulgar de la mano y realizamos la abducción voluntaria del pulgar , ejecutando el movimiento de "pinza" o _pitching_ de forma repetitiva.
La morfología de la señal cumplió con la teoría fisiológica: se observó una zona neutra de bajo voltaje durante la fase de relajación , seguida de ráfagas (_bursts_) de alta frecuencia y amplitud en el momento exacto en que las neuronas motoras inferiores desencadenaron los potenciales de acción en las células musculares para ejecutar el agarre. [4]


**Q5. A tu leal saber y entender, ¿la amplitud del EMG es igual a la cantidad de fuerza que has generado con tu músculo?**

No, no existe una equivalencia lineal estricta entre la amplitud de la señal (mV) y la fuerza mecánica producida (Newtons), aunque sí se encuentran altamente correlacionadas y pudimos verlo durante el laboratorio. A mayor requerimiento de fuerza, el sistema neuromuscular lógicamente recluta más unidades motoras y eleva la frecuencia de disparo de los potenciales de acción. 

Sin embargo, diversos factores complican esta relación directa en la superficie: el grosor del tejido adiposo, la alta impedancia de la piel, y la superposición de señales de músculos adyacentes (_crosstalk_). Además, durante episodios de fatiga, la amplitud puede mostrar un aumento inicial paradójico (por reclutamiento compensatorio) seguido de una reducción paulatina. Los estudios biomecánicos confirman esta falta de equivalencia 1:1 en la electromiografía superficial.

---

## Bibliografia de las preguntas

1. J. Moreno Jiménez, A. Hernández Zavala, and A. G. Morales Hernández, "High density surface electromyography: A review of technology and its applications," _Measurement and Control_, Apr. 2026, doi: 10.1177/00202940251396.
2. J. L. Correa-Figueroa, E. Morales-Sánchez, J. A. Huerta-Ruelas, J. J. González-Barbosa, and C. R. Cárdenas-Pérez, "Sistema de Adquisición de Señales SEMG para la Detección de Fatiga Muscular," _Revista Mexicana de Ingeniería Biomédica_, vol. 37, no. 1, pp. 17-27, Jan.-Apr. 2016, doi: 10.17488/RMIB.37.1.4.
3. J. J. Bernal Sánchez and E. C. Wilches Luna, "Electromiografía de superficie (EMGs) en pacientes adultos en cuidados intensivos: revisión exploratoria," _Revista Colombiana de Medicina Física y Rehabilitación_, vol. 31, no. 1, Jan.-Jun. 2021, doi: 10.28957/rcmfr.v31n1a1.
4. S. Abbaspour, M. Lindén, H. Gholamhosseini, A. Naber, and M. Ortiz-Catalan, "Evaluation of surface EMG-based recognition algorithms for decoding hand movements," _Med. Biol. Eng. Comput._, vol. 58, no. 1, pp. 83-100, Jan. 2020, doi: 10.1007/s11517-019-02073-z.
5. C. Disselhorst-Klug, T. Schmitz-Rode, and G. Rau, "Surface electromyography and muscle force: Limits in sEMG-force relationship and new approaches for applications," _Clinical Biomechanics_, vol. 24, no. 3, pp. 225-235, Mar. 2009, doi: 10.1016/j.clinbiomech.2008.08.003.
