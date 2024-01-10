pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                script {
                    checkout([$class: 'GitSCM', branches: [[name: 'main']], userRemoteConfigs: [[url: 'https://github.com/KBeKind/course3-jenkins-gs-spring-petclinic.git']]])
      
                }
            }
        }

        stage('build') {
            steps {
                script {
                    sh './mvnw package'
                }
            }
        }

        stage('capture') {
            steps {
                script {
                    archiveArtifacts artifacts: '**/target/*.jar'
                    junit '**/target/surefire-reports/TEST*.xml'
                }
            }
        }
    }
}
