pipeline {
    agent any
    environment{
        DIRECTORY_PATH = "/ProgramData/Jenkins/.jenkins/workspace/SIT753"
        //C:\ProgramData\Jenkins\.jenkins\workspace\SIT753
        TESTING_ENVIRONMENT = 'TEST ENV'
        PRODUCTION_ENVIRONMENT = 'FAHMIUDR'
    }
    tools {
        maven "MAVEN"
        jdk "JDK"
    }
    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from the ${DIRECTORY_PATH}."
                echo 'Compile the code and generate any necessary artifacts'
                echo 'This is a test MAVEN build working'
                sh 'mvn install' 
            }
        }
        stage('Test') {
            steps {
                echo 'Unit Test'
                echo 'Integration Test'
            }
        }
        stage('Code Quality Check') {
            steps {
                echo 'Check the quality of the code.'
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploy the application to a testing environment ${TESTING_ENVIRONMENT}"
            }
        }
        stage('Approval') {
            steps {
                sleep(time: 10, unit: 'SECONDS')
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploy to Code to the Production Environment ${PRODUCTION_ENVIRONMENT}"
            }
        }
        
        stage('Build') {
            steps {
                dir("/ProgramData/Jenkins/.jenkins/workspace/6.2C") {
                sh 'mvn -B -DskipTests clean package'
                }
            }
        }
     }
    post {
       always {
          junit(
        allowEmptyResults: true,
        testResults: '*/test-reports/.xml'
      )
      }
    }
}
