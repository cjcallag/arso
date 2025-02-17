---
output:
  html_document: default
bibliography: book.bib
---



# Tipos de Datos de Redes Sociales

Tradicionalmente los analistas de redes sociales trabajan con tres tipos de datos: modo-uno, modo-dos y atributos [@Everton2012]. En esta sección exploraremos estos tipos de datos en más detalle. El objetivo es definir y compararlos antes de empezar a recopilar y manipular estos datos.

## Datos de Modo-Uno

Estos son aquellos que consisten en un solo conjunto de actores o nodos. Por ejemplo, en una red de amistad las personas están unidas a través de lazos amistosos, una red de negocios une diferentes empresas por medio de transacciones financieras, o una red diplomática une naciones con base a lazos diplomáticos. Los tres ejemplos propuestos representan relaciones de modo-uno puesto que los actores que forman parte de estas relaciones constan de un conjunto único de actores. 

Sin embargo, no todas las relaciones de modo-uno son equivalentes. En las siguientes secciones diferenciaremos entre tipos de relaciones modo-uno con base a la simetría o asimetría de la relación. 

### Modo-uno: Simétricos

Las relaciones simétricas de modo-uno son aquellas que constan de un solo tipo de actor y donde no tomamos en cuenta la dirección de los enlaces. Por ejemplo, asumamos que la Figura \@ref(fig:2-2-undirected) representa relaciones familiares entre miembros de esta red. En este caso, la mutualidad entre actores es asumida y por consiguiente vemos un solo borde enlazando los nodos. Es decir, si asumimos que la persona A es familiar de la persona B, sería imposible que la persona B no sea familiar de la persona A.

<div class="figure" style="text-align: center">
<img src="02-types-of-data_files/figure-html/2-2-undirected-1.png" alt="Gráfico no dirigido" width="100%" />
<p class="caption">(\#fig:2-2-undirected)Gráfico no dirigido</p>
</div>

@Everton2012 nos presenta ejemplos de vínculos modo-uno simétricos utilizados para mapear la red terrorista Jemaah Islamiyah en el primer apéndice de *Disrupting Dark Network*: 

| Vínculo | Tipo de Actor | Definición |
|---------|---------------|------------|
| Amistad | Persona | Definido como vínculos de afecto y estima entre dos personas. Los lazos de amistad no son únicamente basados en reuniones y/o vínculos escolares. | 
| Compañeros de clase | Persona | Definido como individuos que reciben educación formal, sirven como empleados (maestro, miembro administrativo, etc.) y/o participan en instrucción educativa [...] simultáneamente en la misma institución. |
| Parentesco familiar | Persona | Definido como cualquier conexión familiar, como un hermano, un cuñado, un sobrino, etc. El parentesco incluye matrimonios actuales y matrimonios pasados debido a divorcios y/o muertes. |

:::{.infobox .note data-latex=""}
Los vínculos modo-uno simétricos se utilizan a menudo cuando es difícil o imposible determinar qué actor inició o envió el enlace y quién lo recibió [@Cunningham2016]. En los tres ejemplos previos podemos asumir mutualidad entre actores.
:::

Ya que hemos definido este tipo de datos, es tiempo de ver como codificarlos. Los datos de modo-uno se pueden representar en un tipo de sociomatriz llamada matriz de adyacencia. La siguiente matriz es una representación de los vínculos familiares de la Figura \@ref(fig:2-2-undirected). El primer paso en generar una matriz de adyacencia es listar todos los nodos relevantes, {A, B, C, D, E, F}, como filas y columnas en la matriz. Representamos la presencia o ausencia de un vínculo con un valor. Se usan 1s para indicar que un nodo tiene una relación con otro. De lo contrario, se coloca un 0. Además, eliminamos la diagonal, ya que no es relevante que un nodo tenga un vínculo simétrico consigo mismo.

$$
\begin{matrix}
  & A & B & C & D & E & F \\
A & - & 1 & 1 & 0 & 0 & 0 \\
B & 1 & - & 1 & 0 & 0 & 0 \\
C & 1 & 1 & - & 1 & 0 & 0 \\
D & 0 & 0 & 1 & - & 1 & 1 \\
E & 0 & 0 & 0 & 1 & - & 1 \\
F & 0 & 0 & 0 & 1 & 1 & - \\
(\#eq:2-2-symmatrix)
\end{matrix}
$$

Se estará preguntando, ¿cómo leemos la matriz? Centrémonos en un nodo a la vez. Por ejemplo, el nodo A, la primera letra de la columna más a la izquierda, está conectado con los nodos B y C, pero no con los demás {D, E, F}. Recuerde que la relación en cuestión es simétrica. Como tal, los dos lados de la matriz se reflejarán entre sí. Esto quiere decir que B y C también están vinculados a A.


### Modo-uno: Asimétricos

Estas también son relaciones entre un solo conjunto de actores; sin embargo, las redes asimétricas de modo-uno generalmente se refieren a bordes que van de un nodo a otro, pero que no siempre son recíprocos [@Borgatti2018; @Everton2012]. Por ejemplo, considere la Figura \@ref(fig:2-2-directed). Inicialmente notará que los vínculos tienen dirección, representada por una flecha. Observe que algunos de los vínculos no son recíprocos (por ejemplo, A envía un enlace no recíproco a C), mientras que otros son correspondidos (por ejemplo, A envía un enlace a B y este lo retorna).

<div class="figure" style="text-align: center">
<img src="02-types-of-data_files/figure-html/2-2-directed-1.png" alt="Gráfico dirigido" width="100%" />
<p class="caption">(\#fig:2-2-directed)Gráfico dirigido</p>
</div>

@Cunningham2016 sugieren que en situaciones donde es posible distinguir la dirección del enlace, es preferible construir matrices asimétricas de modo-uno. Por ejemplo, la siguiente matriz representa los datos de la Figura \@ref(fig:2-2-directed). Como con toda sociomatriz, comenzamos por listar todos los nodos posibles como filas y columnas {A, B, C, D, E, F}. Igualmente, la leemos de izquierda a derecha, comenzando con el nodo A, vemos que este envía lazos a los actores C y B, pero no a los demás {D, E, F}. En este caso, el actor A recibe un enlace de B pero no de C. Ahora, fíjese que ambos lados de la diagonal no so recíprocos, es decir contienen diferentes valores. Más aún, algunos nodos no envían ningún enlace solo reciben (como el actor D).

$$
\begin{matrix}
  & A & B & C & D & E & F \\
A & - & 1 & 1 & 0 & 0 & 0 \\
B & 1 & - & 1 & 0 & 0 & 0 \\
C & 0 & 0 & - & 1 & 0 & 0 \\
D & 0 & 0 & 0 & - & 0 & 1 \\
E & 0 & 0 & 0 & 1 & - & 1 \\
F & 0 & 0 & 0 & 0 & 0 & - \\
(\#eq:2-2-asymmatrix)
\end{matrix}
$$

Para ver ejemplos de datos de red asimétricos de modo-uno, podemos volver a @Everton2012: 

| Vínculo | Tipo de Actor | Definición |
|---------|---------------|------------|
| Comunicación | Persona | La comunicación interna se define como la transmisión de mensajes entre individuos y/o grupos dentro de la red a través de algún tipo de medio. | 


## Datos de Modo-Dos

Las relaciones modo-dos son aquellas, que a diferencia de las modo-uno, consisten de vínculos entre dos clases de actores. Para entender datos de modo-dos, utilicemos la premisa de uno de los conjuntos de datos modo-dos más populares, Davis’s Southern Women [@Davis1941]. En este ejemplo tenemos dos conjuntos de actores. El primero representa personas {A, B, C, D, E, F}, el segundo representa eventos (E) sociales {E1, E2, E3}. En esta red modo-dos, no tenemos vínculos entre personas, sino vínculos de asistencia entre una persona y un evento. Podemos codificar estos datos utilizando una sociomatriz, listando todos los nodos {A, B, C, D, E, F, E1, E2, E3} en las filas y columnas, ver la siguiente matriz. La asistencia se representa de manera binaria con un 1, mientras que la ausencia con un 0.

$$
\begin{matrix}
  & A & B & C & D & E & F & E1 & E2 & E3 \\
A & - & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\
B & 0 & - & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\
C & 0 & 0 & - & 0 & 0 & 0 & 1 & 1 & 0 \\
D & 0 & 0 & 0 & - & 0 & 0 & 0 & 1 & 1 \\
E & 0 & 0 & 0 & 0 & - & 0 & 0 & 0 & 1 \\
F & 0 & 0 & 0 & 0 & 0 & - & 0 & 0 & 1 \\
E1 & 1 & 1 & 1 & 0 & 0 & 0 & - & 0 & 0 \\
E2 & 0 & 0 & 1 & 1 & 0 & 0 & 0 & - & 0 \\
E3 & 0 & 0 & 0 & 1 & 1 & 1 & 0 & 0 & - \\
(\#eq:2-2-bipmat)
\end{matrix}
$$

¿Qué patrones puede ver en la matriz previa? Primero, note la simetría de la matriz, es decir que los datos son simétricos.  Al sumar las filas o columnas, notamos que el evento más asistido es el primer evento (E1) con tres personas. Adicionalmente, la persona con mayor asistencia a eventos son el actor D (2 eventos) y C (2 eventos). La Figura \@ref(fig:2-2-bips) es un sociograma de estos datos, en este las personas y eventos han sido dibujados con dos diferentes tipos de íconos para diferenciar entre las clases de nodos, sin embargo, esta diferenciación es puramente cosmética.

<div class="figure" style="text-align: center">
<img src="02-types-of-data_files/figure-html/2-2-bips-1.png" alt="Gráfico Bipartita" width="100%" />
<p class="caption">(\#fig:2-2-bips)Gráfico Bipartita</p>
</div>

Probablemente el patrón más importante que podemos observar en la matriz y el sociograma de modo-dos es que los nodos solo están conectados *entre* clases. En este ejemplo, las personas solo pueden estar vinculadas con eventos y viceversa. Esta es la regla más importante de las redes modo-dos, solo se permiten conexiones entre nodos de diferentes conjuntos o particiones. Es por ello, que a menudo verán el termino bipartita que refiere a redes modo-dos.

Una suposición clave que subyace al uso de redes de modo-dos es que las personas que tienden a unirse o participar en una organización común y/o eventos, a menudo tienen una razón compartida para hacerlo, como ideología, interés, etc. [@Everton2012]. Como tal, es más probable que dos miembros de un grupo interactúen entre sí y compartan una conexión que dos personas al azar en una población. Más adelante generaremos datos modo-uno empezando con modo-dos. Por el momento, es importante entender por qué utilizamos este tipo de información en nuestro análisis.

Una vez más, veamos algunos ejemplos de redes modo-dos utilizadas para mapear Jemaah Islamiyah en @Everton2012:

| Vínculo | Tipo(s) de Actor(es) | Definición |
|---------|----------------------|------------|
| Afiliación educativa | Persona y Organización | Las relaciones educativas se definen como escuelas donde las personas reciben educación formal, sirven como empleados (maestro, miembro administrativo, etc.) o participan en instrucción educativa o religiosa adicional en la institución. |
| Afiliación Organizacional  | Persona y Evento | Una organización terrorista/insurgente se define como un sistema administrativo y funcional, cuyo principal objetivo común es la conducta operativa de actividades terroristas/insurgentes, que consiste en miembros voluntariamente afiliados.  |
| Eventos de Formación | Persona y Evento | Participación en cualquier actividad específicamente designada que enseñe el conocimiento, las habilidades y las competencias del terrorismo y la insurgencia. La capacitación no incluye la participación en un acto patrocinado por terroristas [...]. |

## Datos de Atributos

Aunque no son el enfoque principal de ARSo, los datos de atributo se utilizan a menudo para acompañar el análisis de la red. Como se discutió anteriormente, a nivel de nodo, los atributos son características no relacionales de los nodos en un gráfico [@Cunningham2016]. Estos se recopilan por separado de las relaciones. Por ejemplo, considere las dos matrices siguientes.

::: {.row}
::: {.lcolumn-50 data-latex="{0.48\\textwidth}"}
$$
\begin{matrix}
  & A & B & C & D & E & F \\
A & - & 1 & 1 & 0 & 0 & 0 \\
B & 1 & - & 1 & 0 & 0 & 0 \\
C & 1 & 1 & - & 1 & 0 & 0 \\
D & 0 & 0 & 1 & - & 1 & 1 \\
E & 0 & 0 & 0 & 1 & - & 1 \\
F & 0 & 0 & 0 & 1 & 1 & - \\
(\#eq:2-2-small-matrix)
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
  & Género    & Edad \\
A & Masculino & 20 \\
B & Femenino  & 20 \\
C & Femenino  & 20 \\
D & Masculino & 29 \\
E & Masculino & 20 \\
F & Masculino & 25 \\
(\#eq:2-2-attribute-matrix)
\end{matrix}
$$
:::
:::

\newline

La matriz de la izquierda es una sociomatriz simétrica de modo-uno, que contiene todas las relaciones entre el conjunto de nodos {A, B, C, D, E, F}. La matriz de la derecha contiene los atributos para el conjunto de nodos, específicamente, género y edad. La Figura \@ref(fig:2-2-attrs) combina estos datos, donde los nodos están coloreados por el atributo categórico (género) y dimensionados por las variables continuas (edad).

<div class="figure" style="text-align: center">
<img src="02-types-of-data_files/figure-html/2-2-attrs-1.png" alt="Gráfico no dirigido, con atributos" width="100%" />
<p class="caption">(\#fig:2-2-attrs)Gráfico no dirigido, con atributos</p>
</div>

:::{.infobox .note data-latex=""}
Al recopilar atributos, solo es necesario tener una entrada por nodo. Además, si se trabaja con redes multimodales (por ejemplo, bipartitas), se pueden recopilar atributos para todas las categorías de nodos.
:::
