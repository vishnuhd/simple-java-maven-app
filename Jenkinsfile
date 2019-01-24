pipeline {
    stages {
        stage('Build') {
            steps {
                powershell 'mvn -B -DskipTests clean package'
            }
        }
    }
}
