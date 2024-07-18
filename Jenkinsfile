pipeline {
    agent any
    stages {
        stage('Handle Pull Request Action') {
            steps {
                script {
                    sh "env"
                    def prAction = env.action ?: 'unknown'
                    
                    if (prAction == 'opened') {
                        echo "Pull request was opened"
                        checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'git_hub', url: 'https://github.com/ramesh-h24/generic-webhook-test.git']]) 
                    } else if (prAction == 'reopened') {
                        echo "Pull request was reopened"
                        checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'git_hub', url: 'https://github.com/ramesh-h24/generic-webhook-test.git']])
                    } else if (prAction == 'closed') {
                        echo "Pull request was closed"
                        echo "No checkout activity"
                    } else {
                        echo "Unknown pull request action: $action"
                    }
                }
            }
        }
        stage('Merge to Main') {
            steps {
                script {
                    // def sourceBranch = env.BRANCH_NAME
                    // def targetBranch = 'main'
                    // sh "git checkout ${targetBranch}"
                    // sh "git pull origin ${targetBranch}"
                    // def mergeResult = sh(script: "git merge ${sourceBranch}", returnStatus: true)
                    
                    // if (mergeResult == 0) {
                    //     sh "git push origin ${targetBranch}"
                    // } else {
                    //     error("Merge conflicts detected. Please resolve manually.")
                    echo "merging to main branch"
                }
            }
        }
        stage('testing quality'){
            steps {
                script {
                    echo "checking quality of code and GE tests"
                }
            }
        }
    }
}
