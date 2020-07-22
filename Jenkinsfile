pipeline {

agent any

tools {
        maven 'maven'
}

stages {
       stage('checking maven installation'){
          steps {
                   sh 'mvn -v'
                }
       }
        stage('security checking by trufflehog'){
                steps{
                        sh 'docker run  --rm  gesellix/trufflehog --json  https://github.com/Rohitkulkarni15/day3rohitdevsecopsjsp.git  >mybugs.txt'
			sh 'cat mybugs.txt'

                }
        }
	stage('vulnerability scan by sonar'){
		steps{
			withSonarQubeEnv('sonar'){
				sh 'mvn sonar:sonar'
				sh 'cat target/sonar/report-task.txt'
			
			}

	}
       stage('build java project'){
          steps {
                   sh 'mvn clean package'
                }
       }


}
}
