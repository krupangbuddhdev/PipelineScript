pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                echo "Building the checked out project"
                sh '/home/codeware/shell_script/build.sh'
            }
        }
        stage('Unit-Test') { 
            steps {
                echo "Running Unit Tests"
                sh '/home/codeware/shell_script/unit.sh'
            }
        }
        stage('Quality-Gate') { 
            steps {
                echo "Verifying Quality Gates"
                sh '/home/codeware/shell_script/quality.sh'
            }
        }
        stage('Deploy') { 
            steps {
                echo "Deploying to stage environments for more tests!"
                sh '/home/codeware/shell_script/deploy.sh'
            }
        }
    }
    post {
        always {
            echo "This will always run"
        }
        success {
            echo "This will run only if successful"
        }
        failure {
            echo "This will run only if failed"
        }
        unstable {
            echo "This will run only if the run was marked as unstable"
        }
        changed {
            echo "This will run only if the state of pipeline has changed"
            echo "For example, if the pipeline was previously failing but is now successful"
        }
    }
}
