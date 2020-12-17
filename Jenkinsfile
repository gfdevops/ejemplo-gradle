pipeline {
    agent any

    parameters { choice(name: 'herramienta', choices: ['gradle', 'maven'], description: '') }
    stages {
        stage('Pipeline') {
            steps {
                script {
                    
                    echo 'EJECUTANDO => '+params.herramienta
                    def ejecucion

                    if (params.herramienta == 'gradle') {
                        ejecucion = load 'gradle.groovy'
                    }else  {
                        ejecucion = load 'maven.groovy'
                        
                    }
                    ejecucion.call()
                }
            }
        }
    }
}
