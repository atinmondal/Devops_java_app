pipeline{
    agent any
    tools{
        jdk  'jdk11'
        maven  'maven3'
    }

    stages{

        stage('Git Checkout'){
            steps{
                script{
                    git branch: 'main', changelog: false, credentialsId: 'aa25114d-9fbc-4212-ad15-50c4c96dfc60', poll: false, url: 'https://github.com/atinmondal/Devops_java_app.git'
                }

            }
        }
    }
}