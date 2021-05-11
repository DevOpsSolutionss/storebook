pipeline {
    
    agent any

        tools{
            maven 'maven'
        }
        stages
        {
            stage("git checkout")
            {
                steps
                {
                    checkout([$class: 'GitSCM', branches: [[name: '*/test']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/DevOpsSolutionss/storebook.git']]])
                }
            }
            stage("maven build")
            {
                steps
                {
                    sh 'mvn clean install package'
                }
                post
            {
                always
                {
                    junit '**/target/surefire-reports/TEST-*.xml'
                }
            }
            }
        }
    }
