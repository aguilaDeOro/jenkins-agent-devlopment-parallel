pipeline {
    agent none
    environment {
        TEXT='Jorge y Ruth'
    }

    stages {
        stage('Paralelismo en multiples nodos') {
            parallel {
                stage('Aplicando funcion Uppercase de C') {
                    agent {
                        label 'production-c'
                    }

                    steps {
                        sh 'gcc -o uppercase uppercase.c'
                        sh "./uppercase ${TEXT}"
                    }
                }

                stage('Aplicando funcion Reverse de C') {
                    agent {
                        label 'production-c'
                    }

                    steps {
                        sh 'gcc -o reverse reverse.c'
                        sh "./reverse ${TEXT}"
                    }
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline terminado...'
        }
        success {
            echo 'completado con exito.'
        }
        failure {
            echo 'completado con errores.'
        }
    }
}