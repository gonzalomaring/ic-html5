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
                sh 'surge ./_build/ gonzalomarin.surge.sh --token $TOKEN'
            }
        }
        
    }
}
