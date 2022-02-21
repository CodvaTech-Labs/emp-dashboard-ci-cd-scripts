pipeline {
    agent any

    stages {
        stage('Build_Infra') {
            steps {
                echo 'Emp-Dashboard-Built-Infra-Using-Terraform'
                build 'emp_dashboard_infra_deployment', parameters: [[$class: 'StringParameterValue', name: 'Env', value: "Create"]]

            }
        }
        stage('GIT Clone') {
            steps {
                echo 'GIT Clone Phase'
                sh '''#!/bin/bash
                 echo "GIT Clone" 
                 git clone https://github.com/CodvaTech-Labs/java_crud_demo.git
                '''
            }
        }
        stage('Build') {
            steps {
                echo 'Hello Build Phase'
                build 'emp_dashboard_create_build'

            }
        }
        stage('Deploy') {
            steps {
                echo 'Hello Deploy Phase'
                build 'emp_dashboard_app_deployment'
            }
        }
        
        stage('Monitoring') {
            steps {
                echo 'Hello Deploy Phase'
                build 'emp_dashboard_monitoring'
            }
        }
    }
    post { 
        always { 
            cleanWs()
        }
    }
}
