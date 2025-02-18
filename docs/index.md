---
title: "Análisis de Redes Sociales"
author: ["CORE Lab + ESGE-EPG"]
site: bookdown::bookdown_site
documentclass: book
bibliography: [book.bib]
csl: [apa-5th-edition.csl]
link-citations: yes
github-repo: cjcallag/arso
description: "Un manual práctico para analistas de redes sociales de habla hispana."
always_allow_html: yes
---

# Introducción {-}

<img src="images/core-esge.png" width="75%" style="display: block; margin: auto;" />

El objetivo de este manual es enseñarle los conceptos básicos del análisis de redes sociales (ARSo) y como estos métodos pueden ser utilizados para comprender dichas redes, asimismo crear estrategias para empoderar o socavarlas. Este proyecto cubre los puntos de vista de los autores sobre la introducción al estudio de las redes oscuras como elementos de análisis clave para todo analista de inteligencia y elementos operativos de fuerzas especiales. De tal manera que, los ejemplos prácticos y el marco teórico en que están integrados giran alrededor de las redes oscuras, definidas como redes encubiertas (o clandestinas) e ilegales [@Raab2003]. Este es un término que puede incluir redes terroristas, criminales e insurgentes. El término "oscura" busca capturar el hecho de que las redes oscuras son aquellas que, por definición, intentan permanecer encubiertas tras ocultar sus actividades de las autoridades [@Cunningham2016; @Everton2012].

Este manual se divide en cuatro secciones. La primera consiste de una introducción a ARSo, que aborda una breve reseña histórica, las diferencias entre este y otros campos de estudio, y los términos, conceptos y supuestos básicos que forman la base de este campo. La siguiente sección cambia el enfoque de los conceptos a la práctica. Es decir, se centra en la recopilación, codificación y manipulación de los datos necesarios para el análisis. En la tercera sección, los autores presentan varias "familias" de métricas, comúnmente utilizadas en el análisis exploratorio de redes. Finalmente, la última sección destaca ejemplos del uso de los métodos presentados en este documento por analistas de inteligencia y equipos de Asuntos Civiles y Operaciones Psicológicas.

Todos los capítulos en la segunda y tercera sección incluyen ejercicios prácticos de cómo utilizar el software Gephi. Para completar estos, se requerirá descargar los conjuntos de datos requeridos del siguiente sitio de web: https://corelab.nps.edu/classes/arso/. Además de los datos requeridos, este sitio web fue diseñado como complemento para este manual e incluye materiales adicionales como diapositivas y videos.

El contenido de este manual fue diseñado conjuntamente entre el [Ambiente Común de Investigación Operativa (CORE Lab, por sus siglas en inglés)](https://nps.edu/web/core) de la [Escuela Naval de Post Grado (NPS, por sus siglas en inglés)](https://nps.edu/) y la [Escuela Superior de Guerra del Ejército, Escuela de Post Grado (ESGE-EPG), Lima, Perú](http://esge.edu.pe/esge-epg/).


## Patrocinio {-}

El desarrollo de este manual fue posible gracias al patrocinio del [Programa de Becas de Defensa Regional (RDFP, por sus siglas en inglés)](https://samm.dsca.mil/glossary/combating-terrorism-fellowship-program-ctfp) de la [Agencia de Cooperación para la Seguridad de la Defensa (DSCA, por sus siglas en inglés)](hhttps://samm.dsca.mil/) con el propósito de apoyar el plan de estudios de ESGE-EPG.

<img src="images/CTFP.jpg" width="50%" style="display: block; margin: auto;" />


## Misión educativa {-}

:::{.boxed}
**El material contenido en este manual se realizó con el propósito de revisión y discusión entre colegas para su posterior aplicación y no necesariamente refleja las opiniones del Departamento de Marina (en inglés, "Department of the Navy") o del Departamento de Defensa (en inglés, "Department of Defense") de los Estados Unidos y la Escuela Superior de Guerra - Escuela de Post Grado del Ejército de Perú.**
:::


## Autores {-}

**Christopher J. Callaghan** es un investigador asociado en el CORE Lab en el [Departamento de Análisis de Defensa](https://nps.edu/web/da) en NPS. Su trabajo aprovecha el análisis de datos de código abierto para comprender y modelar una variedad de problemas de seguridad nacional e internacional. Antes de unirse al NPS, se desempeñó como investigador asociado en el Instituto Middlebury de Estudios Internacionales (MIIS, por sus siglas en inglés) en Monterey California, donde trabajó en múltiples esfuerzos relacionados con la "ciudadanía" local e internacional.

**Sean F. Everton** es un Profesor en el [Departamento de Análisis de Defensa](https://nps.edu/web/da) y Codirector del CORE Lab de NPS. Ha publicado en las áreas de análisis de redes sociales, sociología de la religión, sociología económica y sociología política y se especializa en el uso del análisis de redes sociales para rastrear e interrumpir redes oscuras (por ejemplo, redes criminales y terroristas). Su primer libro, [*Disrupting Dark Networks*](https://www.amazon.com/Disrupting-Networks-Structural-Analysis-Sciences/dp/1107606683), fue publicado por Cambridge University Press en 2012, y su segundo libro, [*Understanding Dark Networks*](https://www.amazon.com/Understanding-Dark-Networks-Daniel-Cunningham/dp/1442249447/ref=pd_lpo_14_img_1/145-9289795-0957343?_encoding=UTF8&pd_rd_i=1442249447&pd_rd_r=a7b19253-9be1-42b7-a6fa-e4ee67f7e2f5&pd_rd_w=kcb7y&pd_rd_wg=Oq37r&pf_rd_p=7b36d496-f366-4631-94d3-61b87b52511b&pf_rd_r=3KX19ZDD20YZ1H2BTMTN&psc=1&refRID=3KX19ZDD20YZ1H2BTMTN) fue publicado por Rowman y Littlefield en 2016. Su libro más reciente, [*Networks and Religion*](https://www.amazon.com/Networks-Religion-Build-up-Structural-Analysis/dp/1108404073/ref=pd_bxgy_img_3/145-9289795-0957343?_encoding=UTF8&pd_rd_i=1108404073&pd_rd_r=d71cd43b-1c10-4abc-bb64-7049818d0f1a&pd_rd_w=FSY0j&pd_rd_wg=Wa7Wy&pf_rd_p=ce6c479b-ef53-49a6-845b-bbbf35c28dd3&pf_rd_r=AH007P8AR7HCWFKEP88J&psc=1&refRID=AH007P8AR7HCWFKEP88J), que explora la interacción de las redes y la religión, fue publicado por Cambridge University Press en 2018.

**Gral. de Brig. EP (R) Augusto Manuel E. Álvarez Torres** ostenta los títulos académicos de Maestro en Seguridad, Defensa y Desarrollo Nacional y en Ciencias Militares con mención en Planeamiento Estratégico y Toma de Decisiones, es egresado de la Escuela de Post Grado de Ciencias Políticas de la Universidad Ricardo Pala. Ha seguido cursos de Terrorismo e Insurgencia, Crimen Organizado, Políticas y Estrategias  de Seguridad, Estrategia y Seguridad Internacional, Relaciones Político, Civil, Militar y Liderazgo Estratégico, Estrategia de Seguridad y Defensa frente a las Amenazas Complejas en la UND/CHDS- EE. UU., y los cursos de Análisis de Redes Nivel I y II, en la Escuela Naval de Post Grado en Monterey, California, EE. UU. Actualmente se desempeña como Catedrático en el [Centro de Altos Estudios Nacionales (CAEN)](https://www.caen.edu.pe/wordpress/), Profesor Principal de la Catedra de Historia Militar y Profesor Adjunto en la [Universidad Conjunta de Operaciones Especiales en Florida, EE. UU](https://www.socom.mil/JSOU/Pages/default.aspx).

<!-- **Sally Baho** ... -->

<!-- ## Colaboradores {-} -->

