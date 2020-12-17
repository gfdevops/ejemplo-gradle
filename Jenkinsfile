pipeline {
    agent any

    parameters { choice(name: 'herramienta', choices: ['gradle', 'maven'], description: '') }
    stages {
        stage('Pipeline') {
            steps {
                script {
                    
                    echo params.herramienta
                    def ejecucion

                    if (params.herramienta == 'gradle') {
                        echo 'ejecutando ejecucion.call() para GRADLE'
                        ejecucion = load 'gradle.groovy'
                    }else  {
                        echo 'ejecutando ejecucion.call() para MAVEN'
                        ejecucion = load 'maven.groovy'
                        
                    }
                    echo 'before'
                    ejecucion.call()
                    echo 'after'

                }
            }
        }
    }
}
