pipeline {
    agent any

    parameters{
        string(name: 'ARTIFACTORY_SERVER', defaultValue: 'repo-name')
        string(name: 'ARTIFACTORY_URL', defaultValue: '')
        string(name: 'MAVEN_TOOL', defaultValue: 'mvn')
        password(name: 'username', defaultValue:'SECRET')
        password(name: 'password', defaultValue:'SECRET')
    }

    tools{
        maven 'Maven 3.6.3'
        jdk 'jdk9'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
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