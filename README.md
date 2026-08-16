# Machine Learning I

**Asignatura:** Machine Learning I - Magíster en Ciencia de Datos e Inteligencia Artificial  
**Integrantes:** Jennifer Nilo – Patricio Núñez  
**Grupo:** 8  

## Descripción del proyecto

Este repositorio reúne las evidencias técnicas desarrolladas durante la asignatura Machine Learning I. El trabajo aborda problemas de aprendizaje supervisado mediante notebooks reproducibles que documentan la definición del problema, la preparación de los datos, la implementación de modelos y la evaluación de sus resultados.

Actualmente, el repositorio contiene dos fases:

- **Fase 1 — Definición y orientación:** análisis del dataset Iris y formulación de un problema de clasificación multiclase dentro de la metodología KDD.
- **Fase 2 — Modelos de regresión supervisada:** implementación y comparación de tres modelos sobre el dataset California Housing.

## Estructura del repositorio

```text
machinelearning1/
├── notebook/
│   ├── F1_Definicion.ipynb
│   └── F2_Regresion.ipynb
└── README.md
```

| Notebook | Dataset | Tipo de problema | Contenido principal |
|---|---|---|---|
| `notebook/F1_Definicion.ipynb` | Iris | Clasificación multiclase | Definición de la problemática, revisión de calidad, caracterización estadística, correlaciones y vinculación con KDD. |
| `notebook/F2_Regresion.ipynb` | California Housing | Regresión supervisada | Preprocesamiento, entrenamiento de tres modelos, evaluación con MSE, RMSE y R², visualización y comparación de resultados. |

## Fase 1 — Dataset Iris

La primera fase formaliza la relación entre las mediciones morfológicas de sépalos y pétalos y la especie de cada flor. El notebook justifica el uso de aprendizaje supervisado para clasificación multiclase y mantiene la trazabilidad entre el problema conceptual, las etapas de KDD y su representación en código.

Incluye:

- definición formal de la problemática y sus objetivos;
- justificación del enfoque de clasificación;
- revisión de calidad de los datos;
- análisis estadístico y matriz de correlaciones;
- integración del algoritmo dentro del ciclo KDD.

## Fase 2 — Modelos de regresión supervisada

La segunda fase utiliza **California Housing**, disponible mediante `sklearn.datasets.fetch_california_housing`, para estimar la variable continua `MedHouseVal`, que representa el valor mediano de las viviendas en cientos de miles de dólares.

El dataset contiene **20.640 registros**, ocho variables predictoras y una variable objetivo. No presenta valores faltantes. Para asegurar una comparación consistente, se utiliza una partición común de **80 % para entrenamiento** y **20 % para prueba**, con semilla `42`.

### Modelos implementados

1. **Regresión lineal simple:** utiliza `MedInc` como único predictor.
2. **Árbol de decisión para regresión:** utiliza las ocho variables predictoras y una profundidad máxima de 5.
3. **Red neuronal MLP:** utiliza las ocho variables estandarizadas, una capa oculta de 100 neuronas, activación ReLU, optimizador Adam y detención temprana.

### Resultados obtenidos

| Modelo | MSE | RMSE | R² |
|---|---:|---:|---:|
| Regresión lineal simple | 0.7091 | 0.8421 | 0.4589 |
| Árbol de decisión | 0.5245 | 0.7242 | 0.5997 |
| Red neuronal MLP | **0.3017** | **0.5493** | **0.7697** |

En esta ejecución, la **red neuronal MLP** presentó el mejor desempeño predictivo: obtuvo el menor MSE y RMSE, además del mayor R². La comparación debe considerar que la regresión lineal utiliza únicamente `MedInc`, mientras que el árbol y la red neuronal emplean las ocho variables predictoras.

## Requisitos

- Python 3.10 o superior
- Jupyter Notebook
- NumPy
- pandas
- Matplotlib
- seaborn
- scikit-learn

## Instrucciones de reproducción

### 1. Clonar el repositorio

```bash
git clone https://github.com/pnunezcarreno/machinelearning1.git
cd machinelearning1
```

### 2. Crear y activar un entorno virtual

```bash
python -m venv .venv
```

En Windows:

```bash
.venv\Scripts\activate
```

En Linux o macOS:

```bash
source .venv/bin/activate
```

### 3. Instalar las dependencias

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

### 4. Iniciar Jupyter Notebook

```bash
jupyter notebook
```

Desde la interfaz de Jupyter, abre el notebook correspondiente y ejecuta sus celdas en orden. También puedes utilizar `Kernel > Restart Kernel and Run All Cells`.

## Fuente de los datos

Ambos conjuntos de datos se obtienen directamente desde scikit-learn:

- Iris mediante `sklearn.datasets`.
- California Housing mediante `sklearn.datasets.fetch_california_housing`.

No es necesario agregar archivos CSV al repositorio. La primera descarga de California Housing puede requerir conexión a internet para almacenar el dataset en la caché local de scikit-learn.
