pipeline {
    environment {
        TOKEN = credentials('SURGE_TOKEN')
      }
    agent {
        docker { image 'josedom24/debian-npm'
        args '-u root:root'
        }
    }
    stages {
        stage('Clone') {
            steps {
                git branch:'master',url:'https://github.com/gonzalomaring/ic-html5.git'
            }
        }
        
        stage('Install surge')
        {
            steps {
                sh 'export http_proxy=http://172.29.0.1:8888 && npm install -g surge'
            }
        }
        stage('Deploy')
        {
            steps{
                sh 'surge ./_build/ gonzalomarin.surge.sh --token $TOKEN'
            }
        }
        
    }
}
