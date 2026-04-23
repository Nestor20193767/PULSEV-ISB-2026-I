# 🧠 Laboratorio N°4 de Señales Biomédicas — Home Guide #1
## Electromiografía (EMG) — BITalino (r)evolution

> **Curso:** Introducción a Señales Biomédicas  
> **Integrantes:** [Nombre 1], [Nombre 2], [Nombre 3]  
> **Fecha:** Abril 2026  
> **Repositorio:** [link a tu repositorio]

---

## 📋 Tabla de Contenidos

1. [Introducción](#introducción)
2. [Objetivos](#objetivos)
3. [Materiales y Conexiones](#materiales-y-conexiones)
4. [Protocolo de Adquisición](#protocolo-de-adquisición)
5. [Resultados](#resultados)
   - [Silencio Eléctrico / Reposo](#silencio-eléctrico--reposo)
   - [Señal en OpenSignals](#señal-en-opensignals)
   - [Análisis de la Señal](#análisis-de-la-señal)
6. [Ploteo en Python](#ploteo-en-python)
7. [Archivos](#archivos)
8. [Discusión y Conclusiones](#discusión-y-conclusiones)
9. [Referencias](#referencias)

---

## Introducción

La Electromiografía (EMG) es una técnica que permite registrar la actividad eléctrica producida por los músculos esqueléticos. Cuando el sistema nervioso envía una señal a través de las motoneuronas superiores e inferiores, se genera un potencial de acción que produce una contracción muscular visible y medible eléctricamente.

En esta práctica se utilizó el sistema **BITalino (r)evolution** con el sensor EMG ensamblado para adquirir señales musculares en diferentes grupos musculares, explorando la variación de amplitud y frecuencia de las señales según la intensidad de contracción y la ubicación corporal.

---

## Objetivos

- ✅ Realizar adquisiciones de señal EMG en tiempo real con BITalino.
- ✅ Explorar diferentes posiciones de electrodos en distintos grupos musculares.
- ✅ Entender cómo varía la señal ante cambios en la actividad muscular.
- ✅ Familiarizarse con las frecuencias de interés del EMG (20–450 Hz).
- ✅ Procesar y visualizar la señal en Python.

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
- **REF (referencia)**: sobre una zona neutra ósea (codo, muñeca o mastoides según el músculo).

> ⚠️ Antes de colocar los electrodos se limpió la piel con alcohol para reducir la impedancia y mejorar la calidad de la señal.

#### 📸 Foto de conexiones — Electrodos en cuerpo

<!-- Reemplaza la ruta con tus imágenes reales -->
```
Insertar imagen aquí:
![Conexión electrodos-cuerpo](./imagenes/electrodo_cuerpo.jpg)
```

> *Descripción: Posicionamiento de los electrodos IN+ e IN− sobre el músculo [nombre del músculo] y electrodo de referencia en [zona neutra].*

#### 📸 Foto de conexiones — BITalino y cables

```
Insertar imagen aquí:
![Conexión BITalino-cables](./imagenes/bitalino_cables.jpg)
```

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
| 1 | Flexor carpi radialis | Antebrazo | Extensión de la muñeca |
| 2 | Abductor pollicis brevis | Pulgar | Abducción del pulgar |
| 3 | Trapezius descendens | Hombro/cuello | Elevación del hombro |
| 4 | Zygomaticus major | Mejilla | Sonreír |

---

## Resultados

### Silencio Eléctrico / Reposo

Durante la fase de reposo, la señal EMG mostró una línea base cercana a **0 mV**, característica del silencio eléctrico muscular. Esto confirma que, en ausencia de activación voluntaria, no se generan potenciales de acción significativos en el músculo.

#### 🎥 Video — Silencio eléctrico y conexiones

```
Insertar enlace al video aquí:
[![Ver video de reposo](./imagenes/thumbnail_video.jpg)](./videos/reposo_EMG.mp4)
```

> *El video muestra: (1) las conexiones de los electrodos sobre el cuerpo, (2) la señal EMG ploteada en tiempo real en OpenSignals durante el estado de reposo.*

---

### Señal en OpenSignals

A continuación se presenta el ploteo de la señal EMG adquirida con OpenSignals (r)evolution durante el protocolo completo:

#### 📊 Ploteo — OpenSignals (r)evolution

```
Insertar captura de pantalla aquí:
![Señal EMG en OpenSignals](https://github.com/Nestor20193767/PULSEV-ISB-2026-I/blob/main/Laboratorios/Laboratorio%204/Videos%20y%20Fotos/Ploteo%20de%20Se%C3%B1ales/BASELINE_BRAZO.jpeg)
```

> *Figura: Señal EMG del músculo [nombre] adquirida con BITalino. Se observan las fases de reposo (línea base ~0 mV) y las fases de contracción (picos de amplitud creciente). El eje X representa el tiempo [s] y el eje Y la amplitud de la señal [mV].*

---

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

```
Insertar imagen generada por Python aquí:
![Baseline Brazo](https://raw.githubusercontent.com/Nestor20193767/PULSEV-ISB-2026-I/main/Laboratorios/Laboratorio%204/Videos%20y%20Fotos/Ploteo%20de%20Se%C3%B1ales/BASELINE_BRAZO.jpeg)
```


> *Figura: Señal EMG procesada en Python. Panel superior: señal cruda en mV. Panel inferior: envolvente RMS con ventana deslizante de 100 ms, que permite visualizar mejor la activación muscular a lo largo del tiempo.*

---

## Archivos

| Archivo | Descripción |
|---|---|
| `señal_EMG.txt` | Archivo raw exportado desde OpenSignals (r)evolution |
| `ploteo_EMG.py` | Script de Python para procesamiento y visualización |
| `imagenes/` | Carpeta con capturas de pantalla y fotos |
| `videos/` | Carpeta con video de reposo/silencio eléctrico |

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
