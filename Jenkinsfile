pipeline {
    agent {
        label 'master'
    }
    stages {
        
        stage('Build') {            
            steps {                
                git credentialsId: '9fb25843-b4e1-4bbd-87e0-180bde56d5e0', url: 'http://10.186.122.166/jiangyinjie/test.git'
            }        
        }        
        stage('Test') {            
            steps {                
                echo 'Testing'            
            }        
        }
        stage('Deploy - Staging') {            
            steps {                
                withMaven(maven: 'maven') {
                    sh "mvn clean package"
                }     
            }        
        }
        stage('Deploy - Staging1') {
            steps {                
                    sh "docker run -d --name test3 hello-world"   
            }        
        } 
    }
    post {        
        always {            
            echo 'One way or another, I have finished'            
        }        
        success {            
            echo 'I succeeeded!'        
        }        
        unstable {            
            echo 'I am unstable :/'        
        }        
        failure {            
            echo 'I failed :('        
        }        
        changed {            
            echo 'Things were different before...'        
        }    
    }
}