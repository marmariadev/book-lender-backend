# book-lender-backend

## Introducción

Este proyecto es un sistema de backend para una aplicación de gestión de bibliotecas, diseñado para ayudar a los bibliotecarios a gestionar libros y autores, y a los usuarios a prestar y devolver libros. Proporciona una API RESTful para una integración con aplicaciones de frontend.

## Tecnologías utilizadas

- TypeScript: Aporta tipado estático, mejorando la seguridad y legibilidad.
- Node.js: Entorno de ejecución para JavaScript en el servidor.
- Express.js: Framework para construir la API REST de forma eficiente.
- TypeORM: Facilita la interacción con la base de datos PostgreSQL.
- PostgreSQL: Gestiona los datos de la aplicación de manera relacional.

## Historias de usuario

- **Como bibliotecario, quiero añadir nuevos libros al sistema** para mantener actualizado el inventario de la biblioteca.
- **Como bibliotecario, quiero listar todos los libros disponibles** para ver qué libros hay en la biblioteca.
- **Como bibliotecario, quiero actualizar la información de los libros** para corregir errores o actualizar datos.
- **Como bibliotecario, quiero eliminar libros** que ya no están disponibles o son obsoletos.
- **Como bibliotecario, quiero registrar nuevos autores en el sistema** para asociarlos con sus respectivos libros.
- **Como bibliotecario, quiero ver una lista de todos los autores** para facilitar la búsqueda de sus libros.
- **Como usuario, quiero registrar un préstamo de libro** para llevar libros a casa.
- **Como usuario, quiero devolver un libro** para evitar multas y que otros lo puedan prestar.
- **Como bibliotecario, quiero ver todos los préstamos activos** para gestionar las devoluciones y multas.

## Esquema de Base de Datos

#### book

- `id` INT, PRIMARY KEY
- `title` VARCHAR
- `publication_year` INT
- `copy_count` INT
- `author_id` INT, FOREIGN KEY to author

#### author

- `id` INT, PRIMARY KEY
- `first_name` VARCHAR
- `last_name` VARCHAR
- `nationality` VARCHAR

#### loan

- `id` INT, PRIMARY KEY
- `loan_date` DATE
- `return_date` DATE, nullable
- `book_id` INT, FOREIGN KEY to book
- `user_id` INT, FOREIGN KEY to user
- `status` ENUM('active', 'returned')

#### user

- `id` INT, PRIMARY KEY
- `name` VARCHAR
- `email` VARCHAR

### Relationships

- **author** can have multiple **books** (One to Many).
- **book** can have multiple **loans** (One to Many).
- **user** can have multiple **loans** (One to Many).
