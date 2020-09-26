node {
    stage ('SCM Checkout') {
        git credentialsId: 'github', url: 'https://github.com/madhunivi555/madhulatest.git'
    }
    stage ('Build Code') {
        sh 'mvn clean package'
    }
    stage ('Deploy war file in to Apache tomcat') {
        sshagent(['pop']) {
        sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war root@192.168.20.20:/opt/apache-tomcat-7.0.96/webapps'
       }
    }
}
