@Library('my-shared-library') _
pipeline{
    agent any
    tools{
        jdk  'jdk11'
        maven  'maven3'
    }

    stages{

        stage('Git Checkout'){
            steps{
                gitCheckout(
                    branch: "main"
                    url: "https://github.com/atinmondal/Devops_java_app.git"
                )
            }
        }
    }
}