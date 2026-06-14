# proyecto3-EDA-Arnaldo

# Proyecto 3 · EDA Covid-19 en Estados Unidos

Análisis Exploratorio de Datos (EDA) sobre la evolución de la pandemia de Covid-19 en Estados Unidos, utilizando los datos diarios recopilados por [The Covid Tracking Project](https://covidtracking.com/data/download) hasta marzo de 2021.

El objetivo del proyecto es extraer conclusiones claras y respaldadas por datos sobre la evolución de la pandemia (casos, muertes, hospitalizaciones, testeo y letalidad), presentadas en un informe ejecutivo orientado a la toma de decisiones.

## Contenido del repositorio

```
proyecto3/
├── notebooks/
│   └── 01_eda_covid19.ipynb   # Notebook con todo el análisis
├── data/
│   └── us_daily.csv            # Dataset descargado de la API (se genera al ejecutar el notebook)
├── images/                      # Gráficas exportadas
├── reports/
│   └── informe_ejecutivo.pdf   # Informe ejecutivo con las conclusiones
├── requirements.txt
├── .gitignore
└── README.md
```

## Fuente de datos

Los datos se descargan automáticamente desde la API pública de The Covid Tracking Project:

```
https://api.covidtracking.com/v1/us/daily.csv
```

El dataset contiene 420 registros diarios (enero 2020 - marzo 2021) con 25 variables, incluyendo casos positivos, fallecimientos, hospitalizaciones, pacientes en UCI, pacientes con ventilación mecánica y resultados de tests.

## Instalación y ejecución

### 1. Clonar el repositorio

```bash
git clone https://github.com/Bootcamp-IA-MAD-P7/proyecto3-EDA-Arnaldo.git
cd proyecto3-EDA-Arnaldo
```

### 2. Crear y activar el entorno virtual

```bash
python -m venv .venv

# Windows
.venv\Scripts\activate

# Mac / Linux
source .venv/bin/activate
```

### 3. Instalar las dependencias

```bash
pip install -r requirements.txt
```

### 4. Ejecutar el notebook

Abre `notebooks/01_eda_covid19.ipynb` en VS Code o Jupyter, selecciona el kernel `.venv` y ejecuta las celdas en orden. La primera celda descarga el dataset automáticamente y lo guarda en `data/`.

## Resumen del análisis

El notebook está organizado en los siguientes bloques:

1. **Carga de datos**: descarga del dataset desde la API y primera inspección (`info()`, `describe()`, nulos).
2. **Limpieza y preprocesado**: eliminación de columnas sin valor analítico, conversión de fechas, ordenación cronológica y tratamiento de valores nulos.
3. **Análisis exploratorio**:
   - Evolución temporal de casos y muertes (diarios y acumulados, con media móvil de 7 días)
   - Tasa de mortalidad acumulada (CFR)
   - Tasa de positividad de tests
   - Presión hospitalaria (hospitalizados, UCI, ventilación mecánica)
   - Matriz de correlación entre variables clave

## Principales hallazgos

- Estados Unidos atravesó **tres olas de contagio** de intensidad creciente, siendo la tercera (invierno 2020-2021) la más severa con diferencia.
- Existe un **desfase de 2 a 4 semanas** entre el pico de contagios y el pico de fallecimientos, útil como indicador de anticipación.
- La **tasa de mortalidad (CFR) descendió** de forma sostenida, de ~5,8% en mayo de 2020 a ~1,8% en marzo de 2021, en gran parte por el aumento de la capacidad de testeo.
- La **presión hospitalaria** sigue de cerca la curva de casos y alcanzó su máximo histórico (~132.000 pacientes) durante la tercera ola.

El detalle completo de estos hallazgos, junto con recomendaciones y limitaciones del análisis, está disponible en [`reports/informe_ejecutivo.pdf`](reports/informe_ejecutivo.pdf).

## Tecnologías utilizadas

- **Python 3**
- **pandas** - manipulación y limpieza de datos
- **requests** - descarga del dataset desde la API
- **matplotlib** y **seaborn** - visualización de datos
- **Jupyter Notebook** (vía VS Code)

## Autor

Arnaldo · Bootcamp IA MAD - P7