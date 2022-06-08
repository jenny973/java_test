pipeline {
  agent none
  stages {
    stage('test') {
      parallel {
        stage('test') {
          steps {
            sh 'ls'
            echo '"Hello world"'
            sh 'mvn clean test'
            git(url: 'https://github.com/jenny973/java_test.git', branch: 'main')
          }
        }

        stage('build') {
          steps {
            sh 'mkdir sparkjava'
            dir(path: 'sparkjava/') {
              pwd()
            }

            git 'https://github.com/kliakos/sparkjava-war-example'
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
        sh 'echo"fin des etapes"'
      }
    }

  }
}