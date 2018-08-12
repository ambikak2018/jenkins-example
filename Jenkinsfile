pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'Maven') {
                    bat 'mvn clean compile'
                }
            }
        }
        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'Maven') {
                    bat 'mvn test'
                }
            }
        }
        stage ('Test Cases Execution'){
		steps{
	        	bat "${MVNHOME}/bin/mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent install -Pcoverage-per-test"
		}
        }
        stage ('Archive Artifacts'){
		steps{
	        	archiveArtifacts artifacts: 'target/*.war'
		}
        }
        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'Maven') {
                    bat 'mvn deploy target/*.jar http://localhost:8080/'
                    //bat 'copy target/*.jar http://localhost:8080/'
                }
            }
        }
    }
}
