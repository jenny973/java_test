pipeline {
  agent none
  stages {
    stage('test') {
      parallel {
        stage('test') {
          steps {
            sh 'touch bonjour'
            echo 'Hello phase de test'
            sh 'mvn clean test'
          }
        }

        stage('build') {
          environment {
            JAVA_HOME = '/usr/lib/java-8-openjdk'
          }
          steps {
            sh 'git clone https://github.com/kliakos/sparkjava-war-example.git'
            sh 'cd sparkjava-war-example'
            sh 'mvn clean install'
            archiveArtifacts 'target/*.war'
          }
        }

      }
    }

    stage('reports') {
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }

    stage('end') {
      steps {
        sh 'echo"fin des taches, ça s\'est bien passé"'
      }
    }

  }
}