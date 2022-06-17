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
	//agent {docker {image 'maven:3.8.3'}}
	environment{
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Checkout'){
			steps{
				sh 'mvn --version'
				sh 'docker version'
				echo "Build" 
			}
		}
		stage('Compile'){
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps{
				sh "mvn test"
			}
		}
		stage('Intregration Test'){
			steps{
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		stage('Package'){
			steps{
				sh "mvn package -DskipTests"
			}
		}
		stage('Docker build image'){
			steps{
			// premitive way of building docker is =====	"docker build -t thilinarat/currency-exchange-devops:$env.BUILD_TAG"
				script{
					dockerImage = docker.build("thilinarat/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}
		stage('Docker push image'){
			steps{
				script{
					docker.withRegistry('','dockerhub'){
						dockerImage.push()
						dockerImage.push('latest')
					}
				}
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
