pipeline {
    agent { label "agentA" }
    
    triggers {
        pollSCM('* * * * *')
    }    

    stages {
        stage('clone') {
            steps {
                echo 'clone the project'
                git branch: 'main', url: 'https://github.com/Gavimass/Flipkart_shop.git'
            }
        }
         stage('copying') {
            steps {
                echo 'verify the project where it is cloned'
                sh 'pwd'
                sh 'ls'
            }
        }
         stage('deploying to httpd') {
            steps {
                echo 'copying the files'
                sh 'scp -i /home/ec2-user/key.pem -r /var/jenkins/workspace/pipeline_project_task/* ec2-user@18.143.118.175:/var/www/html'
                
            }
        }
        stage('deploy') {
            steps {
                echo 'check the deploy'
            }
        }
    }
}
