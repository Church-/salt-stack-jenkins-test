pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
      		steps {
        		salt(authtype: 'pam', clientInterface: local(arguments: '', blockbuild: true, function: 'test.ping', jobPollTime: 6, target: '*', targettype: 'glob'), credentialsId: '70b4cfb23f5cb3349a9c7a40b9fe63ceda0492cd', saveFile: true, servername: 'http://24.186.31.80:8000')
         		script {
          		env.WORKSPACE = pwd()
          		def output = readFile "${env.WORKSPACE}/saltOutput.json"
          		echo output
        		}
        	}
        }
    }
}