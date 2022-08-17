pipeline{
    agent any
    stages{
	stage("Pull latest image"){
		steps{
			bat "docker-pull supernova25k/selenium-docker"
		}
	}
	stage("Start Grid"){
	    steps{
	        bat "docker-compose up -d hub chrome firefox"
		}
	    }
	stage("Run Test"){
		steps{
			bat "docker-compose up search-module book-flight-module"
		}
	}
	
    }
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			bat "docker-compose down"
		}
	}
}
