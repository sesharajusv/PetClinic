pipeline {
    agent any
    stages {
        stage ('Checkout Code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/sesharajusv/PetClinic.git']]])
            }
        }
		stage ( ' SonarQube Code Analysis') {
            steps {
                sh '/home/westpac/apache-maven-3.6.0/bin/mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar'
            }
        }
        stage ( 'Compile') {
            steps {
                sh '/home/westpac/apache-maven-3.6.0/bin/mvn compile'
            }
        }
        stage ( ' Test Cases') {
            steps {
                sh '/home/westpac/apache-maven-3.6.0/bin/mvn test'
            }
        }
        stage ( ' Package' ) {
            steps {
                sh '/home/westpac/apache-maven-3.6.0/bin/mvn package'
            }
        }
    }
}
