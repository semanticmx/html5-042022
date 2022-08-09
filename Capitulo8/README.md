PONGAMOS ESTO FUERA DE LÍNEA

En su forma más simple, una aplicación web sin conexión es una lista de URL : HTML , CSS , JavaScript, imágenes o cualquier otro tipo de recurso. La página de inicio
de la aplicación web sin conexión apunta a esta lista, llamada archivo de manifiesto, que es solo un archivo de texto ubicado en otra parte del servidor web. 
Un navegador web que implemente aplicaciones fuera de línea HTML5 leerá la lista de URL del archivo de manifiesto, descargará los recursos, los almacenará en 
caché localmente y automáticamente mantendrá las copias locales actualizadas a medida que cambien. Cuando llegue el momento en que intente acceder a la aplicación 
web sin una conexión de red, su navegador web cambiará automáticamente a las copias locales.

Hay una bandera en el DOM que te dirá si estás en línea o fuera de línea. Hay eventos que se activan cuando cambia su estado sin conexión.
Si su aplicación crea datos o guarda el estado, depende de usted almacenar esos datos localmente mientras está fuera de línea y sincronizarlos con el servidor
remoto una vez que vuelva a estar en línea. En otras palabras, HTML5 puede desconectar su aplicación web. Lo que hagas una vez que estés allí depende de ti.

EL FLUJO DE EVENTOS

Eventos DOM . Cuando su navegador visita una página que apunta a un manifiesto de caché, desencadena una serie de eventos en el window.applicationCacheobjeto.

1.- Tan pronto como nota un manifestatributo en el <html>elemento, su navegador activa un checkingevento. (Todos los eventos enumerados aquí se activan en el window.
applicationCacheobjeto). El checkingevento siempre se activa, independientemente de si ha visitado previamente esta página o cualquier otra página que apunte al
mismo manifiesto de caché.
2.-Si su navegador nunca ha visto este manifiesto de caché antes 
  
--Activará un downloadingevento y luego comenzará a descargar los recursos enumerados en el manifiesto 
de caché.
--Mientras se descarga, su navegador activará progresseventos periódicamente, que contienen información sobre cuántos archivos ya se han descargado y cuántos archivos
--aún están en cola para descargar.
Después de que todos los recursos enumerados en el manifiesto de caché se hayan descargado correctamente, el navegador activa un evento final, cached. Esta es su señal
de que la aplicación web sin conexión está completamente almacenada en caché y lista para usarse sin conexión.

 3.-Por otro lado, si ha visitado previamente esta página o cualquier otra página que apunte al mismo manifiesto de caché, entonces su navegador ya conoce este manifiesto
de caché. Es posible que ya tenga algunos recursos en el caché de aplicaciones. Puede tener toda la aplicación web sin conexión en funcionamiento en el caché de 
aplicaciones. Entonces ahora la pregunta es, ¿ha cambiado el manifiesto de caché desde la última vez que su navegador lo verificó?

--Si la respuesta es no, el manifiesto de caché no ha cambiado, su navegador activará inmediatamente un noupdateevento. 
--Si la respuesta es sí, el manifiesto de caché ha cambiado, su navegador activará un downloadingevento y comenzará a volver a descargar todos los recursos enumerados en
el manifiesto de caché.
--Después de que todos los recursos enumerados en el manifiesto de caché se hayan vuelto a descargar correctamente, el navegador activa un evento final, updateready
Esta es su señal de que la nueva versión de su aplicación web sin conexión está completamente almacenada en caché y lista para usarse sin conexión. La nueva versión
aún no está en uso. Para "cambiar en caliente" a la nueva versión sin obligar al usuario a recargar la página, puede llamar manualmente a la
window.applicationCache.swapCache()función.

  Si, en algún momento de este proceso, algo sale terriblemente mal, su navegador activará un errorevento y se detendrá. Aquí hay una lista irremediablemente
abreviada de cosas que podrían salir mal:

--El manifiesto de caché devolvió un error HTTP 404 (Página no encontrada) o 410 (Desaparecido permanentemente).
--Se encontró el manifiesto de caché y no había cambiado, pero la página HTML que apuntaba al manifiesto no se pudo descargar correctamente.
--El manifiesto de caché cambió mientras se ejecutaba la actualización.
--Se encontró el manifiesto de caché y había cambiado, pero el navegador no pudo descargar uno de los recursos enumerados en el manifiesto de caché.
  
  
EL FINO ARTE DE LA DEPURACIÓN, TAMBIÉN CONOCIDO COMO "¡MÁTAME! ¡MÁTAME AHORA!"
  
  
Quiero mencionar dos puntos importantes aquí. El primero es algo que acaba de leer, pero apuesto a que realmente no lo entendió, así que aquí está de nuevo: 
si incluso un solo recurso enumerado en su archivo de manifiesto de caché no se descarga correctamente, todo el proceso de almacenamiento en caché de su aplicación 
web fuera de línea fallará. Su navegador activará el errorevento, pero no hay indicación de cuál fue el problema real. Esto puede hacer que la depuración de 
aplicaciones web fuera de línea sea aún más frustrante de lo habitual.

El segundo punto importante es algo que, técnicamente hablando, no es un error, pero parecerá un error grave del navegador hasta que te des cuenta de lo que está
pasando. Tiene que ver exactamente con la forma en que su navegador verifica si un archivo de manifiesto de caché ha cambiado. Este es un proceso de tres fases.


1.-A través de la semántica HTTP normal , su navegador verificará si el manifiesto de caché ha caducado. Al igual que cualquier otro archivo que se sirve a través de
HTTP , su servidor web generalmente incluirá metainformación sobre el archivo en los encabezados de respuesta HTTP . Algunos de estos encabezados HTTP
( Expiresy Cache-Control) le dicen a su navegador cómo puede almacenar en caché el archivo sin siquiera preguntarle al servidor si ha cambiado. Este tipo de 
almacenamiento en caché no tiene nada que ver con las aplicaciones web sin conexión.
Si el manifiesto de caché ha caducado (según sus encabezados HTTP ), su navegador le preguntará al servidor si hay una nueva versión y, de ser así, el navegador la 
descargará. Para hacer esto, su navegador emite una solicitud HTTP que incluye la fecha de última modificación del manifiesto de caché, que su servidor web incluyó en
los encabezados de respuesta HTTP la última vez que su navegador descargó el archivo de manifiesto. Si el servidor web determina que el archivo de manifiesto no ha
cambiado desde esa fecha, simplemente devolverá un 304 (Not Modified)estado. Una vez más, nada de esto es específico de las aplicaciones web sin conexión. Esto sucede
esencialmente para todos los tipos de recursos en la web.
Si el servidor web cree que el archivo de manifiesto ha cambiado desde esa fecha, devolverá un código de estado HTTP 200 (OK) , seguido del contenido del nuevo 
archivo, junto con nuevos Cache-Controlencabezados y una nueva fecha de última modificación, de modo que los pasos 1 y 2 funcione correctamente la próxima vez.
( HTTP es genial; los servidores web siempre están planeando para el futuro. Si su servidor web debe enviarle un archivo, hace todo lo posible para asegurarse de que
no tenga que enviarlo dos veces sin ningún motivo). Una vez que se descarga el nuevo archivo de manifiesto de caché, su navegador comparará el contenido con la copia 
que descargó la última vez. Si el contenido del archivo de manifiesto de caché es el mismo que la última vez, su navegador no volverá a descargar ninguno de los
recursos enumerados en el manifiesto.
Cualquiera de estos pasos puede hacerle tropezar mientras desarrolla y prueba su aplicación web sin conexión. 
Para ser claros, esto no es un error, es una característica. Todo está funcionando exactamente como se supone que debe hacerlo. Si los servidores web no tuvieran una
forma de decirle a los navegadores (y proxies intermedios) que almacenen cosas en caché, la web colapsaría de la noche a la mañana.

Entonces, aquí hay algo que debe hacer absolutamente: reconfigure su servidor web para que su archivo de manifiesto de caché no se pueda almacenar en caché mediante
la semántica HTTP . Si está ejecutando un servidor web basado en Apache, estas dos líneas en su .htaccessarchivo harán el truco:

ExpiresActive On
ExpiresDefault "access"
Eso deshabilitará el almacenamiento en caché para cada archivo en ese directorio y todos los subdirectorios. Probablemente eso no sea lo que desea en producción, por
lo que debe calificar esto con una <Files>directiva para que solo afecte su archivo de manifiesto de caché, o crear un subdirectorio que no contenga nada más que este.
htaccessarchivo y su archivo de manifiesto de caché. Como de costumbre, los detalles de configuración varían según el servidor web, así que consulte la documentación
de su servidor para saber cómo controlar los encabezados de almacenamiento en caché de HTTP .

Una vez que haya deshabilitado el almacenamiento en caché de HTTP en el archivo de manifiesto de caché en sí, aún tendrá momentos en los que haya cambiado uno de los
recursos en el caché de aplicaciones, pero aún está en la misma URL en su servidor web. Aquí, el paso 2 del proceso de tres fases te joderá. Si su archivo de
manifiesto de caché no ha cambiado, el navegador nunca notará que uno de los recursos previamente almacenados en caché ha cambiado. Considere el siguiente ejemplo:

CACHE MANIFEST
# rev 42
clock.js
clock.css
Si lo cambia clock.cssy lo vuelve a implementar, no verá los cambios, porque el archivo de manifiesto de caché en sí no ha cambiado. Cada vez que realice un cambio
en uno de los recursos de su aplicación web sin conexión, deberá cambiar el propio archivo de manifiesto de caché. Esto puede ser tan simple como cambiar un solo
carácter. La forma más sencilla que he encontrado para lograr esto es incluir una línea de comentario con un número de revisión. Cambie el número de revisión en el
comentario, luego el servidor web devolverá el archivo de manifiesto de caché recién modificado, su navegador notará que el contenido del archivo ha cambiado e
iniciará el proceso para volver a descargar todos los recursos enumerados en el manifiesto

CACHE MANIFEST
# rev 43
clock.js
clock.css
