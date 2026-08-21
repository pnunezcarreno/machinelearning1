# Machine Learning I

**Asignatura:** Machine Learning I - Magíster en Ciencia de Datos e
Inteligencia Artificial\
**Integrantes:** Jennifer Nilo -- Patricio Núñez\
**Grupo:** 8

## Descripción del proyecto

Este repositorio reúne las evidencias técnicas desarrolladas durante la
asignatura Machine Learning I. El trabajo aborda problemas de
aprendizaje supervisado mediante notebooks reproducibles que documentan
la definición del problema, la preparación de los datos, la
implementación de modelos y la evaluación de sus resultados.

Actualmente, el repositorio contiene tres fases:

-   **Fase 1 --- Definición y orientación:** análisis del dataset Iris y
    formulación de un problema de clasificación multiclase dentro de la
    metodología KDD.
-   **Fase 2 --- Modelos de regresión supervisada:** implementación y
    comparación de tres modelos sobre el dataset California Housing.
-   **Fase 3 --- Modelos de clasificación supervisada:** preparación y
    análisis del dataset Titanic, implementación de cuatro
    clasificadores tradicionales y tres arquitecturas de redes
    neuronales MLP, con selección de hiperparámetros mediante validación
    cruzada y evaluación comparativa sobre un conjunto de prueba.

## Estructura del repositorio

``` text
machinelearning1/
├── notebook/
│   ├── F1_Definicion.ipynb
│   ├── F2_Regresion.ipynb
│   └── F3_Clasificacion.ipynb
└── README.md
```

  -------------------------------------------------------------------------------------------
  Notebook                            Dataset           Tipo de problema  Contenido principal
  ----------------------------------- ----------------- ----------------- -------------------
  `notebook/F1_Definicion.ipynb`      Iris              Clasificación     Definición de la
                                                        multiclase        problemática,
                                                                          revisión de
                                                                          calidad,
                                                                          caracterización
                                                                          estadística,
                                                                          correlaciones y
                                                                          vinculación con
                                                                          KDD.

  `notebook/F2_Regresion.ipynb`       California        Regresión         Preprocesamiento,
                                      Housing           supervisada       entrenamiento de
                                                                          tres modelos,
                                                                          evaluación con MSE,
                                                                          RMSE y R²,
                                                                          visualización y
                                                                          comparación de
                                                                          resultados.

  `notebook/F3_Clasificacion.ipynb`   Titanic           Clasificación     Análisis
                                                        binaria           exploratorio,
                                                                          preparación
                                                                          mediante pipelines,
                                                                          KNN, árbol de
                                                                          decisión, SVM,
                                                                          Naive Bayes y tres
                                                                          redes neuronales
                                                                          MLP, con validación
                                                                          cruzada
                                                                          estratificada y
                                                                          evaluación mediante
                                                                          métricas de
                                                                          clasificación.
  -------------------------------------------------------------------------------------------

## Fase 1 --- Dataset Iris

La primera fase formaliza la relación entre las mediciones morfológicas
de sépalos y pétalos y la especie de cada flor. El notebook justifica el
uso de aprendizaje supervisado para clasificación multiclase y mantiene
la trazabilidad entre el problema conceptual, las etapas de KDD y su
representación en código.

Incluye:

-   definición formal de la problemática y sus objetivos;
-   justificación del enfoque de clasificación;
-   revisión de calidad de los datos;
-   análisis estadístico y matriz de correlaciones;
-   integración del algoritmo dentro del ciclo KDD.

## Fase 2 --- Modelos de regresión supervisada

La segunda fase utiliza **California Housing**, disponible mediante
`sklearn.datasets.fetch_california_housing`, para estimar la variable
continua `MedHouseVal`, que representa el valor mediano de las viviendas
en cientos de miles de dólares.

El dataset contiene **20.640 registros**, ocho variables predictoras y
una variable objetivo. No presenta valores faltantes. Para asegurar una
comparación consistente, se utiliza una partición común de **80 % para
entrenamiento** y **20 % para prueba**, con semilla `42`.

### Modelos implementados

1.  **Regresión lineal simple:** utiliza `MedInc` como único predictor.
2.  **Árbol de decisión para regresión:** utiliza las ocho variables
    predictoras y una profundidad máxima de 5.
3.  **Red neuronal MLP:** utiliza las ocho variables estandarizadas, una
    capa oculta de 100 neuronas, activación ReLU, optimizador Adam y
    detención temprana.

### Resultados obtenidos

  Modelo                             MSE         RMSE           R²
  ------------------------- ------------ ------------ ------------
  Regresión lineal simple         0.7091       0.8421       0.4589
  Árbol de decisión               0.5245       0.7242       0.5997
  Red neuronal MLP            **0.3017**   **0.5493**   **0.7697**

En esta ejecución, la **red neuronal MLP** presentó el mejor desempeño
predictivo: obtuvo el menor MSE y RMSE, además del mayor R². La
comparación debe considerar que la regresión lineal utiliza únicamente
`MedInc`, mientras que el árbol y la red neuronal emplean las ocho
variables predictoras.

## Fase 3 --- Modelos de clasificación supervisada

La tercera fase utiliza el dataset **Titanic**, disponible mediante
`seaborn.load_dataset("titanic")`, para abordar un problema de
clasificación binaria cuyo objetivo es predecir la variable `survived`.
El conjunto contiene **891 registros y 15 variables** antes de la
selección analítica. Para el modelamiento se utilizan `pclass`, `sex`,
`age`, `sibsp`, `parch`, `fare` y `embarked` como variables predictoras.

La preparación utiliza una partición estratificada de **80 % para
entrenamiento** y **20 % para prueba**, con `random_state=42`. La
imputación, codificación de variables categóricas y estandarización se
integran mediante `Pipeline` y `ColumnTransformer`, de modo que las
transformaciones se ajusten con los datos de entrenamiento. La selección
de configuraciones se realiza con `GridSearchCV`, validación cruzada
estratificada de **5 folds** y **F1-score** como métrica de
optimización.

### Modelos implementados

1.  **K-Nearest Neighbors (KNN):** evalúa distintas cantidades de
    vecinos, ponderaciones y métricas de distancia sobre variables
    numéricas estandarizadas.
2.  **Árbol de decisión:** compara criterios de división, profundidades
    máximas y tamaños mínimos de hoja.
3.  **Support Vector Machine (SVM):** evalúa kernels lineal y RBF, junto
    con distintos valores de `C` y `gamma`, utilizando datos escalados.
4.  **Gaussian Naive Bayes:** evalúa distintos valores de
    `var_smoothing`.
5.  **Red neuronal MLP con una capa oculta:** arquitectura `(100,)`,
    activación ReLU y optimizador Adam.
6.  **Red neuronal MLP con dos capas ocultas:** arquitectura
    `(100, 50)`, activación ReLU y optimizador Adam.
7.  **Red neuronal MLP con tres capas ocultas:** arquitectura
    `(100, 50, 25)`, activación ReLU y optimizador Adam.

### Resultados obtenidos

  -----------------------------------------------------------------------------
  Modelo           Accuracy    Precision       Recall     F1-score      ROC-AUC
  ------------ ------------ ------------ ------------ ------------ ------------
  SVM            **0.8268**   **0.8167**       0.7101   **0.7597**       0.8411

  KNN                0.8156       0.7727   **0.7391**       0.7556       0.8531

  Red                0.7933       0.7353       0.7246       0.7299       0.8530
  Neuronal - 2                                                     
  capas                                                            
  ocultas                                                          

  Red                0.7989       0.7619       0.6957       0.7273   **0.8580**
  Neuronal - 3                                                     
  capas                                                            
  ocultas                                                          

  Naive Bayes        0.7877       0.7385       0.6957       0.7164       0.8191

  Árbol de           0.7933       0.7963       0.6232       0.6992       0.8073
  decisión                                                         

  Red                0.7877       0.7818       0.6232       0.6935       0.8539
  Neuronal - 1                                                     
  capa oculta                                                      
  -----------------------------------------------------------------------------

En esta ejecución, **SVM** presenta el mayor `Accuracy` y `F1-score`,
mientras que **KNN** obtiene el mayor `Recall` para la clase positiva.
La red neuronal de tres capas alcanza el mayor `ROC-AUC`. Los resultados
muestran que no existe un único modelo que domine todas las métricas,
por lo que la selección depende del criterio de evaluación priorizado
para el problema.

### Hiperparámetros seleccionados

  -------------------------------------------------------------------------
  Modelo                              Configuración seleccionada
  ----------------------------------- -------------------------------------
  KNN                                 `n_neighbors=3`, `p=1`,
                                      `weights="uniform"`

  Árbol de decisión                   `criterion="entropy"`, `max_depth=8`,
                                      `min_samples_leaf=1`

  SVM                                 `C=1`, `kernel="rbf"`, `gamma="auto"`

  Naive Bayes                         `var_smoothing=1e-11`

  MLP 1 capa                          `hidden_layer_sizes=(100,)`,
                                      `activation="relu"`, `solver="adam"`,
                                      `max_iter=500`

  MLP 2 capas                         `hidden_layer_sizes=(100, 50)`,
                                      `activation="relu"`, `solver="adam"`,
                                      `max_iter=500`

  MLP 3 capas                         `hidden_layer_sizes=(100, 50, 25)`,
                                      `activation="relu"`, `solver="adam"`,
                                      `max_iter=500`
  -------------------------------------------------------------------------

## Requisitos

-   Python 3.10 o superior
-   Jupyter Notebook o Google Colab
-   NumPy
-   pandas
-   Matplotlib
-   seaborn
-   scikit-learn

## Instrucciones de reproducción

### 1. Clonar el repositorio

``` bash
git clone https://github.com/pnunezcarreno/machinelearning1.git
cd machinelearning1
```

### 2. Crear y activar un entorno virtual

``` bash
python -m venv .venv
```

En Windows:

``` bash
.venv\Scripts\activate
```

En Linux o macOS:

``` bash
source .venv/bin/activate
```

### 3. Instalar las dependencias

``` bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

### 4. Iniciar Jupyter Notebook

``` bash
jupyter notebook
```

Desde la interfaz de Jupyter, abre el notebook correspondiente y ejecuta
sus celdas en orden. También puedes utilizar
`Kernel > Restart Kernel and Run All Cells`. Para la Fase 3 también es
posible abrir `F3_Clasificacion.ipynb` directamente en Google Colab y
ejecutar todas las celdas.

## Fuente de los datos

Los conjuntos de datos utilizados se obtienen desde librerías de Python:

-   **Iris:** mediante `sklearn.datasets`.
-   **California Housing:** mediante
    `sklearn.datasets.fetch_california_housing`.
-   **Titanic:** mediante `seaborn.load_dataset("titanic")`.

No es necesario agregar archivos CSV al repositorio para ejecutar los
notebooks. La primera descarga de California Housing y la carga de
Titanic pueden requerir conexión a internet, dependiendo del entorno y
de la disponibilidad previa de los datasets en caché.
