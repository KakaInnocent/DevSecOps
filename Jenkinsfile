pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' //so that they can be downloaded later
            }
        }
	//Adding a test case stage with jacoco line counting 
	stage('Unit Test') {
	steps {
		sh "mvn test"
		}
		post {
			always {
				junit 'target/surefire-reports/*.xml'
				jacoco execPattern: 'target/jacoco.exec'
			}
		}
	}
    }
}
