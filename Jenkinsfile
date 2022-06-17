//SCRIPTED
// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('Intregration Test') {
// 		echo "Intregration Test"
// 	}
// }

//DECLARATIVE
pipeline {
	//agent any
	agent {docker {image 'maven:3.8.3'}}
	stages{
		stage('Build'){
			steps{
				sh 'mvn --version'
				echo "Build" 
			}
		}
			stage('Test'){
			steps{
				echo "Test"
			}
		}
			stage('Intregration Test'){
			steps{
				echo "Intregration Test"
			}
		}
	}
	post{
		always{
			echo "Run always"
		}
		success{
			echo "Run on success"
		}
		failure{
			echo "Run on failure"
		}
	}
}
