pipeline {
    agent any

    parameters { choice(name: 'herramienta', choices: ['gradle', 'maven'], description: '') }
    stages {
        stage('Pipeline') {
            steps {
                script {
                    
                    echo params.herramienta

                    if (params.herramienta == 'gradle') {
                        echo 'ejecutando ejecucion.call() para GRADLE'
                        def ejecucion = load 'gradle.groovy'
                        ejecucion.call()
                    }else  {
                        echo 'ejecutando ejecucion.call() para MAVEN'
                        def ejecucion = load 'maven.groovy'
                        ejecucion.call()
                    }
                }
            }
        }
    }
}
