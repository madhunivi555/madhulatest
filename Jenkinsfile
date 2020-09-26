pipeline {
    agent any
    stages {
        stage ('SCM Checkout') {
            steps {
                git credentialsId: 'github', url: 'https://github.com/madhunivi555/madhulatest.git'
            }
        }
        stage ('Build Code') {
            steps {
                sh 'mvn clean'
            }    
        }
        stage ('Test') {
            steps {
                sh 'mvn test'
            }    
        }
        stage ('Compile') {
            steps {
                sh 'mvn compile'
            }    
        }
        stage ('Package') {
            steps {
                sh 'mvn package'
            }    
        }
        stage ('Deploy war file in to Apache tomcat') {
            steps {
                 sshagent(['pop']) {
        sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war root@192.168.20.20:/opt/apache-tomcat-7.0.96/webapps'
                 }
            }    
       }
   }
}    
