# Clasificación Multiclase de Frutas con Transfer Learning + MLflow

## Tecnologías utilizadas
- Python
- TensorFlow / Keras (Transfer Learning con MobileNetV2)
- MLflow (versionado de experimentos, métricas y modelos)
- NumPy
- Matplotlib
- Pillow (PIL)

## Estructura del proyecto
Proyecto/
|--- Notebooks/
|    |--- 01_EDA_dataset.ipynb
|    |--- 02_Train_Multilabel_UI_MLflow_REGISTRY_FIX_FAST_RETRAIN.ipynb
|--- src/
|--- reports/
|--- continuous_data/
|    |--- manzana/
|    |--- naranja/
|    |--- platano/
|--- mlruns/  (generado por MLflow)
|--- README.md
## Resumen del proyecto
Este proyecto implementa un clasificador multiclase de imágenes para tres frutas (manzana, naranja y plátano) usando Transfer Learning. 
Se utiliza MobileNetV2 preentrenado en ImageNet como extractor de características y se entrena una nueva cabeza de clasificación para especializar el modelo en las tres clases requeridas.

El entrenamiento y la evaluación se registran con MLflow de forma versionada, incluyendo parámetros del experimento, métricas (accuracy/loss) y artefactos (confusion matrix, historial y modelos). 
Esto permite visualizar resultados en la interfaz web de MLflow y comparar ejecuciones a través del tiempo.

## Resultados (ejemplo)
- Métrica principal: `final_val_accuracy` registrada en MLflow por cada ejecución.
- Artefactos: matriz de confusión, historial de entrenamiento y modelo exportado.

> Para ver los resultados, ejecutar:
`mlflow ui --backend-store-uri file:Proyecto/mlruns --port 5000`

## Aprendizaje continuo (Continuous Learning)
El proyecto incluye un flujo de aprendizaje continuo:
1. Se realiza una predicción sobre una imagen subida a `imagenes_subidas/`.
2. El usuario indica la etiqueta real (manzana/naranja/plátano).
3. La imagen se guarda en `Proyecto/continuous_data/<clase>/`.
4. Se ejecuta un retrain rápido que reentrena la capa final usando un subconjunto del dataset base + nuevas imágenes.
5. Se genera un nuevo run en MLflow con un nuevo modelo versionado.

## Autores
- (Heathear Ulloa-valentina Vallejos)
  
## Repositorio GitHub

Este proyecto se encuentra versionado y organizado en un repositorio GitHub.
La raíz del repositorio corresponde a la carpeta `Proyecto/`, la cual contiene
todos los componentes necesarios para el desarrollo del sistema.

Estructura principal:
- `Notebooks/`: análisis exploratorio, entrenamiento y evaluación
- `App/`: aplicación para inferencia (serving)
- `models/`: modelos entrenados
- `mlruns/`: experimentos y métricas con MLflow
- `src/`: código fuente
- `reports/`: resultados y reportes

Repositorio:
https://github.com/don2233bosco2233-a11y/clasificacion-frutas-mlflow.git

