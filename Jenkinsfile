pipeline {
    agent any

    stages {
        stage('cloning code from github') {
            steps {
                git branch: 'main', url: 'https://github.com/rajudonkeshwar/webapp1.git'
            }
			}	
		stage('building code usig maven tool') {
            steps {
                       
                echo 'packaging the code using maven tool'
				sh 'mvn clean install'
				
            }
			}		
		stage('deploying code in to tomcat-server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'eb92357c-d448-44f4-987b-cde673ce15f2', path: '', url: 'http://3.81.146.17:8080/')], contextPath: 'webapp1-app', war: '**/*.war'
            }
			}			
        }
    }
