pipeline {
    agent any

    parameters{
        string(name: 'ARTIFACTORY_SERVER', defaultValue: 'repo-name')
        string(name: 'ARTIFACTORY_URL', defaultValue: '')
        string(name: 'MAVEN_TOOL', defaultValue: 'mmaven')
        password(name: 'username', defaultValue:'SECRET')
        password(name: 'password', defaultValue:'SECRET')
    }

    tools{
        maven params.MAVEN_TOOL
    }
    environment {
        JFROG_CLI_BUILD_NAME = "${env.JOB_NAME}"
        JFROG_CLI_BUILD_NUMBER = "${env.BUILD_NUMBER}"
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            when{
                expression{
                    BRANCH_NAME == 'master'
                }
            }
            steps {
                echo 'Deploying....'
            }
        }
    }
}