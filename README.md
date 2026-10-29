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
* **Como**: Usuario registrado
* **Quiero**: Iniciar sesión con mi correo electrónico y contraseña.
* **Para**: Acceder a mi cuenta personal y a las funcionalidades que requieren autenticación.
* **Prueba de aceptación**: Con credenciales correctas, el sistema da acceso a la cuenta correspondiente. Con credenciales incorrectas, muestra un mensaje de error y deniega el acceso. Un usuario sin sesión iniciada no puede acceder a las funcionalidades protegidas.


#### R.F.02. Consulta del catálogo musical

* **Como**: Usuario
* **Quiero**: Listar las canciones, artistas y álbumes disponibles en la aplicación, y consultar las canciones asociadas a un álbum o a un artista.
* **Para**: Descubrir la música disponible en el catálogo.
* **Prueba de aceptación**: El sistema muestra las canciones, artistas y álbumes del catálogo (consulta sobre las tablas Cancion, Artista y Album). Al seleccionar un álbum o un artista, devuelve sus canciones asociadas. Si el catálogo está vacío, informa de que no hay contenido disponible. La consulta no modifica ningún dato.


#### R.F.03. Búsqueda de música

* **Como**: Usuario
* **Quiero**: Buscar canciones, artistas y álbumes por su nombre.
* **Para**: Encontrar rápidamente la música que deseo escuchar.
* **Prueba de aceptación**: Al introducir un texto, el sistema devuelve los elementos cuyo nombre coincida, diferenciando si son canciones, artistas o álbumes. Si no hay coincidencias, informa de que no se han encontrado resultados. La búsqueda no modifica ningún dato.


#### R.F.04. Reproducción y pausa de canciones

* **Como**: Usuario
* **Quiero**: Reproducir y pausar canciones del catálogo.
* **Para**: Escuchar la música disponible en la aplicación.
* **Prueba de aceptación**: Al seleccionar una canción disponible, el reproductor inicia la reproducción y muestra su título, el nombre del artista y el estado actual (reproduciendo o en pausa). El usuario puede pausar la canción en curso. Si la canción no está disponible para su reproducción, el sistema informa al usuario.


#### R.F.05. Creación de listas de reproducción

* **Como**: Usuario registrado
* **Quiero**: Crear listas de reproducción con un nombre.
* **Para**: Organizar las canciones según mis preferencias.
* **Prueba de aceptación**: El sistema crea la lista asociada al usuario autenticado y la muestra en su colección personal. No permite crear listas con nombre vacío o formado solo por espacios en blanco, y en ese caso la colección no muestra ninguna lista nueva. El usuario solo ve en su colección las listas propias.


#### R.F.06. Gestión de canciones en una lista de reproducción

* **Como**: Usuario registrado
* **Quiero:** Añadir canciones del catálogo a mis listas y eliminarlas de ellas.
* **Para**: Mantener las listas actualizadas con la música que me interesa.
* **Prueba de aceptación**: Al añadir una canción a una lista propia, esta aparece en su contenido y se conserva tras cerrar sesión y volver a iniciarla. Al eliminarla, deja de aparecer en la lista pero sigue disponible en el catálogo. El usuario no puede modificar el contenido de listas pertenecientes a otras cuentas, y estas permanecen sin cambios.


#### R.F.07. Modificación y eliminación de listas de reproducción

* **Como:** Usuario registrado
* **Quiero:** Cambiar el nombre de mis listas de reproducción o eliminarlas.
* **Para:** Mantener organizada mi colección musical.
* **Prueba de aceptación:** El sistema permite renombrar una lista propia, pero no guardar un nombre vacío. Antes de eliminar una lista solicita confirmación; tras confirmarla, la lista deja de aparecer en la cuenta del usuario. El usuario no puede modificar ni eliminar listas de otras cuentas.


#### R.F.08. Cierre de sesión####

* **Como:** Usuario autenticado
* **Quiero:** Cerrar sesión.
* **Para:** Finalizar mi acceso a la cuenta de forma segura.
* **Prueba de aceptación:** El sistema ofrece una opción de cerrar sesión. Tras usarla, el usuario deja de tener acceso a las funcionalidades que requieren autenticación y debe iniciar sesión de nuevo para volver a acceder.


  
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


