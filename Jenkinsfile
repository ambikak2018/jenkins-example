pipeline {
    agent any

    stages {
        stage ('build'){
	        sh "${MVNHOME}/bin/mvn clean install"
        }
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn clean compile'
                }
            }
        }
        

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn deploy'
                }
            }
        }
    }
}
