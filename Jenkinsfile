pipeline {
    agent any
    tools {
        maven "Maven_Home"
        }
    stages {
        stage('Checkout') {                       
            steps{
            git credentialsId: 'git_Credentials', url: 'https://github.com/Shubham4676/war-web-project.git'
                echo 'Checkout Success'
            }
        }
        
        stage('MavenBuild') {
            steps{
            sh 'mvn clean install'
                echo 'Build Success'
            }
        }
        
        stage('Deploy') {
            steps{
        sshagent(['deploy_user']) {
        
        sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/CICDJOB-2/target/wwp-1.0.0.war  ec2-user@52.53.195.59:/opt/apache-tomcat-9.0.84/webapps"
                echo 'Deploying Success'  
            }
                
            }
        }
    }
}
