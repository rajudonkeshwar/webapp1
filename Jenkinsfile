pipeline {
	agent any
	stages{	
		stage('cloning from github') {
	            steps {
	                echo 'cloning of code from git hub'
			git branch: 'main', url: 'https://github.com/rajudonkeshwar/webapp1.git'
	            }
	        }
				
		stage('FINDING THE JAVA VERSION') {
	            steps {
	                echo 'FIND THE JAVA VERSION'
			sh 'java -version'
					
	            }
	        }
				
	        stage('packaging the code using maven tool') {
	            steps {
	                echo 'packaging the code using maven tool'
			sh 'mvn clean package'
					
	            }
	        }
			
		stage('testing the code using sonar tool') {
	            steps {
	                echo 'testing the code using sonar tool'
			sh 'mvn sonar:sonar install'
					
	            }
	        }
			
		stage('upload the code in to nexus tool') {
	            steps {
	                echo 'upload the code in to nexus tool'
			sh 'mvn clean deploy'
					
	            }
	        }
			
		stage('deploying code in to tomcat-server') {
            		steps {
                	deploy adapters: [tomcat9(credentialsId: 'eb92357c-d448-44f4-987b-cde673ce15f2', path: '', url: 'http://54.221.31.8:8080/')], contextPath: 'webapp1111', war: '**/*.war'
            	}
		}	
	}
}
