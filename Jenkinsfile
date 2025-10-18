pipeline {
    agent any

    stages {
        stage('Clonar código') {
            steps {
                git branch: 'main', url: 'https://github.com/Adrian25450/mi_proyecto_pipeline.git'
                echo 'Código clonado correctamente.'
            }
        }

        stage('Verificar archivos') {
            steps {
                sh '''
                    echo "=== ARCHIVOS EN EL REPOSITORIO ==="
                    ls -la

                    echo "=== CONTENIDO DE index.html ==="
                    if [ -f "index.html" ]; then
                        cat index.html
                    else
                        echo "No se encontró index.html"
                    fi
                '''
                echo 'Archivos verificados'
            }
        }

        stage('Simular validación') {
            steps {
                sh '''
                    echo "=== SIMULACIÓN DE VALIDACIÓN ==="
                    echo "Si PHP estuviera instalado, se validaría la sintaxis con:"
                    echo "php -l index.html"
                    echo "=== SIMULACIÓN COMPLETADA ==="
                '''
                echo 'Validación simulada'
            }
        }

        stage('Desplegar contenedor') {
            steps {
                sh '''
                    echo "=== Desplegando contenedor ==="
                    docker stop miweb_jenkins || true
                    docker rm miweb_jenkins || true
                    docker build -t miweb_jenkins .
                    docker run -d --name miweb_jenkins -p 8081:80 miweb_jenkins
                '''
                echo 'Contenedor desplegado correctamente.'
            }
        }

        stage('Completar') {
            steps {
                echo '✅ PIPELINE COMPLETADO EXITOSAMENTE'
            }
        }
    }
}
