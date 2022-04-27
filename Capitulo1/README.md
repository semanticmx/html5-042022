TIPOS MIME 

Cada vez que su navegador web solicita una página, el servidor web envía "encabezados" antes de enviar el marcado de la página real.
Estos encabezados normalmente son invisibles, los encabezados son importantes porque le dicen a su navegador cómo interpretar el marcado de la página que sigue. 
El encabezado más importante se llama Content-Type, y se ve así:

Content-Type: text/html

“ text/html” se denomina “tipo de contenido” o “ tipo MIME ” de la página. Este encabezado es lo único que determina qué es realmente un recurso en particular y,
por lo tanto, cómo debe representarse. Las imágenes tienen sus propios tipos MIME. Los archivos JavaScript tienen su propio tipo MIME. 
Las hojas de estilo CSS tienen su propio tipo MIME . Todo tiene su propio tipo MIME. La web se ejecuta en tipos MIME.

UNA LARGA DIGRESIÓN SOBRE CÓMO SE ELABORAN LAS NORMAS


El 25 de febrero de 1993, Marc Andreessen escribió :

Me gustaría proponer una nueva etiqueta HTML opcional:

IMG

El argumento requerido es SRC="url".

Esto nombra un archivo de mapa de bits o mapa de píxeles para que el navegador intente acceder a la red e interpretarlo como una imagen, para ser incrustado en 
el texto en el punto de aparición de la etiqueta.

Un ejemplo es:

<IMG SRC="file://foobar.com/foo/bar/blargh.xbm">

Esta etiqueta se puede incrustar en un ancla como cualquier otra cosa; cuando eso sucede, se convierte en un icono que es sensible a la activación como un
ancla de texto regular.

Los navegadores deben tener flexibilidad en cuanto a qué formatos de imagen admiten. Xbm y Xpm son buenos para admitir

Xbm y Xpm eran formatos de gráficos populares en los sistemas Unix.

“Mosaic” fue uno de los primeros navegadores web. (“X Mosaic” era la versión que se ejecutaba en sistemas Unix).
"MIME, algún día, tal vez" es una referencia a la negociación de contenido , una función de HTTP donde un cliente (como un navegador web) le dice al servidor
(como un servidor web) qué tipos de recursos admite (como image/jpeg) para que el servidor pueda regresar algo en el formato preferido del cliente.
El HTTP original, tal como se definió en 1991 (la única versión que se implementó en febrero de 1993), no permitía que los clientes indicaran a los servidores
qué tipo de imágenes admitían, de ahí el dilema de diseño al que se enfrentó Marc.

Tony Johnson

Tengo algo muy similar en Midas 2.0 , excepto que todos los nombres son diferentes y tiene un argumento adicional NAME="name". 
Tiene casi exactamente la misma funcionalidad que la IMGetiqueta propuesta. p.ej

<ICON name="NoEntry" href="http://note/foo/bar/NoEntry.xbm">

La idea del parámetro de nombre era permitir que el navegador tuviera un conjunto de imágenes "incorporadas". Si el nombre coincide con una imagen "incorporada", 
la usaría en lugar de tener que ir a buscar la imagen. El nombre también podría actuar como una pista para los navegadores de "modo de línea" sobre qué tipo de 
símbolo colocar en lugar de la imagen.

Midas fue otro de los primeros navegadores web, contemporáneo de X Mosaic. Era multiplataforma; se ejecutó tanto en Unix como en VMS. “SLAC” se refiere al 
Centro Acelerador Lineal de Stanford , ahora el Laboratorio Nacional de Aceleradores SLAC, que alojó el primer servidor web en los Estados Unidos

en 1993, Dave Raggett propuso HTML+ como una evolución del estándar HTML. La propuesta nunca se implementó y fue reemplazada por HTML 2.0 . 

HTML 2.0 era una "especificación retro", lo que significa que formalizaba características que ya eran de uso común. “ Esta especificación reúne, aclara y
formaliza un conjunto de funciones que corresponde aproximadamente a las capacidades de HTML de uso común antes de junio de 1994”.

Dave escribió HTML 3.0 , basado en su borrador anterior de HTML+. Fuera de la propia implementación de referencia del W3C, Arena , HTML 3.0 nunca se implementó y 
fue reemplazado por HTML 3.2 , otra "especificación retro": " HTML 3.2 agrega características ampliamente implementadas como tablas, applets y flujo de texto 
alrededor de las imágenes, mientras proporcionando total compatibilidad con versiones anteriores con el estándar HTML 2.0 existente”.

Más tarde, Dave fue coautor de HTML 4.0 , desarrolló HTML Tidy y ayudó con XHTML, XForms, MathML y ​​otras especificaciones modernas de W3C.


Intermedia fue un proyecto de hipertexto de la Universidad de Brown. Fue desarrollado entre 1985 y 1991 y se ejecutó en A/UX , un sistema operativo similar a Unix para las primeras computadoras Macintosh.

La idea de un "lenguaje de gráficos procedimentales de propósito general" eventualmente se hizo popular. Los navegadores modernos admiten tanto SVG (marcado 
declarativo con secuencias de comandos incrustadas)como <canvas>(una API de gráficos de modo directo de procedimiento), aunque esta última comenzó como una 
extensión propietaria antes de ser "retro-especificada" por WHATWG .

HyTime fue uno de los primeros sistemas de documentos de hipertexto basados en SGML. Cobró gran importancia en las primeras discusiones sobre HTML y, más tarde,
sobre XML.
La propuesta de Tim para una <INCLUDE> etiqueta nunca se implementó, aunque se pueden ver ecos de ella en <object>, <embed>y el <iframe> elemento.


UNA LINEA ININTERRUMPIDA 
  
--HTTP todavía existe. HTTP evolucionó con éxito de 0.9 a 1.0 y luego a 1.1. Y aún así evoluciona.
--HTML siempre ha sido una conversación entre los creadores de navegadores, los autores, los expertos en estándares y otras personas que acaban de aparecer y les gusta hablar sobre corchetes angulares. La mayoría de las versiones exitosas de HTML han sido "retro-specs", poniéndose al día con el mundo y al mismo tiempo tratando de empujarlo en la dirección correcta.

  
UNA LÍNEA DE TIEMPO DEL DESARROLLO DE HTML DE 1997 A 2004

--En diciembre de 1997, el World Wide Web Consortium (W3C) publicó HTML 4.0 y cerró rápidamente el Grupo de trabajo de HTML.
--comenzar de nuevo con la próxima generación de HTML basada en un conjunto de conjuntos de etiquetas XML.
--Su primer paso, en diciembre de 1998, fue un borrador de una especificación provisional que simplemente reformulaba HTML en XML sin agregar nuevos elementos o atributos
--En agosto de 1999, el mismo HTML Working Group publicó un primer borrador de XHTML Extended Forms.
--" XHTML Extended Forms" pasó a llamarse "XForms" y se trasladó a su propio grupo de trabajo
--En mayo de 2001, publicaron la primera edición de XHTML 1.1 , que agregó solo algunas características menores además de XHTML 1.0, pero también eliminó la laguna del "Apéndice C". A partir de la versión 1.1, todos los documentos XHTML debían servirse con un tipo MIMEapplication/xhtml+xml de.

TODO LO QUE SABES SOBRE XHTML ESTÁ MAL
  
--Los navegadores siempre han sido "perdonadores" con HTML . Si crea una página HTML pero olvida la </head>etiqueta, los navegadores mostrarán la página de todos modos. 
--Según algunas estimaciones, más del 99% de las páginas HTML en la web hoy en día tienen al menos un error. Pero debido a que estos errores no hacen que los navegadores muestren mensajes de error visibles, nadie los corrige.
--XML , publicado en 1997, rompió con la tradición de perdonar a los clientes y exigió que todos los programas que consumieran XML debían tratar los llamados errores de "bien formado" como fatales.
--"Usen algo que se parezca a la sintaxis XHTML , pero siga sirviéndolo con el tipo text/html MIME". Y eso es exactamente lo que hicieron miles de desarrolladores web: "actualizaron" a la sintaxis XHTML pero siguieron sirviéndola con un text/html MIME tipo.

--Cualquier página servida con un tipo MIME de, independientemente del tipo de documento, la sintaxis o el estilo de codificación, se analizará utilizando un analizador HTMLtext/html "perdonador" , ignorando silenciosamente cualquier error de marcado y nunca alertando a los usuarios finales (ni a nadie más) incluso si la página está técnicamente roto.
  
UNA VISIÓN COMPETITIVA
  
En junio de 2004, el W3C realizó el Taller sobre Aplicaciones Web y Documentos Compuestos .
Un grupo de partes interesadas, incluida la Fundación Mozilla y Opera Software, hizo una presentación sobre su visión competitiva del futuro de la web: una evolución del estándar HTML 4 existente para incluir nuevas funciones para los desarrolladores de aplicaciones web modernas.
Un grupo de partes interesadas, incluida la Fundación Mozilla y Opera Software, hizo una presentación sobre su visión competitiva del futuro de la web: una evolución del estándar HTML 4 existente para incluir nuevas funciones para los desarrolladores de aplicaciones web modernas.
  
Los siguientes siete principios representan lo que creemos que son los requisitos más críticos

---Compatibilidad con versiones anteriores, ruta de migración clara:Las tecnologías de aplicaciones web deben basarse en tecnologías con las que los autores estén familiarizados
---Manejo de errores bien definido:El manejo de errores en las aplicaciones web debe definirse con un nivel de detalle en el que los agentes de usuario no tengan que inventar sus propios mecanismos de manejo de errores
---Los usuarios no deben estar expuestos a errores de autoría:Las especificaciones deben especificar el comportamiento exacto de recuperación de errores para cada escenario de error posible. 
---Uso práctico:Cada característica que entra en las especificaciones de las aplicaciones web debe estar justificada por un caso de uso práctico.
---Uso práctico: Cada característica que entra en las especificaciones de las aplicaciones web debe estar justificada por un caso de uso práctico.
---Se debe evitar la creación de perfiles específicos del dispositivo:Los autores deberían poder depender de que se implementen las mismas funciones en las versiones de escritorio y móvil de la misma AU.
---Proceso abierto:Las aplicaciones web serán el núcleo de la web, y su desarrollo también debe tener lugar al aire libre.
  
¿QUÉ GRUPO DE TRABAJO?
  
El Grupo de Trabajo de Tecnología de Aplicaciones de Hipertexto Web es una colaboración flexible, no oficial y abierta de fabricantes de navegadores Web y partes interesadas. 
El grupo tiene como objetivo desarrollar especificaciones basadas en HTML y tecnologías relacionadas para facilitar el despliegue de aplicaciones web interoperables, con la intención de enviar los resultados a una organización de estándares.
El enfoque principal hasta este punto ha sido ampliar los formularios HTML4 para admitir las funciones solicitadas por los autores, sin romper la compatibilidad con versiones anteriores del contenido existente.
El grupo de trabajo WHAT decidió adoptar un enfoque diferente: documentar los algoritmos de manejo de errores "perdonadores" que los navegadores realmente usaban.
El grupo de trabajo WHAT documentó con éxito cómo analizar HTML de una manera que sea compatible con el contenido web existente.
Una especificación, inicialmente denominada Web Forms 2.0 , que agregaba nuevos tipos de controles a los formularios HTML . 
Un borrador de especificación llamado "Aplicaciones web 1.0", que incluía importantes características nuevas como un lienzo de dibujo en modo directo y soporte nativo para audio y video sin complementos.

VOLVER AL W3C

En octubre de 2006, Tim Berners-Lee, el fundador del propio W3C, anunció que el W3C trabajaría junto con el grupo de trabajo WHAT para desarrollar HTML .
El plan es constituir un grupo HTML completamente nuevo. A diferencia del anterior, este se encargará de realizar mejoras incrementales en HTML, así como también en xHTML paralelo.
Es importante mantener HTML de forma incremental, así como continuar la transición a un mundo bien formado y desarrollar más poder en ese mundo.
Una de las primeras cosas que decidió el grupo de trabajo de HTML del W3C, recientemente renovado, fue cambiar el nombre de "Aplicaciones web 1.0" a "HTML5".

