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

##Parte 2 (15 Septiembre 2016)  

###Métodos de requerimiento HTTP  
El protocolo HTTP define una variedad de métodos de requerimiento. Un cliente puede usar uno de estos métodos de requerimiento para enviar un mensaje de petición al servidor HTTP. Los métodos son los siguientes:  

- GET. Un cliente puede usar el GET para obtener recursos del server.  
- HEAD. Un cliente puede usar el requerimiento HEAD para obtener la cabecera que requiere un requerimiento GET. La cabecera contiene la última fecha de modificación de los datos, esto puede ser usado para checar la memoria caché local.  
- POST. Se usa para subir mensajes al servidor web.  
- PUT. Pregunta al servidor el guardado de los datos.  
- DELETE. Pregunta al servidor el borrado de los datos.  
- TRACE. Pregunta al servidor el regreso de un trazo de diagnóstico de las acciones tomadas.  
- OPTIONS. Pregunta al servidor la lista de métodos de requerimientos que soporta.  
- CONNECT. Usa para decirle como realizar una conexión con otro host y simplificar la respuesta del contenido, sin afectar el rendimiento o memoria. Esto es usualmente usado para hacer conexiones SSL con el proxy.  
- Otros métodos de extensión.  

###Método de requerimiento “GET”  
GET es el método de requerimiento más común en HTTP. Un cliente puede usar el método GET para solicitar una sola cosa como recurso de un servidor HTTP. Un mensaje de requerimiento GET toma la siguiente sintaxis:  

*GET request-URI HTTP-version  
(optional request headers)  
(blank line)  
(optional request body)*

- La palabra GET es sensitivo a lo que se debe de escribir en mayúscula.  
- *request-URI*: Especifica la parte del recurso requerido, con esto debe de comenzar con la raíz “/” del directorio base del documento.  
- *HTTP-version*: Either HTTP/1.0 or HTTP/1.1. Este cliente negocia con el protocolo que usará la sesión. Por ejemplo, el cliente puede requerir que use HTTP/1.1. Si el servidor no soporta HTTP/1.1, puede informar al cliente en respuesta que use HTTP/1.0.  
- El cliente usa las cabeceras de requerimiento opcionales (como es Aceptar, Lenguaje de Aceptación, etc) para negociar con el servidor y preguntar el contenido preferido (ej. Puede ser el lenguaje preferido del cliente).  
- El mensaje de requerimiento del GET tiene un cuerpo de requerimiento opcional que contiene una cadena (que será explicado más adelante).  

###Testeando requerimientos HTTP  
Existen algunas formas de testear los requerimientos HTTP. Tú puedes usar un programa de utilidad llamado “Telnet” o “hyperterm” (búscalo como “telnet.exe” o “hypertrm.exe” bajo c:\windows), o escribe tu propio programa de red para enviar un mensaje de requerimiento al servidor HTTP y testear varios requerimientos HTTP.  

####Telnet  
“Telnet” es una utilidad de red muy usada. Tú puedes usar telnet para establecer una conexión TCP con un servidor, y seguir un requerimiento HTTP. Por ejemplo, supongamos que tu comienzas tu servidor HTTP en localhost (dirección IP 127.0.0.1) en el puerto 8000:  

*> telnet  
telnet> help  
... telnet help menu ...  
telnet> open 127.0.0.1 8000  
Connecting To 127.0.0.1...  
GET /index.html HTTP/1.0  
(Hit enter twice to send the terminating blank line ...)  
... HTTP response message ...*

Telnet es protocolo basado en caracteres. Cada carácter que tú ingreses en el cliente de Telnet será enviado al servidor inmediatamente.  En cualquier caso, tu no puedes ingresar algún tipo de acción especial, como la tecla de borrado porque se enviarán como tal al servidor. Tú puedes habilitar la opción “local echo” para ver los caracteres que colocas. Checa el manual de telnet (busca en la ayuda de Windows) para más detalle de como usar telnet.  

####Programa Network  
Tú puedes escribir tú propio programa de red para observar los requerimientos de un servidor HTTP. Tú programa debe primero establecer conexión TCP/IP con el servidor. Una vez que la conexión haya sido establecida, tú puedes ves la muestra del requerimiento.  

Un ejemplo de un programa de red escrito en Java se muestra a continuación (asumiendo que el servidor HTTP está corriendo en localhost (dirección IP 127.0.0.1) en el puerto 8000):  

import java.net.*;  
import java.io.*;  
   
public class HttpClient {  
   public static void main(String[] args) throws IOException {  
      // The host and port to be connected.  
      String host = "127.0.0.1";  
      int port = 8000;  
      // Create a TCP socket and connect to the host:port.  
      Socket socket = new Socket(host, port);  
      // Create the input and output streams for the network socket.  
      BufferedReader in  
         = new BufferedReader(  
              new InputStreamReader(socket.getInputStream()));  
      PrintWriter out  
         = new PrintWriter(socket.getOutputStream(), true);  
      // Send request to the HTTP server.  
      out.println("GET /index.html HTTP/1.0");  
      out.println();   // blank line separating header & body  
      out.flush();  
      // Read the response and display on console.  
      String line;  
      // readLine() returns null if server close the network socket.  
      while((line = in.readLine()) != null) {  
         System.out.println(line);  
      }  
      // Close the I/O streams.  
      in.close();  
      out.close();  
   }  
}  

###Requerimiento GET HTTP/1.0  
Lo siguiente muestra la respuesta de un requerimiento GET en HTTP/1.0 (via telnet o con un programa de red – asumiendo que tú hayas comenzado un servidor HTTP):  

*GET /index.html HTTP/1.0  
(enter twice to create a blank line)*  

*HTTP/1.1 200 OK  
Date: Sun, 18 Oct 2009 08:56:53 GMT  
Server: Apache/2.2.14 (Win32)  
Last-Modified: Sat, 20 Nov 2004 07:16:26 GMT  
ETag: "10000000565a5-2c-3e94b66c2e680"  
Accept-Ranges: bytes  
Content-Length: 44  
Connection: close  
Content-Type: text/html  
X-Pad: avoid browser bug  
Connection to host lost.*  

En este ejemplo, el cliente usa GET para preguntar por un documento llamado “/index.html”; y negocia usando el protocolo HTPP/1.0. Una línea en blanco se necesita después de la cabecera del requerimiento. Este mensaje de requerimiento no contiene cuerpo.  

El servidor recibe el mensaje de requerimiento, interpreta y mapea el request-URI de un documento bajo el directorio del documento. Si el documento requerido es accesible, el servidor regresa el documento con un código de respuesta “200 OK”. La cabecera de respuesta provee la descripción necesaria del documento que regresa, con la última fecha de modificación (Last-Modified), el tipo MIME (Content-Type), y el largo del documento (Content-Length). El cuerpo de la respuesta contiene el documento requerido. El navegador le da formato y muestra el documento de acuerdo al tipo que está hecho (ej. Texto plano, HTML, JEPG, GIF, etc) y en otra información obtiene las cabeceras de respuesta.  

Notas:  

- El nombre del requerimiento “GET” es sensitivo, por lo que debe de escribirse en mayúsculas.  
- Si el método de requerimiento es escrito incorrectamente, el servidor regresará el mensaje de error “501 Method Not Implemented”.  
- Si el método de requerimiento fue incorrectamente llamado, el servidor regresará como mensaje de error “405 Method Not Allowed”. Ej. DELETE es nombre de método válido, pero no puede ser llamado (o implementado) por el servidor.  
- Si la dirección del requerimiento no existe, el servidor regresará un mensaje de error “404 Not Found”. Para que tengas una dirección apropiada, comienza desde la raíz del documento “/”. En cualquier caso, el servidor regresará un mensaje de error “400 Bad Request”.  
- Si la versión HTTP es incorrecta, el servidor regresará un mensaje de error “400 Bad Request”.  
- En HTTP/1.0, por default,  el servidor ciérrala conexión TCP después de que la respuesta fue liberada. Si tú estás usando Telnet para conectarte al servidor, el mensaje “Connection to host lost” aparecerá inmediatamente después de que el cuerpo fue recibido. Puedes usar una cabecera de reuqerimiento opcional “Connection: Keep-Alive” para requerir una conexión persistente, entonces puede hacerse otro requerimiento ya que la misma conexión TCP sigue viva y con la misma eficiencia. Por otra parte, HTTP/1.1 mantiene la conexión viva por default.  

###Respuesta de código de estado
La primera línea del mensaje de respuesta (línea de estado) contiene el código de estado, que es generado por el servidor para indicar el estado del requerimiento.  

El código de estado está compuesto por un número de 3 dígitos:  

- 1xx (Información): Recibe el requerimiento, el servidor continúa con el requerimiento.  
- 2xx (Exitoso): El requerimiento fue exitosamente recibido, entendido, aceptado y atendido.  
- 3xx (Redirección): Se requiere de otra acción para poderse completar el requerimiento.  
- 4xx (Error del cliente): El requerimiento contiene mala sintaxis o no puede ser entendida.  
- 5xx (Error del servidor): El servidor falló al validar el requerimiento.  

Algunos códigos de estado comúnmente encontrados:  

- 100 Continue: El servidor recibe el requerimiento y lo procesa para dar una respuesta.  
- 200 OK: El requerimiento fue completado.  
- 301 Move Permanently: El requerimiento del recurso ha sido permanentemente movido a una nueva localización. La URL de la nueva localización es dada como respuesta en la cabecera Location. El cliente debe de dar un nuevo requerimiento con la nueva localización. La aplicación de subir todas las referencias a esta nueva localización.  
- 302 Found & Redirect (or Move Temporarily): Lo mismo que el 301, pero la nueva localización es temporal. El cliente debe de dar un nuevo requerimiento, pero esta vez las aplicaciones no necesitan actualizar las referencias.  
- 304 Not Modified: En respuesta de la condicional If-Modified-Since del requerimiento GET, el servidor notifica que el recurso requerido no ha sido modificado.  
- 400 Bad Request: El servidor no interpreta o entiende el requerimiento, probablemente error de sintaxis en el mensaje de requerimiento.  
- 401 Authentication Required: El recurso de requerimiento está protegido, y requiere una credencial del cliente (usuario/contraseña). El cliente debería de volver a enviar el requerimiento con su credencia (usuario/contraseña).  
- 403 Forbidden: El servidor se niega a atender el recurso, debido a la identidad del cliente.  
- 404 Not Found: El recurso de requerimiento no puede ser encontrado en el servidor.  
- 405 Method Not Allowed: El método de requerimiento usado, ej. POST, PUT, DELETE, es un método válido. En cualquier caso, el servidor no da a éstos métodos en un recurso de requerimiento.  
- 408 Request Timeout.  
- 414 Request URI too Large.  
- 500 Internal Server Error: El servidor está confundido, o se está causando un error del lado de la respuesta de requerimiento por parte del programa del servidor.  
- 501 Method Not Implemented: El método de requerimiento usado es invalido (podría ser causado por escritura, ej. “GET” por “Get”).  
- 502 Bad Gateway. Proxy o Gateway indica que recibe una mala respuesta de la información del servidor.  
- 503 Service Unavailable: El servidor no puede responder debido a sobrecarga o mantenimiento. El cliente puede volver a intentarlo más tarde.  
- 504 Gateway Timeout: Proxy o Gateway indica que recibe un tiempo fuera de la información del servidor.  

###Más ejemplos de requerimientos GET HTTP/1.0

####Ejemplo: Método de requerimiento Misspelt  
En el requerimiento, “GET” es cambiado como “get”. El servido regresará un error “501 Method Not Implemented”. La cabecera de respuesta “Allow” le dice al cliente los métodos que seguirá.  

*get /test.html HTTP/1.0  
(enter twice to create a blank line)*  

*HTTP/1.1 501 Method Not Implemented  
Date: Sun, 18 Oct 2009 10:32:05 GMT  
Server: Apache/2.2.14 (Win32)  
Allow: GET,HEAD,POST,OPTIONS,TRACE  
Content-Length: 215  
Connection: close  
Content-Type: text/html; charset=iso-8859-1*  

####Ejemplo: 404 Archivo No Encontrado  

En este requerimiento GET, la URL requerida “/t.html” no puede ser encontrada bajo la documentación del directorio del servidor. El servidor regresa un error “404 Not Found”.  

*GET /t.html HTTP/1.0  
(enter twice to create a blank line)*

*HTTP/1.1 404 Not Found  
Date: Sun, 18 Oct 2009 10:36:20 GMT  
Server: Apache/2.2.14 (Win32)  
Content-Length: 204  
Connection: close  
Content-Type: text/html; charset=iso-8859-1*    

####Ejemplo: Mala versión de numeración HTTP  
En este requerimiento de GET, la versión de HTTP está mal escrita. El servidor regresa un error de “404 Bad Request”. La versión de HTTP debe de ser HTTP/1.0 o HTTP/1.1.  

*GET /index.html HTTTTTP/1.0  
(enter twice to create a blank line)*

*HTTP/1.1 400 Bad Request  
Date: Sun, 08 Feb 2004 01:29:40 GMT  
Server: Apache/1.3.29 (Win32)  
Connection: close  
Content-Type: text/html; charset=iso-8859-1*    

Nota: La última versión de Apache 2.2.14 ignora este error y regresa el documento con código de estado “200 OK”.  

####Ejemplo: Mal requerimiento URI  
En el siguiente requerimiento GET, la dirección requerida no comienza desde la raíz “/”, resultando en un “Bad request”.  

*GET test.html HTTP/1.0  
(blank line)*  

*HTTP/1.1 400 Bad Request  
Date: Sun, 18 Oct 2009 10:42:27 GMT  
Server: Apache/2.2.14 (Win32)  
Content-Length: 226  
Connection: close  
Content-Type: text/html; charset=iso-8859-1*    

####Ejemplo: Mantiene la conexión viva  
Por default, HTTP/1.0, cierra la conexión TCP una vez que la respuesta es liberada. Tú puedes requerir que la conexión TCP se mantenga (entonces puedes enviar otro requerimiento usando la misma conexión TCP, probando la eficiencia de la red), usando una cabecera de requerimiento opcional “Connection: Keep-Alive”. El servidor incluye una “Connection: Keep-Alive” responde a la cabecera para informar al cliente que puede enviar otro requerimiento usando esta conexión, antes de que el tiempo de conexión venza. Otra cabecera “Keep-Alive: timeout=x, max=x” le dice al cliente el tiempo que queda (en segundos) y el máximo número de requerimientos que pueden ser enviados por esta conexión persistente.  

*GET /test.html HTTP/1.0  
Connection: Keep-Alive  
(blank line)*  

*HTTP/1.1 200 OK  
Date: Sun, 18 Oct 2009 10:47:06 GMT  
Server: Apache/2.2.14 (Win32)  
Last-Modified: Sat, 20 Nov 2004 07:16:26 GMT  
ETag: "10000000565a5-2c-3e94b66c2e680"  
Accept-Ranges: bytes  
Content-Length: 44  
Keep-Alive: timeout=5, max=100  
Connection: Keep-Alive  
Content-Type: text/html*  

Notas:  

- El mensaje “Connection to host lost” (para telnet) aparece después de que el tiempo vence en “keep-alive”.  
- Antes de que el mensaje de “Connection to host lost” aparezca, debes de poder enviar otro requerimiento con la misma conexión TCP.  
- La cabecera “Connection: Keep-alive” no es sensitivo. El espacio es opcional.  
- Si en una cabecera opcional es mal escrita o es inválida, esto será ignorado por el servidor.  

####Ejemplo: Accesando a un recurso protegido.  
El siguiente requerimiento GET intenta acceder a un recurso protegido. El servidor regresa un error “403 Forbidden”. En este ejemplo, el directorio “htdocs\forbidden” está configurado para negar todo acceso al servidor HTTP Apache al archivo “http.conf” como sigue:  

*<Directory "C:/apache/htdocs/forbidden">  
   Order deny,allow  
   deny from all  
</Directory>*  

*GET /forbidden/index.html HTTP/1.0  
(blank line)*  

*HTTP/1.1 403 Forbidden  
Date: Sun, 18 Oct 2009 11:58:41 GMT  
Server: Apache/2.2.14 (Win32)  
Content-Length: 222  
Keep-Alive: timeout=5, max=100  
Connection: Keep-Alive  
Content-Type: text/html; charset=iso-8859-1*  

###Requerimiento GET HTTP/1.1  

El servidor HTTP/1.1 soporta los auto llamados hosts virtuales. Estos es, lo mismo que un servidor físico pero con severos hosts virtuales, con diferentes hostnames (ej. www.nowhere123.com y www.test909.com) y su propio raíz de directorio de documentos. En cualquier caso, en un HTTP/1.1 un requerimiento GET, es mandado incluir una cabecera de requerimiento llamado “Host”, para seleccionar uno de los hosts virtuales.  

####Ejemplo: Requerimiento HTTP/1.1  
HTTP/1.1 se mantiene persistente (o viva) la conexión por default y provee eficiencia en la red. Tu puedes usar una cabecera de requerimiento “Connection: Close”  para preguntar al servidor si cierra la conexión TCP una vez que la respuesta ha sido liberada.  

*GET /index.html HTTP/1.1  
Host: 127.0.0.1  
(blank line)*  

*HTTP/1.1 200 OK  
Date: Sun, 18 Oct 2009 12:10:12 GMT  
Server: Apache/2.2.14 (Win32)  
Last-Modified: Sat, 20 Nov 2004 07:16:26 GMT  
ETag: "10000000565a5-2c-3e94b66c2e680"  
Accept-Ranges: bytes  
Content-Length: 44  
Content-Type: text/html*  

####Ejemplo: HTTP/1.1 Cabecera de Host perdida  
El siguiente ejemplo muestra la cabecera del “Host” es mandado en un requerimiento HTTP/1.1. Si la cabecera del “Host” está perdida, el servidor regresa un error “400 Bad Request”.  

*GET /index.html HTTP/1.1  
(blank line)*  

*HTTP/1.1 400 Bad Request  
Date: Sun, 18 Oct 2009 12:13:46 GMT  
Server: Apache/2.2.14 (Win32)  
Content-Length: 226  
Connection: close  
Content-Type: text/html; charset=iso-8859-1*  

###Requerimientos GET condicionales  
En todos los ejemplos previos, el servidor regresa el documento entero si el requerimiento  puede ser completado. Tu puedes usar un requerimiento adicionar “conditional request”. Por ejemplo, para preguntar por el documento basado en la última fecha de modificación (entonces se decide usar una copia del copy), para preguntar por una porción de un documento (o rango) del documento completo (usualmente descargando largos documentos).  

Las cabeceras de requerimiento incluyen:  

- If-Modified-SInce (checa por el código de respuesta “304 Not Modified”).  
- If-Unmodified-Since.  
- If-Match.  
- If-None-Match.  
- If-Range.  

###Cabeceras de requerimiento.  
Esta sección describe algunos de las comúnmente cabeceras de requerimiento. Referido a las especificaciones HTTP para más detalles. La sintaxis de la cabecera está en palabras usando dash (-) ej. Content-Length, If-Modified-Since.  

Host: domain-name – HTTP/1.1 soporta hosts virtuales. Multiples nombres DNS (ej. www.nowhere123.com y www.nowhere456.com) pueden coexistir en el mismo servidor físico, con su propia documentación en el directorio de raíz. La cabecera del host es mandada por HTTP/1.1 para seleccionar uno de los hosts.  

Las siguientes cabeceras pueden ser usadas para contener negociaciones entre el cliente que pregunta al servidor sobre el preferido tipo de documento (en términos de media, ej. JPEG vs. GIF, o lenguaje usado ej. Ingles vs. Francés) si el servidor mantiene múltiples versiones del mismo documento.  

**Accept: mime-type-1, mime-type-2, …** - El cliente puede usar la cabecera de Aceptación para decirle al servidor los tipos de MIME que prefiere. Si el servidor posee multiples versiones del documento requerido (ej. Una imagen GIF y PNG, o un documento TXT y PDF), checa esta cabecera y decide que versión libera al cliente (ej. PNG es más avanzado que GIF, pero no todos los navegadores soportan PNG.) Este proceso es llamado Negociación de Contenido-Tipo.  

**Accept-Language: Language-1, Language-2, …** - El cliente puede usar la cabecera Accept-Language para decirle al servidor que lenguaje de los que posee prefiere. Si el servidor posee múltiples versiones del documento requerido (ej. En Inglés, Chino, Francés), checa la cabecera y decide que versión regresa. Este proceso es llamado Negociación de lenguaje.  

**Accept-Charset: Charset-1, Charset-2, …** - Para negociación de carácter, el cliente puede usar esta cabecera para decirle al servidor que caracteres coloca o prefiere. Ejemplos de sets de caracteres son ISO-8859-1, ISO-8859-2, ISO-8859-5, BIG5, UCS2, UCS4, UTF8.  

**Accept-Encoding: encoding-method-1, encoding-method-2, …** - El cliente puede usar esta cabecera para decirle al servidor el tipo de soporte de codificación. Si el servidor contiene un documento codificado (o comprimido) y es requerido, puede regresar una versión decodificada para el cliente. El servidor puede decodificar el documento antes de regresarlo al cliente para reducir el tiempo de trasmisión. El servidor puede responder con la cabecera “Content-Encoding” para informar al cliente que el documento esta decodificado. Los métodos de decodificación comunes son “x-gzip (.gz, .tgz)” y “x-compress (.z)”.  

**Connection: Close|Keep-Alive** – El cliente puede usar esta cabecera para decirle al servidor que cierre la conexión después de este requerimiento, o mantenga la conexión viva para otro requerimiento. HTTP/1.1 usa conexión persistente por default. HTTP/1.0 cierra la conexión por default.  

**Referer: referer-URL** – El cliente puede usar esta cabecera para indicar la referencia de este requerimiento. Si tu das click al enlace página 1 web para visitar la página 2, la página 1 es referenciada por requerimiento a la página 2 web. Todos los navegadores mayores usan esta cabecera, puede ser usada para dar ese requerimiento (para aviso web, o modificación de contenido). De cualquier manera, esta cabecera no es rentable. Como nota Referrer está mal escrito de “Referer” (afortunadamente, lo sabías también).  

**User-Agent: browser-type** – Identifica el tipo de navegador que se usó para hacer el requerimiento. El servidor puede usar esta información para regresar un documento distinto dependiendo del tipo de navegador.  

**Content-Length: number-of-bytes** – Usado por el requerimiento POST, informa al servidor de lo largo del cuerpo del requerimiento.  

**Content-type: mime-type** – Usado por requerimiento POST, para informar al servidor del tipo de media que requiere el cuerpo del requerimiento.  

**Cache-Control: no-cache|…** - El cliente puede usar esta cabecera para especificar cuantas páginas pueden ser usadas en un servidor. “no-cache” requiere obtener una copia fesca del servidor original, esto si la copia es válida. (el servidor HTTP/1.0 no reconoce “Cache-Control: no-cache”. Se usa para tal, “Pragma: no-cache”. Incluyendo cabeceras de requerimiento si no se está seguro de la versión del servidor).  

**Authorization**: Usado por el cliente para ofrecer su credencial (usuario/contraseña) para acceder a recursos protegidos. (Esta cabecera será descrita al final del capítulo en autentificación).  

**Cookie: cookie-name-1=cookie-value-1, cookie-name-2=cookie-value-2, …** - El cliente usa esta cabecera para regresar las cookies de regreso al servidor, esto usando un estado de administración (esta cabecera será discutida al final del capítulo).  

**If-Modified-Since: date** – Le dice al servidor que envíe la página si sólo ha sido modificada después de una fecha específica.  

###Requerimiento por directorio GET  

Supongamos que un directorio es llamado “testdir” está presente en documento de directorio base llamado “htdocs”.  

Si un cliente hace un requerimiento GET a “/testdir/” (al directorio).  

1.	El servidor regresará “/testdir/index.html” si el directorio contiene el archivo “index.html”.
2.	En cualquier caso, el servidor regresará la lista del directorio, si la lista del directorio está permitida en la configuración del servidor.  
3.	En cualquier otra forma, el servidor regresará “404 Page Not Found”.  

Si está interesado en tomar nota del cliente que hizo el requerimiento GET a “/testdir” (sin especificar la parte del directorio “/”), el servidor regresa un “301 Move Permanently” con una nueva localización de “/testdir/”, como se muestra:  

*GET /testdir HTTP/1.1  
Host: 127.0.0.1  
(blank line)*  

*HTTP/1.1 301 Moved Permanently  
Date: Sun, 18 Oct 2009 13:19:15 GMT  
Server: Apache/2.2.14 (Win32)  
Location: http://127.0.0.1:8000/testdir/  
Content-Length: 238  
Content-Type: text/html; charset=iso-8859-1*  

Más del navegador y lo que indica en el requerimiento a “/testdir/”. Por ejemplo, si tu ruta http://127.0.0.1:8000/testdir no posee “/” para el navegador, no se te va a notificar que fue agregada a la dirección después de que la respuesta fue dada. La moraleja de la historia es: tu deberías inculir la “/” para el requerimiento del directorio para salvar requerimientos adicionales GET.  

###Ruta de un requerimiento GET en un servidor Proxy  

Al enviar un requerimiento GET a un servidor proxy, (a) estableces una conexión al servidor proxy; (b) usas una URI de requerimiento http://hostname:port/path/fileName al objetivo del servidor.  

Las siguientes rutas fueron capturadas usando telnet. Una conexión es establecida con el servidor proxy, y un requerimiento GET. Un requerimiento a un absoluto URI es usada en la línea de petición.  

*GET http://www.amazon.com/index.html HTTP/1.1  
Host: www.amazon.com  
Connection: Close  
(blank line)*  

*HTTP/1.1 302 Found  
Transfer-Encoding: chunked  
Date: Fri, 27 Feb 2004 09:27:35 GMT  
Content-Type: text/html; charset=iso-8859-1  
Connection: close  
Server: Stronghold/2.4.2 Apache/1.3.6 C2NetEU/2412 (Unix)  
Set-Cookie: skin=; domain=.amazon.com; path=/; expires=Wed, 01-Aug-01 12:00:00 GMT  
Connection: close  
Location: http://www.amazon.com:80/exec/obidos/subst/home/home.html  
Via: 1.1 xproxy (NetCache NetApp/5.3.1R4D5)*  

Toma nota que dé respuesta regresa un “chunks”.  

###Método de requerimiento “HEAD”  

El requerimiento HEAD es similar al requerimiento GET. El servidor regresa solo la cabecera de respuesta sin el cuerpo de respuesta, el que contiene el actual documento. El requerimiento HEAD es usualmente usado para checar cabeceras, como Last-Modified, Content-Type, Content-Length, antes de enviar propiamente un requerimiento GET del documento.  

La sintaxis del requerimiento HEAD es el siguiente  

*HEAD request-URI HTTP-version  
(other optional request headers)  
(blank line)  
(optional request body)*  

####Ejemplo  

*HEAD /index.html HTTP/1.0  
(blank line)*  

*HTTP/1.1 200 OK  
Date: Sun, 18 Oct 2009 14:09:16 GMT  
Server: Apache/2.2.14 (Win32)  
Last-Modified: Sat, 20 Nov 2004 07:16:26 GMT  
ETag: "10000000565a5-2c-3e94b66c2e680"  
Accept-Ranges: bytes  
Content-Length: 44  
Connection: close  
Content-Type: text/html  
X-Pad: avoid browser bug*  

Notifica que la respuesta consiste de la cabecera sola sin el cuerpo, el cual contiene el documento actual.  

###Método de requerimiento “OPTIONS”  

Un cliente puede usar un requerimiento OPTIONS para que el servidor muestre los métodos de requerimientos que son soportados. La sintaxis del requerimiento de OPTIONS es el siguiente:  

*OPTIONS request-URI|* HTTP-version  
(other optional headers)  
(blank line)  

“*” puede ser usado en lugar de una dirección para indicar que el requerimiento no aplica en un recurso en particular.  

####Ejemplo  

Por ejemplo, las siguientes OPTIONS son enviadas de un servidor proxy:  

*OPTIONS http://www.amazon.com/ HTTP/1.1  
Host: www.amazon.com  
Connection: Close  
(blank line)*  

*HTTP/1.1 200 OK  
Date: Fri, 27 Feb 2004 09:42:46 GMT  
Content-Length: 0  
Connection: close  
Server: Stronghold/2.4.2 Apache/1.3.6 C2NetEU/2412 (Unix)  
Allow: GET, HEAD, POST, OPTIONS, TRACE  
Connection: close  
Via: 1.1 xproxy (NetCache NetApp/5.3.1R4D5)  
(blank line)*  

Todos los servidores soportan GET y como se ve el requerimiento HEAD. Algunas veces, HEAD no está listado.  

###Método de requerimiento “TRACE”  
Un cliente puede enviar un requerimiento TRACE para preguntar al servidor que regrese una ruta de diagnóstico.  

Un requerimiento TRACE toma la siguiente sintaxis:  

*TRACE / HTTP-version  
(blank line)*  

####Ejemplo
El siguiente ejemplo muestra un requerimiento de un servidor proxy.  

*TRACE http://www.amazon.com/ HTTP/1.1  
Host: www.amazon.com  
Connection: Close  
(blank line)*  

*HTTP/1.1 200 OK  
Transfer-Encoding: chunked  
Date: Fri, 27 Feb 2004 09:44:21 GMT 
Content-Type: message/http  
Connection: close  
Server: Stronghold/2.4.2 Apache/1.3.6 C2NetEU/2412 (Unix)  
Connection: close  
Via: 1.1 xproxy (NetCache NetApp/5.3.1R4D5)*  

(Compara el requerimiento TRACE con la ruta seguida).