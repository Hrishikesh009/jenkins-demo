pipeline{
  agent any

  tools{
      maven 'Maven'
      jdk 'Java'
  }

  environment{
    APP_NAME= "jenkins-demo"
  }

  stages{

    stage('Clone'){
        steps{
              echo "Cloning repo...."
              git branch: 'main' , url: 'https://github.com/Hrishikesh009/jenkins-demo.git'
        }
    }

    stage('Verify tools'){
        steps{
              sh 'echo versions of java and maven........'
              sh 'mvn -version'
              sh 'java -version'
        }
    }

    stage('Build'){
        steps{
              echo "Building Project......"
              sh 'mvn clean package'
        }
    }

    stage('Test'){
        steps{
              echo "Running tests......"
              sh 'mvn test'
        }
    }

    stage('Deploy'){
        steps{
              echo 'Deploying.......'
              sh 'echo Deployment success'
        }
    }

  }

  post{

      success {
              echo "Build Succeeded!"
              archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
      }

      failure{
              echo "Build failed"
      }

  }

}
