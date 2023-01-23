pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
		sh 'mvn clean package'
            }
        }
        stage('test') {
            steps {
                echo 'test..'
		sh 'mvn test'
            }
        }
        stage('delopy') {
            steps {
                echo 'deploying....'
		sshagent(['deploy_user']) {
		sh "scp /var/lib/jenkins/workspace/Jenkins-CI-CD/target/webapp-0.2.war centos@34.213.144.128:/home/centos/apache-tomcat-11.0.0-M1/webapps"
		 }
            }
        }
    }
}
