pipeline {
    agent any
    tools {nodejs "node17.8"}
    environment{
        NODE_ENV='production'
    }

    stages {
        stage('source') {
            steps {
                git 'https://github.com/JayDevOps1016/aws_codebuild_codedeploy_nodeJs_demo.git'
                
                echo 'index.js file content'
                sh 'cat index.js'
            }
        }
        
         stage('build') {
            steps {
                echo NODE_ENV
                withCredentials([string(credentialsId: 'c2ee9f7c-677b-4f25-b534-0e0b67dfaf9b', variable: 'secver')]) {
    // some block
                    echo 'this is secrect value'
                    echo secver
                }
               sh 'npm install'
            }
        }
        
         stage('archiveArtifacts-save') {
            steps {
              archiveArtifacts artifacts: '**', followSymlinks: false
            }
        }
    }
}
