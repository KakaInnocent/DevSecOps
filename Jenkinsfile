pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' //so that they can be downloaded later
            }
        }
	//Adding a test case stage 
	stage('Unit Test') {
	steps {
		sh "mvn test"
		}
	}
    }
}