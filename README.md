  # Laboratorio-5
# Variabilidad de la Frecuencia Cardiaca (HRV) y balance auntonómico
# TABBLA DE CONTENIDOS
1. Objetivos y metodología del experimento.
2. Marco conceptual.
3. Diagramas de flujo.
4. Adquisición de la señal.
5. Análisis de resultados.
6. Conclusiones.
7. Aplicaciones biomédicas.

# 1. Objetivos y metodología del experimento
La presente práctica tiene como objetivo principal el identificar los cambios en el balance auntonómico mediante análisis temporal de la variabilidad de la frecuencia cardiaca (HRV).

# 2. Marco conceptual.

**Actividad simpática y parasimpática del sistema nerviosos autónomo**

**Variabilidad de la frecuencia cardiaca (HRV)**

**Diagrama de Poincaré**

# 3. Diagramas de flujo.
# 4. Adquisición de la señal.

Para la captura de la señal, se colocaron dos electrodos en las muñecas de cada brazo y uno en el tobillo del sujeto de prueba. La señal analógica fue acondicionada utilizando un módulo AD8232. Posteriormente, la señal fue digitalizada y adquirida por un sistema de adquisición de datos (DAQ) de National Instruments (controlado a través de la librería nidaqmx de Python), y exportada al archivo de texto para su análisis.
Las características de la señal cargada en el script de análisis son:
Archivo:.txt
Frecuencia de Muestreo (fs): 2000 Hz (Detectada desde los datos del archivo)

**Materiales utilizados**

DAQ

AD8232

Cables

Electrodos

# 5. Análisis de resultados.

-**Parte A:**

Luego de hacer una revisión bibliográfica acerca de la actividad simpática y parasimpática del sistema nervioso autónomo, de conocer los efectos de la misma en la frecuencia cardiaca y como sucede la variabilidad de la misma, además de descubrir el diagrama de Poincaré como una herramienta de análisis, se planteó el siguiente plan de acción para cumplir con el objetivo de la presente práctica:

<img width="540" height="1400" alt="image" src="https://github.com/user-attachments/assets/c52c0005-b0d4-4978-a52f-0c452ff13f64" />

Seguido de esto, con ayuda de un sujeto de prueba se capturó una señal ECG durante 4 minutos, en el que los primeros 2 minutos se encuentra en reposo total y los 2 ultimos leyendo un escrito en voz alta, obteniendo la siguiente señal:

<img width="1159" height="457" alt="image" src="https://github.com/user-attachments/assets/6b3db755-10f7-4791-be10-9541a3dbccb1" />

-**Parte B:**

Para este apartado, se aplicaron los filtros digitales necesarios para eliminar el ruido de la señal, para que esta pueda visualizarse de una manera más clara. Para esto, se aplicó un filtro pasa banda de 0.5 Hz a 45 Hz, siendo valores típicos para un ECG, obteniendo la siguiente señal:

<img width="1073" height="414" alt="image" src="https://github.com/user-attachments/assets/9febfcdc-6ef1-43eb-95a8-6193caf112f4" />

Seguido de esto, se obtuvo la ecuación en diferencia del filtro, siendo esto muy importante para el modelamiento y la descripción del comportamiento del filtro, ya que supone la forma matemática de representar la relación entre la señal de entrada y la señal de salida del filtro digital, la cual resultó:

y[n] = 0.000020·x[n-0] + 0.000000·x[n-1] + -0.000080·x[n-2] + 0.000000·x[n-3] + 0.000120·x[n-4] + 0.000000·x[n-5] + -0.000080·x[n-6] + 0.000000·x[n-7] + 0.000020·x[n-8] - (-7.633977·y[n-1] + 25.504121·y[n-2] + -48.704339·y[n-3] + 58.149418·y[n-4] + -44.447512·y[n-5] + 21.241116·y[n-6] + -5.802561·y[n-7] + 0.693734·y[n-8])

Luego de esto, se hizo la respectiva segmentación de la señal para cuando el sujeto de prueba se encuentra en reposo y leyendo, y con estás señales se identificaron los picos R, obteniendo lo siguiente:

- En reposo:

<img width="1124" height="414" alt="image" src="https://github.com/user-attachments/assets/ca58683a-d8c6-44f2-a255-2f45cfe46300" />

- Leyendo e voz alta:

<img width="1116" height="416" alt="image" src="https://github.com/user-attachments/assets/a563654f-0fd5-4ef9-937b-0aa370b99cdc" />

Además de esto, se hizo el cálculo de los intervalos R-R para cada segmento de nuestra señal y con base a esta información se obtuvo una nueva señal, en donde cada punto representa el tiempo entre un pico R y el siguiente:

<img width="1206" height="459" alt="image" src="https://github.com/user-attachments/assets/13d0ed93-1073-4b0d-9c93-b4cbf5b11241" />

<img width="1204" height="454" alt="image" src="https://github.com/user-attachments/assets/4d462d94-5e35-44d3-b813-62db496bd897" />


Luego de esto, se hizo el análisis de la HRV (variabilidad de la frecuencia cardiaca) y se compararon los datos entre ambos segmentos, obteniendo:

**HRV Segmento 1:**

Media RR: 0.6995s  SDNN: 0.0665s  RMSSD: 0.0524s  HR: 85.78 bpm

**HRV Segmento 2:**

Media RR: 0.6561s  SDNN: 0.1482s  RMSSD: 0.1864s  HR: 91.44 bpm

Estos valores son muy importantes dentro del análisis de la variabilidad de la frecuencia cardiaca por varias razones, tales como:

1. La **media RR** nos indica la duración promedio de los intervalos entre latidos cardiacos, por lo que su valor ayudará a definir que tan rápido está latiendo el corazón. Con base a lo obtenido, se observa una ligera diferencia, ya que cuando el sujeto está leyendo, la media RR es más baja, por ende, su corazón late más rápido.

2. La desviación estandar de los intervalos NN (**SDNN**) representada la variabilidad total de la frecuencia cardiaca. Este tipo de valores ayudan a indicar la capacidad del cuerpo para manejar el estrés, por lo que entre más alto sea, mayor capacidad de manejo tendrá. Para nuestro caso, cuando el sujeto se encuentra en reposo, tiene un manejo del estres más bajo que cuando está leyendo, a lo que se puede interpretar que para la persona resulta ser "relajante" leer.

3. El **RMSSD** permite medir la actividad del sistema nervioso parasimpático, por lo que nos indica el nivel de recuperación o estado de descanso. Para este valor, ocurrió que el sujeto se encuentra más "descansado" en el momento en que se encuentra leyendo, que cuando estaba en total reposo. Esto se puede interpretar que para el sujeto de prueba resultó poco interesante la lectura, generando un ligero sueño.

4. La frecuencia cardiaca (**HR**) es lo más conocido dentro del comportamiento cardiaco, ya que nos indica las veces que late el corazón por minuto, por lo que su frecuencia será proporcional al numero de látidos. En cuanto a los resultados obtenidos, se evidenció un ligero aumento de la frecuencia cardiaca al momento que el sujeto lee, lo cual resulta normal, ya que cuando una persona hace una actividad, su frecuencia cardiaca generalmente aumenta de valor.

-**Parte C:**

Finalmente, se obtuvo el diagrama de Poincaré para cada segmento de la señal ECG, obteniendo lo siguiente:

- Para el segmento 1:

<img width="596" height="587" alt="image" src="https://github.com/user-attachments/assets/f2626772-6aff-4ac3-b03d-243c8be0337b" />

- Para el segmento 2:

<img width="583" height="591" alt="image" src="https://github.com/user-attachments/assets/5f2d3b59-9760-4a10-805d-f7397c91b222" />

Con base a los diagrama obtenidos, se puede afirmar que el segmento 1 evidencia una mayor estabilidad, ya que los puntos se encuentran concentrados en una zona especifica adoptando una forma de elipse, reflejando la estabilidad de la señal. En cambio, para el segmento 2 se puede ver una mayor disperción de los datos, a pesar de que la mayoria de ellos también se ubiquen concentrados en una zona determinada, por lo que se puede afirmar que los puntos más variados reflejan el cambio en la variabilidad de la frecuencia cardiaca cuando la persona está leyendo. 

Finalmente, con base a los diagramas obtenidos se calcularon el indice de actividad vagal (CVI) y el indice de actividad simpática (CSI), a lo que se obtuvo lo siguiente:

Poincaré Segmento 1:

SD1=0.0370  SD2=0.0861 CSI=2.3300  CVI= 2.4972

Poincaré Segmento 2:

SD1=0.1318  SD2=0.1622 CSI=1.2307  CVI= 1.6698

El Indice de Actividad Simpática (**CSI**) es importante para el análisis de la variabilidad de la frecuencia cardiaca, ya que, como sus siglas lo mencionan, es el principal indicador del componente simpático del sistema nervioso autónomo, relacionado con la respuesta huida del cuerpo. Con base a nuestros reusltados, se puede ver que el CSI es más alto en el segmento 1 que en el 2, a lo que se puede interpretar que la persona se encontraba en un estado de "estrés", cuando estaba en total reposo. Esto puede significar que para el sujeto le generó una molestia el tener que estar en total reposo.

En cuanto al Indice de Actividad vagal (**CVI**), nos permite evaluar la influencia del sistema nervioso parasimpático en el corazón y esto se obtiene calculando el logaritmo del producto de la variabilidad longitudinal (4*SD2) y transversal (4*SD1) del diagrama de poincaré. Este valor nos permite estudiar la función parasimpática, reflejando el nivel de recuperación del estres y por ende, una mayor salud cardiovascular. En la práctica, se evidencia que el sujeto de prueba tiene una mejor recuperación del estrés cuando está en reposo, que cuando está leyendo en voz alta. Esto se puede interpretar que a la persona le genera cierto estrés o molestía cuando está leyendo, ya sea por el tipo de lectura u otro tipo de situación.

# 6. Conclusiones.
# 7. Aplicaciones biomédicas.
