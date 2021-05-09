pipeline {
    agent { label 'nodo' }
    stages {
        stage('download') {
            steps {
                sh '''
                ls
                echo "hola"
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
                cd /home/prueba/workspace/prueba2
                docker run -it --rm --name my-maven-project -v "$(pwd)":/usr/src/mymaven -w /usr/src/mymaven maven:3.3-jdk-8 mvn clean install
                '''
            }
        }
        stage('deployar') {
            steps {
                sh '''
                cd /home/prueba/workspace/prueba2
                docker cp /home/prueba/workspace/prueba2/target/sparkjava-hello-world-1.0.war 8c9062f5eb4d://usr/local/tomcat/webapps
                '''
            }
        }
    }
}