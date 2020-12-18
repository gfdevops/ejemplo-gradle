def ejecucion
def success_msg: 'Build Success: [Gerardo Felmer][${env.JOB_NAME}]'+params.HERRAMIENTA+' Ejecución Exitosa',
def failure_msg: 'Build Success: [Gerardo Felmer][${env.JOB_NAME}]'+params.HERRAMIENTA+' Ejecución Fallida en stage [${env.JENKINS_STAGE}]',

pipeline {
    agent any

    parameters { 
        choice(name: 'HERRAMIENTA', choices: ['gradle', 'maven'], description: '') 
        }

    environment {
        JENKINS_STAGE = ''
    }

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
            slackSend color: "good", message: success_msg
        }
        failure {
            slackSend color: "good", message: failure_msg
        }
    }
}
