pipeline {
  agent any
  stages {
    stage('Load') {
      steps {
        git(url: 'https://github.com/anhnguyenhoang01/jenkins.git', branch: 'origin')
        mail(subject: 'Build project A', body: 'Start build', from: 'Jenkin')
        sh '''echo "HELLO WORLD"
echo "${env.PATH}"'''
      }
    }

    stage('BUILD') {
      steps {
        build 'job'
      }
    }

    stage('DEPLOY') {
      parallel {
        stage('DEPLOY') {
          steps {
            sh 'mvn clean build'
          }
        }

        stage('ROLLBACK') {
          steps {
            sh 'echo "ROLL BACK"'
          }
        }

      }
    }

  }
}