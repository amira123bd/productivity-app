pipeline {
    agent any
    environment {
        SONAR_SCANNER_HOME = tool 'sonar-scanner'
       
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        /* stage('OWASP Scan') {
            steps {
                dependencyCheck additionalArguments: '--scan ./ ', odcInstallation: 'OWASP Dependency-Check Plugin'*/
               // dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            /*}
        } */
        stage('Sonarqube Analysis') {
            steps {
                withSonarQubeEnv('sonar-server'){
                   sh ''' $SONAR_SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=MiniProjet  -Dsonar.sources=.  -Dsonar.host.url=http://localhost:9000 -Dsonar.login=squ_4b3840e043593d352dbb4a4528815048bb1bfb3f '''
               }
            }
        }
    }
}
