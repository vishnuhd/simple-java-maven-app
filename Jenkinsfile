pipeline {
	agent any
    stages {
        stage('Build') {
            steps {
                powershell 'mvn -B -e -DskipTests clean package'
            }
        }
		stage('Test') {
            steps {
                powershell 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
		stage('Deliver') {
            steps {
                powershell ('''
				$Name = (ls .\target\*.jar).Name 
				java -jar $Name
				''')
            }
        }
    }
}
