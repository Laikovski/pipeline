pipeline {
  agent any
  stages {
    stage('BizzBazz') {
      steps {
        echo 'test text'
      }
    }

    stage('Bees') {
      steps {
        echo 'Buzz, Bees, Buzz!'
      }
    }

    stage('tests') {
      parallel {
        stage('tests') {
          steps {
            sh 'sleep 10'
            echo 'messgae after 10 s'
          }
        }

        stage('unit tests') {
          steps {
            echo 'simple unit tests'
          }
        }

      }
    }

    stage('deploy') {
      steps {
        sleep 10
        echo 'Finish all'
      }
    }

    stage('exec_script') {
      steps {
        input(message: 'Continie to Deploy', ok: 'Yes')
        sh 'echo $PWD'
        archiveArtifacts(artifacts: 'target/*.jar', fingerprint: true)
      }
    }

  }
}