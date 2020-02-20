pipeline {
    agent any
    
    tools{
        maven 'mvn_home'
    }

    stages {
        
        stage ('Static Scan'){
            steps {
                withMaven(maven : 'mvn_home') {
                    sh 'mvn verify sonar:sonar -Dsonar.projectKey=devops-conference -Dsonar.organization=kmayer10 -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=1c413160ec451fe75e316d376b1646e73a992176'
                }
            }
        }
        
        stage ('Packaging and Distribution') {
            steps {
                withMaven(maven : 'mvn_home') {
                    sh 'mvn clean package'
                }
            }
        }
        
        stage ('Archive Artifacts') {
            steps {
                archiveArtifacts 'target/*.jar'
            }
        }
    }
}
