# VC_P3

**TAREA 1: Captura una o varias imágenes con monedas no solapadas y algún objeto que no lo sea. Filtra los contornos que no se correpondan con monedas, y muestra el número total de monedas presentes en la imagen..**

En esta tarea hemos convertido la imagen a escala de grises para luego umbralizarla, con un valor de 145, usando el THRESH_BINARY_INV. Con este imagen hemos conseguido los contornos externos. Finalmente, para cada contorno se ha calculado el area usando la función contourArea(contorno) y también se ha calculado el área haciendo uso del radio devuelto por la función minEnclosingCirlce(contorno). Con estas dos áreas se ha podido comparar si los contornos correspondían a un círculo (moneda) o no.


**TAREA 2: Captura una o varias imágenes con monedas no solapadas, y otras con monedas solapadas. Identificada una moneda de un euro en la imagen, por ejemplo con un clic de ratón, calcular la cantidad de dinero presente en la imagen. ¿Qué problemas han observado?**

Para realizar esta tarea hemos partido de la imagen de monedas propuesta para obtener la relación entre el área de cada moneda con la moneda de un euro. 
Para resolver esta tarea, hemos utilizado dos variantes.
    En la primera variante, hemos hecho uso del cálculo previo utilizado en la tarea uno. Con los contornos filtrados de las monedas, hemos obtenido sus respectivas áreas y los centros de los círculos. Luego, para obtener la referencia con la cuál hacer el cálculo del dinero, hemos usado las coordenadas del ratón para seleccionar la moneda de un euro y a partir de esta y de las relaciones de las áreas, calcular el dinero total de la imagen.
    Esta variante cuenta con dos problemas, el principal es la diferenciación de áreas cuando las monedas son muy similares, en nuestro caso se confunde con la moneda de 20 céntimos y la de 10 céntimos, y también está el problema del solape de monedas al usar las funciones de contornos básicas de OpenCV, la detección de círculos falla.

Problemas: a veces no pilla bien la moneda de 1 euro y no se puede calcular el precio.

![image](https://github.com/Kronn0/VC_P3/assets/92724148/06b62add-7d74-43f2-908c-8faa60ce9c19)

![image](https://github.com/Kronn0/VC_P3/assets/92724148/3859d677-8223-4b1b-9b9c-e40b5a875e93)

Monedas juntas:
![image](https://github.com/Kronn0/VC_P3/assets/92724148/e72b1004-ed2a-43de-997c-5c8f5052d91e)


![image](https://github.com/Kronn0/VC_P3/assets/92724148/de36c8d3-4013-4e0d-9d27-16aa9abf4782)



En la segunda variante, hemos usado la Transformada de Hough para la detección de círculos.

Primero nos dimos cuenta que la relación de Hue/Saturación en las monedas de referencia dadas en la practica, destaca que justo la de 1 euro supera el umbral de 1. Entonces identificamos la moneda de 1 euro en las imagenes, usamos el Hough para las monedas solapadas con otros objetos, y luego buscamos el area de las monedas y las relacionamos con la moneda de 1 euro, luego con un array sacado de las relaciones de la moneda de 1 euro de la referencia, aproximamos al valor más cercano esa relacion y le damos el valor de la moneda a la que corresponda.

    

**TAREA 3: Estas tres imágenes han sido extraidas de las imágenes de mayor tamaño contenidas en la carpeta. Determina patrones geométricos para cada una de las tres clases y evalúa los aciertos y fallos con las imágenes completas la matriz de confusión. Para cada clase, determina el número de muestras que se clasifican correctamente de dicha clase, y el número de muestras que se clasifica incorrectamente por cada una de las otras dos clases.**

Hemos usado la detección de contornos para sacar información de los objetos de la imagenes, tales como: radio, color, perimetro, area... Hemos usado principalmente el color para el Alquitrán ya que es muy oscuro y normalmente por debajo de una media de 80. Para las pellets hemos calculado su cercania con los circulos ya que son los unicos objetos que se asmilian a ellos y por último hemos por descarte dejado los fragmentos para los que no caen en estos ya que los fragmentos son erraticos pero muy claros. 


Fragment:

![image](https://github.com/Kronn0/VC_P3/assets/92724148/08ee6774-e6cd-436d-a0d5-33fc909568b8)
![image](https://github.com/Kronn0/VC_P3/assets/92724148/25388510-e22e-40d8-ab5a-01ca95510c28)

Alquitran
![image](https://github.com/Kronn0/VC_P3/assets/92724148/f3c5fec9-f462-4169-af67-a0333097c762)
![image](https://github.com/Kronn0/VC_P3/assets/92724148/689ece97-167c-4d37-a41d-fe170cc2b889)

Pellet:
![image](https://github.com/Kronn0/VC_P3/assets/92724148/9dbc4c4d-1afa-4205-aa6a-b66b20e3ea3e)
![image](https://github.com/Kronn0/VC_P3/assets/92724148/74a7724f-8ef0-4491-9ac7-2229277c6bf9)









 
