pipeline {
    agent {label 'centos'}
    stages {
        stage('download') {
            steps {
                sh '''
                ls
                echo "hola"
                echo $prueba
                pwd
                ls -lrt
                echo $password
                pwd
                uname
                docker ps
                hostname
                touch 1
                '''
            }
        }
        stage('compilar') {
            steps {
                sh '''
                cd /ome/devops/workspace/academia
                pwd
                docker run --rm --name my-maven-project -v "$(pwd)":/usr/src/mymaven -w /usr/src/mymaven maven:3.3-jdk-8 mvn clean install
                '''
            }
        }
        stage('deployar') {
            steps {
                sh '''
                cd /home/devops/workspace/academia
                docker cp /home/devops/workspace/academia/target/sparkjava-hello-world-1.0.war tomcat://usr/local/tomcat/webapps
                '''
            }
        }
    }
}
