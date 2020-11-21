# Practica

# Decision Trees

Practica LP Haskell Gabriel Domínguez Piernas Q1 2020-2021.

## Descripción

Esta practica genera un árbol de decisión en base al archivo "agaricus-lepiota.data" para poder determinar el carácter (venenoso/comestible) de una seta en función de sus atributos y características.

## Instalación

Para ejecutar la practica solamente hace falta compilar el archivo main.hs y ejecutarlo:

-> ghc dts.hs
./dts

## Entrada
La entrada por defecto es el fichero "agaricus-lepiota.data". Para cambiar esta entrada por defecto habría que cambiar el archivo que lee la función "readFile":

contents <- readFile "ejemplo.data" 



## Ejemplo de ejecución

Welcome to Decision Trees from Gabriel Domínguez

wich odor?
-> hacer luego


## Contenido
- dts: Archivo que ejecuta la totalidad del programa que contiene todas las funciones necesarias para el correcto funcionamiento y resolución de este
- agar.data: Archivo donde se almacenan los datos a evaluar, extraídos de https://archive.ics.uci.edu/ml/datasets/Mushroom









## Explicación del algoritmo

El algoritmo implementado en esta práctica es el denominado ID3. Dicho algoritmo basa su ejecución es la selección de, entre todas las variables posibles a diferenciar, la que mayor entropía tenga, siendo entropía como el cálculo explicado en el siguiente apartado.  
Una calculada la entropía de todas las variables del problema, se selecciona la máxima, esta representa la variable más determinante de las posibles y representará la raíz de nuestro árbol de decisión.
A continuación y de manera recursiva, se volverá a realizar el mismo cálculo pero esta vez condicionado por la elección anterior. Siendo X la variable escogida como nodo raíz del árbol, a partir de este se observarán las variables estando condicionadas por X. Para cada posible atributo que puede adoptar X se calcularán las entropías de las variables respecto de los datos que contengan la aparición de ese atributo en la condición. 
Es decir, siendo X,Y,Z los posibles valores posibles para adoptar la posición de raíz del árbol y siendo a,b,c los posibles atributos que puede adoptar cada variable, se calculará la entropía para Y y Z en función de a, de b y de c. 
Se realizará este proceso hasta llegar a un punto donde la entropía del atributo sea = 0. En este punto nos encontramos en una hoja, es decir, al llegar a ese punto del árbol podemos afirmar el carácter de la seta, podremos afirmar si se trata de una venenosa o no. 
El algoritmo procederá a construir recursivamente de este modo el árbol de decisión para poder determinar el carácter de la seta. 



## Explicación del cálculo entropico

El cálculo entrópico se basa en las siguientes fórmulas:

![alt text](https://miro.medium.com/max/700/0*08CaHVjPCgs_fZyp)


![alt text](https://miro.medium.com/max/391/1*nNY_7_aWRwp8E2DyGduEPg.png)





Siendo el cálculo entrópico el valor negado de la probabilidad que este sea edible multiplicado por el logaritmo en base dos de la probabilidad que sea edible menos la probabilidad que este sea poisonous multiplicado el logaritmo en base dos de la probabilidad de que sea poisonous.

El "gain" es equivalente a la operación resultante entre el cálculo entrópico de la variable menos el sumatorio de todos los cálculos entrópicos de los atributos de este.

Por ejemplo, imaginemos que las muestras totales de una variable, en un de sus atributos encontramos 10 apariciones, 3 de ellas comestibles y 7 venenosas, el cálculo seria el siguiente:

![alt text](https://miro.medium.com/max/700/0*R2ifm13OVNp9ZvVX)

Al valor resultante del cálculo entrópico de las 10 muestras habria que restarle sumatorio del cálculo entrópico de cada uno de los atributos (respecto de sus apariciones) que pertenecen a la variable.

El cálculo repetido de todas las posibles variables en cada llamada recursiva determina el comportamiento y construcción del árbol de decisión resultante.



## Webgrafia

https://gebakx.github.io/ml/#35

https://archive.ics.uci.edu/ml/datasets/Mushroom

https://es.wikipedia.org/wiki/Algoritmo_ID3

https://towardsdatascience.com/entropy-how-decision-trees-make-decisions-2946b9c18c8

https://sefiks.com/2017/11/20/a-step-by-step-id3-decision-tree-example/

https://medium.com/coinmonks/what-is-entropy-and-why-information-gain-is-matter-4e85d46d2f01






