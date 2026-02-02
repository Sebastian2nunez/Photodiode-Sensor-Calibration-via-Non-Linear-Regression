# Calibración de Sensores UV mediante Regresión No Lineal

Sistema integrado Arduino-Python para calibración de fotodiodos en entornos controlados de laboratorio, aplicado a experimentos de astrobiología.

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Arduino](https://img.shields.io/badge/Arduino-IDE-00979D.svg)](https://www.arduino.cc/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 📋 Descripción

Este proyecto desarrolla un **procedimiento sistemático de calibración** para sensores de radiación UV (fotodiodos) utilizados en experimentos de astrobiología. El sistema permite cuantificar con precisión la irradiancia UV que reciben muestras microbiológicas en entornos controlados.

### Logro Principal

Formulación y validación de un **modelo matemático de calibración** que relaciona el voltaje de salida del sensor con la irradiancia incidente, considerando:
- Responsividad espectral del fotodiodo
- Corrección por corriente oscura
- Validación estadística mediante R² y RMSE

La ecuación desarrollada permite convertir lecturas digitales del microcontrolador a valores calibrados de irradiancia (W/m²).

## 🎯 Objetivos

- **Calibrar sensores UV** (GUVA-S12SD, ML8511) con fuentes de radiación conocidas
- **Evaluar transmitancia** de materiales ópticos (vidrio vs PDMS) en diferentes longitudes de onda
- **Desarrollar metodología reproducible** para caracterización de sensores en laboratorio

## 🔬 Resultados Destacados

1. **Calibración validada** de sensores UV con métricas estadísticas (R², RMSE)
2. **Relación inversamente proporcional** entre irradiancia y distancia confirmada experimentalmente
3. **Caracterización de materiales**:
   - PDMS y vidrio tienen ~100% transmitancia en UVA (390 nm)
   - PDMS superior a vidrio en transmitancia UVB (310 nm)

## 🛠️ Stack Técnico

### Hardware
- **Microcontrolador:** Arduino (Leonardo/Uno/Mega compatible)
- **Sensores:** GUVA-S12SD, ML8511 (fotodiodos UV)
- **Fuentes de radiación:**
  - Simulador solar Ossila (350-1000 nm)
  - LED UVB 310nm (TAOYUAN)

### Software
- **Python 3.8+:** Análisis de datos y visualización
  - NumPy, SciPy (regresión no lineal)
  - Pandas (procesamiento de datos)
  - Matplotlib, Seaborn (visualización)
- **Arduino IDE:** Adquisición de datos desde sensores
- **Jupyter Notebook:** Análisis interactivo

## 📂 Estructura del Repositorio

```
photodiode-sensor-calibration/
│
├── arduino/
│   └── sensor_acquisition.ino    # Código Arduino para lectura de sensores
│
├── notebooks/
│   └── calibration_analysis.ipynb  # Análisis completo y visualizaciones
│
├── data/
│   ├── raw/                       # Datos experimentales (XLSX)
│   └── processed/                 # Datos procesados
│
├── results/
│   └── figures/                   # Gráficos generados
│
└── README.md
```

## 🚀 Uso

### 1. Configuración del Hardware

1. Cargar `sensor_acquisition.ino` al Arduino
2. Conectar sensor GUVA-S12SD según diagrama de pines
3. Conectar Arduino a PC vía USB

### 2. Ejecución del Análisis

```bash
# Clonar repositorio
git clone https://github.com/Sebastian2nunez/Photodiode-Sensor-Calibration.git
cd Photodiode-Sensor-Calibration

# Instalar dependencias
pip install -r requirements.txt

# Ejecutar notebook de análisis
jupyter notebook notebooks/calibration_analysis.ipynb
```

### 3. Calibración de Nuevos Sensores

El notebook `calibration_analysis.ipynb` incluye:
- Lectura de datos desde Arduino
- Conversión de lecturas ADC a voltaje
- Aplicación del modelo de calibración
- Cálculo de irradiancia corregida
- Visualización de resultados

## 📊 Metodología de Calibración

### Modelo Matemático

La conversión de voltaje a irradiancia se realiza mediante:

1. **Conversión ADC a Voltaje:**
   ```
   V_sensor = (lectura_ADC / 1023) × V_ref
   ```

2. **Corrección por Corriente Oscura:**
   ```
   V_corregido = V_sensor - V_dark
   ```

3. **Cálculo de Irradiancia:**
   ```
   E = V_corregido / (A × R × S(λ))
   ```
   
   Donde:
   - E: Irradiancia (W/m²)
   - A: Area del fotodiodo
   - R: Resistencia de carga (Ω)
   - S(λ): Responsividad espectral (A/W)

### Validación Estadística

- **Métricas utilizadas:** R², RMSE
- **Método:** Validación cruzada con fuentes calibradas
- **Reproducibilidad:** Metodología documentada paso a paso

## 🔍 Aplicaciones

- **Astrobiología:** Cuantificación de dosis UV en muestras microbiológicas
- **Óptica:** Caracterización de transmitancia de materiales
- **Instrumentación:** Calibración de sensores de bajo costo para investigación

## 📈 Trabajo Futuro

- [ ] Calibración completa del sensor GUVA-S12SD
- [ ] Caracterización de irradiancia en canales microfluídicos
- [ ] Evaluación de transmitancia en función de altura/grosor de PDMS
- [ ] Automatización completa del proceso de calibración

## 📄 Licencia

MIT License - ver archivo [LICENSE](LICENSE) para más detalles.

## 📧 Contacto

**Sebastián Núñez**  
📧 sebastian.mauricio.nunez@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/sebastian-mauricio-nuñez)  
💻 [GitHub](https://github.com/Sebastian2nunez)

---

⭐ Si este proyecto te resulta útil, considera darle una estrella en GitHub
