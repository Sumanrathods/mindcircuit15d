pipeline {
    agent any
     tools{
        maven'maven_3.9.9'
    }
     
    stages {
        stage('cloning code from git') {
            steps {
                echo 'cloning the code from the git'
				git branch: 'main', url: 'https://github.com/Sumanrathods/mindcircuit15d.git'
            }
        }
		
		
		
		stage('Build the code') {
            steps {
                echo 'Building the code from maven build tool'
				sh 'mvn clean install'
            }
        }
		
		
		
		stage('deploye the war.file') {
            steps {
                echo 'deployement of the war.file or artifactory to tomact'
				deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://52.201.239.218:8084')], contextPath: 'facebookmyapp', war: '**/*.war'
            }
        }
    }
}
