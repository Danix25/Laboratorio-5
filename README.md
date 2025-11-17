  # Laboratorio-5
# Variabilidad de la Frecuencia Cardiaca (HRV) y balance auntonómico
# TABBLA DE CONTENIDOS
1. Objetivos y metodología del experimento.
2. Marco conceptual.
4. Diagramas de flujo.
6. Adquisición de la señal.
7. Análisis de resultados.
8. Conclusiones.
9. Aplicaciones biomédicas.

# 1. Objetivos y metodología del experimento
La presente práctica tiene como objetivo principal el identificar los cambios en el balance auntonómico mediante análisis temporal de la variabilidad de la frecuencia cardiaca (HRV).

# 2. Marco conceptual.
Para analizar el estado del cuerpo, no basta con saber qué tan rápido late el corazón, sino qué tan adaptable es su ritmo. Esta adaptabilidad es controlada por el Sistema Nervioso Autónomo y puede medirse cuantitativamente mediante la Variabilidad de la Frecuencia Cardíaca (HRV), la cual se visualiza y analiza eficazmente con herramientas como el Diagrama de Poincaré.

Sistema Nervioso Autónomo (SNA)

El SNA regula todas las funciones involuntarias de nuestro cuerpo desde la digestión hasta la respiración. Funciona a través de un balance delicado entre dos ramas opuestas:

Actividad Simpática (SNS): Es el acelerador del cuerpo. Se activa en situaciones de estrés, ejercicio o alerta. Libera adrenalina y noradrenalina, lo que aumenta la frecuencia cardíaca y la fuerza de contracción.
Actividad Parasimpática (SNP): Es el freno del cuerpo. Domina en estados de calma, relajación y digestión. Libera acetilcolina a través del nervio vago, lo que disminuye la frecuencia cardíaca y promueve la recuperación.

El estado del corazón en cualquier momento es el resultado directo del balance autonómico, es decir, la competencia entre las señales simpáticas y parasimpáticas.

Variabilidad de la Frecuencia Cardíaca (HRV)

La HRV es una de las mejores formas no invasivas de medir este balance autonómico.

La HRV no es la frecuencia cardíaca (latidos por minuto), sino la medida de la variación en el tiempo entre latidos consecutivos. En un electrocardiograma (ECG), esto se mide como la variación en los intervalos R-R (el tiempo entre cada pico R). Un corazón sano no es un metrónomo perfecto; sus ritmos varían ligeramente de un latido a otro. Una HRV alta (gran variación) es positiva. Indica que el sistema parasimpático  está activo y que el cuerpo es adaptable, saludable y capaz de responder a los cambios. Una HRV baja se asocia con un dominio del sistema simpático. Es un indicador de estrés, fatiga, enfermedad o una pobre capacidad de adaptación.

Diagrama de Poincaré.

El Diagrama de Poincaré (también conocido como "Lorenz plot" en el artículo de Toichi) es una herramienta gráfica poderosa que nos permite visualizar la HRV y cuantificar el balance autonómico.

 Es un gráfico de dispersión donde cada intervalo R-R (llamado $RR_n$) se grafica en el eje X contra el intervalo R-R siguiente ($RR_{n+1}$) en el eje Y. Esto genera una "nube de puntos" cuya forma y dispersión revelan el estado del SNA. Una nube grande, redonda y dispersa indica una HRV alta, sugiriendo un dominio parasimpático. Una nube pequeña, estrecha y alargada indica una HRV baja, sugiriendo un dominio simpático.

El Índice Vagal (Parasimpático) se relaciona con el área o dispersión total de la nube. Un CVI alto significa mayor actividad parasimpática.
CSI  El Índice Simpático se relaciona con la elongación de la nube qué tan larga es en comparación con qué tan ancha es. Un CSI alto significa mayor actividad simpática.

En este laboratorio se utilizo el Diagrama de Poincaré (Punto 3) como método para cuantificar la HRV (Punto 2) y, a su vez, usar esos valores (CVI y CSI) para determinar objetivamente la influencia del Sistema Simpático y Parasimpático (Punto 1) durante el reposo y la lectura.

# 3. Diagramas de flujo.

<img width="400" height="1000" alt="codigo" src="https://github.com/user-attachments/assets/ae0c9345-277a-47d8-8e50-b2668dd39b51" />

# 4. Adquisición de la señal.

Para la captura de la señal, se colocaron dos electrodos en las muñecas de cada brazo y uno en la foza iliaca derecha. La señal analógica fue acondicionada utilizando un módulo AD8232. Posteriormente, la señal fue digitalizada y adquirida por un sistema de adquisición de datos (DAQ) de National Instruments (controlado a través de la librería nidaqmx de Python), y exportada al archivo de texto para su análisis.
Las características de la señal cargada en el script de análisis son:
Archivo:.txt
Frecuencia de Muestreo (fs): 2000 Hz (Detectada desde los datos del archivo)

![imagen de refencia](https://github.com/user-attachments/assets/7ca01aa7-5fec-48c5-b654-5a996463fac9)

**Materiales utilizados**

DAQ

AD8232

Cables

Electrodos



# 5. Análisis de resultados.

-**Parte A:**

Luego de hacer una revisión bibliográfica acerca de la actividad simpática y parasimpática del sistema nervioso autónomo, de conocer los efectos de la misma en la frecuencia cardiaca y como sucede la variabilidad de la misma, además de descubrir el diagrama de Poincaré como una herramienta de análisis, se planteó el siguiente plan de acción para cumplir con el objetivo de la presente práctica:

<img width="400" height="1000" alt="plan de accion" src="https://github.com/user-attachments/assets/868b471c-ed7a-4e98-bf72-77c6fb64a2bd" />


Seguido de esto, con ayuda de un sujeto de prueba se capturó una señal ECG durante 4 minutos, en el que los primeros 2 minutos se encuentra en reposo total y los 2 ultimos leyendo un escrito en voz alta, obteniendo la siguiente señal:

<img width="1059" height="357" alt="image" src="https://github.com/user-attachments/assets/6b3db755-10f7-4791-be10-9541a3dbccb1" />

-**Parte B:**

Para este apartado, se aplicaron los filtros digitales necesarios para eliminar el ruido de la señal, para que esta pueda visualizarse de una manera más clara. Para esto, se aplicó un filtro pasa banda de 0.5 Hz a 45 Hz, siendo valores típicos para un ECG, obteniendo la siguiente señal:

<img width="973" height="314" alt="image" src="https://github.com/user-attachments/assets/9febfcdc-6ef1-43eb-95a8-6193caf112f4" />

Seguido de esto, se obtuvo la ecuación en diferencia del filtro, siendo esto muy importante para el modelamiento y la descripción del comportamiento del filtro, ya que supone la forma matemática de representar la relación entre la señal de entrada y la señal de salida del filtro digital, la cual resultó:

y[n] = 0.000020·x[n-0] + 0.000000·x[n-1] + -0.000080·x[n-2] + 0.000000·x[n-3] + 0.000120·x[n-4] + 0.000000·x[n-5] + -0.000080·x[n-6] + 0.000000·x[n-7] + 0.000020·x[n-8] - (-7.633977·y[n-1] + 25.504121·y[n-2] + -48.704339·y[n-3] + 58.149418·y[n-4] + -44.447512·y[n-5] + 21.241116·y[n-6] + -5.802561·y[n-7] + 0.693734·y[n-8])

Luego de esto, se hizo la respectiva segmentación de la señal para cuando el sujeto de prueba se encuentra en reposo y leyendo, y con estás señales se identificaron los picos R, obteniendo lo siguiente:

- En reposo:

<img width="1024" height="314" alt="image" src="https://github.com/user-attachments/assets/ca58683a-d8c6-44f2-a255-2f45cfe46300" />

- Leyendo e voz alta:

<img width="1016" height="316" alt="image" src="https://github.com/user-attachments/assets/a563654f-0fd5-4ef9-937b-0aa370b99cdc" />

Además de esto, se hizo el cálculo de los intervalos R-R para cada segmento de nuestra señal y con base a esta información se obtuvo una nueva señal, en donde cada punto representa el tiempo entre un pico R y el siguiente:

<img width="1106" height="359" alt="image" src="https://github.com/user-attachments/assets/13d0ed93-1073-4b0d-9c93-b4cbf5b11241" />

<img width="1104" height="354" alt="image" src="https://github.com/user-attachments/assets/4d462d94-5e35-44d3-b813-62db496bd897" />


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

<img width="496" height="487" alt="image" src="https://github.com/user-attachments/assets/f2626772-6aff-4ac3-b03d-243c8be0337b" />

- Para el segmento 2:

<img width="483" height="491" alt="image" src="https://github.com/user-attachments/assets/5f2d3b59-9760-4a10-805d-f7397c91b222" />

Con base a los diagrama obtenidos, se puede afirmar que el segmento 1 evidencia una mayor estabilidad, ya que los puntos se encuentran concentrados en una zona especifica adoptando una forma de elipse, reflejando la estabilidad de la señal. En cambio, para el segmento 2 se puede ver una mayor disperción de los datos, a pesar de que la mayoria de ellos también se ubiquen concentrados en una zona determinada, por lo que se puede afirmar que los puntos más variados reflejan el cambio en la variabilidad de la frecuencia cardiaca cuando la persona está leyendo. 

Finalmente, con base a los diagramas obtenidos se calcularon el indice de actividad vagal (CVI) y el indice de actividad simpática (CSI), a lo que se obtuvo lo siguiente:

Poincaré Segmento 1:

SD1=0.0370  SD2=0.0861 CSI=2.3300  CVI= 2.4972

Poincaré Segmento 2:

SD1=0.1318  SD2=0.1622 CSI=1.2307  CVI= 1.6698

El Indice de Actividad Simpática (**CSI**) es importante para el análisis de la variabilidad de la frecuencia cardiaca, ya que, como sus siglas lo mencionan, es el principal indicador del componente simpático del sistema nervioso autónomo, relacionado con la respuesta huida del cuerpo. Con base a nuestros reusltados, se puede ver que el CSI es más alto en el segmento 1 que en el 2, a lo que se puede interpretar que la persona se encontraba en un estado de "estrés", cuando estaba en total reposo. Esto puede significar que para el sujeto le generó una molestia el tener que estar en total reposo.

En cuanto al Indice de Actividad vagal (**CVI**), nos permite evaluar la influencia del sistema nervioso parasimpático en el corazón y esto se obtiene calculando el logaritmo del producto de la variabilidad longitudinal (4*SD2) y transversal (4*SD1) del diagrama de poincaré. Este valor nos permite estudiar la función parasimpática, reflejando el nivel de recuperación del estres y por ende, una mayor salud cardiovascular. En la práctica, se evidencia que el sujeto de prueba tiene una mejor recuperación del estrés cuando está en reposo, que cuando está leyendo en voz alta. Esto se puede interpretar que a la persona le genera cierto estrés o molestía cuando está leyendo, ya sea por el tipo de lectura u otro tipo de situación.

# 6. Conclusiones.
Se cumplió el objetivo de la práctica, logrando adquirir una señal de ECG, procesarla y cuantificar la variabilidad de la frecuencia cardíaca (HRV) en dos estados distintos, reposo y lectura en voz alta. Los métodos de dominio del tiempo (SDNN, RMSSD) y no lineales (Poincaré) permitieron identificar cambios claros en el balance autonómico. 

La parte de leer en voz alta indujo un aumento en la frecuencia cardíaca media (de 85.78 a 91.44 lpm) y una disminución del Índice Vagal Cardíaco (CVI) (de 2.49 a 1.66). Ambos resultados son consistentes con la hipótesis de que una tarea cognitiva y física  genera una ligera carga de estrés provocando un aumento en la actividad simpática y una disminucion de la actividad parasimpática.

Se encontró un resultado paradójico: aunque la frecuencia cardíaca aumentó, las métricas de variabilidad como SDNN (0.06 a 0.14 s) y RMSSD (0.05 a 0.18 s) también aumentaron drásticamente. Un RMSSD alto generalmente indica mayor relajación.

La explicación para este suceso no es que el sujeto se relajó al leer, sino el efecto de la Arritmia Sinusal Respiratoria (ASR). Al leer en voz alta el sujeto se ve forzado a adoptar un patrón de respiración profundo y rítmico  como lo es inhalar, hablar, inhalar, hablar. Esta respiración controlada se acopla fuertemente con el nervio vago, exagerando artificialmente las métricas de HRV especialmente el RMSSD y la dispersión en el gráfico de Poincaré, enmascarando el verdadero estado de estrés autonómico.

Esto demuestra que, si bien el análisis de HRV es una herramienta muy biena  su interpretación no perfecta. Factores como la respiración son una variable de confusión. En este experimento, la frecuencia cardíaca  y el Índice Vagal  fueron los indicadores más fiables del ligero estrés inducido por la tarea, mientras que el SDNN y RMSSD fueron dominados por el artefacto respiratorio.

# 7. Aplicaciones biomédicas.

El análisis de la Variabilidad de la Frecuencia Cardíaca (HRV) ha trascendido la investigación para convertirse en una herramienta de diagnóstico y monitoreo no invasiva fundamental en múltiples campos de la medicina y la salud:

La HRV es un potente predictor de riesgo después de un infarto agudo de miocardio. Pacientes con una HRV baja (poca adaptabilidad) tienen una tasa de mortalidad significativamente mayor. También se usa para evaluar el riesgo de arritmias súbitas.

Se utiliza para monitorear la carga de entrenamiento en atletas de élite. Una caída sostenida en la HRV (específicamente en RMSSD) es un indicador clave de sobreentrenamiento y fatiga, señalando al entrenador que el atleta necesita más días de recuperación para evitar lesiones y optimizar el rendimiento.

Es la herramienta estándar muy importante para el diagnóstico temprano de la  neuropatía autonómica diabética. En pacientes con diabetes, el daño a los nervios (incluido el nervio vago) reduce drásticamente la HRV, y esta prueba puede detectarlo antes de que aparezcan síntomas severos.

El análisis de la HRV se usa para cuantificar objetivamente el estrés crónico, la ansiedad y la depresión, condiciones que se correlacionan con una HRV baja (un sistema simpático hiperactivo).

El monitoreo de la variabilidad de la frecuencia cardíaca fetal es crucial durante el parto. Una disminución en la variabilidad es un signo de alerta de sufrimiento fetal o falta de oxígeno, permitiendo al equipo médico intervenir a tiempo.
