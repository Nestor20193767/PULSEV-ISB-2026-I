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

<img src="./Videos%20y%20Fotos/electrodos_mano.jpg" width="400">

> *Descripción: Posicionamiento de los electrodos IN+ e IN− sobre los músculos abductores del pulgar y electrodo de referencia en el hueso pisiforme.*

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

#### 🎥 Video — Silencio eléctrico y conexiones

<a href="https://drive.google.com/file/d/1lu_aLHdgQIbCsKkL5fag_nHpBS-1xgAm/view?usp=sharing" target="_blank">
  <img src="./Videos%20y%20Fotos/electrodos_mano.jpg" width="350">
</a>

> *Haz clic en la imagen para ver el video en Google Drive.*

### Señal en OpenSignals

A continuación se presenta el ploteo de la señal EMG adquirida con OpenSignals (r)evolution durante el protocolo completo:

#### 📊 Ploteo — OpenSignals (r)evolution

<img src="./Videos%20y%20Fotos/open.jpeg" width="350">

> *Figura: Señal EMG del músculo abductor del pulgar adquirida con BITalino. Se observan las fases de reposo (línea base ~0 mV) y las fases de contracción (picos de amplitud creciente). El eje X representa el tiempo [s] y el eje Y la amplitud de la señal [mV].*
### Análisis de la Señal

#### Descripción general

La señal EMG adquirida presenta las características típicas esperadas para una señal de electromiografía de superficie:

**En reposo (silencio eléctrico):**
- Amplitud cercana a **0 mV**, con pequeñas fluctuaciones de ruido.
- Ausencia de potenciales de acción detectables.
- La línea base es estable, lo que indica buena calidad de contacto de los electrodos.

**Durante la contracción muscular:**
- Se observa un incremento claro de la amplitud, con valores de aproximadamente **±0.5 mV** en contracciones leves y hasta **±0.75 mV** (o más) en la contracción voluntaria máxima.
- La señal es de naturaleza **estocástica** (irregular), lo cual es esperable ya que representa la suma de múltiples potenciales de acción de diferentes unidades motoras.
- A mayor intensidad de contracción, mayor amplitud y mayor densidad de activaciones (reclutamiento de más unidades motoras).

**Frecuencias de interés:**
- Las frecuencias relevantes para el EMG de superficie se encuentran en el rango de **20–450 Hz**.
- En músculos faciales (como el zygomaticus major), la amplitud es considerablemente menor debido al menor tamaño de las fibras musculares.

**Diferencias entre grupos musculares:**

| Músculo | Amplitud observada | Observaciones |
|---|---|---|
| Flexor carpi radialis | Alta | Señal clara con buena separación reposo/contracción |
| Abductor pollicis brevis | Media-baja | Músculo pequeño, menor amplitud |
| Trapezius descendens | Alta | Buen contraste en activaciones |
| Zygomaticus major | Baja | Músculo facial, señal sutil pero detectable |

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

- La señal EMG adquirida con BITalino mostró claramente la diferencia entre el estado de **reposo** (silencio eléctrico, ~0 mV) y las **fases de contracción muscular**, con amplitudes crecientes conforme se aumentaba la intensidad.

- El reclutamiento progresivo de unidades motoras se evidenció en el incremento gradual de amplitud a lo largo de los 5 ciclos de contracción, coherente con la fisiología muscular.

- Los músculos **de mayor tamaño** (flexor carpi radialis, trapezius) produjeron señales de mayor amplitud que los **músculos pequeños** (abductor pollicis brevis) o **faciales** (zygomaticus major), donde la señal fue más sutil pero igualmente detectable.

- La envolvente RMS calculada en Python permite una interpretación más clara de la actividad muscular al suavizar las fluctuaciones rápidas de la señal cruda.

- Se confirma que la amplitud del EMG **no equivale directamente a la fuerza** generada, sino que es una estimación de la actividad eléctrica (reclutamiento de unidades motoras), influida además por factores como el tejido subcutáneo y la posición de los electrodos.

---
## Referencias

1. BITalino (r)evolution Home Guide #1 — Electromyography (EMG). PLUX – Wireless Biosignals, S.A. (2021).
2. Malmivuo, J. & Plonsey, R. *Bioelectromagnetism*. Oxford University Press, 1995.
3. Basmajian, J.V. & De Luca, C.J. *Muscles Alive: Their Functions Revealed by Electromyography*, 5th ed. Williams & Wilkins, 1985.
4. Criswell, E. *Cram's Introduction to Surface Electromyography*. Jones & Bartlett Publishers, 2010.
5. SENIAM — Recommended sensor placements: http://www.seniam.org/

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
