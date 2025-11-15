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

-**Parte A**
Luego de hacer una revisión bibliográfica acerca de la actividad simpática y parasimpática del sistema nervioso autónomo, de conocer los efectos de la misma en la frecuencia cardiaca y como sucede la variabilidad de la misma, además de descubrir el diagrama de Poincaré como una herramienta de análisis, se planteó el siguiente plan de acción para cumplir con el objetivo de la presente práctica:

<img width="540" height="1400" alt="image" src="https://github.com/user-attachments/assets/c52c0005-b0d4-4978-a52f-0c452ff13f64" />


# 6. Conclusiones.
# 7. Aplicaciones biomédicas.
