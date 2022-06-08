pipeline {
  agent any
  stages {
    stage('test') {
      steps {
        sh 'touch bonjour'
        echo 'Hello phase de test'
        sh 'mvn clean test'
      }
    }

    stage('reports') {
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }

    stage('end') {
      steps {
        sh 'echo "fin des taches, ça s\'est bien passé"'
      }
    }

  }
}