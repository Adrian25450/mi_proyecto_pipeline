pipeline {
    agent any

    stages {
        stage('Clonar repositorio') {
            steps {
                git 'https://github.com/Adrian25450/mi_proyecto_pipeline.git'
                echo 'Repositorio clonado correctamente.'
            }
        }

        stage('Construir imagen Docker') {
            steps {
                sh '''
                    echo "=== Construyendo imagen Docker ==="
                    docker build -t miweb_jenkins .
                '''
            }
        }

        stage('Desplegar contenedor') {
            steps {
                sh '''
                    echo "=== Desplegando contenedor ==="
                    docker stop miweb_jenkins || true
                    docker rm miweb_jenkins || true
                    docker run -d --name miweb_jenkins -p 8081:80 miweb_jenkins
                '''
            }
        }

        stage('Finalizar') {
            steps {
                echo '✅ Pipeline completado exitosamente. Visita http://localhost:8081 para ver el sitio.'
            }
        }
    }
}
