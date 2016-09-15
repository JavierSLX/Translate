#HTTP (PROTOCOLO DE TRANSFERENCIA DE HIPERTEXTO)  
##BASES  

###Introducción

###La Web  
Internet (o la Web) es un masivo sistema de información distribuido por cliente/servidor como se representa en el siguiente diagrama:  

![](http://res.cloudinary.com/javierslx/image/upload/v1473897194/IMG01_ygo8yv.png)  

Algunas aplicaciones están corriendo concurrentemente en la Web, tal como navegar/surfear, correo electrónico, transferencias de archivos, streaming de audio y video, y varias más. En cualquier caso, una comunicación apropiada toma lugar entre el cliente y el servidor, y estás aplicaciones usan un nivel específico del protocolo como HTTP, FTP, SMTP, POP, y etc.

###Protocolo de Tranferencia de Hipertexto (HTTP) 
HTTP es quizás el protocolo de aplicación más popular usado en internet (o Web).

- HTTP es un protocolo de requerimiento asimétrico de respuesta cliente-servidor como se ilustra. Un cliente HTTP envía un mensaje de requerimiento a un servidor HTTP. El servidor, en cambio, regresa un mensaje de respuesta. En otras palabras, HTTP es un protocolo de tirar, el cliente “tira” información del servidor (al instante del servidor baja información al cliente).  

![](http://res.cloudinary.com/javierslx/image/upload/v1473897194/IMG02_mifyjb.png)

- HTTP es un protocolo independiente. En otras palabras, la corriente del requerimiento no conoce lo que hace antes del requerimiento previo.   
- HTTP permite negociar el tipo de dato y su representación, para que cualquier sistema construido independientemente de los datos puedan ser transferidos.
- Citando del RFC2616: "El protocolo HTTP es un protocolo de aplicación  para distribuir, colaborar, información hipermedia. Es genérico, independiente, y puede ser usado para algunas tareas por el uso de hipertexto, con servidores distribuyendo sistemas de administración, extendido por métodos de requerimiento, código de errores y cabeceras".

###El Navegador
Cuando tú colocas una URL en tu navegador estás usando un recurso como HTTP, por ejemplo: *http://www.nowhere123.com/index.html*, el navegador cambia la URL por un mensaje de requerimiento y lo envía al servidor HTTP. El servidor interpreta el mensaje de requerimiento, y regresa un mensaje apropiado de respuesta, el cual puede ser un recurso de requerimiento o un mensaje de error. Ese proceso se ilustra a continuación:

![](http://res.cloudinary.com/javierslx/image/upload/v1473897194/IMG03_bj4p0s.png)

###Localizador Uniforme de Recursos (URL)
Una URL es usada para identificar un recurso alojado en la Web. Una URL usa la siguiente sintaxis:

*protocol://hostname:port/path-and-file-name*

Existen 4 partes en una URL:  
1.	*Protocolo*: El nivel de protocolo que usará el cliente y el servidor, ejemplo: HTTP, FTP y telnet.
2.	*Hostname*: Es el nombre del dominio DNS (ejemplo: www.nowhere123.com) o dirección IP (ejemplo: 192.128.1.2) del servidor.  
3.	*Puerto*. El número del puerto TCP del servidor que está escuchando para la llegada de los requerimientos de los clientes.  
4.	*Dirección y nombre del archivo*. El nombre y la localización del recurso de requerimiento, bajo el directorio base del servidor.  

Por ejemplo, en la URL *http://www.nowhere123.com/docs/index.html*, el protocolo de comunicación es **HTTP**; el hostname es *www.nowhere123.com*. El número de puerto no está específico en la URL, pero toma el número por default, que es puerto TCP 80 para HTTP. La dirección y el nombre del archivo del recurso está localizado en "/docs/index.html".  

Otro ejemplo de URL es:  

*ftp://www.ftp.org/docs/test.txt   
mailto:user@test101.com  
news:soc.culture.Singapore  
telnet://www.nowhere123.com/*

###Protocolo HTTP
Como se mencionó, cuando tú introduces la URL en caja de dirección del navegador, el navegador traduce la URL en un mensaje de requerimiento acordado con el protocolo específico; y envía el mensaje de requerimiento al servidor.  

Por ejemplo, el navegador traduce la URL *http://www.nowhere123.com/doc/index.html* en el siguiente mensaje de requerimiento:  

*GET /docs/index.html HTTP/1.1  
Host: www.nowhere123.com  
Accept: image/gif, image/jpeg, */*  
Accept-Language: en-us  
Accept-Encoding: gzip, deflate  
User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)  
(blank line)*

Con este mensaje de requerimiento, el servidor puede tomar una de las siguientes acciones:

1.	El servidor interpreta el requerimiento recibido, mapea el requerimiento dentro de un archivo bajo el documento de directorio del servidor, y regresa el archivo requerido por el cliente.
2.	El servidor interpreta el requerimiento recibido, mapea el requerimiento dentro del programa de mantenimiento del servidor, ejecuta el programa, y regresa la salida del programa al cliente.  
3.	El requerimiento no puede ser satisfecho, el servidor regresa un mensaje de error.  

Un ejemplo de la respuesta de un mensaje HTTP es el siguiente:  

***HTTP/1.1 200 OK**  
Date: Sun, 18 Oct 2009 08:56:53 GMT  
Server: Apache/2.2.14 (Win32)  
Last-Modified: Sat, 20 Nov 2004 07:16:26 GMT*  

*ETag: "10000000565a5-2c-3e94b66c2e680"   
Accept-Ranges: bytes  
Content-Length: 44  
Connection: close  
**Content-Type: text/html**  
X-Pad: avoid browser bug*

El servidor recibe el mensaje de respuesta, interpreta el mensaje y muestra el contenido del mensaje en la ventana del navegador acordando el tipo de datos de la respuesta (como el tipo de encabezado de respuesta del contenido). Los datos comunes de datos incluyen “texto/plano”, “texto/html”, “imagen/gif”, “imagen/jpeg”, “audio/mpeg”, “video/mpeg”, “application/msword”, y “aplicación”pdf”.  

En caso de que no exista ninguna acción, un servidor HTTP solamente escucha las direcciones IP y los puertos específicos a los cuales fue configurado para la llegada de un requerimiento. Cuando el requerimiento llega, el servidor analiza la cabecera del mensaje, aplica las reglas específicas de configuración, y toma una acción apropiada. El administrador principal posee el control principal de las acciones que tenga el servidor web, esto está tratado más adelante.  

###HTTP cambiando a TCP/IP  
HTTP es un protocolo de aplicación de cliente-servidor. Este corre bajo la conexión TCP/IP, como se ilustra. (HTTP no necesita correr en TCP/IP. Solo presume usar el nivel de transporte. Los protocolos de transporte proveen que pueda ser usado.)  

![](http://res.cloudinary.com/javierslx/image/upload/v1473897192/IMG04_y2ex76.png) 

TCP/IP (Protocolo de Control de Transmisión/ Protocolo de Internet) es un conjunto de leyes de transporte y protocolos de redes para poder comunicar máquinas con alguna otra en la red.  

IP (Protocolo de Internet) es un protocolo de ley de red, trata con direcciones y enrutamiento de red. En una red IP, cada máquina es asignada una única dirección IP (ej. 165.1.2.3) y el software IP es responsable de enrutar el mensaje de recurso de tal IP a la IP del destino. En IPv4 (IP versión 4), la dirección IP consta de 4 bytes, con rango de 0 a 255, separados por puntos, el cual es llamado una forma de puntos y rayas. Este esquema de números soporta direcciones 4G en la red. El último IPv6 (IP versión 6) soporta más direcciones. Como memorizar número es más difícil para la gente, un nombre se les asigna a los dominios, como www.nowhere123.com por dar un ejemplo.  

El DNS (El servicio de nombrar dominios) traduce el nombre del dominio a la dirección IP (esto usando tablas). Una dirección IP especial 127.0.0.1 siempre es referida a la propia máquina. Este dominio es llamado como “localhost” y puede ser usado para pruebas locales.  

TCP (Protocolo de Transmisión de Control) es un protocolo de ley de transporte, responsable de establecer una conexión entre dos máquinas. TCP consiste en 2 protocolos: TCP y UDP (Paquete de Datagrama del Usuario). TCP es de confianza, cada paquete contiene una secuencia de números, y un reconocimiento es esperado. Un paquete será retransmitido en caso de no ser recibido. El paquete está garantizado de entrega en TCP. UDP no garantiza la entrega del paquete, y esto no es rentable. En cualquier caso, UDP es una red pobre que sólo puede ser usada en aplicaciones de streaming de video y audio, donde la rentabilidad no es tan crítica.  

Las aplicaciones de multiplexores TCP están dentro de una máquina IP. Por cada máquina IP, los soportes TCP (multiplexores) son arriba de los 65536 puertos (o sockets), desde el puerto número 0 al 65535. Una aplicación, tanto como HTTP o FTP, corre (o escucha) en un número de puerto en particular para la llegada de requerimientos. Del puerto 0 al 1023 están pre-asignados a los protocolos populares, ej. HTTP al 80, FTP al 21, Telnet al 23, SMTP al 25, NNTP al 119, y DNS al 53. EL puerto 1024 y más arriba son puertos disponibles para el usuario.  

El puerto TCP 80 está pre-asignado a HTTP, como el puerto por default de HTTP, esto no prohíbe que corra un servidor HTTP en otro puerto asignado por el usuario (1024-65535) como el 8000, 8080, especialmente para las pruebas del servidor. Tú no puedes correr múltiples servidores HTTP en diferentes números de puertos. Cuando un cliente coloca una URL sin especificar un puerto específico, ej. http://www.nowhere123.com/docs/index.html el navegador conectará al puerto por default, 80 al host www.nowhere123.com. Tú necesitas específicamente colocar el número de puerto en la URL, ej. http://www.nowhere123.com:8000/docs/index.html si el servidor está escuchando en el puerto 8000 y no por default en el puerto 80.  

En resumen, para comunicarse con TCP/IP, tú necesitas conocer la dirección IP o el nombre del dominio así como el número de puerto.  

###Especificaciones HTTP  
Las especificaciones están mantenidos por W3C (World-wide Consortium)  la cual se encuentra http://www.w3.org/standards/techs/http. Hay dos versiones HTTP, usualmente, HTTP/1.0 y HTTP/1.1. Las versiones originales, HTTP/0.9 (1991), escrito por Tim Berners-Lee, es un protocolo simple para la transferencia de datos que cruza el Internet. HTTP/1.0 (1996) (definido en RFC 1945), improvido el protocolo para seguir mensajes MIME. HTTP/1.0 no realiza direcciones en los poxies, datos, conexiones persistentes, hosts y rango de descarga. Estas características fueron provistas en HTTP/1.1 (1999) (definido en RFC 2616).  

###Servidor HTTP Apache o Servidor Tomcat Apache  
Un servidor HTTP (tal como servidor HTTP o servidor Apache Tomcat) es necesitado al estudio del protocolo HTTP.  

El servidor HTTP Apache es un servidor popular para la producción industrial, es producido por  Apache Software Foundation (ASF) @ www.apache.org. ASF es una fundación de software de código abierto. Tal como se dice, el servidor HTTP Apache es libre, con su código abierto.  

El primer servidor HTTP está escrito por Tim Berners Lee en el CERN (Centro Europeo para la Investigación Nuclear) en Ginebra, Suiza, quien el mismo inventó HTML. Apache fue realizado en NCSA (Centro Nacional para las Aplicaciones de Supercomputadoras, USA) servidor “httpd 1.3”, cerca de 1995. Apache probablemente recibió ese nombre por la consistencia del código original (cerca del httpd NCS) y algunos parches, o por el nombre de tribu India de Norteamérica.  

###Requerimiento HTTP y mensajes de respuesta
El cliente HTTP y el servidor se comunican enviándose mensajes de texto. El cliente envía mensajes de requerimiento al servidor. El servidor, en cambio, regresa mensajes de respuesta.  

Un mensaje de HTTP consiste de una cabecera de mensaje y un opcional cuerpo de mensaje, separados por una línea en blanco, ilustrado a continuación:  

![](http://res.cloudinary.com/javierslx/image/upload/v1473897191/IMG05_qdr372.png) 

###Mensaje de requerimiento HTTP  
El formato de un mensaje de requerimiento de HTTP es el siguiente:  

![](http://res.cloudinary.com/javierslx/image/upload/v1473897192/IMG06_z5i7dm.png)  

####Línea de requerimiento
La primera línea de la cabecera es llamada línea de requerimiento, seguida por las opcionales cabeceras de requerimiento.  

La sintaxis de la línea de requerimiento es la siguiente:  

*request-method-name request-URI HTTP-version*  

- *request-method-name*: El protocolo HTTP define los métodos de requerimiento, ej. GET, POST, HEAD, y OPTIONS. El cliente puede usar uno de estos métodos para enviar el requerimiento del servidor.
- *request-URI*: Recursos específicos requeridos.
- *HTTP-version*: Dos versiones se usan frecuentemente en uso: HTTP/1.0 y HTTP/1.1.

Ejemplos de líneas de requerimiento:  

*GET /test.html HTTP/1.1  
HEAD /query.html HTTP/1.0  
POST /index.html HTTP/1.1*  

####Cabeceras de requerimiento  
Las cabeceras de requerimiento son en forma de nombre: valores pares. Multiples valores, separados por comas, puede ser específicos.  

*request-header-name: request-header-value1, request-header-value2, ...*  

Ejemplos de cabeceras de requerimientos son:  

*Host: www.xyz.com  
Connection: Keep-Alive  
Accept: image/gif, image/jpeg,  
Accept-Language: us-en, fr, cn*  

####Ejemplo  

La siguiente imagen muestra un mensaje de requerimiento HTTP:  

![](http://res.cloudinary.com/javierslx/image/upload/v1473897194/IMG07_iowhws.png)  

###Mensaje de respuesta HTTP  
El formato de respuesta de un mensaje HTTP es el siguiente:  

![](http://res.cloudinary.com/javierslx/image/upload/v1473897193/IMG08_ai9czf.png)  

####Línea de Estado
La primera línea es llamada como línea de estado, seguida de la cabecera opcional de respuesta.
El estado de la línea tiene la siguiente sintaxis:

*HTTP-version status-code reason-phrase*  

- *HTTP-version*: La versión de HTTP usada en esta sesión. Puede ser HTTP/1.0 y HTTP/1.1.
- *status-code*: Un número generado de 3 dígitos por el servidor que refleja la salida de requerimiento.
- *reason-phrase*: Da una pequeña explicación acerca del estado del código.
- Estado del código común y la frase que expresa una razón como “200 OK”, “400 Not Found”, “403 Forbidden”, “500 Internal Server Error”.  

Ejemplos de la línea de estado son:  

*HTTP/1.1 200 OK  
HTTP/1.0 404 Not Found  
HTTP/1.1 403 Forbidden* 

####Cabeceras de respuesta  
Las cabeceras de respuesta son de cierta forma, valores pares:  

*response-header-name: response-header-value1, response-header-value2, ...*

Ejemplos de cabeceras de respuesta son:  

*Content-Type: text/html  
Content-Length: 35  
Connection: Keep-Alive  
Keep-Alive: timeout=15, max=100*  

El mensaje de cuerpo de respuesta contiene los datos de requerimiento.  

####Ejemplo  
La siguiente imagen muestra un mensaje de respuesta:  

![](http://res.cloudinary.com/javierslx/image/upload/v1473897194/IMG09_pcfljm.png)  

