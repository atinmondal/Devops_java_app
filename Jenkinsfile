@Library('my-shared-library') _
pipeline{
    agent any

    stages{
        stage('Git Checkout'){
            steps{
                gitCheckout(
                    branch: "main",
                    url: "https://github.com/atinmondal/Devops_java_app.git"
                )
            }
        }

        stage('Unit test maven'){
            steps{
                script{
                    mvnTest()
                }
            }
        }
    }
}