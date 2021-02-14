pipeline{
    agent any
    stages{
        stage('code checkout'){
            steps{
                git credentialsId: 'github', url: 'https://github.com/yuvin-ram/my-tomcat.git'
            }
        }
        stage('code build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('code deploy'){
            steps{
                sshagent(['tomcat']){
                    sh 'scp -o StrictHostKeyChecking=no target/webapp.war ubuntu@172.31.34.221:/opt/tomcat8/webapps/'
                }
            }
        }
    }
}

