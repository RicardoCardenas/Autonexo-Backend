# AutoNexo

Backend de **AutoNexo**, una plataforma para la **gestión integral del mantenimiento vehicular**, desarrollada con **Java y Spring Boot**, que expone una **API REST** orientada a la administración de usuarios, vehículos, inventario y solicitudes de mantenimiento.

El proyecto está diseñado bajo una **arquitectura modular basada en Bounded Contexts**, siguiendo principios de **Domain-Driven Design (DDD)**, lo que permite una clara separación de responsabilidades, alta mantenibilidad y escalabilidad del sistema.

---

## Tecnologías Utilizadas

- **Java 21**
- **Spring Boot**
- **Spring Web**
- **Spring Data JPA**
- **Spring Security**
- **JWT (JSON Web Tokens)** para autenticación y autorización
- **MySQL** como base de datos relacional
- **Swagger / OpenAPI** para documentación de la API
- **BCrypt** para hashing de contraseñas
- **Maven** para gestión de dependencias
- **Azure Web Application** (despliegue previo)
- **Git / GitHub** para control de versiones

---

## Arquitectura del Proyecto

AutoNexo sigue una **arquitectura basada en DDD**, organizada en **Bounded Contexts**, donde cada contexto encapsula su propio dominio, lógica de negocio y persistencia.

### Capas principales

- **Interfaces (Presentation Layer)**
  - Controladores REST
  - Exposición de endpoints HTTP

- **Application Layer**
  - Casos de uso
  - Servicios de aplicación
  - Orquestación de la lógica de negocio

- **Domain Layer**
  - Entidades
  - Reglas de negocio
  - Servicios de dominio

- **Infrastructure Layer**
  - Persistencia (JPA / MySQL)
  - Seguridad (JWT, hashing, autorización)
  - Integraciones técnicas

Esta estructura permite:
- Bajo acoplamiento
- Alta cohesión
- Facilidad para escalar o extender funcionalidades

---

## Bounded Contexts

### Vehicles Context
Gestiona la información relacionada con los vehículos registrados en la plataforma.

**Responsabilidades:**
- Registro de vehículos
- Asociación de vehículos a usuarios
- Consulta y gestión del estado del vehículo

---

### Maintenance Requests Context
Encargado de las solicitudes y el historial de mantenimiento.

**Responsabilidades:**
- Creación de solicitudes de mantenimiento
- Seguimiento del estado del servicio
- Registro histórico de mantenimientos

---

### Inventory Context
Administra los recursos y repuestos asociados al mantenimiento vehicular.

**Responsabilidades:**
- Gestión de inventario
- Disponibilidad de repuestos
- Asociación de recursos a mantenimientos

---

### User Context
Gestiona la información de los usuarios del sistema y sus mecanismos de acceso a la plataforma.

**Responsabilidades:**
- Registro y gestión de usuarios
- Gestión de roles (conductores, mecánicos, administradores)
- Asociación de usuarios con vehículos y solicitudes
- Autenticación y autorización de usuarios mediante JWT

Este contexto incluye un módulo de **infraestructura de seguridad**, encargado de la implementación técnica de:
- Generación y validación de tokens JWT
- Hashing de contraseñas con BCrypt
- Filtros y configuración de Spring Security

---

## Autenticación y Seguridad

El sistema utiliza **JWT (JSON Web Tokens)** para asegurar los endpoints privados.

### Características de seguridad:

- Hashing de contraseñas con **BCrypt**
- Generación de tokens Bearer JWT
- Validación de tokens en cada request protegido
- Separación clara de responsabilidades en el módulo de seguridad

### Flujo de autenticación:

1. El usuario inicia sesión
2. El backend valida credenciales
3. Se genera un JWT
4. El cliente envía el token en el header: `Authorization: Bearer <token>`
5. Spring Security valida el token antes de permitir el acceso

---

## Base de Datos

AutoNexo utiliza **MySQL** como sistema de base de datos relacional, accedido mediante **Spring Data JPA**.

### Repositorios principales:

- `UserRepository`
- `DriverRepository`
- `MechanicRepository`

La base de datos permite mantener integridad referencial y consistencia en las relaciones entre usuarios, vehículos y mantenimientos.

---

## Documentación de la API (Swagger)

La API REST está documentada con **Swagger / OpenAPI**, lo que permite:

- Visualizar todos los endpoints disponibles
- Probar solicitudes directamente desde el navegador
- Consultar modelos de datos y respuestas

Ruta local: http://localhost:8080/swagger-ui

---

## Despliegue en Azure

El backend fue desplegado previamente utilizando **Azure Web Applications**.

### Características del despliegue:

- Build del proyecto con Maven
- Configuración de variables de entorno
- Conexión a base de datos MySQL
- Preparado para despliegue continuo

> Actualmente, la aplicación **no se encuentra activa en Azure**, pero la arquitectura y configuración permiten su redepliegue sin cambios estructurales.

---

## Estado del Proyecto

- Arquitectura base implementada
- Seguridad y autenticación funcional
- API documentada
- Preparado para escalabilidad futura


