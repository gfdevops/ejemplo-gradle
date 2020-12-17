pipeline {
    agent any

    parameters { choice(name: 'herramienta', choices: ['gradle', 'maven'], description: '') }
    stages {
        stage('Pipeline') {
            steps {
                script {
                    
                    echo params.herramienta

                    if (params.herramienta == 'gradle') {
                        def ejecucion = load 'gradle.groovy'
                        ejecucion.call()
                    }else if (params.herramienta == 'maven')  {
                        def ejecucion = load 'maven.groovy'
                        ejecucion.call()
                    }
                }
            }
        }
    }
}
