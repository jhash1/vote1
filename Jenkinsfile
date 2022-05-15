pipeline {

    agent any
    
    tools{
       maven 'Maven 3.6.1'
    }

    stages{
        stage('worker-build'){
            echo 'Compiling worker app'
            dir('worker'){
            sh 'mvn compile'
            }
        }
    
        stage('worker-item-test'){
            echo 'Running Unit tests on worker app'
            dir('worker'){
  	    sh 'mvn clean test' 
            }
        }   
        stage('worker package'){
            echo 'Packaging worker app'
 	    dir('worker'){
            sh 'mvn package -DskipTests'
            }
        }
    }
}  

post {
    always{
        archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true 
        echo "Build pipeline for the worker is complete.."
    }
}
