pipeline {
    agent any
    
    environment {
        PYENV_HOME = '/var/lib/jenkins/.pyenv' // Path to pyenv home directory
        PATH = "${PYENV_HOME}/shims:${PATH}"
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from your version control system
                git 'https://github.com/kdhani/python.git'
            }
        }
        
        stage('Install PyBuilder and Build') {
            steps {
                // Install PyBuilder
                sh 'pip install pybuilder'
                
                // Build the project using PyBuilder, X= verbose
                sh 'pyb -X'
            }
        }
        
        stage('Run Tests') {
            steps {
                // Run tests using PyBuilder
                sh 'pyb test'
            }
        }
        
        stage('Static Analysis') {
            steps {
                // Perform static code analysis using PyBuilder, to edit analysis modify build.py in project
                sh 'pyb analyze'
            }
        }
        
        stage('Package') {
            steps {
                // Package the project using PyBuilder
                sh 'pyb publish'
            }
        }
}
