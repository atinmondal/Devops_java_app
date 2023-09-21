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
        stage('Git Checkout'){
        when { expression { params.action == 'create'}}
            steps{
                gitCheckout(
                    branch: "main",
                    url: "https://github.com/atinmondal/Devops_java_app.git"
                )
            }
        }

        stage('Unit Test Maven'){
        when { expression { params.action == 'create'}}
            steps{
                script{
                    mvnTest()
                }
            }
        }

        stage('Integration Test Maven'){
        when { expression { params.action == 'create'}}
            steps{
                script{
                    mvnIntegrationTest()
                }
            }
        }

        stage('Static code analysis: Sonarqube'){
        when { expression { params.action == 'create'}}
            steps{
                script{
                    def SonarQubeCredentialsId = 'sonarqube-api'
                    staticCodeAnalysis(SonarQubeCredentialsId)
                }
            }
        }

        stage('Quality Gate Status Check: Sonarqube'){
        when { expression { params.action == 'create'}}
            steps{
                script{
                    def SonarQubeCredentialsId = 'sonarqube-api'
                    qualityGateStatus(SonarQubeCredentialsId)
                }
            }
        }

        stage('Maven Build'){
        when { expression { params.action == 'create'}}
            steps{
                script{
                    mvnBuild()
                }
            }
        }
    }
}