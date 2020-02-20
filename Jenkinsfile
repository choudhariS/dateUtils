pipeline {
    agent any
    
    tools{
        maven 'mvn_home'
    }

    stages {
        
        stage ('Static Scan'){
            steps {
                sh 'chmod 777'
                sh './script.sh'
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
