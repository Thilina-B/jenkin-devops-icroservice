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
	agent any
	stages{
		stage('Build'){
			steps{
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
}
