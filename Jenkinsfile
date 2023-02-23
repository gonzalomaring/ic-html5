pipeline {
    environment {
        TOKEN = credentials('SURGE_TOKEN')
      }
    agent {
        docker { image 'gonzalomarin/taller2'
        args '-u root:root'
        }
    }
    stages {
        stage('Clone') {
            steps {
                git branch:'master',url:'https://github.com/gonzalomaring/ic-html5.git'
            }
        }
        
        stage('Deploy')
        {
            steps{
                sh 'export http_proxy=http://172.29.0.1:8888 && surge ./_build/ gonzalomarin.surge.sh --token $TOKEN'
            }
        }
        
    }
}
