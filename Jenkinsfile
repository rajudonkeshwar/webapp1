pipeline {
    agent any

    stages {
        stage('cloning code from github') {
            steps {
                git branch: 'main', url: 'https://github.com/rajudonkeshwar/webapp1.git'
            }
	}	

	stage('testing the code using sonar') {
            steps {
                       
                echo 'testing the code using sonar'
				sh 'mvn clean sonar:sonar install'
				
            }
	}
	    
	stage('deploying code in to tomcat-server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'eb92357c-d448-44f4-987b-cde673ce15f2', path: '', url: 'http://3.81.146.17:8080/')], contextPath: 'webapp1-app', war: '**/*.war'
            }
	}			
}
}
