<h1 align="center">🌟 Práctica 4 - Visión por Computador (Curso 2024/2025)</h1>

<img align="left" width="150" height="150" src="https://github.com/AlejandroDavidArzolaSaavedra/Kata-Working-With-Sqlite/assets/90756437/f83020eb-76e4-4224-87e4-ae2a2d370b05g"></a>
Se han completado todas las tareas solicitadas de la **Práctica 4** para la asignatura **Visión por Computador**. Reconocimiento de matrículas

*Trabajo realizado por*:

[![GitHub](https://img.shields.io/badge/GitHub-Heliot%20J.%20Segura%20Gonzalez-purple?style=flat-square&logo=github)](https://github.com/kratoscordoba7)

[![GitHub](https://img.shields.io/badge/GitHub-Alejandro%20D.%20Arzola%20Saavedra%20-darkblue?style=flat-square&logo=github)](https://github.com/AlejandroDavidArzolaSaavedra)

## 🛠️ Librerías Utilizadas

[![OpenCV](https://img.shields.io/badge/OpenCV-%23FF8C00.svg?style=for-the-badge&logo=opencv&logoColor=white)](https://opencv.org/)
[![Pytesseract](https://img.shields.io/badge/Pytesseract-%2300A3E0.svg?style=for-the-badge&logo=pytorch&logoColor=white)](https://github.com/madmaze/pytesseract)
[![YOLO](https://img.shields.io/badge/YOLO-%231f77b4.svg?style=for-the-badge&logo=python&logoColor=white)](https://github.com/ultralytics/yolov5)
[![EasyOCR](https://img.shields.io/badge/EasyOCR-%23009639.svg?style=for-the-badge&logo=python&logoColor=white)](https://github.com/JaidedAI/EasyOCR)
[![Math](https://img.shields.io/badge/Math-%23013243.svg?style=for-the-badge&logo=python&logoColor=white)](https://docs.python.org/3/library/math.html)
[![Regex](https://img.shields.io/badge/Regex-%234C4CFF.svg?style=for-the-badge&logo=python&logoColor=white)](https://docs.python.org/3/library/re.html)



---
## 🚀 Cómo empezar

Para comenzar con el proyecto, sigue estos pasos:

> [!NOTE]  
> Debes de situarte en un environment configurado como se definió en el cuaderno de la práctica 1  de [otsedom](https://github.com/otsedom/otsedom.github.io/blob/main/VC/P1/README.md#111-comandos-basicos-de-anaconda) y el de la práctica 4 de [otsedom](https://github.com/otsedom/otsedom.github.io/blob/main/VC/P4/README.md).

### Paso 1: Abrir VSCode y situarse en el directorio:
   
   `C:\Users\TuNombreDeUsuario\anaconda3\envs\VCP4
   
### Paso 2: Clonar y trabajar en el proyecto localmente (VS Code)
1. **Clona el repositorio**: Ejecuta el siguiente comando en tu terminal para clonar el repositorio:
   ```bash
   git clone https://github.com/kratoscordoba7/VCP4.git
   ```
2. Una vez clonado, todos los archivos han de estar situado en el envioronment del paso 1

### Paso 3: Abrir Anaconda prompt y activar el envioroment:
   ```bash
   conda activate NombreDeTuEnvironment
   ```
Tras estos pasos debería poder ejecutar el proyecto localmente

---

<h2 align="center">📋 Tareas</h2>

### Tarea 1 Reconocimiento de matrículas

Para la entrega de esta práctica, la tarea consiste en desarrollar un prototipo que procese uno (vídeo ejemplo proporcionado) o varios vídeos (incluyendo vídeos de cosecha propia)):

detecte y siga las personas y vehículos presentes
detecte y lea las matrículas de los vehículos presentes
cuente el total de cada clase
vuelque a disco un vídeo que visualice los resultados
genere un archivo csv con el resultado de la detección y seguimiento. Se sugiere un formato con al menos los siguientes campos:

```python
  fotograma, tipo_objeto, confianza, identificador_tracking, x1, y1, x2, y2, matrícula_en_su_caso, confianza, mx1,my1,mx2,my2, texto_matricula
````

La entrega del cuaderno o cuadernos se hace efectiva a través del campus virtual por medio de un enlace github. Además del archivo README, debe incluirse el resultado del vídeo proporcionado como test (o enlace al mismo), y el correspondiente archivo csv. En el caso de entrenarse algún detector, por ejemplo de matrículas, debe proporcionarse acceso al conjunto de datos.

Se considerarán extras:

- Determine el flujo de personas y vehículos en el vídeo de test en distintas direcciones (vehículos que dejan la imagen por la derecha, por la izquierda, etc.)

Participar en 
 - Evaluar dos alternativas para la detección de matrículas: basada en YOLO, y basada en contornos.
 - Anonimizar a las personas y vehículos presentes en un vídeo.


En primer lugar se optó por realizar un entrenamiento mediante la plataforma RoboFlow para entrenar un modelo que distinga tanto coches como matrículas. Las métricas de entrenamiento se pueden ver en las siguientes figuras:
<div style="text-align: center;" align="center"> <img src="img/metrica_overflow.png" height="400px" width="500px" alt="Metricas roboflow 1"> </div>
A continuación se van a explicar la diferentes gráficas de la fotografía:

- **El mAP** es una métrica utilizada en tareas de detección de objetos para evaluar la precisión del modelo en diferentes umbrales de intersección sobre la unión (IoU). En este caso, se muestran dos variantes del mAP:
  - **mAP** (línea en púrpura oscuro): mide la precisión media en varios umbrales de IoU (desde 0.5 hasta 0.95).
  - **mAP@50:95** (línea en púrpura claro): evalúa el rendimiento a un umbral específico de IoU (0.50), lo que suele ser más permisivo.

En el ambito del mAP, se puede concluir que a lo largo de las épocas, se observa una tendencia general de mejora en ambas métricas. El mAP se estabiliza cerca de 0.9, lo que indica un buen rendimiento del modelo.
El mAP@50:95 es más bajo pero sigue una tendencia ascendente, estabilizándose en alrededor de 0.6, lo que muestra que el modelo sigue mejorando, aunque con menor precisión a mayores umbrales.

Por otro lado,  la pérdida asociada a la predicción de las cajas delimitadoras (bounding boxes), que representan los objetos en una imagen. La pérdida se refiere a la diferencia entre las predicciones del modelo y las cajas reales (ground truth).
- Inicialmente, la Box Loss es alta (alrededor de 2.2), lo que significa que el modelo cometía muchos errores en la localización de los objetos.
- A medida que las épocas avanzan, la pérdida disminuye y se estabiliza en torno a 1.0, indicando que el modelo mejora en su capacidad para predecir las posiciones de los objetos.

La pérdida de clasificación, que mide la capacidad del modelo para identificar correctamente a qué clase pertenece un objeto detectado.
- Al principio, la pérdida es alta, alrededor de 3.5, lo que indica un mal rendimiento en la clasificación de los objetos.
- A medida que el modelo entrena, la pérdida disminuye y se estabiliza entre 0.5 y 1.0, lo que significa que el modelo se vuelve mucho más preciso al identificar las clases de los objetos.

En el gráfico de la derecha, se muestra la pérdida de objetos, que está relacionada con la capacidad del modelo para detectar correctamente la presencia de objetos en una imagen.
- Inicialmente, la pérdida es alta (alrededor de 4.5), indicando que el modelo fallaba con frecuencia al detectar la presencia de objetos.
- Aunque hay algunos picos pronunciados en las primeras épocas, la pérdida disminuye y se estabiliza cerca de 1.5, lo que sugiere que el modelo mejora en su habilidad para identificar objetos con mayor precisión.

Este modelo, en cuanto a métricas se refiere, presentó un rendimiento atractivo. Existen dos problemas por parte de Roboflow por lo cual terminamos descartando dicha opción:
- La primera de ellas es que roboflow exige el usao de la API para poder usar el modelo, el modus operandi es el siguiente:
   - Primero pides a la API de roboflow mediante una API key que te dé el modelo (no lo tienes en local, lo tienes mediante una conexión a la API).
   - Para obtener las predicción de una imagen se tiene que requerir a la API para que cada frame por individual lo procese.
      - El gran problema de  esto es que un vídeo cualquiera de no mucha duración se hace eterno para que termine.
- El segundo problema es que el resultado que se obtuvo por parte de este modelo no fue bueno, de hecho se podría decir que fue bastante malo.

En vista a lo sucedido, decimos cambiar de estrategia y como nos comentaron los docentes de la materia decidimos seguir el siguiente algoritmo:
- Usar un clasificador de personas y coches. Cuando este esté clasificando algo se lo pasamos a un clasificador únicamente de matrículas que también decidimos entrenar mediante roboflow y estos fueron las métricas obtenidas

<div style="text-align: center;" align="center"> <img src="img/metrica_2_overflwo.png" height="400px" width="500px" alt="Vehículo detectado con YOLO"> </div>

Los resultados de este segundo modelo fueron similares a los del primero, a pesar de que este se enfocaba únicamente en la clasificación de matrículas. Aunque las métricas iniciales indicaban un modelo prometedor, los resultados finales fueron decepcionantes: el modelo tuvo dificultades para manejar tanto imágenes con ruido (por ejemplo, imágenes con interferencias o baja calidad) como sin él. Consideramos que el problema no se debía al dataset, ya que contábamos con más de 290 imágenes, muchas de ellas modificadas para evitar el sobreajuste. De igual manera, al tener que llamar a la API de roboflow por cada frame el vídeo se ralentzió demasiado. 

En esta situacion, se optó por entrenar un modelo con el mismo dataset que se usó con roboflow pero en local clonando el git de ultralytics para YOLO v8 y los resultados que se obtuvieron son:

<div class="image-grid">
</div>

<table>
    <td width="50%">
        <img src="img/F1_curve.png" alt="Imagen 1">
    </td>
    <td width="50%">
       <img src="img/PR_curve.png" alt="Imagen 2">
    </td>
</table>
<table>
    <td width="50%">
       <img src="img/P_curve.png" alt="Imagen 3"> 
    </td>
       <img src="img/R_curve.png" alt="Imagen 4">
    <td width="50%">
    </td>
</table>

- El recall se mantiene muy cerca de 1.0 para la mayoría de los valores de confianza (desde 0 hasta aproximadamente 0.8), lo que indica que el modelo es capaz de detectar la mayoría de los ejemplos positivos (matrículas en este caso) en una amplia gama de niveles de confianza.
- A partir de un umbral de confianza cercano a 0.8, el recall comienza a decaer rápidamente, lo que indica que el modelo se vuelve más estricto al aceptar predicciones positivas y, por lo tanto, comienza a perder algunos ejemplos positivos. Este comportamiento es esperado porque a medida que se aumenta el umbral de confianza, el modelo es más cauteloso, prefiriendo no hacer una predicción antes que cometer errores.
- La curva indica que tanto la precisión como el recall están cerca de 1.0 para la clase de "matrícula", lo cual es un excelente resultado. Esto significa que el modelo tiene una capacidad sobresaliente para identificar matrículas sin cometer muchos errores.
- El hecho de que la curva esté casi en la esquina superior derecha sugiere que el modelo mantiene altos niveles de precisión incluso cuando también tiene un alto recall, lo cual es lo ideal en cualquier modelo de detección.

Se obtuvieron buenos resultados y a la hora de probarlo no era malo, se comportó decentemente. Sin embargo, decimos quedarnos con dos modelos preentrenado que encontramos:
- Uno detecta personas y coches
- Otro detecta matrículas

A continuación, presentamos los resultados obtenidos:

<div style="text-align: center;" align="center"> <img src="img/coche_dectectado.png" height="400px" width="500px" alt="Vehículo detectado con YOLO"> </div>

Primer caso: Utilizamos YOLO para detectar el vehículo, indicando el nivel de confianza con el que se ha logrado la identificación.

<div style="text-align: center;" align="center"> <img src="img/yolo_matricula.png" width="400px" alt="YOLO detectando matrícula"> </div>

Segundo caso: El sistema detecta las matrículas de los vehículos y nos proporciona la confianza asociada a cada detección.

<div style="text-align: center;" align="center"> <img src="img/consola_matricula_detectada.png" width="400px" alt="Consola mostrando matrícula detectada"> </div>

En esta imagen, correspondiente al segundo caso, se muestra en consola la matrícula detectada por el sistema.

<div style="text-align: center;" align="center"> <img src="img/matricula_coche.png" alt="Matrícula reconocida"> </div>

Tercer caso: Aquí se ilustra cómo el sistema ha detectado y reconocido correctamente la matrícula, mostrándola en pantalla.

<div style="text-align: center;" align="center"> <img src="img/person_anonymous.png"  height="350px" width="500px" alt="Detección de vehículos y personas con anonimato"> </div>

Cuarto caso: Además de detectar los vehículos, el sistema también identifica a las personas y aplica un filtro que oculta su identidad, respetando su privacidad.

<div style="text-align: center;"> <img src="img/roboflow.gif" alt="Vehículo detectado con RoboFlow"> </div>

En este caso como podemos ver, nuestra primera impresion usando roboflow, usando 100 imagenes.


> [!IMPORTANT]  
> Los archivos presentados aquí son una modificación de los archivos originales de [otsedom](https://github.com/otsedom/otsedom.github.io/tree/main/VC).



---

## 📚 Bibliografía

1. [Why does rotation of an image using cv2.getRotationMatrix2D and cv2.warpAffine result in clipping?](https://stackoverflow.com/questions/62370352/why-does-rotation-of-an-image-using-cv2-getrotationmatrix2d-and-cv2-warpaffine-r)
2. [OpenCV Histogram Equalization](https://docs.opencv.org/4.x/d5/daf/tutorial_py_histogram_equalization.html)
3. [Python Pytesseract image to string can't read text in image](https://stackoverflow.com/questions/59496336/python-pytesseract-image-to-string-cant-read-text-in-image)
4. [Tesseract OCR fails to correctly recognize text in vehicle license plates](https://stackoverflow.com/questions/78899657/tesseract-ocr-fails-to-correctly-recognize-text-in-vehicle-license-plates)
5. [OpenCV Thresholding](https://docs.opencv.org/3.4/d7/d4d/tutorial_py_thresholding.html)
6. [Reconocimiento de matrículas vehiculares con OpenCV y Pytesseract OCR en Python](https://omes-va.com/reconocimiento-de-matriculas-vehiculares-opencv-pytesseract-ocr-python/)

---

**Universidad de Las Palmas de Gran Canaria**  

EII - Grado de Ingeniería Informática  
Obra bajo licencia de Creative Commons Reconocimiento - No Comercial 4.0 Internacional

---
