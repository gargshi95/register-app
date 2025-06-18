pipeline{
  agent {label 'Jenkins-Agent'}
  tools{
       jdk 'Java17'
       maven 'Maven3'
  }
  stages{
    stage('Cleanup workspace'){
          step{
          cleanWs()
          }
    }
    stage('Checkout from SCM'){
          step{
          git branch: 'main', credentialsId: 'github', url: 'https://github.com/gargshi95/register-app'
          }
    }
      stage('Build Application'){
          step{
          sh "mvn clean package"
          }
    }
      stage('Test application'){
          step{
          sh "mvn test"
          }
    }
      
  }
}
