import groovy.json.JsonSlurperClassic

def jsonParse(def json) {
    new groovy.json.JsonSlurperClassic().parseText(json)
}
pipeline {
    agent any
    stages {
        stage("Paso 1: Saludar"){
            steps {
                script {
                env.STAGE='Paso 1: Saludar'
                sh "echo 'Hello, World Usach!'"
                }
            }
            post{
                failure{
                    slackSend color: 'danger', message: "[Francisca Olave] - Ejecucion fallida en stage [${env.STAGE}]"
                }
            }
        }
        stage("Paso 2: Crear Archivo"){
            steps {
                script {
                env.STAGE='Paso 2: Crear Archivo'
                sh "echo 'Hello, World Usach!!' > hello-devops-usach-.txt"
                }
            }
            post{
                failure{
                    slackSend color: 'danger', message: "[Francisca Olave] - Ejecucion fallida en stage [${env.STAGE}]"
                }
            }
        }
        stage("Paso 3: Guardar Archivo"){
            steps {
                script {
                env.STAGE='Paso 3: Guardar Archivo'
                tsh "echo 'Persisitir Archivo!'"
                }
            }
            post{
                failure{
                    slackSend color: 'danger', message: "[Francisca Olave] - Ejecucion fallida en stage [${env.STAGE}]"
                }
            }
        }
    }
    post {
            always {
                    slackSend color: '#ADD8E6', message: "[Francisca Olave] - [Acceso a al job (<${env.BUILD_URL}|Open>)"
                }
            success {
                    slackSend color: 'good', message: "[Francisca Olave] - [Rama: ${env.JOB_NAME}][Stage: ${env.BUILD_NUMBER}][Resultado: Success]- (<${env.BUILD_URL}|Open>)"
                }
            failure {
                    slackSend color: 'danger', message:"[Francisca Olave] - [Rama: ${env.JOB_NAME}][Stage: ${env.BUILD_NUMBER}][Resultado: Failed]- (<${env.BUILD_URL}|Open>)"
                }
    }
}
