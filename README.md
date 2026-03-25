DESCRIPCION GENERAL
Este proyecto consiste en una plataforma de participacion ciudadana en tiempo real diseñada para el evento del CCCB. Permite que los usuarios envien propuestas desde sus dispositivos moviles y que estas aparezcan de forma instantanea en una pantalla central.

TECNOLOGIAS UTILIZADAS

Firebase Realtime Database: Almacenamiento y sincronizacion de datos en la nube.

HTML5 / CSS3: Estructura y diseño visual.

JavaScript (ES6 Modules): Logica de conexion y manipulacion del DOM.

1. ARCHIVO: votar.html (INTERFAZ DE USUARIO)
FUNCION
Actua como el punto de entrada para los participantes. Esta optimizado para dispositivos moviles.

COMPONENTES TECNICOS

Area de texto: Un elemento textarea donde el usuario redacta su propuesta.

Validacion: El sistema verifica que el campo no este vacio antes de intentar el envio.

Metodo de envio: Utiliza la funcion "push" de Firebase. Esto genera un identificador unico para cada mensaje dentro del nodo "propuestas", evitando colisiones de datos.

Feedback: Tras un envio exitoso, el campo se limpia y se muestra un mensaje temporal de confirmacion.

2. ARCHIVO: resultados.html (PANTALLA DEL STAND)
FUNCION
Visualizacion centralizada de todas las propuestas recibidas. Esta diseñado para ser proyectado o mostrado en un monitor de gran tamaño.

COMPONENTES TECNICOS

Contenedor QR: Muestra la imagen "unitag_qrcode_standard.png" para facilitar el acceso a la web de votacion.

Cuadro de ultima respuesta: Un area dedicada justo debajo del QR que resalta el texto de la propuesta mas reciente mediante una animacion de escala y cambio de color de borde.

Muro de ideas: Un sistema de rejilla (flexbox) que organiza las propuestas en tarjetas.

Sincronizacion en tiempo real: Utiliza el oyente "onChildAdded". A diferencia de otros metodos que recargan toda la base de datos, este solo detecta cuando se añade un nuevo elemento, optimizando el rendimiento.

Orden cronologico: Las nuevas propuestas se insertan al inicio del contenedor mediante el metodo "prepend", asegurando que lo mas reciente sea lo primero en verse.

CONFIGURACION Y DESPLIEGUE
BASE DE DATOS
Ambos archivos apuntan a la URL: https://stand-ingenieria-default-rtdb.firebaseio.com. Para su funcionamiento correcto, las reglas de seguridad de Firebase deben permitir lectura y escritura publica (Modo de prueba).

HOSTING
Para que el sistema sea accesible via QR, los archivos deben alojarse en un servidor web. Se recomienda GitHub Pages por su compatibilidad con archivos estaticos.

MANTENIMIENTO
Para limpiar el muro durante el evento, se debe acceder a la consola de Firebase y eliminar el nodo "propuestas". El sitio web se actualizara automaticamente eliminando todas las tarjetas de la pantalla.
