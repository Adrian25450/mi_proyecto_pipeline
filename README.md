🚀 Proyecto CI/CD con Jenkins y Docker
Este proyecto automatiza el despliegue de una página web simple utilizando Jenkins, Docker y GitHub. A través de un pipeline definido en Jenkins, se construye una imagen Docker y se despliega un contenedor que expone el sitio web en el navegador del dispositivo anfitrión.

📁 Estructura del repositorio
Código
mi_proyecto_pipeline/
├── Dockerfile
├── Jenkinsfile
├── index.html
└── README.md
🧩 Requisitos previos
Docker y Docker Compose instalados

Git instalado

Acceso a GitHub

Jenkins ejecutándose en un contenedor Docker

⚙️ Configuración del entorno
Clona este repositorio:

bash
git clone https://github.com/Adrian25450/mi_proyecto_pipeline.git
cd mi_proyecto_pipeline
Usa el siguiente archivo docker-compose.yml para levantar Jenkins:

yaml
version: '3.8'

services:
  jenkins:
    container_name: jenkins-php
    image: jenkins/jenkins:2.462.1-lts-jdk21
    ports:
      - "8080:8080"
      - "50000:50000"
    volumes:
      - jenkins_data:/var/jenkins_home
      - /var/run/docker.sock:/var/run/docker.sock
      - /usr/bin/docker:/usr/bin/docker
    user: root
    restart: unless-stopped

volumes:
  jenkins_data:
Levanta Jenkins:

bash
docker-compose up --build -d
🛠️ Archivos clave
index.html: Página web que se desplegará en el contenedor

Dockerfile: Define la imagen basada en php:8.2-apache y copia el contenido al servidor web

Jenkinsfile: Define el pipeline con las siguientes etapas:

Clonar código desde GitHub

Verificar archivos

Simular validación

Construir imagen Docker

Desplegar contenedor

Finalizar

🧪 Crear el pipeline en Jenkins
Accede a Jenkins en http://localhost:8080

Crea un nuevo proyecto tipo Pipeline

En la configuración:

Selecciona Pipeline script from SCM

Tipo de SCM: Git

URL del repositorio: https://github.com/Adrian25450/mi_proyecto_pipeline.git

Rama: main

Script path: Jenkinsfile

🚀 Ejecutar el pipeline
Haz clic en Build Now

El pipeline ejecutará todas las etapas y desplegará el contenedor

Abre tu navegador en http://localhost:8081 para ver la página web

✅ Resultado esperado
Una vez completado el pipeline, deberías ver en tu navegador:

¡Hola desde Jenkins y Docker! 🚀 Proyecto automatizado de Adrián Pedroza Marín.
