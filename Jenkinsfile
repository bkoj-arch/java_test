pipeline {
  agent any
  stages {
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