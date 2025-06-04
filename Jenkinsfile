pipeline{
  agent any
  tools{
    maven 'Maven'
  }
  stages{
    stage('checkout'){
      steps{
        git 'https://github.com/Akashmishra1421/MAWA.git'
      }
    }
    stage('build'){
      steps{
        sh 'mvn clean install'
      }
    }
    stage('archive'){
      steps{
        archiveArtifacts artifacts:'target/*.war', fingerprint: true
      }
    }
    stage('deploy'){
      steps{
        sh 'sudo ansible-playbook ansible/deploy.yml -i ansible/hosts.ini'
    }
  }
}
}
