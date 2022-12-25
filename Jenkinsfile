pipeline {
    agent any
    triggers { pollSCM('* * * * *')}
    stages {
        stage('Checkout'){
            steps {
                git branch: 'main', credentialsId: 'davidingle_github_key', url: 'https://github.com/davidingle/jgsu-spring-petclinic.git'
            }
        }
        stage('Build') {
            steps {
                bat './mvnw clean package'
            }

            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
