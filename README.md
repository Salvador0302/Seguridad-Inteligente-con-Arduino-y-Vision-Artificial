# 🔒 Seguridad Inteligente con Arduino y Visión Artificial

Sistema de seguridad inteligente que integra Arduino, sensores, visión artificial y análisis de datos para monitoreo y detección de eventos.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![Arduino](https://img.shields.io/badge/Arduino-00979D?logo=arduino&logoColor=white)](https://www.arduino.cc/)

---

## 📋 Tabla de Contenidos

- [Características](#-características)
- [Estructura del Proyecto](#-estructura-del-proyecto)
- [Requisitos](#-requisitos)
- [Instalación](#-instalación)
- [Uso](#-uso)
- [Notebooks](#-notebooks)
- [Configuración](#-configuración)
- [Contribuir](#-contribuir)
- [Licencia](#-licencia)

---

## ✨ Características

- 📊 **Ingesta y procesamiento de datos** desde exportaciones de Telegram
- 🔍 **Análisis exploratorio (EDA)** con visualizaciones interactivas
- ⚙️ **Feature Engineering** para análisis avanzados
- 🤖 **Integración con Arduino** para sensores (PIR, puertas, etc.)
- 📸 **Visión artificial** con OpenCV para detección de objetos
- 📈 **Reportes automáticos** en Markdown con gráficos
- 🔔 **Sistema de alertas** en tiempo real

---

## 📁 Estructura del Proyecto

```
Seguridad-Inteligente-con-Arduino-y-Vision-Artificial/
├── README.md                          # Documentación principal
├── LICENSE                            # Licencia MIT
├── .gitignore                         # Archivos ignorados por git
├── .env.example                       # Plantilla de variables de entorno
├── requirements.txt                   # Dependencias de Python
│
├── configs/
│   └── config.yaml                    # Configuración del proyecto
│
├── notebooks/
│   ├── 01_ingesta_y_limpieza.ipynb    # Notebook de ingesta de datos
│   └── 02_eda_y_features.ipynb        # Notebook de EDA y features
│
├── src/
│   ├── ingest.py                      # Módulo de ingesta de datos
│   ├── features.py                    # Módulo de feature engineering
│   └── eda.py                         # Módulo de análisis exploratorio
│
├── data/
│   ├── raw/
│   │   └── telegram_export/           # Datos exportados de Telegram
│   │       ├── result.json            # Archivo JSON con mensajes
│   │       └── photos/                # Carpeta con fotografías
│   └── processed/
│       └── events_clean.csv           # Datos procesados y limpios
│
└── reports/
    ├── informe_EDA.md                 # Informe de análisis
    └── figures/                       # Gráficos generados
```

---

## 🔧 Requisitos

### Software

- **Python** 3.10 o superior
- **Arduino IDE** (para programación de Arduino)
- **Git** para control de versiones

### Hardware (Opcional)

- Arduino UNO/Mega
- Sensor PIR (movimiento)
- Sensores magnéticos (puertas/ventanas)
- Cámara USB o módulo de cámara
- Buzzer o LED para alarmas

---

## 🚀 Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/Salvador0302/Seguridad-Inteligente-con-Arduino-y-Vision-Artificial.git
cd Seguridad-Inteligente-con-Arduino-y-Vision-Artificial
```

### 2. Crear entorno virtual

```bash
python -m venv venv

# En Linux/Mac
source venv/bin/activate

# En Windows
venv\Scripts\activate
```

### 3. Instalar dependencias

```bash
pip install -r requirements.txt
```

### 4. Configurar variables de entorno

```bash
cp .env.example .env
# Edita .env con tus credenciales
```

---

## 💻 Uso

### 1. Preparar los datos

Coloca tu exportación de Telegram en `data/raw/telegram_export/`:

```
data/raw/telegram_export/
├── result.json
└── photos/
```

Ver instrucciones detalladas en `data/raw/telegram_export/README.md`

### 2. Ejecutar ingesta de datos

```bash
python src/ingest.py
```

O usando el notebook: `notebooks/01_ingesta_y_limpieza.ipynb`

### 3. Generar características

```bash
python src/features.py
```

### 4. Análisis exploratorio

```bash
python src/eda.py
```

O usando el notebook: `notebooks/02_eda_y_features.ipynb`

### 5. Ver el informe

El informe generado estará en: `reports/informe_EDA.md`

---

## 📓 Notebooks

### 01_ingesta_y_limpieza.ipynb

- Carga de datos desde Telegram
- Limpieza y preprocesamiento
- Exploración inicial
- Guardado de datos limpios

### 02_eda_y_features.ipynb

- Feature engineering completo
- Análisis exploratorio visual
- Generación de gráficos interactivos
- Creación de informes

**Para ejecutar los notebooks:**

```bash
jupyter notebook notebooks/
```

---

## ⚙️ Configuración

Edita `configs/config.yaml` para personalizar:

- Rutas de datos
- Configuración de Arduino
- Parámetros de cámara
- Umbrales de detección
- Opciones de visualización

### Ejemplo de configuración:

```yaml
data:
  raw_path: "data/raw/telegram_export/"
  processed_path: "data/processed/"

arduino:
  port: "/dev/ttyUSB0"
  baud_rate: 9600

camera:
  index: 0
  resolution:
    width: 640
    height: 480
```

---

## 🔐 Variables de Entorno

Crea un archivo `.env` basado en `.env.example`:

```bash
# Telegram API
TELEGRAM_API_ID=your_api_id
TELEGRAM_API_HASH=your_api_hash
TELEGRAM_PHONE=your_phone

# Arduino
ARDUINO_PORT=/dev/ttyUSB0
ARDUINO_BAUD_RATE=9600

# Cámara
CAMERA_INDEX=0
```

---

## 📊 Pipeline de Datos

```
1. Exportación Telegram → result.json + photos/
                          ↓
2. Ingesta (src/ingest.py) → events_clean.csv
                          ↓
3. Features (src/features.py) → events_features.csv
                          ↓
4. EDA (src/eda.py) → informe_EDA.md + figures/
```

---

## 🤝 Contribuir

Las contribuciones son bienvenidas. Por favor:

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

---

## 📝 Licencia

Este proyecto está bajo la Licencia MIT. Ver archivo `LICENSE` para más detalles.

---

## 👤 Autor

**Salvador0302**

- GitHub: [@Salvador0302](https://github.com/Salvador0302)

---

## 🙏 Agradecimientos

- OpenCV por las herramientas de visión artificial
- Arduino por la plataforma de hardware
- Telegram por la API de mensajería
- Comunidad de Python y Data Science

---

## 📞 Soporte

Si tienes preguntas o problemas:

1. Revisa la documentación en los notebooks
2. Abre un [Issue](https://github.com/Salvador0302/Seguridad-Inteligente-con-Arduino-y-Vision-Artificial/issues)
3. Consulta la Wiki del proyecto (próximamente)

---

**⭐ Si te gusta este proyecto, dale una estrella en GitHub!**
