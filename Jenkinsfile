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
		    withDockerRegistry([credentialsId: "docker-hub", url: ""]) {
		        sh 'printenv'
			sh 'docker build -t 741042553/numeric-app:""$GIT_COMMIT"" .'
			sh 'docker push 741042553/numeric-app:""$GIT_COMMIT""'
			}
		}  
	}

	stage("Mutation Tests - PIT") {
	    steps {
	        sh "mvn org.pitest:pitest-maven:mutationCoverage"
		}
	     post {
	         always {
		     pitmutation mutationStatsFile: '**/target/pit-reports/**/mutations.xml'
		     }
		  }
         }
	
	}
	//always add after mutation stage
	stage('SonarQube - SAST'){
		steps {
			sh "mvn sonar:sonar -Dsonar.projectKey=numeric-application Dsonar.host.url=http://mambo-ops.eastus.cloudapp.azure.com/ -Dsonar.login={REPLACE_ME}"
		}
	}
}

