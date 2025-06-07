# Gatección: Detección del Estado de Ánimo en Gatos mediante Imágenes
## Desarrollado por:

Este proyecto está contenido en un único Jupyter Notebook que cubre todo el flujo: desde la preparación de datos hasta la inferencia interactiva.
        Erik Eduardo Gómez López
        Maryam Michelle Del Monte Ortega
        Sahara Mariel Monroy Romero
---

## Estructura del Notebook

1. **Introducción y Objetivos**  
   Descripción del problema, datasets utilizados y objetivo final.

2. **Indexado de Imágenes y Etiquetas**  
   - Definición de rutas (`train_root`, `val_root`).  
   - Mapeo de nombres de carpeta a índices (`label_map`).  
   - Función `recolectar_imagenes()` para obtener `train_paths`, `train_labels`, `val_paths`, `val_labels`.

3. **Exploración de Datos**  
   - Detección de clases únicas y conteo por etiqueta (`Counter`), para verificar balance.

4. **Dataset y DataLoaders**  
   - Clase `CatsEmotionDataset`.  
   - Pipelines de transformaciones (`train_transforms`, `val_transforms`).  
   - Instanciación de `train_loader` y `val_loader` con `batch_size=4`.

5. **Definición de la CNN**  
   - Clase `CatMoodNET` con 2 bloques conv+pool y 3 fully-connected.  
   - Método `train_model()` que entrena y valida por época mostrando métricas y gráficas.

6. **Entrenamiento**  
   - Instanciación del modelo.  
   - Elección de dispositivo (CPU vs GPU).  
   - Configuración de `CrossEntropyLoss` y `Adam (lr=1e-4)`.  
   - Ejecución de `train_model(epochs=60, ...)`, con explicación de por qué 60 épocas.

7. **Evaluación**  
   - Cálculo de precisión global (`calcularPrecisionGlobal`).  
   - Precisión por clase y ranking (`clases_menor_precision`).  
   - Matriz de confusión (`plot_confusion_matrix`).

8. **Inferencia Interactiva**  
   - Widget `create_image_uploader()` con `ipywidgets` para subir y clasificar imágenes en tiempo real.

---

## Estructura de Carpetas de Datos

- **Entrenamiento**  
  `archive/data/labeled/conjunto2/`  
    alerta/
    dormido/
    enojado/
    neutral/
- **Validación / Pruebas**  
  `archive/data/labeled/conjunto-pruebas/`  
    alerta/
    dormido/
    enojado/
    neutral/
    
Cada subcarpeta contiene las imágenes correspondientes a esa emoción.

---

## Cómo ejecutar paso a paso

1. **Abrir el Notebook**  
   Ejecuta `jupyter lab` o `jupyter notebook` y abre `Gateccion.ipynb`.

2. **Instalar dependencias**  
   ```bash
   pip install torch torchvision matplotlib scikit-learn ipywidgets
   Si hay alguna dependencia que se solicite y no este instalada, favor de instalar con: 

Si al ejecutar el notebook aparece un error de módulo faltante, favor de instala la dependencia.

Para más información detallada, consultar la documentación de Gateccion.ipynb ó Gateccion_Reporte.pdf.

