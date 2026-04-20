# Mahalanobis — segmentación por color en imágenes

Este repositorio contiene notebooks para segmentación en el espacio de color RGB usando la **distancia de Mahalanobis** (y, opcionalmente, distancia euclidiana al fijar la matriz de covarianza como identidad).

## Contexto de aplicación

El flujo de trabajo está orientado al análisis de **imágenes de macolla de forrajes**: a partir de fotografías de campo o laboratorio, el usuario delimita la zona de tejido verde de interés (mediante clics en píxeles o sobre un área rectangular) y el algoritmo segmenta los píxeles asociados a ese color en RGB. El resultado permite **cuantificar la cobertura verde** de la macolla contando los **píxeles clasificados como verdes** frente al total relevante de la imagen o de la región analizada, como apoyo a estudios fenotípicos y de biomasa foliar.

## Publicaciones y uso del código

- **Artículo publicado (MDPI *AgriEngineering*)**: este enfoque de procesamiento se utilizó como parte del trabajo reportado en  
  [AgriEngineering 2025, 7(4), 111](https://www.mdpi.com/2624-7402/7/4/111).
- **Manuscrito en revisión**: el mismo código sirvió de apoyo al procesamiento de imágenes en un trabajo enviado a la revista ***Data*** (MDPI). **Este README se actualizará con el enlace oficial al artículo cuando sea publicado.**

Si citas este repositorio o los notebooks en un trabajo académico, enlaza tanto el artículo de *AgriEngineering* como este repositorio cuando corresponda.

## Contenido del repositorio

| Archivo | Descripción breve |
|--------|-------------------|
| `9-Mahalanobis_Color_PIXEL.ipynb` | Selección de muestras con **clics** sobre píxeles individuales (botón derecho). Recomendación en el código: ~10 puntos. |
| `10-Mahalanobis_Color_AREA.ipynb` | Selección mediante **dos clics** que definen una región rectangular; se usa el conjunto de píxeles del área para estimar estadísticas y segmentar. |

Los notebooks conservan enlaces de referencia (SciPy lecture notes en español, material de imágenes con NumPy, eventos de ratón en OpenCV, ejemplo de Mahalanobis en Python/MATLAB, etc.).

## Dependencias

Entorno típico: **Python 3** con Jupyter y al menos:

- `numpy`
- `matplotlib`
- `opencv-python` (`cv2`)
- `scipy` (`distance.mahalanobis`, `numpy.linalg.inv` para la inversa de la covarianza)

Instalación con versiones fijadas (recomendado):

```bash
pip install -r requirements.txt
```

Instalación mínima sin archivo de bloqueo:

```bash
pip install numpy matplotlib opencv-python scipy jupyter
```

## Uso

1. Abrir el notebook deseado en Jupyter Lab / Jupyter Notebook / VS Code.
2. **Rutas e imágenes**: las celdas usan `os.chdir(...)` con rutas absolutas de Windows y nombres de archivo de ejemplo (`39.jpg`, `15.jpg`). Antes de ejecutar, ajusta la carpeta y el nombre del archivo a **tu** imagen local (el repositorio no incluye esas imágenes).
3. Ejecutar las celdas en orden: carga de imagen, interacción con la ventana de OpenCV (clics), cálculo de covarianza/media en RGB y generación del mapa de segmentación (máscara o imagen filtrada).
4. **Conteo de píxeles verdes**: a partir de la salida segmentada (por ejemplo una máscara binaria o la imagen filtrada donde solo permanece el verde de interés), puedes obtener el **número de píxeles verdes** sumando los píxeles clasificados como pertenecientes a la clase objetivo y, si lo necesitas, el porcentaje respecto al área total o a una región ROI.

Los notebooks incluyen visualizaciones intermedias (histogramas, ventanas interactivas) útiles para verificar que la muestra de color representa bien la macolla antes de fijar el umbral o la distancia de Mahalanobis.

## Nota sobre Mahalanobis vs. Euclides

Si la matriz de covarianza RGB se reemplaza por la identidad `I₃`, el criterio equivale a segmentar por **distancia euclidiana** en RGB (como se indica en las celdas markdown de ambos notebooks).

## Licencia y autoría

Especifica aquí la licencia si aplica. Los notebooks citan varias fuentes externas en comentarios; conviene mantener esas atribuciones si redistribuyes el código.

---

Repositorio remoto: [mahalanobis-image-processing](https://github.com/claumiseimbett1/mahalanobis-image-processing)
