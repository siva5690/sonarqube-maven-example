pipeline {
  agent any

  environment {
    MAVEN_SETTING = '/root/.m2/settings.xml'
  }

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/siva5690/sonarqube-maven-example.git'
      }
    }

    stage('Build') {
      steps {
        sh "/usr/local/maven/bin/mvn clean package"
      }
    }

    stage('SonarQube Test') {
      steps {
            sh "/usr/local/maven/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=webapp -Dsonar.projectName='webapp' -Dsonar.host.url=http://35.167.240.135:9000 -Dsonar.token=sqp_16f3bf972f5f2df553ccf743c4119edb20008b5c"
        }
      }
    

    stage('Artifact Upload') {
      steps {
        sh "/usr/local/maven/bin/mvn clean deploy -s $MAVEN_SETTING" 
              }
    }
  }
}
