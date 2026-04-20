# Mahalanobis — segmentación por color en imágenes

Notebooks de demostración para segmentación en el espacio de color RGB usando la **distancia de Mahalanobis** (y, opcionalmente, distancia euclidiana al fijar la matriz de covarianza como identidad).

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
3. Ejecutar las celdas en orden: carga de imagen, interacción con la ventana de OpenCV (clics), cálculo de covarianza/media en RGB y generación del mapa de segmentación.

## Nota sobre Mahalanobis vs. Euclides

Si la matriz de covarianza RGB se reemplaza por la identidad `I₃`, el criterio equivale a segmentar por **distancia euclidiana** en RGB (como se indica en las celdas markdown de ambos notebooks).

## Licencia y autoría

Especifica aquí la licencia si aplica. Los notebooks citan varias fuentes externas en comentarios; conviene mantener esas atribuciones si redistribuyes el código.

---

Repositorio remoto: [mahalanobis-image-processing](https://github.com/claumiseimbett1/mahalanobis-image-processing)
