# FOURIER ANALISYS OF KALLPA AND SPT SIGNALS

## 1. Descripción del archivo con extensión .ctn
El programa inicia leyendo el archivo ctn ubicado en data, en esta versión solo cuento con un archivo llamado "profundidad_-.ctn". 

El archivo cuenta con 5 columnas:
* Las primeras $4$ filas son datos de cabecera que se utilizan para otros cálculos que no son parte de este análisis 
* La columna tiempo está mal tomada, pero podemos notar que al restar dos datos seguidos nos da el periodo de muestreo que corresponde a una frecuencia de 50 KHz.
* Luego siguen las columnas de dos sensores strain gages cuyas unidades están en micro strain
* Las últimas dos columnas son de dos acelerómetros con unidades en g (aceleración de la gravedad).

## 2. Descripción general del programa:
* El programa inicia mostrando los datos originales.
* Se calcula y muestra los Power Spectrum Density de las 4 señales (2 strain gages y 2 acelerómetros).
* Se integra usando la librería Obspy la aceleración para obtener velocidad.
* Se grafica la velocidad.
* Se calcula el Power Spectrum Density de la velocidad.
* Se verifica que hay unos picos extraños en el PSD y se procede a eliminarlos con filtro pasa alta del obspy (freq de corte = 60Hz)
* Se grafica la nueva velocidad filtrada
* Se grafica el PSD de la nueva velocidad filtrada.
* Se realiza un segundo método de filtro que consiste en crear una mascara en base a un umbral (amplitud del PSD) y retirar las frecuencias que pasan dicho umbral.
* El umbral escogido fue de 5 (se escogió de manera visual).
* Se reailiza tranformada inversa de fourier para obtener la señal filtrada y graficarla. La señal obtenida no es tan buena como la obtenida por Obspy.
* Se grafica las velocidades de la señal filtrada por el segundo método.
* Se procede a utilizar el primer método en el programa Kallpa Processor, verificando que el filtrado disminuye bastante la energía en comparación con el Software PDA.

## 3. Como usar este repositorio
* Debemos tener anaconda o minicodan instalado.
* Clonar el repositorio.
* Abrir tu conda prompt
* Usar el archivo yml para instalar la version de Python y sus paquetes respectivos con el comando: conda env create -f kallpa_fourier.yml
* Activar el entorno virtual llamado kallpa_v1 con el comando: conda activate kallpa_v1
* Abrir un jupyter notebook con el comando: jupyter notebook
