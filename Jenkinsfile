pipeline {
    agent any

    stages {
        stage('Pipeline') {
            steps{
                script{
                    stage("Build & test") {
                        sh "./gradlew clean build"
                        sh "./gradlew clean build"
                    }
                    stage("Sonar") {
                            def scannerHome = tool 'sonar-scanner';
                            withSonarQubeEnv('sonar-server') { // If you have configured more than one global server connection, you can specify its name
                            sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=ejemplo-gradle -Dsonar.java.binaries=build"
                    }
                    stage("Run") {
                        sh 'gradlew bootRun &'
                        sleep 20
                    }
                    stage("Rest") {
                        sh "curl -X GET 'http://localhost:8085/rest/mscovid/test?msg=testing'"
                    }
                    stage("Nexus") {
                        nexusPublisher nexusInstanceId: 'nexus', nexusRepositoryId: 'test-repo', 
                        packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: 'jar', 
                        filePath: 'build/libs/DevOpsUsach2020-0.0.1.jar']], 
                        mavenCoordinate: [artifactId: 'DevOpsUsach2020', groupId: 'com.devopsusach2020', packaging: 'DevOpsUsach2020', version: '1.0.0']]]
                    }
                }
            }
        }
    }
}
}
