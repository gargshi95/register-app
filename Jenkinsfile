pipeline{
  agent {label 'Jenkins-Agent'}
  tools{
       jdk 'Java17'
       maven 'Maven3'
  }
  stages{
    stage('Cleanup workspace'){
            steps {
          cleanWs()
          }
    }
    stage('Checkout from SCM'){
            steps {
          git branch: 'main', credentialsId: 'github', url: 'https://github.com/gargshi95/register-app'
          }
    }
      stage('Build Application'){
          steps {
          sh "mvn clean package"
          }
    }
      stage('Test application'){
          steps {
          sh "mvn test"
          }
    }
      stage('SonarQube Analysis'){
          steps {
             script {
                 withSonarQubeEnv(credentialsId: 'jenkins-sonarqube-token')
                 sh "mvn sonar:sonar"
          }
      }
    }    
  }
}
