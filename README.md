# Fase 1 - Definición y orientación de la situación: Dataset Iris

**Asignatura:** Machine Learning I - Magíster en Ciencia de Datos e Inteligencia Artificial  
**Integrantes:** Jennifer Nilo – Patricio Núñez  
**Grupo:** 8  

## Descripción del Proyecto
Este proyecto corresponde a la evidencia técnica de la Fase 1 aplicada al dataset Iris. Su propósito es formalizar analíticamente el problema, establecer la relación entre las mediciones morfológicas (sépalo y pétalo) y la especie de la flor, y justificar la selección del enfoque metodológico (aprendizaje supervisado de clasificación multiclase). Asimismo, vincula cada paso del proceso con las etapas de la metodología KDD, garantizando la trazabilidad entre el problema conceptual y su representación en código.

## Estructura del Repositorio
* `notebook/`: Directorio que aloja el código fuente y el flujo reproducible. Contiene el *notebook* ejecutable (`F1_Definicion.ipynb`) con el análisis exploratorio inicial, la revisión de calidad de datos y la caracterización estadística.

## Instrucciones de Reproducción
Para ejecutar este proyecto garantizando la reproducibilidad del entorno computacional, sigue estos pasos en tu terminal:

### 1. Clonar el repositorio:
```bash
git clone https://github.com/pnunezcarreno/machinelearning1.git
cd machinelearning1
```

### 2. Fuente de datos:
Los datos numéricos del dataset Iris se importan de forma nativa a través del módulo `sklearn.datasets`, por lo cual **no se requiere** descargar archivos `.csv` externos ni configurar directorios adicionales de *data*. La obtención se ejecuta automáticamente en la inicialización del código.

### 3. Crear y activar el entorno virtual:
```bash
python -m venv .venv
# En Windows: .venv\Scripts\activate
# En Linux/macOS: source .venv/bin/activate
```

### 4. Instalar dependencias requeridas:
El proyecto utiliza el ecosistema de ciencia de datos de Python. Instala las librerías base necesarias para levantar el notebook:
```bash
pip install pandas numpy seaborn matplotlib scikit-learn jupyter
```
*(Si incluyes posteriormente un archivo de dependencias estricto, utiliza: `pip install -r requirements.txt`)*

## Ejecución de la Fase 1 (Definición)
1. Con el entorno virtual activo, inicializa el servidor de Jupyter:
```bash
jupyter notebook
```
2. Navega y abre el archivo ubicado en la ruta `notebook/F1_Definicion.ipynb`.
3. Ejecuta el *notebook* de forma secuencial (o desde la barra superior utiliza `Kernel > Restart Kernel and Run All Cells`).
4. Al finalizar la ejecución de las celdas, podrás visualizar la documentación técnica del proceso, que incluye:
   * La definición formal de la problemática y los objetivos.
   * La justificación de la clasificación del aprendizaje.
   * La inserción del algoritmo como componente dentro del ciclo KDD.
   * Las salidas del código relacionadas a calidad de datos, matriz de correlaciones y distribuciones base.
