---
output: html_document
---




# Redes Oscuras en el Perú

Este proyecto de tener una doctrina propia, que se adapte a la realidad del Perú es un punto de vista de los autores sobre la introducción al estudio de las redes oscuras como elemento de análisis clave para todo analista de inteligencia y elementos operativos de Fuerzas Especiales, basados en el estudio analítico de la interacción de las redes sociales.
 
Este capítulo trata de definir lo que es una “red oscura”, palabras muy escuchadas en los trabajos de organización, redes y jerarquías, basada en la definición de guerra en red, de los Doctores Arquilla y Ronfeldt [-@Arquilla2001], así como en definiciones y postulados de Everton [-@Everton2012], Cunningham y col. [-@Cunningham2016], y de la Escuela Superior de Guerra del Ejército del Perú, Escuela de Post Grado (ESGE/EPG).

En este capítulo único nos abocaremos, principalmente a definir lo que se denominan redes oscuras en el Perú, su organización, características y la metodología para degradarlas y neutralizarlas. Igualmente estudiaremos los métodos aplicados por los analistas de Inteligencia, de Fuerzas Especiales, de Asuntos Civiles y Operaciones Psicológicas en la identificación de redes oscuras.

## Análisis de Redes Oscuras

Cuando hablamos del análisis de redes sociales (ARSo), aplicadas al terrorismo, crimen organizado trasnacional (COT) y otros flagelos de este tipo, podemos decir que nos referimos a las redes oscuras. Las cuales podemos definir como un conjunto de entidades clandestinas, encubiertas, ilegítimas, subrepticias, delictivas o escondidas fuera de la ley que se relacionan entre sí [@Cunningham2016]. Por ejemplo, las organizaciones que participan en el terrorismo, la minería ilegal, el tráfico ilícito de drogas, la corrupción y otros crímenes que forman parte de lo que se denomina COT y las redes ilícitas que este desarrolla. 

El análisis de redes sociales se ha utilizado en el estudio de redes oscuras de manera exitosa para comprender mejor las redes de terroristas/ insurgentes [@Krebs2002; @Koschade2006; @Cunningham2016], distribución de narcóticos [@Morselli2007], dinámicas entre pandillas [@Papachristos2013], intercambio de información en grupos de hackers [@DecaryHetu2014], entre otras aplicaciones. En el contexto ilícito, el objetivo del analista puede ser el utilizar las herramientas empíricas del ARSo, que hemos visto a lo largo de este manual, para captar y comprender las estructuras de estos grupos con el objetivo de mejorar el entendimiento de estas y forjar mejores estrategias de disrupción. Es por ello que el estudio de redes oscuras, a través del prisma del ARSo como se ha presentado, llega a ser un método ordenado, sistemático y lógico para estructurar datos, visualizar redes, y generar hipótesis sobre el comportamiento de la red y sus miembros que se pueden llegar a sustentar por medio de herramientas y métodos adicionales.  

Este proceso de entendimiento de las redes oscuras, desde nuestra perspectiva, se centra alrededor de cuantificar las relaciones entre entidades sociales para entender el contexto social en el que se sitúa un actor [@Wasserman1994]. Igualmente suponemos que el comportamiento de los actores se ve afectado por sus vínculos con los demás y las redes en las que estos están incrustados (ver Capítulo 1 para una lista completa de los supuestos en el análisis de redes). Por ejemplo, en una red terrorista, los vínculos pueden servir como conductos de información para compartir ideas, mejores tácticas criminales o terroristas, tecnología, conocimiento, acciones, etc. Al analizar la red desde la perspectiva del análisis de redes sociales oscuras, intentamos reconocer las relaciones entre entidades para plasmarlas en un mapa del sistema social y llegar a identificar:

  - Las macro, meso, y microestructuras de la red (ver Capítulos 8, 9 y 10 de este manual);
  - Quienes forman parte de la red y donde se encuentran (periferia o centro); y
  - Las distancias sociales entre nodos, las cuales proveen pistas sobre el potencial flujo de información, conocimiento u otros recursos compartidos entre nodos
 
Como conjunto de teorías y métodos empíricos, el estudio de redes oscuras a través del ARSo se da por medio de la recolección y uso de conjuntos de datos de relaciones entre actores (llamados nodos o vértices). Este manual incluye ejercicios analíticos utilizando la red terrorista Noordin Top [@Roberts2014]. Este conjunto de datos contiene :

  - Relaciones, divididas en dos modalidades:
    - Modo-Uno: relaciones entre el mismo conjunto de actores (persona a persona, organización a organización, grupo insurgente a grupo insurgente, etc.), estas pueden ser dirigidas o no dirigidas. En este conjunto de datos, los autores se centran en analizar el dominio humano. Por ello, las relaciones modo-uno han sido recopiladas de persona a persona. Por ejemplo, en la red de Noordin Top los autores incluyen lazos de comunicación, parentesco, compañerismo en clases, reclutamiento, amistad, mentorías, entre otros.  
    - Modo-Dos: relaciones entre dos conjuntos de actores (persona a evento, persona a grupo insurgente, etc.). En la red de Noordin Top, los autores incluyen relaciones de modo-dos como afiliaciones comerciales entre personas y organizaciones con fines de lucro, afiliación con una organización terrorista/insurgente, participación en entrenamientos designados para enseñar el conocimiento y habilidades terroristas entre otros. Como mencionan Cunningham y colegas, el recopilar interacciones entre miembros de una organización que intenta mantenerse oculta es difícil por naturaleza, por ello en ocasiones los analistas de redes recopilan sus datos de afiliación como modo-dos, pues el registrar cuales  sitios o eventos visitan miembros de una red oscura en relación con la organización puede ser más viable [@Cunningham2016].
  
  - Atributos: Datos no relacionales sobre los actores de la red, como su nivel educativo, entrenamiento militar, nacionalidad del individuo, rol, etc. 

El ejemplo de la red terrorista de Noordin Top demuestra el uso de vínculos formales (personas a criminales) e informales (amistad) en el análisis de la red con el objetivo de entender como la combinación de relaciones puede facilitar o impedir, generar o degradar la creación y difusión de ideas en estas organizaciones criminales. Más aún, una de las dificultades principales de trabajar con redes oscuras es la interdependencia entre múltiples diferentes entidades ilícitas [@Everton2012]; por ejemplo, vemos evidencia de vínculos entre Al Qaeda y estados fallidos en África Occidental, donde la compra y venta de diamantes provee los fondos necesarios para Al Qaeda y de manera recíproca este mercado ilícito facilita la transferencia de armamento a los combatientes de milicias locales [@Raab2003]. Similarmente, en Perú donde uno de los desafíos de seguridad involucra una combinación interdependiente de terrorismo, narcotráfico y otras actividades ilícitas el entender las redes que habilitan estos desafíos requiere un enfoque holístico basado en la interrelación entre actores, así como las organizaciones a las que pertenecen y como estas se interconectan entre ellas. 

## ¿Por qué el Análisis de Redes Oscuras?

Cabe preguntarse, ¿por qué es importante el análisis de las redes oscuras? En los conflictos modernos el dominio humano es el factor más importante que todo adversario quiere conocer, influenciar y dominar; por ello, el comprender las redes sociales del enemigo, es el elemento más crítico y desafiante en los conflictos del Siglo XXI. El analizar el dominio humano con una herramienta empírica, que facilite el estudio e investigación de las organizaciones criminales, grupos radicales y/u organizaciones terroristas, tiene un valor incalculable para los miembros de las fuerzas armadas y seguridad nacional.

En términos prácticos, el análisis de redes oscuras nos permite de manera sistemática contestar preguntas sobre las redes ilícitas de interés. Por ejemplo, si el enfoque del analista es detectar nodos cruciales para la red.  Uno identificaría a los nodos centrales los cuales pueden representar actores muy activos en la red, los cabecillas de estas organizaciones, o miembros de alto valor. Con esta información a la mano, una estrategia para neutralizar la red podría centrarse en remover dichos nodos valiosos, continuar investigándoles, etc. Como menciona Everton [-@Everton2012], el enfoque en identificar y remover nodos de “alto valor” suele ser una estrategia atractiva y a plazo corto puede proporcionar satisfacción; sin embargo, el remover nodos centrales en una red estructurada alrededor de un puñado de actores importantes no es lo mismo que tomar la misma acción contra una red sin jerarquía [@Everton2012]. Por ello la estrategia del analista de redes dependerá del tipo de estructura de red.

Puesto a que las propiedades de las organizaciones terroristas o del COT varían con base a el contexto social, histórico y geográfico de cada nación, el análisis de redes  es una herramienta interesante y necesaria para toda agencia de Inteligencia o Policial. Las conexiones entre nodos en una red social son mantenidas entre dos o más nodos, los nodos pueden ser personas, grupos, organizaciones, estados, etc. Traducido a términos relevantes al analista de Inteligencia , Fuerzas Especiales y Policiales podemos contextualizar los nodos como sujetos estratégicos. 

La estrategia del analista debe basarse en el contexto de la red, así como la estructura de esta. La Figura \@ref(fig:4-1-dimensions),  adaptada de una conferencia sobre Redes Sociales a cargo de la Doctora Nancy Roberts de la Escuela Naval de Post Grado, presenta la estructura de redes como polos opuestos [@Roberts2014a]. Esta dicotomía se basa en el estudio de organizaciones, la cual separa las jerarquías de las redes. Asimismo, compartimenta características, asociando las redes con estructuras sociales informales, igualitarias y de gobernanza compartida; igualmente, asume que las organizaciones jerárquicas son formales, estructuradas y con gobernanza centralizada [@Everton2012]. 

<div class="figure" style="text-align: center">
<img src="images/04-dimensions.png" alt="Dimensiones de Organizaciones" width="100%" />
<p class="caption">(\#fig:4-1-dimensions)Dimensiones de Organizaciones</p>
</div>

Al analizar redes oscuras es importante preguntarse si esta distinción es útil. Algunos [@Everton2012] argumentan que la distinción es apropiada en algunos contextos, pero desde la perspectiva del análisis de redes  esta división es inapropiada [@Everton2012]. Esto es puesto que tanto en las organizaciones jerárquicas como en las redes el análisis se basa en las relaciones entre actores, el entendimiento sobre las propiedades organizacionales de la red se determina por medidas estructurales que cuantifican la jerarquía o heterarquía de dicha red. En este manual, hemos explorado las medidas estructurales de las redes en el Capítulo “Topología”. 

En términos prácticos, un analista de redes  puede comenzar su exploración investigando esta dimensión estructural. Por ejemplo, haciéndose la pregunta “El MOVADEF, ¿cómo está estructurado? ¿Cómo red o jerarquía?” es un buen comienzo en entender las características estructurales de la red con el fin de generar la estrategia que mejor se acople a la realidad. Es importante mencionar, que hay organizaciones que, sin tener una jerarquía establecida, tienen un orden informal. Para aclarar esto podemos utilizar un ejemplo presentado por el Capitán de Navío, R. Devoto [-@Devoto2016] en su presentación para los oficiales alumnos de la Escuela de Inteligencia del Ejército en el curso básico y superior de Inteligencia:

> Dentro de Sendero Luminoso, teníamos comunistas y simpatizantes de acuerdo a su propia definición. Luego estos se subdividían en Dirigentes, Cuadros, Militantes, Combatientes y Masas, implícitamente ya adoptan una jerarquía a pesar de que siempre pregonaban que todos eran iguales...
    
Podemos complementar las observaciones de Cap. de  Navío Devoto, con la definición de la guerra en red de Arquilla y Ronfeldt [-@Arquilla2001, página 6], que para ser exacto citaremos textualmente:

> El termino de guerra en red hace referencia a un modo emergente de conflicto (y de delincuencia) en el ámbito social, alejado de la guerra militar tradicional, en el que los protagonistas utilizan estructuras de organización en red y doctrinas, estrategias y tecnologías en relación con aquellas, acordes con la era de la información.

Esta definición nuevamente retorna el enfoque a la estructura de la red, pero incluye las cualidades adicionales de las redes oscuras, como las doctrinas, estrategias y tecnologías que van mano a mano con la guerra en red. Nuevamente, podemos recalcar el valor del análisis sistemático de redes utilizando los métodos empíricos presentados en este manual y en la literatura del ARSo.

El ejemplo previo de Sendero Luminoso recalca una de las cualidades adicionales de la guerra en red, según Arquilla y Ronfeldt, una red se compone de muchas piezas pequeñas y dispersas, las cuales comparten conjuntos de ideas y están interconectadas para lograr un fin común [@Arquilla2001]. Nuevamente, Arquilla y Ronfeldt presentan tres tipos de topologías de redes que podemos ver en la siguiente tabla: 


--------------------------------------------------------------------------
   Tipo              Explicación                        Dibujo            
---------- -------------------------------- ------------------------------
  Cadena        Como en una cadena de         ![](images/04-cade2a.png)   
               contrabando de personas,                                   
             bienes, o información donde                                  
            estos se mueven a lo largo de                                 
            la línea de contactos y donde                                 
            la comunicación de un extremo                                 
             a otro viaja únicamente por                                  
                   nodos aledaños.                                        

 Estrella    Donde un conjunto de actores    ![](images/04-estrella2.png) 
               está ligado con un nodo                                    
                central o actor, para                                     
                comunicarse entre sí o                                    
            coordinarse deben atravesar el                                
                    nodo central.                                         

  Malla      Una estructura de red en la      ![](images/04-malla2.png)   
                que todo el mundo está                                    
                      conectado.                                          
--------------------------------------------------------------------------

En una red oscura, la composición estructural puede contener una mezcla de estas tipologías (Figura \@ref(fig:4-1-mix)). Por ejemplo, el núcleo de la red puede estar organizado como malla, pero en estrellas o cadenas en otras partes de la red como en los comandos operativos [@Arquilla2001]. Más aun, los actores generalmente están conectados entre sí de varias maneras, y estas conexiones pueden empujarlos en direcciones múltiples y a veces contradictorias [@Cunningham2016]. Por ejemplo, la mayoría de los individuos tienen lazos de intercambio, amistad y parentesco; las organizaciones criminales y terroristas generalmente, intercambian personal, armas, dinero, información y forman alianzas entre ellos. 

<div class="figure" style="text-align: center">
<img src="04-redes_oscuras_en_el_peru_files/figure-html/4-1-mix-1.png" alt="Red hipotética, mezcla de cadenas, estrellas y mallas" width="100%" />
<p class="caption">(\#fig:4-1-mix)Red hipotética, mezcla de cadenas, estrellas y mallas</p>
</div>

En el Perú, el análisis de redes oscuras nos ha permitido mapear, degradar, y neutralizar redes criminales como la red criminal “Los cuellos blancos del Puerto”, la facción de Sendero Luminoso denominada Línea Oportunista de Derecha (LOD), entre otras (ver Capítulo “Ejemplos Prácticos” de este manual). El análisis de redes oscuras también se ha utilizado para verificar la convergencia que existe entre las organizaciones criminales y los partidos políticos, tema de alta importancia pues en los últimos años hemos presenciado en el mundo y especialmente en la región Sudamericana, el surgimiento de redes de actores, dedicados a limitar las acciones de fuerza de diversos gobiernos, así como activistas que reclaman la no contaminación del medio ambiente, la movilización en los conflictos sociales contra las asimetrías de poder, terroristas en convergencia con partidos políticos de ideología radical a fin de derrocar a un gobierno legítimamente constituido, organizándose en redes inmensas formadas por poblaciones interconectadas por múltiples canales, apoyándose en la internet, desde donde se han  coordinado y organizado [@Arquilla2001].

Hay que tener en cuenta que la difusión del crimen organizado trasnacional constituye la amenaza más importante para la seguridad de las Américas [@Garzon2013], y estas organizaciones se manifiestan en redes. Es por ello, que nuevamente retornamos a las sabias palabras de Arquilla y Rondefeldt, quienes afirman que "se necesita una red para luchar contra las redes” [@Arquilla2001]. Esto depende, hasta cierto punto de nuestra habilidad de comprender al enemigo y desarrollar estrategias innovativas basadas en nuestro entendimiento de la red.

## Conclusiones

Para concluir este breve capítulo, los autores proponen algunas conclusiones basadas en la literatura del análisis de redes (dentro y fuera de este manual), la realidad en el Perú y sus observaciones como catedráticos y miembro en situación de retiro de las fuerzas armadas: 

  1. Las redes y organizaciones pertenecen a un sistema complejo e interdependientes y hay que estudiarlas como un todo, y cuando estas son demasiadas extensas podemos dividirlas en subsistemas, pero sin perder el punto de vista sistémico. Por ejemplo, las redes terroristas pueden dividirse por su afiliación política o ideológica, sin embargo, es importante no olvidar como estas se interrelacionan.
  2. Las redes sociales oscuras sean cual fuera su tipo, son difíciles de comprender porque pueden ser de cualquier estructura y pueden estar totalmente dispersas.
  3. Observar las redes/organizaciones como sistemas nos ayuda a identificar a sus elementos, características y componentes. Entendiendo todos estos aspectos podemos contrarrestar a este tipo de organizaciones con estrategias que tomen en cuenta los patrones estructurales de la red, sus miembros, y los retos y oportunidades que presentan. 
  4. Debido a la complejidad de las redes y la dificultad en codificar interacciones sociales, es crucial que los equipos intra e interorganizacionales de seguridad nacional creen y compartan estándares de documentación, recopilación y codificación de datos de red. En este manual, hemos presentado una serie de “libros de código” (ver “Libro de Códigos”) para ejemplificar el uso de esta estrategia en el análisis de redes oscuras. En el Perú, en la instrucción de ARSo hemos denominado este documento guía como “libro de términos”. El enfoque ha sido el incluir definiciones y características de los grupos en estudio adaptadas a la realidad del país. Por ejemplo, en el libro de código de Roberts, Everton y Cunningham [-@Roberts2014] los autores utilizan términos como “tribu ” el cual debe ser adaptado a “centro poblado menor” (CPM). Además de términos y definiciones consistentes, es importante tener un entendimiento común en diferentes niveles organizacionales de los departamentos de defensa y seguridad nacional. Por ejemplo, el libro de términos creado para el estudio del MOVADEF (brazo político de Sendero Luminoso) debe ser el mismo para todos los niveles de análisis encargados de su estudio, desde el nivel táctico hasta el nivel estratégico nacional.
  5. Durante la enseñanza del análisis de redes sociales, se debe preparar e instruir a los analistas de redes  en diversos campos; sin embargo, el objetivo debe ser crear expertos en determinado campo. De tal manera que, el analista pueda responder preguntas de investigación enfocadas. Es un error que un analista sea “todista”, porque nos puede llevar a errores. La formación de redes entre entidades policiales y de seguridad es una estrategia para dividir y conquistar. 

