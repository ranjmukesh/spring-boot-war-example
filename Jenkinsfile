pipeline {
    agent any
     tools {
        maven 'Maven' 
        }
    stages {
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                //slackSend channel: 'youtubejenkins', message: 'Job Started'
                
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
                
            }
            
        }
        stage("Deploy on Test"){
            steps{
                // deploy on container -> plugin
               // deploy adapters: [tomcat9(credentialsId: 'tomcat9servverdetails', path: '', url: 'http://192.168.44.128:8081')], contextPath: '/app', war: '**/*.war'
              echo "========Deploy on Test========"
            }
            
        }
        stage("Deploy on Prod"){
             input {
                message "Should we continue?"
                ok "Yes we Should"
            }
            
            steps{
                // deploy on container -> plugin
                // deploy adapters: [tomcat9(credentialsId: 'ssh-worker-node-2', path: '', url: 'http://192.168.44.139:8081')], contextPath: '/app', war: '**/*.war'
                echo "========Deploy on Prod========"
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
             //slackSend channel: 'youtubejenkins', message: 'Success'
        }
        failure{
            echo "========pipeline execution failed========"
            // slackSend channel: 'youtubejenkins', message: 'Job Failed'
        }
    }
}
