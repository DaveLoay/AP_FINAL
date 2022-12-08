# AP_FINAL

Este repositorio contiene los archivos de un auto-encoder variacional  (VAE) que genera muestras de audio.

DataSet:

El conjunto de datos con que se trabajo fue NSytn, el cual se puede encontar en:

https://magenta.tensorflow.org/nsynth

NSynth es un conjunto de datos de 12,768 muestras de audio monofónicas de 4 segundos de duración, con un sample rate 
de 16 KHz y correspondientes a 1006 instrumentos distintos.

Pre-procesamiento del DataSet:

Las muestras de audio (1D) son convertidas a espectograma (2D), en donde se sigue el siguinte proceso:
 
 1.- Cargar archivo\\
 2.- Aplicar padding a la señal (en caso de ser necesario)
 3.- Obtener el espectograma logaritmico de la señal 
 4.- Normalizar el espectograma
 5.- Guardar el spectograma normalizado


Modelo:

Se trata de un autencoder variacional que toma como entrada una imagen de (256,64,1) [H,W,C], con 5 capas 
convolucionales de 512, 256, 128, 64, 32 respectivamente y un espacio latente de 128 dimensiones.

Entrenamiento:

Detalles de implementación:
* 150 epocas de entrenamiento
* Inicializador Adam
* Tasa de aprendizaje: 0.0005
* NVIDIA 1080 Ti 

Generación de audio:

El modelo genera espectogramas de tamaño y dimensión iguales a las de la entrada, por lo que mediante el algoritmo de 
Griffin- Lim se convierte de espectograma ogaritmico de nuevo a audio.
Las muestras de audio generadas pueden verse en la carpeta de "Muestras generadas"

