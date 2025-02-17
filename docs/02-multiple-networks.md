---
output:
  pdf_document: default
  html_document: default
bibliography: book.bib
always_allow_html: yes
---



# Múltiples Relaciones

Hasta este punto, solo hemos trabajado con un tipo (modo-uno o modo-dos) de relaciones a la vez. Sin embargo, en el mundo real los actores incrustados en redes sociales se encuentran entrelazados los unos con otros por múltiples relaciones [@Hanneman2005]. Imagine su red social, es decir, los círculos sociales en los que usted se encuentra involucrado. ¿Qué relaciones ha considerado? Es probable que incluya vínculos familiares, amistosos, profesionales, membresía ligas de deportes o clubes religiosos. El punto clave es que las redes sociales constan de múltiples tipos de relaciones que unen a los actores. 

Por consiguiente, los analistas de redes trabajan con múltiples relaciones para poder abarcar la gama de interacciones en un sistema social. En este capítulo, cubriéremos algunas técnicas utilizadas al trabajar con múltiples tipos de relaciones, tomando pauta para recalcar las ventajas y desventajas de diferentes enfoques. Concluiremos con un ejercicio práctico en Gephi que le dará la oportunidad de utilizar estos conceptos. 

## Matrices y Listas de Aristas

Empecemos por considerar como trabajar con múltiples relaciones utilizando matrices. Las matrices subsecuentes representan dos relaciones diferentes, la matriz izquierda contiene relaciones familiares y la matriz derecha financieras. Por separado, cuentan una historia diferente de los miembros de la red.

::: {.row}
::: {.lcolumn-50 data-latex="{0.48\\textwidth}"}
$$
\begin{matrix}
  & A & B & C & D & E & F \\
A & 0 & 1 & 1 & 0 & 0 & 0 \\
B & 1 & 0 & 1 & 0 & 0 & 0 \\
C & 1 & 1 & 0 & 0 & 0 & 0 \\
D & 0 & 0 & 0 & 0 & 1 & 1 \\
E & 0 & 0 & 0 & 1 & 0 & 1 \\
F & 0 & 0 & 0 & 1 & 1 & 0 \\
(\#eq:2-5-mat1)
\end{matrix}
$$
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

::: {.rcolumn-50 data-latex="{0.48\\textwidth}"}
$$
\begin{matrix}
  & A & B & C & D & E & F \\
A & 0 & 0 & 0 & 0 & 0 & 0 \\
B & 0 & 0 & 0 & 0 & 0 & 0 \\
C & 0 & 0 & 0 & 1 & 0 & 0 \\
D & 0 & 0 & 1 & 0 & 0 & 0 \\
E & 0 & 0 & 0 & 0 & 0 & 0 \\
F & 0 & 0 & 0 & 0 & 0 & 0 \\
(\#eq:2-5-mat2)
\end{matrix}
$$
:::
:::

\break

El objetivo es analizar la combinación de estas relaciones de manera que podamos identificar los límites de la red. La Figura \@ref(fig:2-5-combined) es una representación de los datos descritos previamente en formato de sociomatriz. El grafo incluye dos tríadas cerradas que consisten de miembros familiares, los cuales se unen por una relación financiera. 

<div class="figure" style="text-align: center">
<img src="02-multiple-networks_files/figure-html/2-5-combined-1.png" alt="Múltiples Relaciones" width="100%" />
<p class="caption">(\#fig:2-5-combined)Múltiples Relaciones</p>
</div>

Como hemos mencionado previamente, el recopilar información en sociomatrices es laborioso e ineficiente. Por consiguiente, al recopilar múltiples tipos de relaciones es sugerible utilizar una lista de aristas, el formato básico de dos columnas puede ser expandido para incluir una columna clasificando el tipo de vínculo. Recuerde que en una lista de aristas cada fila representa un vínculo, por lo tanto, es posible apilar relaciones de la siguiente manera.

\break

<table class="table" style="margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;"> Origen </th>
   <th style="text-align:left;"> Destino </th>
   <th style="text-align:left;"> Relación </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;font-weight: bold;color: red !important;"> A </td>
   <td style="text-align:left;font-weight: bold;color: red !important;"> B </td>
   <td style="text-align:left;font-weight: bold;color: red !important;"> Familiar </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;color: red !important;"> A </td>
   <td style="text-align:left;font-weight: bold;color: red !important;"> C </td>
   <td style="text-align:left;font-weight: bold;color: red !important;"> Familiar </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;color: red !important;"> B </td>
   <td style="text-align:left;font-weight: bold;color: red !important;"> C </td>
   <td style="text-align:left;font-weight: bold;color: red !important;"> Familiar </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;color: red !important;"> D </td>
   <td style="text-align:left;font-weight: bold;color: red !important;"> E </td>
   <td style="text-align:left;font-weight: bold;color: red !important;"> Familiar </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;color: red !important;"> D </td>
   <td style="text-align:left;font-weight: bold;color: red !important;"> F </td>
   <td style="text-align:left;font-weight: bold;color: red !important;"> Familiar </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;color: red !important;"> E </td>
   <td style="text-align:left;font-weight: bold;color: red !important;"> F </td>
   <td style="text-align:left;font-weight: bold;color: red !important;"> Familiar </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;color: #018571 !important;"> C </td>
   <td style="text-align:left;font-weight: bold;color: #018571 !important;"> D </td>
   <td style="text-align:left;font-weight: bold;color: #018571 !important;"> Financiera </td>
  </tr>
</tbody>
</table>

El incorporar múltiples relaciones en una sola lista con una variable categórica, permite la importación de datos de manera efectiva. Sin embargo, es común encontrar analistas que mantienen sus relaciones en múltiples archivos por propósitos de manipulación de datos. 

## Combinar

El combinar datos relacionales en ARSo se puede lograr mediante diferentes métodos. @Cunningham2016 proponen tres técnicas: apilar, agregar y recombinar. En esta sección discutiremos las tres. 

### Apilar

El apilar es una técnica comúnmente utilizada por analistas para mantener y utilizar múltiples relaciones de manera independiente [@Cunningham2016]. El mantener e incorporar estos archivos varia con base a la herramienta de software. Por ejemplo, las matrices subsecuentes contienen relaciones de manera independiente, al apilarlas podemos crear un gráfico (ver Figura \@ref(fig:2-5-apiladas)) que incorpora ambas sin tener que unir estos datos; por consiguiente, todos los datos se mantienen íntegros.

::: {.row}
::: {.lcolumn-50 data-latex="{0.48\\textwidth}"}
$$
\begin{matrix}
  & A & B & C & D & E & F \\
A & 0 & 1 & 1 & 0 & 0 & 0 \\
B & 1 & 0 & 1 & 0 & 0 & 0 \\
C & 1 & 1 & 0 & 0 & 0 & 0 \\
D & 0 & 0 & 0 & 0 & 1 & 1 \\
E & 0 & 0 & 0 & 1 & 0 & 1 \\
F & 0 & 0 & 0 & 1 & 1 & 0 \\
(\#eq:2-5-mat3)
\end{matrix}
$$
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

::: {.rcolumn-50 data-latex="{0.48\\textwidth}"}
$$
\begin{matrix}
  & A & B & C & D & E & F \\
A & 0 & 0 & 0 & 0 & 0 & 0 \\
B & 0 & 0 & 0 & 0 & 1 & 0 \\
C & 0 & 0 & 0 & 1 & 0 & 0 \\
D & 0 & 0 & 1 & 0 & 0 & 0 \\
E & 0 & 1 & 0 & 0 & 0 & 0 \\
F & 0 & 0 & 0 & 0 & 0 & 0 \\
(\#eq:2-5-mat4)
\end{matrix}
$$
:::
:::

<div class="figure" style="text-align: center">
<img src="02-multiple-networks_files/figure-html/2-5-apiladas-1.png" alt="Relaciones Apiladas" width="100%" />
<p class="caption">(\#fig:2-5-apiladas)Relaciones Apiladas</p>
</div>

El objetivo de apilar es el poder agregar o remover datos al análisis con base en las necesidades del analista. Algunas plataformas de software tratan datos apilados como separados y por consiguiente calculan las medidas de cada matriz de manera independiente. Por ejemplo, el contar vínculos de las matrices  apiladas previamente produce dos valores diferentes. Es por ello, que usualmente el apilar relaciones solo se utiliza como una herramienta visual.

### Agregar

Como lo sugiere el nombre, agregar es una técnica que consiste en crear una nueva red de un conjunto de relaciones; usualmente, sumando las relaciones en un nuevo producto [@Cunningham2016]. Nuevamente, el proceso de agregar relaciones varía con base al programa de software. Sin embargo, podemos visualizar el proceso utilizando una sumación de matrices. Por ejemplo, las matrices a continuación representan dos tipos de relaciones asimétricas. Note que ambas matrices constan del mismo número de filas y columnas, lo cual es requerido para sumar matrices.

::: {.row}
::: {.lcolumn-50 data-latex="{0.48\\textwidth}"}
$$
\begin{matrix}
  & A & B & C & D \\
A & 0 & 1 & 1 & 0 \\
B & 1 & 0 & 1 & 0 \\
C & 1 & 1 & 0 & 0 \\
D & 0 & 0 & 0 & 0 \\
E & 0 & 0 & 0 & 1 \\
F & 0 & 0 & 0 & 1 \\
(\#eq:2-5-mat5)
\end{matrix}
$$
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

::: {.rcolumn-50 data-latex="{0.48\\textwidth}"}
$$
\begin{matrix}
  & A & B & C & D \\
A & 0 & 0 & 0 & 0 \\
B & 0 & 0 & 0 & 0 \\
C & 0 & 0 & 0 & 1 \\
D & 0 & 0 & 1 & 0 \\
E & 0 & 1 & 0 & 0 \\
F & 0 & 0 & 0 & 0 \\
(\#eq:2-5-mat6)
\end{matrix}
$$
:::
:::

\newline

El proceso en este ejemplo es simple, se suman las entradas correspondientes y genera una nueva matriz producto. Aquí el producto de la suma se representa en la Figura \@ref(fig:2-5-agregadas). Sin embargo, diferentes herramientas de software incluyen modificaciones de esta operación como el tomar un promedio de valores correspondientes, o solo incluir el valor mínimo o máximo, etc.

$$
\begin{matrix}
  & A & B & C & D \\
A & 0 & 1 & 1 & 0 \\
B & 1 & 0 & 1 & 0 \\
C & 1 & 0 & 0 & 0 \\
D & 0 & 0 & 1 & 0
\end{matrix}
\enspace + \enspace
\begin{matrix}
  & A & B & C & D \\
A & 0 & 1 & 0 & 0 \\
B & 0 & 0 & 0 & 0 \\
C & 0 & 0 & 0 & 1 \\
D & 0 & 0 & 1 & 0
\end{matrix}
\enspace = \enspace
\begin{matrix}
  & A & B & C & D \\
A & 0 & 2 & 1 & 0 \\
B & 1 & 0 & 1 & 0 \\
C & 1 & 0 & 0 & 2 \\
D & 0 & 0 & 1 & 0
\end{matrix}
(\#eq:2-5-matsum)
$$


<div class="figure" style="text-align: center">
<img src="02-multiple-networks_files/figure-html/2-5-agregadas-1.png" alt="Relaciones Agregadas" width="100%" />
<p class="caption">(\#fig:2-5-agregadas)Relaciones Agregadas</p>
</div>

El agregar redes tiene ventajas y desventajas. Permite consolidar datos antes de ejecutar medidas. Sin embargo, al consolidarlos perdemos información acerca del tipo de vínculo. Por ejemplo, en la matriz producto anterior vemos algunos valores de “2”, los cuales corresponden a la presencia de vínculos precursores en ambas matrices. Para los vínculos con un valor de “1” es imposible determinar a qué categoría o matriz precursora pertenece dicho vínculo sin evaluar las entradas correspondientes. Por consiguiente, los analistas de redes tienden a agregar datos y retener los conjuntos precursores.

### Recombinar

Ocasionalmente al trabajar con datos de redes encontraremos situaciones en las cuales es necesario evaluar si la presencia de un enlace es suficiente evidencia para determinar la conexión entre dos actores. Particularmente al trabajar con redes oscuras donde las actividades se mantienen encubiertas, el triangular una relación a menudo requiere utilizar umbrales o filtros para confirmar una conexión entre actores [@Cunningham2016]. 

@Cunningham2016 da un ejemplo práctico de recombinación de redes. Supongamos que tenemos dos redes modo-dos. La primera (matriz izquierda) vincula a personas con ubicaciones. La segunda (matriz derecha) vincula personas con roles operacionales. 

::: {.row}
::: {.lcolumn-50 data-latex="{0.48\\textwidth}"}
$$
\begin{matrix}
  & Lima & Cusco & Arequipa \\
A & 0    & 0     & 1        \\
B & 0    & 0     & 1        \\
C & 1    & 0     & 0        \\
D & 0    & 1     & 0        \\
E & 0    & 1     & 0        \\
F & 0    & 1     & 0        \\
G & 0    & 1     & 0        \\
H & 0    & 1     & 0        \\
I & 1    & 0     & 0        \\
(\#eq:2-5-mat7)
\end{matrix}
$$
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

::: {.rcolumn-50 data-latex="{0.48\\textwidth}"}
$$
\begin{matrix}
  & Finanza & Logística & Operativo \\
A & 1        & 0         & 0         \\
B & 1        & 0         & 0         \\
C & 1        & 0         & 0         \\
D & 0        & 1         & 0         \\
E & 0        & 1         & 0         \\
F & 0        & 0         & 1         \\
G & 0        & 0         & 1         \\
H & 1        & 0         & 0         \\
I & 0        & 1         & 0         \\
(\#eq:2-5-mat8)     
\end{matrix}
$$
:::
:::

\break

El vincular a todas las personas en una ubicación no siempre es adecuado, por ejemplo, en una ciudad de millones de habitantes es probable que dos personas que residen en dicha ciudad no se conozcan. Similarmente, el hecho de que dos personas compartan el mismo rol operacional en una organización no significa que estas estén enlazadas. Sin embargo, podemos recombinar nuestros datos para generar una sociomatriz donde actores en la misma ubicación y con el mismo rol operacional comparten un vínculo mutuo. Para ello, utilizamos los siguientes pasos:

$$
\begin{smallmatrix}
  & Lima & Cusco & Arequipa \\
A & 0    & 0     & 1        \\
B & 0    & 0     & 1        \\
C & 1    & 0     & 0        \\
D & 0    & 1     & 0        \\
E & 0    & 1     & 0        \\
F & 0    & 1     & 0        \\
G & 0    & 1     & 0        \\
H & 0    & 1     & 0        \\
I & 1    & 0     & 0        \\
\end{smallmatrix}
\enspace\times\enspace
\begin{smallmatrix}
         & A & B & C & D & E & F & G & H & I \\
Lima     & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 1 \\
Cusco    & 0 & 0 & 0 & 1 & 1 & 1 & 1 & 1 & 0 \\
Arequipa & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
\end{smallmatrix}
$$

$$
\enspace \circ \enspace
$$

$$
\begin{smallmatrix}
  & Finanza & Logística & Operativo \\
A & 1        & 0         & 0         \\
B & 1        & 0         & 0         \\
C & 1        & 0         & 0         \\
D & 0        & 1         & 0         \\
E & 0        & 1         & 0         \\
F & 0        & 0         & 1         \\
G & 0        & 0         & 1         \\
H & 1        & 0         & 0         \\
I & 0        & 1         & 0         \\
\end{smallmatrix}
\enspace\times\enspace
\begin{smallmatrix}
          & A & B & C & D & E & F & G & H & I \\
Finanza   & 1 & 1 & 1 & 0 & 0 & 0 & 0 & 1 & 0 \\
Logística & 0 & 0 & 0 & 1 & 1 & 0 & 0 & 0 & 1 \\
Operativo & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 0 & 0 \\
\end{smallmatrix}
$$

El proceso es simple, primero cada matriz de incidencia se debe multiplicar por su matriz equivalente transpuesta, como se presentó en la sección de [Proyección]. Puesto que el objetivo es recombinar los enlaces, el siguiente paso es multiplicar las matrices resultantes utilizando el producto Hadamard (operación por elementos) que vimos previamente. Esta última operación genera una sociomatriz modo-uno donde los nodos se encuentran enlazados si viven en la misma ubicación y comparten el mismo rol operacional (ver Figura \@ref(fig:2-5-recombinar)).

$$
\begin{matrix}
  & A & B & C & D & E & F & G & H & I \\
A & - & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
B & 1 & - & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
C & 0 & 0 & - & 0 & 0 & 0 & 0 & 0 & 0 \\
D & 0 & 0 & 0 & - & 1 & 0 & 0 & 0 & 0 \\
E & 0 & 0 & 0 & 1 & - & 0 & 0 & 0 & 0 \\
F & 0 & 0 & 0 & 0 & 0 & - & 1 & 0 & 0 \\
G & 0 & 0 & 0 & 0 & 0 & 1 & - & 0 & 0 \\
H & 0 & 0 & 0 & 0 & 0 & 0 & 0 & - & 0 \\
I & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & - \\
(\#eq:2-5-hadd) 
\end{matrix}
$$

<div class="figure" style="text-align: center">
<img src="02-multiple-networks_files/figure-html/2-5-recombinar-1.png" alt="Relaciones Recombinadas" width="100%" />
<p class="caption">(\#fig:2-5-recombinar)Relaciones Recombinadas</p>
</div>

Además de multiplicaciones de matriz, existen múltiples otras estrategias para recombinar relaciones. Sin embargo, esta discusión será continuada más adelante. Por ahora, solo nos enfocaremos en familiarizarlo con el concepto de recombinación. 


## Ejercicio Práctico

Los datos que utilizaremos son los datos de la red del Monasterio Sampson recopilados por Samuel Sampson, quien registró las interacciones sociales entre un grupo de hombres preparándose para unirse a una orden monástica. Grabó cuatro tipos de "lazos" entre estos actores: gusto (en tres períodos de tiempo diferentes) y disgusto (un período de tiempo); alta y baja estima; influencia positiva y negativa; alabanza y culpa. Es decir, este conjunto de datos tiene nominaciones positivas y negativas. Cada novicio clasificó sus tres preferencias para cada tipo de enlace, donde 3 indica su primera opción, 2 la segunda y 1 la tercera. Por ello, los vínculos son ponderados.

Durante el período de observación de Sampson, ocurrió una "crisis en el claustro" en respuesta a algunos de los cambios propuestos por el Concilio Vaticano II. Esto condujo a la expulsión de cuatro novicios y la partida voluntaria de varios otros. Según sus observaciones, Sampson dividió (es decir, ordenó y clasificó) a los novatos en cuatro grupos: (1) los jóvenes turcos, (2) la oposición leal, (3) los marginados y (4) los neutrales. Los jóvenes turcos llegaron más tarde y cuestionaron las prácticas del monasterio, a diferencia de la oposición leal que defendieron estas prácticas. Los marginados eran novatos que no fueron aceptados en el grupo principal, mientras que los neutrales fueron aquellos que no tomaron partido en el debate sobre las prácticas del monasterio. La mayor parte de la oposición leal había asistido a un seminario, "Cloisterville", antes de su llegada al monasterio.

### Importar múltiples redes a Gephi

:::{.row}
:::{.lcolumn-20 data-latex="{0.18\\textwidth}"}
*[Vista general]*

*Archivo > Abrir*
*Importar como > Tabla de nodos*
*Separador > Coma* 
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

:::{.rcolumn-80 data-latex="{0.78\\textwidth}"}
  1.	Para "apilar" redes en Gephi, cargaremos redes por separado. Por esto, encontramos nuestros datos de red en formato de tablas de nodos y de aristas.  Comience importando la tabla de nodos de Sampson, que puede descargar [del sitio de web que acompaña este manual ](https://cjcallag.github.io/arso-materiales-educativos/). Para hacerlo, use el comando *Archivo > Abrir*. Asegúrese de que Gephi reconozca la hoja de cálculo como una tabla de nodos y separada por comas. Dado que esta hoja de cálculo solo consta de nodos y sus atributos, en el informe de importación no tiene que preocuparse por las opciones. Sin embargo, debemos ser un poco más selectivos cuando importamos las listas de borde. Después de importar la tabla de nodos, examine brevemente los datos en la ventana *Laboratorio de datos*. 
:::
:::

\newline

:::{.row}
:::{.lcolumn-20 data-latex="{0.18\\textwidth}"}
*[Vista general]*

*Archivo > Abrir*
*Importar como > Tabla de aristas*
*Separador > Coma* 
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

:::{.rcolumn-80 data-latex="{0.78\\textwidth}"}
  2.	Use el comando *Archivo > Abrir* para importar el archivo `Liking 1.csv`, que puede descargar [del sitio de web que acompaña este manual ](https://cjcallag.github.io/arso-materiales-educativos/). En el primer cuadro de diálogo (Figura \@ref(fig:2-5-aristas)), asegúrese de que Gephi sepa que es una tabla de aristas y que los datos están separados por comas. Haga clic en *Siguiente* y en el siguiente cuadro de diálogo (no se muestra) acepte los valores predeterminados de Gephi y haga clic en *Terminar*. En el *Informe de importación* (Figura \@ref(fig:2-5-importacion)), indique que los datos no son dirigidos, no desea mezclar los bordes, pero sí desea agregar los datos al espacio de trabajo existente. Luego haga clic en *Aceptar*.
:::
:::

<div class="figure" style="text-align: center">
<img src="images/02-06-01_aristas.png" alt="Importar lista de aristas" width="100%" />
<p class="caption">(\#fig:2-5-aristas)Importar lista de aristas</p>
</div>

<div class="figure" style="text-align: center">
<img src="images/02-06-02_reporte.png" alt="Reporte de Importación" width="100%" />
<p class="caption">(\#fig:2-5-importacion)Reporte de Importación</p>
</div>

:::{.row}
:::{.lcolumn-20 data-latex="{0.18\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

:::{.rcolumn-80 data-latex="{0.78\\textwidth}"}
  3.	Repita el proceso para importar las nueve listas de aristas restantes (descárguelas individualmente: [`blame.csv`](https://raw.githubusercontent.com/cjcallag/arso/main/data/multiple_networks/blame.csv), [`dislike.csv`](https://raw.githubusercontent.com/cjcallag/arso/main/data/multiple_networks/dislike.csv), [`high_esteem.csv`](https://raw.githubusercontent.com/cjcallag/arso/main/data/multiple_networks/dislike.csv), [`liking_2.csv`](https://raw.githubusercontent.com/cjcallag/arso/main/data/multiple_networks/liking_2.csv), [`linking_3.csv`](https://raw.githubusercontent.com/cjcallag/arso/main/data/multiple_networks/liking_3.csv), [`low_esteem.csv`](https://raw.githubusercontent.com/cjcallag/arso/main/data/multiple_networks/low_esteem.csv), [`negative_influence.csv`](https://raw.githubusercontent.com/cjcallag/arso/main/data/multiple_networks/negative_influence.csv), [`positive_influence.csv`](https://raw.githubusercontent.com/cjcallag/arso/main/data/multiple_networks/positive_influence.csv), y [`praise.csv`](https://raw.githubusercontent.com/cjcallag/arso/main/data/multiple_networks/praise.csv)). **Tenga cuidado al importar cada archivo, fíjese en importar cada relación al espacio de trabajo existente.** Note que en el *Informe de importación* para cada lista de aristas, Gephi mantendrá seleccionadas la mayoría de las opciones anteriores, pero no *Nuevo espacio de trabajo*. Cada vez que importe un nuevo conjunto de vínculos, el gráfico parecerá cada vez más denso. Esto se debe a que cada vez que importa una nueva relación, agrega vínculos a la red. Si selecciona la *Tabla de bordes* en la ventana *Laboratorio de datos* y luego se desplaza hacia abajo, verá que cada conjunto de vínculos (relaciones) se apilan unos sobre otros.
:::
:::

\newline

:::{.row}
:::{.lcolumn-20 data-latex="{0.18\\textwidth}"}
*[Vista general]*

*Appearance > Edges*
*Color > Partición*
*--Escoge un atributo > relation > Apply*

*Paleta... > Generar*
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

:::{.rcolumn-80 data-latex="{0.78\\textwidth}"}
  4.	En la ventana *Vista general*, ubique la pestaña *Apariencia* y luego haga clic en la pestaña *Aristas*, luego en el ícono de la paleta de colores, luego en *Partición* y luego con el menú desplegable *--Escoge un atributo*, seleccione *relation* (en español: relación) y haga clic en *Aplicar*. Recuerde que el número predeterminado de colores de partición de Gephi es ocho, pero aquí tenemos 10 tipos de vínculos (relaciones). Por lo tanto, haga clic en el enlace *Paleta ...*, y en el cuadro de diálogo, seleccione *Generar*, al igual que hizo anteriormente, cambie el número de colores a 10 y genere un nuevo conjunto de colores. Una vez más, haga clic en *Aplicar*. El gráfico de red probablemente se verá un poco colorido (Figura \@ref(fig:2-5-apilada)). Esto se debe a que cada conjunto de bordes está coloreado por una sola clasificación.
:::
:::

<div class="figure" style="text-align: center">
<img src="images/02-06-03_apilada.png" alt="Red apilada de datos Monasterio de Sampson" width="100%" />
<p class="caption">(\#fig:2-5-apilada)Red apilada de datos Monasterio de Sampson</p>
</div>


:::{.row}
:::{.lcolumn-20 data-latex="{0.18\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

:::{.rcolumn-80 data-latex="{0.78\\textwidth}"}
  5.	Ahora podríamos aplicar uno de los algoritmos de diseño para hacer el gráfico más atractivo, pero por la combinación de vínculos positivos y negativos, el gráfico podría ser engañoso. **¿Por qué?** En las siguientes secciones extraeremos diferentes conjuntos de relaciones y las examinaremos por separado. Antes de esto, guarde su trabajo en un archivo de Gephi.
:::
:::

### Extrayendo y visualizando múltiples lazos en Gephi

:::{.row}
:::{.lcolumn-20 data-latex="{0.18\\textwidth}"}
*[Vista general]*

*Filtros > Atributos > Partición*

*Consultas > Partición > Filtrar > Exportar gráfico filtrado a un nuevo espacio de trabajo*

:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

:::{.rcolumn-80 data-latex="{0.78\\textwidth}"}
  1.	Extraer múltiples relaciones en Gephi es similar a extraer un subconjunto de red basado en atributos de nodo, que hemos hecho previamente. En esta sección, separaremos los enlaces positivos de la red apilada. En la pestaña *Filtros* a la derecha, primero seleccione *Atributos*, luego *Partición*. Arrastre la partición *relation* a la sección *Consultas*. En el cuadro debajo de la sección Consultas, seleccione `Liking 3` (Me gusta 3), `Positive Influence` (Influencia positiva), `High Esteem` (Alta estima) y `Praise` (Elogio). Luego haga clic en *Filtrar* y use el botón *Exportar gráfico filtrado a un nuevo espacio de trabajo*.
:::
:::

<div class="figure" style="text-align: center">
<img src="images/02-06-04_positivos.png" alt="Enlaces positivos de la red Monasterio de Sampson" width="100%" />
<p class="caption">(\#fig:2-5-positivos)Enlaces positivos de la red Monasterio de Sampson</p>
</div>


:::{.row}
:::{.lcolumn-20 data-latex="{0.18\\textwidth}"}
*[Vista general]*

*Espacio de Trabajo > Renombrar*
*Diseño > Yifan Hu*
:::

:::{.col data-latex="{0.04\\textwidth}"}
\ <!-- an empty Div (with a white space), serving as
a column separator for tex -->
:::

:::{.rcolumn-80 data-latex="{0.78\\textwidth}"}
2.	En el nuevo espacio de trabajo, que puede renombrar `Vínculos positivos`, aplique el algoritmo de diseño Yifan Hu. Los nodos probablemente estarán demasiado apegados y será difícil distinguir cualquier patrón. Para rectificar esto, en el cuadro debajo del menú desplegable del algoritmo de diseño, cambie la *Distancia óptima* de 100 a 600 y haga clic en *Ejecutar*. Usando algunas de las otras técnicas discutidas en ejercicios prácticos anteriores, termine de modificar la red de lazos positivos en la red del Monasterio Sampson. La Figura \@ref(fig:2-5-positivos) es un ejemplo. Como antes, el color de los lazos refleja varios tipos de relaciones. Si no le gusta el color que heredaron cuando exportó el gráfico a este espacio de trabajo, puede volver a la pestaña *Apariencia*, hacer clic en *Aristas*, luego en el ícono de la paleta de colores, luego en la opción *Particiones*, y luego con el menú desplegable *Elegir un atributo*, seleccione *relation* y haga clic en *Aplicar*. Exporte su gráfico de relaciones positivas con etiquetas. **¿Qué patrones observa? ¿Qué nodos son centrales? ¿Qué significa ser central en esta red? (Tome en cuenta los tipos de enlaces).**
:::
:::
