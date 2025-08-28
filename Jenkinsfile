pipeline {
    agent any
 
    stages {
        stage('Compile') {
            steps {
                echo "Hello compile Stage"
                sh 'mvn compile'
            }
        }
     stage('test') {
            steps {
                echo "Hello test Stage"
                sh 'mvn test'
            }
        }   
     stage('package') {
            steps {
                echo "Hello Package Stage"
                sh 'mvn package'
            }
        } 
     stage('deploy') {
            steps {
                echo "Hello deploy Stage"
                sh 'java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App'
            }
        } 
    }
}
