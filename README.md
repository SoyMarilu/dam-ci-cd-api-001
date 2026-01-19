# API REST con Spring Boot y CI/CD en AWS Elastic Beanstalk


Este proyecto implementa una API REST básica utilizando **Spring Boot 3** y **Java 17**, integrada en un flujo completo de DevOps. El objetivo principal es demostrar la automatización del ciclo de vida del software mediante **Integración Continua (CI)** y **Despliegue Continuo (CD)** utilizando GitHub Actions y AWS.

## 📋 Tabla de Contenidos
- [Arquitectura del Flujo CI/CD](#-arquitectura-del-flujo-cicd)
- [Tecnologías Utilizadas](#-tecnologías-utilizadas)
- [Requisitos Previos](#-requisitos-previos)
- [Ejecución en Local](#-ejecución-en-local)
- [Endpoints Disponibles](#-endpoints-disponibles)
- [Despliegue en AWS](#-despliegue-en-aws)

## 🚀 Arquitectura del Flujo CI/CD

El pipeline automatizado sigue la siguiente secuencia cada vez que se realiza un `push` a la rama `main`:

1.  **GitHub Actions (CI):**
    * Descarga el código.
    * Configura el entorno con **Java 17 (Amazon Corretto)**.
    * Ejecuta los tests unitarios y compila el proyecto con Maven (`mvn clean package`).
2.  **Empaquetado:**
    * Genera un archivo `.zip` que contiene el JAR ejecutable y un `Procfile` para la configuración de Elastic Beanstalk.
3.  **AWS Elastic Beanstalk (CD):**
    * Despliega automáticamente el artefacto en el entorno de producción en la nube.

## 🛠 Tecnologías Utilizadas
* **Lenguaje:** Java 17 (Amazon Corretto)
* **Framework:** Spring Boot 3.x
* **Gestor de Dependencias:** Maven (con Maven Wrapper)
* **Control de Versiones:** Git & GitHub
* **Orquestación CI/CD:** GitHub Actions
* **Nube:** AWS Elastic Beanstalk (Entorno Java SE)

## ⚙️ Requisitos Previos
Para ejecutar este proyecto localmente necesitas:
* Java JDK 17 instalado.
* Maven (opcional, se incluye el wrapper `mvnw`).
* Git configurado.

## 💻 Ejecución en Local

1.  **Clonar el repositorio:**
    ```bash
    git clone [https://github.com/TU_USUARIO/TU_REPO.git](https://github.com/TU_USUARIO/TU_REPO.git)
    cd TU_REPO
    ```

2.  **Compilar y Ejecutar:**
    ```bash
    ./mvnw spring-boot:run
    ```

3.  **Verificar:**
    Abre tu navegador en `http://localhost:8080`.

## 📡 Endpoints Disponibles

La API expone los siguientes recursos públicos:

| Método | Ruta | Descripción |
| :--- | :--- | :--- |
| `GET` | `/` | Mensaje de bienvenida confirmando la ejecución. |
| `GET` | `/api/estado` | Devuelve un JSON con el estado del servicio, nombre del servicio y mensaje de sistema. |

**Ejemplo de respuesta `/api/estado`:**
```json
{
  "estado": "OK",
  "mensaje": "API operativa",
  "servicio": "dam-ci-cd-api-001"
}
