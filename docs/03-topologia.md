---
output: html_document
---



# Topología

La topología consta de una familia de medidas que son calculadas sobre el conjunto completo de datos relacionales que componen una red; por consiguiente, proveen una indicación cuantitativa sobre la estructura de esta [@Valente2010]. Es relevante puesto que ciertos estudios sugieren que redes centralizadas alrededor de un conjunto de nodos centrales tienden a ser más eficientes en movilizar recursos humanos o financieros [@McCormick2000]; asimismo, esta configuración hace a la red más vulnerable a disrupción al remover un puñado de actores clave. De manera opuesta, las redes altamente descentralizadas son relativamente invulnerables a la eliminación de actores clave, pero pueden tener dificultades para movilizar recursos [@Cunningham2016].

Observe las Figuras \@ref(fig:3-1-star) y \@ref(fig:3-1-full), ambas tienen la misma cantidad de nodos, pero las características estructurales son diferentes y presentan ventajas y desventajas. Por ejemplo, en la Figura \@ref(fig:3-1-star) la mayoría de los nodos rodean a un actor en el centro de la red. Este tipo de configuración es comúnmente asociada con organizaciones jerárquicas con protocolos establecidos de comando y control. La ventaja de esta topología es que un nodo central controla el flujo de recursos e información, en teoría haciendo la diseminación de estos más eficiente. Sin embargo, esta estructura tiene un defecto clave. ¿Qué pasa si removemos al actor central? La red se deshace por completo y el flujo es interrumpido de manera indeterminada.

Ahora, en la Figura \@ref(fig:3-1-full) no encontramos una formación centrada alrededor de un actor clave. Al contrario, en este caso todos los nodos se encuentran conectados entre ellos. La ventaja es clara, no hay un solo punto de disrupción como en la Figura \@ref(fig:3-1-star). Sin embargo, las características estructurales no sugieren un solo camino para el flujo de información o recursos, lo cual en algunas ocasiones retrasa ciertos procesos organizacionales. Es decir, si todos son líderes, nadie puede estar a cargo de dar instrucciones a los demás. 

Es probable que sea mejor considerar ambas configuraciones (centralizada y descentralizada) como polos opuestos de un continuo. Como tal, el nivel óptimo de centralización en dicho espectro cambiará con el tiempo y en función de las presiones ambientales [@Cunningham2016; @Everton2012]. Por ejemplo, en un entorno hostil, la red puede priorizar la seguridad de actores clave; así, avanzando hacia una estructura más descentralizada. Es precisamente por este dinamismo intrínseco  que el estudio de la estructura de red debe ir acompañado con contexto.

<div class="figure" style="text-align: center">
<img src="03-topologia_files/figure-html/3-1-star-1.png" alt="Red estrella" width="100%" />
<p class="caption">(\#fig:3-1-star)Red estrella</p>
</div>

<div class="figure" style="text-align: center">
<img src="03-topologia_files/figure-html/3-1-full-1.png" alt="Red completa" width="100%" />
<p class="caption">(\#fig:3-1-full)Red completa</p>
</div>

En este capítulo, examinaremos una serie de medidas que capturan características estructurales de la red completa. Comenzaremos con una serie de medidas básicas comúnmente utilizadas para describir una red como: tamaño, distancia y diámetro. Después, exploraremos dos dimensiones topológicas: interconexión y centralización. Esta discusión será complementada por una serie de medidas correspondientes. Finalmente, este capítulo concluirá con un ejercicio práctico en Gephi.

## Medidas Básicas de Topología

Estas proveen al analista contexto sobre la red en discusión. Aquí cubriremos: tamaño, distancia promedio, y diámetro.  

### Tamaño

El tamaño se refiere a el número de actores en una red [@Everton2012]. Es importante pues afecta otras medidas topológicas de la red. Por ello, conocer el tamaño de una red es importante al interpretar medidas basadas en este valor, como densidad o diámetro [@Cunningham2016].

Comúnmente denotamos el tamaño de una red con la letra $N$. Por ejemplo, en las Figuras \@ref(fig:3-1-g5) y \@ref(fig:3-1-g10) $N$ es equivalente a 5 y 10 respectivamente. 

<div class="figure" style="text-align: center">
<img src="03-topologia_files/figure-html/3-1-g5-1.png" alt="Grafo de red, tamaño = 5" width="100%" />
<p class="caption">(\#fig:3-1-g5)Grafo de red, tamaño = 5</p>
</div>

<div class="figure" style="text-align: center">
<img src="03-topologia_files/figure-html/3-1-g10-1.png" alt="Grafo de red, tamaño = 10" width="100%" />
<p class="caption">(\#fig:3-1-g10)Grafo de red, tamaño = 10</p>
</div>

En teoría, hay un límite práctico a la cantidad de enlaces que puede mantener cada persona en la red, por ello, el tamaño habitualmente no es una de las medidas más interesantes sino un indicador de los límites de la red [@Valente2010]. El analista debe considerar como establecer los límites para reflejar de manera adecuada el tamaño real de la red [@Cunningham2016].

### Distancia Promedio

La distancia promedio se refiere a la longitud promedio de todos los caminos más cortos entre todos los actores de una red [@Everton2012]. Para un grafo no dirigido binario $G$, definimos la distancia promedio como:

$$
l_G = \frac{1}{N(N-1)}\sum\limits_{i \neq j}d(v_i,v_j)
$$

Examinemos esta definición, con la Figura \@ref(fig:3-1-circ). Supongamos que el objetivo del actor 1 es transferir información a los otros actores en la red de la manera más eficiente. 

<div class="figure" style="text-align: center">
<img src="03-topologia_files/figure-html/3-1-circ-1.png" alt="Grafo circular" width="100%" />
<p class="caption">(\#fig:3-1-circ)Grafo circular</p>
</div>

Si $d$ es la distancia entre un par de nodos, podemos expresar la distancia entre el nodo 1 y los demás de la siguiente manera:

$d(1, 2) = 1$

$d(1, 3) = 2$

$d(1, 4) = 2$

$d(1, 5) = 1$

Por consiguiente, debemos calcular la distancia ($d$) entre cualquier nodo ($i$) y todos los demás en la red ($j$), sumar estos valores ($\sum\limits_{i \neq j}d(v_i,v_j)$)  y multiplicar este valor por la fracción del total de enlaces posibles en el gráfico ($\frac{1}{N(N-1)}$). La Figura \@ref(fig:3-1-circ) se vería reflejada como la siguiente operación: 

$$
l_G = \frac{1}{5(5-1)} \times 5(1 + 2 + 2 + 1) = 1.5
$$

Al calcular la distancia promedio, podemos decir que en promedio todos los nodos en la Figura \@ref(fig:3-1-circ) se encuentran a 1.5 pasos entre ellos. Puesto que este es un promedio de distancias, podemos comparar este valor con el promedio de otra red.

En términos prácticos, la distancia promedio es indicativa de la velocidad con la cual la información puede viajar a través de una red. Es decir, en una red compacta la información se puede difundir rápidamente; al contrario, en una red con una distancia promedio alta la difusión de información tomará lugar en un periodo de tiempo más amplio [@Everton2012]. Esta interpretación no es ley, sino una suposición comúnmente hecha por analistas. Es importante considerar que en ciertas situaciones las redes con distancia promedio pequeñas no gozan de difusión rápida puesto que algunos actores tienden a retener información de sus vecinos [@Cunningham2016]. Adicionalmente, se debe recalcar que la fórmula de distancia promedio se centra en eficiencia, es decir, distancias más cortas entre nodos. Es posible que, en una red oscura donde los nodos no conozcan a sus vecinos o a los vecinos de sus vecinos, un actor envié información a través de caminos con distancias mayores al promedio. Por lo tanto, la distancia promedio solo sugiere eficiencias con base a la estructura de una red. 

### Diámetro

La distancia geodésica mayor entre todos los nodos en un grafo [@Everton2012]. Formalmente, @Wasserman1994 definen esta medida como la máxima $d(i, j)$ o $maxd(i,j)$. Por ejemplo, podemos calcular las distancias geodésicas de la Figura \@ref(fig:3-1-diam):

<div class="figure" style="text-align: center">
<img src="03-topologia_files/figure-html/3-1-diam-1.png" alt="Grafo ejemplo" width="100%" />
<p class="caption">(\#fig:3-1-diam)Grafo ejemplo</p>
</div>

El diámetro del grafo es equivalente a $max d(i,j)$ = $d(1,5)$= 3.

Esta medida es importante pues cuantifica cuán lejos se encuentran los nodos más distantes entre sí [@Wasserman1994]. Como con la distancia promedio, consideremos una red en la cual la información viaja a través de los vínculos entre actores. Suponiendo que los mensajes siguen las rutas más cortas, tomará tiempo para que un mensaje recurra toda la red cuando el diámetro es mayor. 

## Interconexión 

En una red oscura, la interconexión entre los actores es crucial para la red como organismo dinámico. Por ejemplo, puesto que la seguridad de la organización es crucial, a menudo el reclutamiento de nuevos miembros toma lugar a través de los vínculos preexistentes de miembros de la red [@Cunningham2016]. Es por este aislamiento que las redes oscuras enfocadas en el anonimato tienden a volverse cada vez más densas con vínculos entre miembros de la red y pocos enlaces al mundo exterior. Sin embargo, el cortar vínculos con el mundo exterior conlleva un costo al limitar el acceso a recursos (por ejemplo, materiales, logísticos, financieros, etc.). Es por ello, que algunos investigadores y analistas sugieren que los vínculos a actores externos a la red oscura son esenciales para acceder recursos y sobrevivir retos [@Uzzi1996]. 

Esta dinámica entre acceso a recursos y seguridad, fuerza a las organizaciones y a los actores que las conforman a balancear aislamiento (por ejemplo, interconexión alta) con acceso a recursos exteriores (por ejemplo, interconexión moderada o baja). En esta sección, nos enfocamos en las medidas comúnmente utilizadas para medir este proceso, específicamente, densidad y grado medio.

### Densidad

La densidad ($d$) es el número de enlaces en un grafo dividido por el número total posible de enlaces en el mismo [@Cunningham2016]. En una red no dirigida, se define como:

$$
d = \frac{2L}{n(n-1)/2}
$$

Donde $L$ se refiere al número actual de enlaces y $n$ es el número de actores en la red. Para una red dirigida, no es necesario multiplicar el numerador por dos, y la ecuación es diferente:

$$
d = \frac{L}{n(n-1)}
$$

En términos prácticos, ambas ecuaciones producen puntuaciones de densidad de 0 a 1. Es decir, una red con una densidad de 0 es una en la que no existen vínculos entre los actores. Mientras que una red con una densidad de uno es un gráfico completamente conectado en el que todos los actores están vinculados entre sí.

<div class="figure" style="text-align: center">
<img src="03-topologia_files/figure-html/3-1-den-1.png" alt="Grafo no dirigido" width="100%" />
<p class="caption">(\#fig:3-1-den)Grafo no dirigido</p>
</div>

Pongamos esta herramienta en práctica; específicamente, con la Figura \@ref(fig:3-1-den) la cual podemos representar como matriz de adyacencia:

$$
\begin{matrix}
  & 1 & 2 & 3 & 4 \\
1 & - & 1 & 1 & 1 \\
2 & 1 & - & 0 & 0 \\
3 & 1 & 0 & - & 0 \\
4 & 1 & 0 & 0 & -
(\#eq:3-1-den)
\end{matrix}
$$


El número actual ($L$) de enlaces es tres y contamos con cuatro nodos en este gráfico. Entonces, la densidad de esta red es equivalente a $d =$ 0.5. Es decir, la interconexión de la red es 0.5 o solo la mitad de los actores están conectados.

### Grado Medio

La medida de densidad está inversamente relacionada con el tamaño de la red, puesto que al agregar actores a la red, el número de vínculos posibles aumenta exponencialmente mientras que el número de vínculos que cada actor puede mantener se mantiene constante [@Everton2012]. Es por ello, que a menudo las redes más grandes tendrán densidades más bajas. Con base en esta observación, los analistas de redes utilizan la medida de grado medio para comparar el nivel de interconexión entre redes de diferentes tamaños. El grado medio se define formalmente como el promedio de enlaces que tiene cada actor en la red. Si el grado de cada nodo es $k$, entonces:

$$
\bar{k} = \frac{E}{N}
$$




Donde $N$ es el número de nodos y $E$ es el número de vínculos en la red. En términos prácticos, esta ecuación retorna un número promedio de vínculos para todos los actores en la red. Esto nos ayuda a comparar redes de diferentes tamaños. Por ejemplo, las redes \@ref(fig:3-1-avg1) y \@ref(fig:3-1-avg2) tienen un grado medio similar, de 1.98 y 1.99 respectivamente. La densidad es equivalente a 0.02 y a 0.01.

<div class="figure" style="text-align: center">
<img src="03-topologia_files/figure-html/3-1-avg1-1.png" alt="Grafo sin escala de 100 nodos" width="100%" />
<p class="caption">(\#fig:3-1-avg1)Grafo sin escala de 100 nodos</p>
</div>

<div class="figure" style="text-align: center">
<img src="03-topologia_files/figure-html/3-1-avg2-1.png" alt="Grafo sin escala de 200 nodos" width="100%" />
<p class="caption">(\#fig:3-1-avg2)Grafo sin escala de 200 nodos</p>
</div>

Es decir, aunque la densidad de estos gráficos es disímil podemos atribuir esta discrepancia a el número de nodos en cada red. Sin embargo, la medida más adecuada en esta situación sería el grado medio, la cual como vemos nos permite comparar el nivel de interconexión entre redes de diferente tamaño. 

## Centralización

Para recapitular, la eficiencia operacional de una red se ve afectada por la habilidad de esta para movilizar recursos materiales o humanos [@McCormick2000]. Algunos sugieren que esta capacidad operacional se encuentra íntimamente relacionada con la topología de la red social; específicamente, la centralización de la red [@Morselli2001; @Cunningham2016]. Sin embargo, las redes altamente centralizadas no son libres de desafíos. Sino que pueden ser vulnerables a la eliminación de un puñado clave de nodos [@Bakker2011]. Por ello, @Everton2012a hace el argumento "demasiado de algo bueno puede llevar a las redes a tener un rendimiento inferior ... [desde la perspectiva de la red oscura] no deben encontrase demasiado centralizadas o descentralizadas, mientras que desde la nuestra así es exactamente como queremos que sean" [@Everton2012a]. 

Es crucial que como analistas de redes sepamos como determinar el nivel de centralización de una red. En la siguiente sección presentamos la medida de centralización, la cual es comúnmente utilizada para capturar de manera cuantitativa el nivel de centralización de una red.

### Centralización

La centralización es el grado en que los vínculos de una red se centran en una persona o un conjunto de personas, de modo que en una red centralizada, una o varias personas ocupan puestos de poder y control en la red, mientras que las redes descentralizadas tienen estructuras de poder y control difusas [@Valente2010].

Esta medida se basa en la centralidad de cada nodo en la red para calcular que tan variables o heterogéneas es la distribución de estos índices para cada actor [@Wasserman1994]. Podemos observar un ejemplo de red centralizada en la Figura \@ref(fig:3-1-star). En el grafo estrella el actor uno (1) tiene contacto directo con todos los demás, los cuales no tienen contacto entre ellos. Utilizando el concepto de centralidad de grado, que es el número de vínculos que tiene cada nodo, exploremos como calcular la centralización de grado. Aquí utilizamos la definición general matemática de Freeman [-@Freeman1979] para calcular el índice de centralización de grado a nivel grupo:

$$
C = \frac{\sum [C(n^*) - C(n_i)]}{max\sum [C(n^*) - C(n_i)]}
$$

Donde $C(n_i)$ representa el índice de centralidad de un actor y $C(n^*)$ es el mayor valor del índice de centralidad en la red. Por lo tanto, $\sum [C(n^*) - C(n_i)]$ es la suma de las diferencias entre el valor máximo y los valores observados; adicionalmente, $max\sum [C(n^*) - C(n_i)]$ es la suma teórica máxima [@Wasserman1994]. El producto de esta operación es un índice entre 0 y 1. Una red con un índice de centralización 0 sería aquella donde todos los actores tienen la misma centralidad. De manera opuesta, una red con índice de centralización 1 representa una configuración donde un solo actor domina el índice de centralidad comparado con los demás nodos en la red. Utilizando la fórmula de Freeman, calculemos la centralización de grado para la red estrella (ver Figura \@ref(fig:3-1-star)). 

$C_D = \frac{\sum [C(n^*) - C(n_i)]}{max\sum [C(n^*) - C(n_i)]}$

$C_D = \frac{(4-4)+(4-1)+(4-1)+(4-1)+(4-1)}{12}$

$C_D = 1.0$

En la red estrella la centralización de grado es 1.0. Por consiguiente, de manera matemática asumimos que los nodos en este gráfico convergen alrededor de un actor central.

Veamos que sucede al introducir vínculos adicionales al grafo. En la Figura \@ref(fig:3-1-star3) el actor uno retiene el mismo número de vínculos que le proveen contacto directo con todos los demás,  sin embargo, en esta ocasión los actores dos (2) y tres (3) tienen acceso mutuo. 

<div class="figure" style="text-align: center">
<img src="03-topologia_files/figure-html/3-1-star3-1.png" alt="Red estrella modificada" width="100%" />
<p class="caption">(\#fig:3-1-star3)Red estrella modificada</p>
</div>

Recalculemos, la centralización de la red con base a la centralidad de grado:

$C_D = \frac{\sum [C(n^*) - C(n_i)]}{max\sum [C(n^*) - C(n_i)]}$

$C_D = \frac{(4-4)+(4-2)+(4-2)+(4-1)+(4-1)}{12}$

$C_D = 0.833$

El índice de centralización de grado es 0.833. Lo cual sugiere que la mayoría de los vínculos en la red se encuentran enlazados con un actor central. Sin embargo, al agregar vínculos en la periferia de la red vemos una reducción en la homogeneidad de los valores individuales, la cual reduce el índice grupal.

Antes de concluir esta sección, es importante recalcar dos cosas. Primero, como se ha mencionado la centralización es un índice grupal generado a base de las medidas de centralidad para cada vértice. En los siguientes capítulos veremos múltiples medidas de centralidad que pueden servir como precursores para calcular una medida de centralización. En este capítulo solamente hemos utilizado la centralidad de grado como precursor, pero es importante tener en mente que es posible generar índices de centralización con medidas de centralidad como intermediación, cercanía, o eigenvector. Segundo, Gephi no tiene la capacidad de calcular centralización, sin embargo, otras plataformas de software (como ORA, UCInet, o igraph) tienen esta capacidad y complementan las funciones de Gephi. 


## Ejercicio Práctico

En este ejercicio consideramos varias métricas para examinar la topología de la red, por ejemplo: tamaño de la red, densidad, grado medio, distancia promedio, y diámetro. El tamaño es igual al número de actores en una red. La densidad es igual al número de enlaces dividido por el total de lazos posibles. Sin embargo, el número de enlaces posibles en una red está inversamente relacionado con el tamaño de la red (es decir, cuanto más grande es la red, menor es la densidad); por consiguiente, los investigadores usan otras medidas como el grado promedio para comparar redes de diferente tamaño. La distancia promedio de la ruta es la longitud promedio de todas las rutas más cortas (es decir, geodésicas) entre todos los actores en una red, y el diámetro es la geodésica más larga de una red.

Para este ejercicio utilizaremos un conjunto de datos con diez redes diferentes apiladas, que se encuentran ya cargadas en el archivo: [`Noordin.gephi`](https://github.com/cjcallag/arso/blob/main/data/topology/Noordin.gephi?raw=true). [Descargue del sitio de web que acompaña este manual ](https://cjcallag.github.io/arso-materiales-educativos/).

### Antes de Empezar

Para este ejercicio, deberá instalar el módulo *Clustering Coefficient* (o coeficiente de agrupación) en Gephi. Haga esto siguiendo los mismos pasos que utilizamos para descargar el módulo *MultimodeNetworks Transformation* en ejercicio práctico en el capítulo [Derivando Datos Modo-Uno de Modo-Dos]. 


### Topología de redes en Gephi

:::{.row}
:::{.lcolumn-20 data-latex="{0.18\\textwidth}"}
*[Gephi]*
*Archivo>Abrir*
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

:::{.rcolumn-80 data-latex="{0.78\\textwidth}"}
  1.	Abra el archivo `Noordin.gephi`. En el primer espacio de trabajo, encontrará la red Noordin apilada. Los otros 10 espacios de trabajo son subredes por tipo de relación individual. 
:::
:::

\newline

:::{.row}
:::{.lcolumn-20 data-latex="{0.18\\textwidth}"}
*[Vista General]*
*Contexto*
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

:::{.rcolumn-80 data-latex="{0.78\\textwidth}"}
  2.	Comenzaremos por ver cómo encontrar el tamaño de una red. En la esquina superior derecha de la ventana *Descripción general*, debe verá una pestaña *Contexto* (cuadro rojo en la Figura \@ref(fig:3-1-1); si no se encuentra visible, seleccione la opción *Contexto* en el menú *Ventana*). En esta ventanilla ver el tamaño (número de nodos), cuántos lazos (aristas) tiene la red/subred y si los datos son dirigidos o no. **¿Cuál es el tamaño de "Noordin (Red apilada)" (en inglés “Noordin (Stacked Network)”)?** Cambie al espacio de trabajo "Red de amistad (en inglés “Friendship”). **¿Qué tamaño tiene? ¿Cuántas aristas hay?**
:::
:::

<div class="figure" style="text-align: center">
<img src="images/02-08-01.png" alt="Ventana de descripción general, ventanilla de contexto" width="100%" />
<p class="caption">(\#fig:3-1-1)Ventana de descripción general, ventanilla de contexto</p>
</div>

:::{.row}
:::{.lcolumn-20 data-latex="{0.18\\textwidth}"}
*Estadísticas > Densidad de grafo > Ejecutar* 
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

:::{.rcolumn-80 data-latex="{0.78\\textwidth}"}
  3.	Calcular la densidad de la red en Gephi es sencillo. Seleccione la pestaña *Estadísticas* que se encuentra debajo de la ventana *Contexto* (consulte la Figura \@ref(fig:3-1-2)) y haga clic en el botón *Ejecutar* junto a la opción *Densidad de grafo*. Cuando se le solicite, trate el gráfico como no dirigido. *¿Cuál es la densidad de la red apilada?* De clic en *Cerrar* para cerrar la ventanilla de reporte. Si desea volver a consultar la densidad, el resultado aparece junto a *Densidad de grafo*. Siempre puede volver a ver el reporte dando clic en el círculo con el *?* a la derecha de la opción *Ejecutar*. Repita el proceso para las redes de Amistad (en inglés "Friendship”) y Comunicaciones (en inglés “Comunications”). **¿Cuál es la densidad de la red de amistad? ¿Y la red de comunicaciones?**
:::
:::

<div class="figure" style="text-align: center">
<img src="images/02-08-02.png" alt="Ventana de descripción general, pestaña Estadísticas" width="100%" />
<p class="caption">(\#fig:3-1-2)Ventana de descripción general, pestaña Estadísticas</p>
</div>

:::{.row}
:::{.lcolumn-20 data-latex="{0.18\\textwidth}"}
*Estadísticas > Grado medio > Ejecutar* 
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

:::{.rcolumn-80 data-latex="{0.78\\textwidth}"}
  4.	La densidad de la red es igual a el número de enlaces dividido por todos los lazos posibles. Sin embargo, los puntajes de densidad tienden a disminuir a medida que las redes sociales se hacen más grandes porque el número de enlaces posibles aumenta exponencialmente con cada actor adicional, pero el número de lazos que cada actor puede mantener permanece relativamente constante. Por esto, la densidad de la red se debe usar para comparar redes del mismo tamaño (que hacemos aquí). Una medida alternativa a la densidad es el grado medio puesto que esta no es sensible al tamaño de la red. Por consiguiente, podemos utilizar esta segunda medida para comparar redes de diferentes tamaños. Podemos estimar el grado promedio de la red apilada haciendo clic en *Ejecutar* junto a *Grado medio* en la ventana de *Estadísticas*.  En este caso, solo nos interesa la medida de grado medio estándar en lugar de la medida de *Grado medio con pesos* porque no queremos incorporar los pesos de las conexiones. La puntuación aparecerá en la esquina superior izquierda de la ventana del informe (no se muestra). **¿Cuál es el grado medio de la red apilada?** El informe también produce un gráfico de *distribución de grados* que indica el número de actores en diferentes niveles de centralidad de grado. Si observa de cerca, verá que parece que hay un actor con un grado de centralidad de 130. Volveremos a este informe en un ejercicio posterior cuando veamos los puntajes de centralidad individuales. **¿Cuál es el grado medio de la red de amistad? ¿Comunicaciones? De las 10 redes individuales, ¿cuál tiene el grado medio más alto?**
:::
:::

\newline

:::{.row}
:::{.lcolumn-20 data-latex="{0.18\\textwidth}"}
*Estadísticas > Clustering Coefficient > Ejecutar*
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

:::{.rcolumn-80 data-latex="{0.78\\textwidth}"}
  5.	Otra medida que podemos usar para capturar el nivel general de cohesión es el coeficiente de agrupación. Se estima identificando primero la red del ego para cada actor (es decir, los lazos de cada actor con otros actores vecinos o alteres y los lazos entre ellos), después calcular la densidad de esta misma (sin incluir el ego o los lazos del ego en el cálculo), y luego tomando el promedio de todos los puntajes de densidad de la red del ego. Esta medida toma en cuenta el número de los vecinos de cada actor que están conectados entre sí (también conocido como cierre triádico) y calcula el promedio de toda la red. Para obtener esta medida, en la pestaña *Estadísticas*, busque la sección denominada *Visión general de la red*. Haga clic en *Ejecutar* junto a *Clustering Coefficient*. Indique que desea utilizar el *Basic method* (método básico) y haga clic en *Aceptar*. El resultado aparecerá en la parte inferior de la ventana del informe después de las puntuaciones individuales, bajo *General C*. **¿Cuál es el coeficiente de agrupación de la red apilada? ¿La red de la amistad? ¿Red de comunicaciones? ¿Qué coeficiente de agrupamiento de red es más alto?**
:::
:::

\newline

:::{.row}
:::{.lcolumn-20 data-latex="{0.18\\textwidth}"}
*Estadísticas > Longitud media de camino > Ejecutar*
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

:::{.rcolumn-80 data-latex="{0.78\\textwidth}"}
6.	Ahora veremos cómo obtener la distancia promedio y el diámetro en una red. La primera medida captura la distancia promedio entre todos los pares de actores (conectados) en la red, y puede indicar la velocidad con que la información puede viajar a través de una red. En otras palabras, la información se ha de difundir más eficazmente en una red de menor distancia promedio que en una red con una distancia promedio alta. El diámetro de la red se refiere a la geodésica más larga de una red (es decir, la ruta más corta entre todos los pares de actores) y podría indicar qué tan dispersa o extendida está una red. Por lo tanto, puede capturar el grado en que una red está centralizada o descentralizada. Sin embargo, debemos tener un poco de cuidado al interpretar el diámetro porque es, en parte, una función del tamaño de la red. Por ejemplo, las redes grandes probablemente tendrán diámetros mayores. Para calcular la distancia y el diámetro promedio de la ruta de la red apilada, regrese a la pestaña *Estadísticas* y busque la sección *Visión general de las aristas*. Allí, haga clic en el botón *Ejecutar* a la derecha de *Longitud media de camino*. En el cuadro de diálogo, seleccione la opción no dirigida, no se preocupe por normalizar la centralidad en este momento (lo cubriremos en la sección de centralidad) y haga clic en *Aceptar*. Esto abrirá un informe (Figura \@ref(fig:3-1-3)) que proporciona mucha información, parte de la cual no nos ocuparemos en este momento. En la parte superior izquierda del informe, en *Results* (Resultados), Gephi nos dice cuál es el diámetro (*diameter*) y la distancia promedio de la ruta (*Average Path length*) para la red Noordin apilada **¿Cuál es la distancia y el diámetro promedio de las redes de comunicaciones y amistad?**
:::
:::

<div class="figure" style="text-align: center">
<img src="images/02-08-03.png" alt="Ventana de descripción general, pestaña Estadísticas" width="100%" />
<p class="caption">(\#fig:3-1-3)Ventana de descripción general, pestaña Estadísticas</p>
</div>
