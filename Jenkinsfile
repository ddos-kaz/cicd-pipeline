pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'script scripts/build.sh'
      }
    }

    stage('Test') {
      steps {
        sh 'script scripts/test.sh'
      }
    }

    stage('Docker Publish') {
      steps {
        sh '''sudo docker build -t myjenkins-blueocean .


'''
        sh 'docker login -u damir.doszhan@gmail.com --password-stdin'
        sh '''docker tag myjenkins-blueocean doszhdam/cicd_repo:tagname
'''
        sh 'sudo docker push doszhdam/cicd_repo:tagname'
      }
    }

  }
}