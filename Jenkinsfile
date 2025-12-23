pipeline {
    agent any
    environment {
        project = 'expense'
        component = 'backend'
        appVersion = ''
        ACC_ID = '854681582083'
    }
    options {
        disableConcurrentBuilds()
        timeout(time: 30, unit: 'MINUTES')
    }

     parameters{
        booleanParam(name: 'deploy', defaultValue: false, description: 'Toggle this value')
    }

    stages {
        stage('read version'){
            steps {
                script {
                    def packageJson = readJSON file: 'package.json'
                    appVersion = packageJson.appVersion
                    echo " app version is: $appVersion"
                }
            }
        }

        stage('install dependency') {
            steps {
                script {
                    sh """
                        npm install
                    """
                }
            }
        }

        // stage('Run Sonarqube') {
        //     environment {
        //         scannerHome = tool 'sonar-scanner-7.1';
        //     }
        //     steps {
        //       withSonarQubeEnv('sonar-scanner-7.1') {
        //         sh "${scannerHome}/bin/sonar-scanner"
        //         // This is generic command works for any language
        //       }
        //     }
        // }
    }


}