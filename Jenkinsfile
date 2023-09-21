@Library('my-shared-library') _
pipeline{
    agent any
    tools{
        jdk  'jdk11'
        maven  'maven3'
    }

    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'Choose Create/Destroy')
    }

    stages{
        when { expression { param.action == 'create'}}
        stage('Git Checkout'){

            steps{
                gitCheckout(
                    branch: "main",
                    url: "https://github.com/atinmondal/Devops_java_app.git"
                )
            }
        }

        stage('Unit Test Maven'){
        when { expression { param.action == 'create'}}
            steps{
                script{
                    mvnTest()
                }
            }
        }

        stage('Integration Test Maven'){
        when { expression { param.action == 'create'}}
            steps{
                script{
                    mvnIntegrationTest()
                }
            }
        }

        stage('Static code analysis: Sonarqube'){
        when { expression { param.action == 'create'}}
            steps{
                script{
                    staticCodeAnalysis()
                }
            }
        }
    }
}