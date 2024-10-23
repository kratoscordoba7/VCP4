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
2. Una vez clonado, todos los archivos han de estar situado en el environment del paso 1

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



A continuación, presentamos los resultados obtenidos:

<div style="text-align: center;"> <img src="img/coche_dectectado.png" alt="Vehículo detectado con YOLO"> </div>

Primer caso: Utilizamos YOLO para detectar el vehículo, indicando el nivel de confianza con el que se ha logrado la identificación.

<div style="text-align: center;"> <img src="img/yolo_matricula.png" alt="YOLO detectando matrícula"> </div>

Segundo caso: El sistema detecta las matrículas de los vehículos y nos proporciona la confianza asociada a cada detección.

<div style="text-align: center;"> <img src="img/consola_matricula_detectada.png" alt="Consola mostrando matrícula detectada"> </div>

En esta imagen, correspondiente al segundo caso, se muestra en consola la matrícula detectada por el sistema.

<div style="text-align: center;"> <img src="img/matricula_coche.png" alt="Matrícula reconocida"> </div>

Tercer caso: Aquí se ilustra cómo el sistema ha detectado y reconocido correctamente la matrícula, mostrándola en pantalla.

<div style="text-align: center;"> <img src="img/person_anonymous.png" alt="Detección de vehículos y personas con anonimato"> </div>

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
