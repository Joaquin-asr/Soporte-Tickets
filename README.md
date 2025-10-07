# HelpCore

**HelpCore** es un sistema de soporte a usuarios diseñado para centros académicos o laborales, que permite gestionar solicitudes, reportes y atención de incidencias mediante una arquitectura basada en microservicios.

---

## Objetivo

Brindar una plataforma centralizada para la gestión de tickets y soporte técnico, optimizando la comunicación entre usuarios y personal de asistencia.

---

## Arquitectura General

El proyecto está dividido en múltiples microservicios independientes que se comunican a través de un API Gateway, bajo una arquitectura basada en Spring Cloud.

---

### Back-End

Desarrollado con **Spring Boot (Java)**, utilizando microservicios para separar responsabilidades.

#### api-gateway

Gestor de las peticiones provenientes del Front-End. Se encarga de enrutar las solicitudes hacia el microservicio correspondiente, ofreciendo un punto de entrada unificado.

#### auth-service

Módulo de autenticación y autorización:

* Implementa **JWT** para sesiones seguras.
* Tokens con duración de **15 minutos**, con soporte de **refresh tokens**.
* Gestión de roles, usuarios y permisos de acceso.

#### config-server

Servicio centralizado para la configuración de todos los microservicios, sustituyendo los archivos `application.properties` por configuraciones **.yml** unificadas.

#### service-register

Implementación de **Eureka Server** para el registro y descubrimiento de microservicios, permitiendo detectar los servicios activos y su disponibilidad.

#### notification-service

Servicio encargado de la mensajería y notificaciones:

* Envío de **correos electrónicos** para confirmaciones, creación de tickets y validaciones.
* Manejo de **códigos temporales** con expiración para operaciones seguras.

#### ticket-service

Contiene la **lógica de negocio principal**:

* Creación y seguimiento de tickets.
* Gestión de respuestas y estados.
* Procesamiento de interacciones entre usuarios y personal de soporte.

---

### Front-End

El cliente web está desarrollado en **Angular**, dentro del proyecto `helpcore-fe`.
Estructura principal:

* **Servicios (Services)** para la comunicación con el back-end.
* **Interceptors** para manejo de tokens y errores HTTP.
* **DTOs e Interfaces** para la tipificación de datos.
* **Components** modulares para cada funcionalidad.
* **Environments** configurables para distintos entornos (desarrollo, producción, etc.).

---

## Base de Datos

Motor de base de datos: **MySQL**

### Esquemas utilizados

* **DB_HELPCORE_SEGURIDAD**
  Contiene datos relacionados con autenticación, roles, menús y tokens.
* **DB_HELPCORE_OPERATIVA**
  Gestiona la lógica operativa del sistema, incluyendo los tickets y su trazabilidad.

---

## Tecnologías Principales

| Capa                 | Tecnología                                             |
| -------------------- | ------------------------------------------------------ |
| Backend              | Java, Spring Boot, Spring Cloud, Eureka, Config Server |
| Frontend             | Angular                                                |
| Seguridad            | JWT, Refresh Tokens                                    |
| Observabilidad       | Grafana, OpenTelemetry, Prometheus                     |
| Base de Datos        | MySQL                                                  |
| Control de Versiones | Git / GitHub                                           |

---

## Estado del Proyecto

Versión **1.0.0 (Alpha)**
Primera versión funcional orientada a centros académicos.

---

## Contacto

**Desarrollado por:** Joaquín Suarez Romero
[joaquin.asr.16@gmail.com]

---