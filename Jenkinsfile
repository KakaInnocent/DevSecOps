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

	stage('Docker Build and Push') {
		steps {
		sh 'printenv'
		sh 'docker build -t 741042553/numeric-app:""$GIT_COMMIT""' .'
		sh 'docker push 741042553/numeric-app:""$GIT_COMMIT""'
		}
	       }
	}
}
