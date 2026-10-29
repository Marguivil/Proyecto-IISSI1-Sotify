# Sotify

## Miembros del grupo L2-ABS-11

1. Pérez Ponce, Ignacio
2. Guichot Vila, Mario
3. Redondo Rosco, Diana
4. Barbero Luna, Alvaro

## 1. Introducción al problema

Spotify ha caido en una demanda por practicas monopolisticas por la CNMC (Comisión Nacional de los Mercados y la Competencia) y actualmente se encuentra inoperativa. Para ello, la empresa de Spotify decide partir la empresa en dos. Una parte con Spotify o otra con Sotify, la alternativa antimonopolio que ha ofrecido la CNMC. El proyecto consiste en diseñar la aplicación de streaming musical junto con su base de datos que permita organizar y gestionar la información de manera eficiente (incluso mejor que la original).

Los usuarios podrán crear sus propias listas de reproduccion, seguir a sus artistas favoritos, reproducir canciones y consultar su historial de música. Por otro lado, los artistas podrán publicar álbumes y canciones, así como reproducir música dentro de la plataforma.

La finalidad del proyecto es desarrollar un modelo de base de datos que represente correctamente las relaciones entre las distintas entidades, facilite la consulta y actualización. De esta forma, se pretende crear una estructura que permita cumplir las necesidades de los usuarios y los artistas.

![Logo de Sotify](img/Sotify_Logo.png)
*Logo de Sotify*

## 2. Glosario de términos

Este glosario recoge los principales términos relacionados con el dominio del problema de la aplicación de reproducción musical. Su finalidad es establecer un vocabulario común que facilite la comprensión de los requisitos, las funcionalidades y el modelo de datos del sistema.

**Álbum:** Conjunto de canciones publicadas como una misma obra musical. Un álbum dispone de información como el título, la fecha de publicación y la portada, y puede estar asociado a uno o varios artistas.

**Artista:** Persona o grupo musical que interpreta o crea canciones. Un artista puede estar asociado a varias canciones y álbumes.

**Búsqueda musical:** Funcionalidad que permite localizar canciones, artistas o álbumes mediante criterios como el título de una canción o el nombre de un artista.

**Canción:** Unidad de contenido musical que el usuario puede consultar y reproducir desde la aplicación. Puede tener atributos como el título, la duración y el álbum al que pertenece.

**Catálogo musical:** Conjunto de canciones, álbumes y artistas disponibles en la aplicación para su consulta y reproducción.

**Cuenta de usuario:** Conjunto de datos que identifica a un usuario registrado y permite gestionar su acceso a las funcionalidades personalizadas de la aplicación.

**Género musical:** Categoría que permite clasificar canciones según sus características musicales, como pop, rock, jazz o música clásica.

**Lista de reproducción:** Colección de canciones creada por un usuario para agrupar y organizar música según sus preferencias. Puede tener un nombre y contener varias canciones.

**Reproducción:** Acción mediante la cual el usuario escucha una canción a través de la aplicación.

**Reproductor musical:** Componente de la aplicación que permite controlar la reproducción de canciones, incluyendo acciones como reproducir y pausar.

**Streaming de audio:** Tecnología que permite transmitir contenido de audio para su reproducción a través de una conexión de red, sin necesidad de descargar previamente el archivo completo.

**Usuario:** Persona que utiliza la aplicación para buscar música, escuchar canciones y gestionar sus listas de reproducción. En caso de disponer de una cuenta registrada, podrá acceder a las funcionalidades personalizadas que ofrezca el sistema.

**Modo aleatorio:** Funcionalidad que permite al usuario escuchar una lista de reproducción sin un orden definido

## 3. Visión general del sistema

### 3.1. Requisitos generales
* **Gestión de usuarios**: la aplicación permitirá el registro y la administración de los distintos usuarios del sistema: Administrador, Cliente y Artista. Los artistas podrán 
* **Gestión de catálogo musical**: se podrá realizar registro, creación, modificación y administración del catálogo musical (Canciones, Álbumes y Artistas).
* **Gestión de listas de reproducción personales**: la aplicación permitirá crear de listas personales por los usuarios para almacenar canciones de álbumes (sea una o varias). También se podría almacenar el álbum entero, añadiendo todas las canciones dentro de la lista.
* **Gestión de control de reproducción multimedia**: la aplicación podrá reproducir el contenido multimedia, pudiendo iniciar y pausar canciones. Además, también se podrá adelantar a la siguiente canción o retroceder a la anterior.

### 3.2. Usuarios del sistema

* **Usuario**: usuario registrado dentro de la aplicación, haciendo uso de la misma. El usuario puede buscar contenido en el catálogo, reproducir y pausar canciones, y gestionar sus propias listas de reproducción personales.
* **Administrador**: responsable de la aplicación con la capacidad de realizar las acciones CRUD de todo el contenido (música, álbumes, listas, artistas y usuarios.
* **Artista**: usuario de tipo especial con la capacidad de crear contenido multimedia (música y álbumes), además de las capacidades de un usuario básico, es decir, pudiendo reproducir música y crear listas personales.

## 4. Catálogo de requisitos

### 4.1. Requisitos funcionales

#### R.F.01. Inicio de sesión

Como usuario registrado, quiero iniciar sesión con mi correo electrónico y contraseña, para acceder a mi cuenta personal.

***Prueba de aceptación***
- El sistema debe permitir introducir las credenciales de acceso.
- Si las credenciales son correctas, el sistema debe permitir el acceso a la cuenta correspondiente.
- Si las credenciales son incorrectas, el sistema debe mostrar un mensaje de error y denegar el acceso.
- Un usuario que no haya iniciado sesión no debe poder acceder a las funcionalidades que requieran autenticación.
- Tras iniciar sesión, el usuario debe poder consultar los datos de su cuenta personal.
- Si el acceso es denegado, el usuario no debe poder consultar información de ninguna cuenta.


#### R.F.02. Consulta del catálogo musical

Como usuario, quiero consultar el catálogo musical, para descubrir las canciones, los artistas y los álbumes disponibles en la aplicación.

***Prueba de aceptación***
- El sistema debe mostrar las canciones disponibles en el catálogo.
- El usuario debe poder consultar la información de una canción.
- El usuario debe poder consultar la información de los artistas y álbumes disponibles.
- Si el catálogo está vacío, el sistema debe informar de que no hay contenido disponible.
- El usuario debe poder consultar las canciones asociadas a un álbum o a un artista.
- La consulta del catálogo no debe modificar ningún dato.


#### R.F.03. Búsqueda de música

Como usuario, quiero buscar canciones, artistas y álbumes por su nombre, para encontrar fácilmente la música que deseo escuchar.

***Prueba de aceptación***
- El sistema debe permitir introducir un texto de búsqueda.
- Los resultados deben mostrar el contenido que coincida con el criterio de búsqueda.
- Los resultados deben permitir distinguir entre canciones, artistas y álbumes.
- Si no existen coincidencias, el sistema debe informar de que no se han encontrado resultados.
- El usuario debe poder consultar la información detallada de cualquier elemento mostrado en los resultados.
- La búsqueda no debe modificar ningún dato.


#### R.F.04. Reproducción y pausa de canciones

Como usuario, quiero reproducir y pausar canciones del catálogo, para escuchar la música disponible en la aplicación.

***Prueba de aceptación***
- El sistema debe permitir iniciar la reproducción de una canción disponible.
- El usuario debe poder pausar una canción que se esté reproduciendo.
- El reproductor debe mostrar el título de la canción y el nombre del artista.
- Si una canción no está disponible para su reproducción, el sistema debe informar al usuario.
- El usuario debe poder consultar el estado actual del reproductor (reproduciendo o en pausa).
- El usuario debe poder consultar qué canción está cargada en el reproductor.


#### R.F.05. Creación de listas de reproducción

Como usuario registrado, quiero crear listas de reproducción con un nombre, para organizar las canciones según mis preferencias.

***Prueba de aceptación***
- El sistema debe permitir introducir el nombre de una nueva lista.
- El sistema debe asociar la lista al usuario que la ha creado.
- La lista debe aparecer en la colección personal del usuario.
- El sistema no debe permitir crear listas con nombres vacíos o formados únicamente por espacios en blanco.
- El usuario debe poder consultar su colección personal y ver el nombre de cada lista creada.
- El usuario no debe poder consultar, en su colección, listas pertenecientes a otras cuentas.
- Tras un intento de crear una lista con nombre vacío, la consulta de la colección no debe mostrar ninguna lista nueva.


#### R.F.06. Añadir canciones a una lista de reproducción

Como usuario registrado, quiero añadir canciones del catálogo a mis listas de reproducción, para reunir en ellas la música que me interesa.

***Prueba de aceptación***
- El sistema debe permitir seleccionar una canción del catálogo.
- El sistema debe permitir añadirla a una lista de reproducción propia.
- La canción debe aparecer en el contenido de la lista seleccionada.
- Los cambios deben conservarse después de cerrar la sesión y volver a iniciarla.
- El usuario no debe poder modificar las listas pertenecientes a otras cuentas.
- El usuario debe poder consultar el contenido de una lista propia y ver las canciones añadidas.
- Tras volver a iniciar sesión, la consulta de la lista debe mostrar las mismas canciones.
- La consulta de las listas de otras cuentas no debe mostrar ningún cambio realizado por el usuario.


#### R.F.07. Eliminar canciones de una lista de reproducción

Como usuario registrado, quiero eliminar canciones de mis listas de reproducción, para mantenerlas actualizadas según mis preferencias.

***Prueba de aceptación***
- El sistema debe permitir seleccionar una canción incluida en una lista propia.
- Tras eliminarla, la canción debe dejar de aparecer en esa lista.
- La canción debe seguir disponible en el catálogo musical.
- El usuario no debe poder eliminar canciones de listas pertenecientes a otras cuentas.
- Tras eliminar la canción, la consulta del contenido de la lista no debe mostrarla.
- Tras eliminar la canción, la consulta del catálogo debe seguir mostrándola.
- La consulta de las listas de otras cuentas debe mostrar su contenido sin cambios.


### R.F.08. Modificación y eliminación de listas de reproducción

Como usuario registrado, quiero cambiar el nombre de mis listas de reproducción o eliminarlas, para mantener organizada mi colección musical.

***Prueba de aceptación***
- El sistema debe permitir modificar el nombre de una lista propia.
- El sistema no debe permitir guardar un nombre vacío.
- El sistema debe solicitar confirmación antes de eliminar una lista.
- Tras eliminarla, la lista debe dejar de aparecer en la cuenta del usuario.
- El usuario no debe poder modificar ni eliminar listas pertenecientes a otras cuentas.
- El usuario debe poder consultar las canciones asociadas a un álbum o a un artista.
- La consulta del catálogo no debe modificar ningún dato.


#### R.F.09. Cierre de sesión

Como usuario autenticado, quiero cerrar sesión, para finalizar mi acceso a la cuenta de forma segura.

***Prueba de aceptación***
- El sistema debe ofrecer una opción para cerrar sesión.
- Al cerrar sesión, el usuario debe dejar de tener acceso a las funcionalidades que requieren autenticación.
- Para volver a acceder a su cuenta, el usuario debe iniciar sesión de nuevo.
- El usuario debe poder consultar la información detallada de cualquier elemento mostrado en los resultados.
- La búsqueda no debe modificar ningún dato.


  
### 4.1.1. Requisitos de información

##### R.I.01. Información sobre canciones

Como gestor de la aplicación, quiero disponer de la información correspondiente a cada canción del catálogo, incluyendo título, duración, artistas participantes, fecha de lanzamiento, letra, álbum al que pertenece y número de reproducciones, para mantenerla actualizada

##### R.I.02. Información sobre usuarios

Como gestor de la aplicación, quiero almacenar la siguiente información correspondiente a los usuarios registrados: nombre de usuario, correo electrónico, contraseña y fecha de nacimiento, para poder gestionarlos correctamente y mejorar su experiencia

##### R.I.03. Información sobre álbumes

Como gestor de la aplicación, quiero disponer de la información sobre el título, los artistas participantes, la portada y la fecha de lanzamiento de los álbumes, para poder gestionarlos dentro de la aplicación

##### R.I.04. Información sobre artistas

Como gestor de la aplicación, quiero almacenar la siguiente información sobre los artistas: nombre, nombre artístico, país, número de canciones, número de álbumes y número total de reproducciones

##### R.I.05. Información sobre listas de reproducción

Como gestor de la aplicación, quiero disponer de la información sobre el nombre, la cantidad de canciones incluidas, el creador de la lista y las canciones que contiene cada lista de reproducción, para poder gestionar las listas

##### R.I.06. Información sobre favoritos

Como gestor de la aplicación, quiero disponer de la información correspondiente a las canciones marcadas como favoritos, como el título, el usuario que la ha marcado como favorito, y la lista completa de canciones marcadas como favorito por un mismo usuario, para poder crear una lista de reproducción con las canciones favoritas de cada usuario

##### R.I.01. Información sobre canciones




### 4.1.2. Reglas de negocio

##### R.N.01. Unicidad del correo electrónico

Cada cuenta de usuario debe estar asociada a una dirección de correo electrónico única. No se permitirá registrar dos cuentas con la misma dirección de correo electrónico.

##### R.N.02. Validación de los datos de registro

Para crear una cuenta, el usuario debe proporcionar todos los datos obligatorios y una dirección de correo electrónico con formato válido. La contraseña debe cumplir las condiciones de seguridad establecidas para la aplicación.

##### R.N.03. Protección de las credenciales

Las contraseñas de los usuarios no deben almacenarse en texto plano. El sistema debe utilizar un mecanismo seguro de almacenamiento de contraseñas y comprobar las credenciales durante el inicio de sesión.

##### R.N.04. Autenticación para operaciones personales

Las operaciones de creación, modificación y eliminación de listas de reproducción requieren que el usuario haya iniciado sesión. El sistema debe verificar la identidad del usuario antes de permitir estas operaciones.

##### R.N.05. Disponibilidad del contenido musical

Solo podrán consultarse y reproducirse como contenido disponible las canciones que estén registradas en el catálogo y habilitadas para su reproducción.

##### R.N.06. Propiedad de las listas de reproducción

Cada lista de reproducción debe estar asociada a un único usuario propietario. El usuario propietario será el responsable de gestionar el nombre de la lista y las canciones que contiene.

##### R.N.07. Validez del nombre de una lista

Toda lista de reproducción debe tener un nombre no vacío. No se permitirá crear una lista ni modificar su nombre utilizando únicamente espacios en blanco.

##### R.N.08. Control de acceso a las listas

Un usuario solo podrá modificar o eliminar las listas de reproducción de las que sea propietario. Tampoco podrá añadir o eliminar canciones de listas pertenecientes a otros usuarios.

##### R.N.09. Integridad del catálogo musical

Eliminar una canción de una lista de reproducción no debe eliminar la canción del catálogo musical. La canción debe seguir disponible para otros usuarios y para otras listas, siempre que continúe habilitada en el catálogo.

##### R.N.10. Integridad de las relaciones entre datos

Toda lista de reproducción debe estar asociada a un usuario existente, y toda canción incluida en una lista debe existir en el catálogo musical. El sistema no debe permitir relaciones que hagan referencia a usuarios, listas o canciones inexistentes.

##### R.N.11. Conservación de la información personal

Las listas de reproducción y sus asociaciones con las canciones deben mantenerse almacenadas al cerrar sesión. Cuando el usuario vuelva a iniciar sesión, debe poder recuperar sus listas y consultar su contenido.

### 4.2. Mapa de historias de usuario (opcional)
<img width="1651" height="525" alt="image" src="https://github.com/user-attachments/assets/657aeab3-bc3f-414b-800d-e63115f4fc3c" />



### 4.3. Requisitos no funcionales (opcional)

**R.N.F. 01. Disponibilidad 24/7**
Como gestor de la aplicación, quiero que la disponibilidad del sistema sea 24/7, para que los usuarios puedan reproducir contenido ininterrumpidamente

**R.N.F. 02. Disponibilidad sin conexión**
Como gestor de la aplicación, quiero que los usuarios puedan descargarse contenido, para que en caso de que pierdan la conexión, puedan seguir reproduciendo todo aquel contenido que tienen descargado

**R.N.F. 03. Seguridad**
Como gestor de la aplicación, quiero que no se pueda acceder a los datos personales de los usuarios y que las contraseñas estén cifradas de manera segura, para cumplir con la Ley de Protección de Datos y garantizar la tranquilidad del usuario

**R.N.F. 04. Rendimiento**
Como gestor de la aplicación, quiero que esta sea capaz de atender las peticiones de todos los usuarios, garantizando que los resultados se mostraran en pocos segundos

**R.N.F. 05. Compatibilidad**
Como gestor de la aplicación, quiero que garantice que los datos del usuario (listas de reproducción, artistas favoritos, etc) están sincronizados desde donde abra la aplicación, incluídos dispositivos distintos

**R.N.F. 06. Facilidad de uso**
Como gestor de la aplicación, quiero que sea intuitiva y sencilla de navegar, y que los usuarios puedan encontrar lo que busquen sin complicaciones

-- fin entregable 1 --

## 5. Modelo conceptual

### 5.1. Diagramas de clases UML

- con restricciones.

### 5.2. Escenarios de prueba

- con descripción textual y diagrama de objetos UML.

## 6. Matrices de trazabilidad

- Matriz de trazabilidad entre los elementos del modelo conceptual y los requisitos.

|       | EntidadX   | AsociaciónX  | RestricciónX  | Entidad2 ...   | 
|:------|:-----------|:-----------|:-----------|:-----------|
| RI-1  | X          | X          | X          | X          |
| RI-2  |            | X          |            | X          |
| RF-1  |            | X          |            | X          |
| RF-2  | X          |            | X          | X          |
| RN-1  |            | X          |            |            |
| RN-2  | X          | X          | X          |            |
| ...   |            |            |            |            |

-- fin entregable 2 --

## 7. Modelo relacional en 3FN

- Relaciones obtenidas al aplicar la transformación del modelo conceptual.

### 7.1.  Justificación de la estrategia de transformación de jerarquías

- si se identificaron jerarquías en el MC.


### 8. Matriz de trazabilidad MC/SQL (opcional):

- Restricciones sobre el MC / Elementos del modelo tecnológico (SQL) (Triggers, checks, etc.)
- Incluir Reglas de negocio — Constraints/Triggers en las matrices de trazabilidad para el entregable 3

|       | EntidadX   | AsociaciónX  | RestricciónX  | Entidad2 ...   | 
|:-------|:-------|:-------|:-------|:-------|
| TABLA-1 |        |        |        |        |
| TABLA-2 |        |        |        |        |
| TABLA-3 |        |        |        |        |
| TABLA-4 |        |        |        |        |
| TRIG-1 |        |        |        |        |
| TRIG-2 | X      | X      |        | X      |
| TRIG-3 |        | X      |        | X      |
| TRIG-4 |        |        | X      |        |
| CONST-1 |        |        |        |        |
| CONST-2 | X      | X      |        | X      |
| CONST-3 |        | X      |        | X      |
| CONST-4 |        |        | X      |        |

Se consideran todo tipo de constraints declarativas (aquellas definidas durante el CREATE TABLE).
-- fin entregable 3 --

## Referencias


