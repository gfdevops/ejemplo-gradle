
pipeline {
    agent any

    parameters { 
        choice(name: 'HERRAMIENTA', choices: ['gradle', 'maven'], description: '') 
        }

    environment {
        JENKINS_STAGE = ''
    }

    def ejecucion
    // def success_msg = "Build Success: [Gerardo Felmer][${env.JOB_NAME}]'+params.HERRAMIENTA+' Ejecución Exitosa",
    // def failure_msg = "Build Success: [Gerardo Felmer][${env.JOB_NAME}]'+params.HERRAMIENTA+' Ejecución Fallida en stage [${env.JENKINS_STAGE}]",

    stages {
        stage('Pipeline') {
            steps {
                script {
                    if (params.HERRAMIENTA == 'gradle') {
                        ejecucion = load 'gradle.groovy'
                    }else  {
                        ejecucion = load 'maven.groovy'
                    }
                    ejecucion.call()
                }
            }
        }
    }

    post {
        success {
            echo 'ENVIANDO MENSAJE SLACK '+"Build Success: [Gerardo Felmer][${env.JOB_NAME}]'+params.HERRAMIENTA+' Ejecución Exitosa"
            slackSend color: "good", message: "Build Success: [Gerardo Felmer][${env.JOB_NAME}]'+params.HERRAMIENTA+' Ejecución Exitosa"
        }
        failure {
            echo 'ENVIANDO MENSAJE SLACK '+"Build Success: [Gerardo Felmer][${env.JOB_NAME}]'+params.HERRAMIENTA+' Ejecución Fallida en stage [${env.JENKINS_STAGE}]"
            slackSend color: "danger", message: "Build Success: [Gerardo Felmer][${env.JOB_NAME}]'+params.HERRAMIENTA+' Ejecución Fallida en stage [${env.JENKINS_STAGE}]"
        }
    }
}
