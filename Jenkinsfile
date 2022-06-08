pipeline {
  agent any
  stages {
    stage('test') {
      parallel {
        stage('test') {
          environment {
            var1 = '"bonjour"'
          }
          steps {
            sh 'touch bonjour'
            echo 'hello phase de test'
            sh 'mvn clean test'
          }
        }

        stage('build') {
          steps {
            sh 'mkdir sparkjava'
            dir(path: 'sparkjava/') {
              pwd()
            }

            git(url: 'https://github.com/kliakos/sparkjava-war-example.git', branch: 'master')
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
        sh 'echo "Fin des taches, ca s\'est bien passé"'
      }
    }

  }
}