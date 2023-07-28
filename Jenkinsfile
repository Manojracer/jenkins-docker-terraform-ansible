pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        script{
                def mvnHome = tool name: 'MAVEN_HOME', type: 'maven'
                sh "${mvnHome}/bin/mvn package"
        }
      }
    }
    stage('Building Docker Image') {
      steps{
        script {
          sh "docker build -t manojracer/cicd-poc-jenkins-cicdprojectdamo:$BUILD_NUMBER ."
        }
      }
    }
    stage('Push Image To Docker Hub') {
      steps{
        script {
          sh "echo $USER"
          sh "docker login -u manojracer -p Manojmano@6"
          sh "docker push manojracer/cicd-poc-jenkins-cicdprojectdamo:$BUILD_NUMBER"
          }
        }
      }
    }
}

