pipeline {
    agent any
    parameters {
        choice(name: 'BRANCH_TYPE', choices: ['feature', 'development'], description: 'Select the branch type')
        string(name: 'BRANCH_NAME', defaultValue: '', description: 'Specify the branch name')
    }
    stages {
        stage('Checkout') {
            steps {
                script {
                    def branchPattern = "${params.BRANCH_TYPE}/.*"
                    if (params.BRANCH_NAME ==~ branchPattern) {
                        checkout([$class: 'GitSCM', branches: [[name: params.BRANCH_NAME]], userRemoteConfigs: [[url: 'git@github.com:Kibria7533/jenkins-filter-branch.git']]])
                    } else {
                        error("Branch name does not match the selected branch type pattern")
                    }
                }
            }
        }
        // Add additional stages as needed
    }
}
