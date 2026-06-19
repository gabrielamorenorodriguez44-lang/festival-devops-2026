[![Integración Continua - Landing Page](https://github.com/gabrielamorenorodriguez44-lang/festival-devops-2026/actions/workflows/ci.yml/badge.svg)](https://github.com/gabrielamorenorodriguez44-lang/festival-devops-2026/actions/workflows/ci.yml)

# Festival DevOps Music Fest 🎸⚡

Este proyecto consiste en el despliegue y control de versiones de una aplicación contenedorizada para la gestión de un festival de música, desarrollada en el marco de la formación de DevOps y Contenedores en el CTMA.

---

## 🛠️ Tecnologías Documentadas

### 1. Git & GitHub (Control de Versiones)
Se implementó un flujo de trabajo basado en ramas (Git Flow básico) para garantizar un desarrollo organizado y sin conflictos:
* **main:** Rama principal que contiene el código estable y listo para producción.
* **feature-landing:** Rama independiente utilizada para el desarrollo del diseño y maquetación del frontend.
* **feature-backend:** Rama dedicada a la configuración del entorno lógico y la API en Flask.

### 2. Docker (Contenedorización)
Cada componente de la aplicación se encuentra aislado en su propio entorno utilizando contenedores independientes para asegurar la portabilidad:
* **Dockerfile (Backend):** Configura la imagen base de Python, instala las dependencias necesarias mediante `requirements.txt` y expone el puerto correspondiente para la API de Flask.

### 3. Docker Compose (Orquestación Local)
Se utiliza un archivo de configuración unificado `docker-compose.yml` para gestionar el ciclo de vida de los servicios del festival de forma simultánea. Este archivo coordina de manera automatizada:
* La construcción de las imágenes de los servicios (`frontend` y `backend`).
* La asignación de puertos locales para la comunicación externa.
* La creación de redes virtuales internas para permitir el intercambio de datos seguro entre el contenedor del backend y la interfaz.
* La persistencia de datos mediante volúmenes locales.

---

## 🚀 Instrucciones de Despliegue Local

Para levantar el entorno completo del festival en tu máquina local, ejecuta el siguiente comando en la raíz del proyecto:

```bash
docker-compose up --build

## 💾 ¿Cómo guardar y subir esta documentación final?

Una vez que guardes el archivo `README.md` con este contenido en VS Code, ejecuta estas últimas líneas en tu terminal de Windows (CMD) para actualizar los cambios en GitHub:

```cmd
git add README.md
git commit -m "FASE 9: Documentación completa del proyecto en el README"
git push origin main

---

## 🔄 Integración Continua (CI) - GitHub Actions

Se ha implementado un flujo de trabajo automatizado que se ejecuta en cada evento de `push` o `pull_request` hacia la rama principal `main`. 

### Validaciones Automatizadas:
* **Entorno Virtual:** Levanta un contenedor con el sistema operativo estable `ubuntu-latest`.
* **Checkout del Código:** Descarga de forma segura el código fuente actualizado del repositorio en el servidor de compilación.
* **Validación de Estructura Mínima:** Comprueba de forma estricta la presencia de los archivos esenciales del proyecto: `frontend/index.html`, `frontend/style.css` y `README.md`. Si alguno de estos archivos falta o se encuentra mal ubicado, el flujo fallará automáticamente, notificando al equipo de desarrollo antes de integrar cambios dañados.
