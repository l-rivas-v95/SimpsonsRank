# Simpsons Rank

Simpsons Rank es una aplicación web para consultar y puntuar personajes de Los Simpson.

El proyecto permite mostrar personajes, registrar valoraciones y generar un ranking según las puntuaciones recibidas.

## Índice

- [Descripción](#descripción)
- [Funcionalidades principales](#funcionalidades-principales)
- [Tecnologías utilizadas](#tecnologías-utilizadas)
- [Estructura del proyecto](#estructura-del-proyecto)
- [Modelo funcional](#modelo-funcional)
- [Sistema de puntuación](#sistema-de-puntuación)
- [Configuración](#configuración)
- [Ejecución del proyecto](#ejecución-del-proyecto)
- [Endpoints principales](#endpoints-principales)
- [Capturas](#capturas)
- [Posibles mejoras](#posibles-mejoras)

## Descripción

Simpsons Rank es una aplicación orientada a la gestión de un ranking de personajes de Los Simpson.

La aplicación permite consultar personajes, asignar puntuaciones y ordenar los resultados según las valoraciones registradas.

El proyecto está planteado como una aplicación sencilla para practicar la creación de una API, la organización por capas y la gestión de datos mediante una base de datos.

## Funcionalidades principales

- Consulta de personajes.
- Consulta del detalle de un personaje.
- Registro de puntuaciones.
- Cálculo de puntuación media.
- Ordenación de personajes por puntuación.
- Gestión básica de datos.
- Validaciones sobre las puntuaciones introducidas.

## Tecnologías utilizadas

- Java
- Spring Boot
- Spring Data JPA
- MySQL
- Maven
- API REST

## Estructura del proyecto

El proyecto sigue una estructura por capas:

```text
controller  -> recibe las peticiones HTTP
service     -> contiene la lógica de la aplicación
repository  -> acceso a base de datos
entity      -> entidades JPA
dto         -> objetos de entrada y salida de datos
exception   -> gestión de errores
```

Ejemplo de estructura general:

```text
src
└── main
    ├── java
    │   └── ...
    │       ├── controller
    │       ├── service
    │       ├── repository
    │       ├── entity
    │       ├── dto
    │       └── exception
    └── resources
        └── application.properties
```

## Modelo funcional

El funcionamiento básico de la aplicación es el siguiente:

1. Se registran o cargan personajes.
2. El usuario consulta el listado de personajes.
3. El usuario puede ver el detalle de un personaje.
4. El usuario asigna una puntuación.
5. La aplicación guarda la valoración.
6. El ranking se actualiza en función de las puntuaciones registradas.

## Sistema de puntuación

Cada personaje puede recibir valoraciones numéricas.

Ejemplo de escala de puntuación:

```text
1 -> puntuación mínima
5 -> puntuación máxima
```

A partir de las valoraciones registradas, se puede calcular una puntuación media para cada personaje.

Ejemplo:

```text
Homer Simpson recibe varias puntuaciones.
La aplicación calcula la media.
El personaje se ordena dentro del ranking según esa media.
```

## Configuración

La aplicación utiliza una base de datos MySQL.

La configuración principal se encuentra en:

```text
src/main/resources/application.properties
```

Ejemplo de configuración:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/simpsonsrank
spring.datasource.username=root
spring.datasource.password=

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```

Ajusta el nombre de la base de datos, usuario y contraseña según tu entorno local.

## Ejecución del proyecto

Para clonar el repositorio:

```bash
git clone https://github.com/l-rivas-v95/SimpsonsRank.git
```

Entrar en la carpeta del proyecto:

```bash
cd SimpsonsRank
```

Compilar el proyecto:

```bash
mvn clean install
```

Ejecutar la aplicación:

```bash
mvn spring-boot:run
```

La aplicación quedará disponible normalmente en:

```text
http://localhost:8080
```

## Endpoints principales

Algunos endpoints representativos del proyecto:

```text
GET    /personajes
GET    /personajes/{id}
POST   /personajes
PUT    /personajes/{id}
DELETE /personajes/{id}

GET    /ranking
POST   /valoraciones
GET    /valoraciones/personaje/{id}
```

> Los endpoints pueden variar según la implementación final del proyecto.

## Ejemplo de petición

Ejemplo de creación de una valoración:

```json
{
  "personajeId": 1,
  "puntuacion": 5
}
```

Ejemplo de respuesta de un personaje dentro del ranking:

```json
{
  "id": 1,
  "nombre": "Homer Simpson",
  "descripcion": "Personaje de la serie Los Simpson",
  "puntuacionMedia": 4.7,
  "numeroValoraciones": 15
}
```

## Capturas

Pendiente de añadir capturas de la aplicación.

Capturas recomendadas:

```text
- Listado de personajes
- Detalle de personaje
- Pantalla de valoración
- Ranking de personajes
```

## Posibles mejoras

- Añadir filtros de búsqueda por nombre.
- Añadir ordenación por puntuación.
- Añadir paginación en el listado de personajes.
- Añadir imágenes de los personajes.
- Documentar la API con Swagger/OpenAPI.
- Añadir tests unitarios.
- Añadir tests de integración.
- Mejorar la gestión global de errores.
- Añadir control para evitar puntuaciones fuera de rango.
- Añadir carga inicial de personajes.
