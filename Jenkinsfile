pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
		sh '/usr/share/maven/bin/mvn package'
            }
        }
        stage('test') {
            steps {
                echo 'Building..'
		sh '/usr/share/maven/bin/mvn test'
            }
        }
        stage('delopy') {
            steps {
                echo 'Deploying....'
		sshagent(['Deploy_user']) {
		sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/jenkins-pipe/target/webapp-0.2.war centos@3.83.100.92:/home/centos/apache-tomcat-7.0.94/webapps"
		 }
            }
        }
    }
}
