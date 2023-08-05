pipeline{
	agent any
	stages{
		stage('1-version control'){
			steps{
				checkout scmGit(branches: [[name: '(main|feature|develop.*)']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-id', url: 'https://github.com/akudogithub/jenkins-multibranch3.git']])
			}
		}
		stage('2-code build'){
			steps{
				sh 'lscpu'
			}
		} 
		stage('parallel-job1'){
			parallel{
				stage('sub-job-code'){
					steps{
						sh 'lsblk'
					}
				}
				stage('sub-job-sast'){
					when{
						branch 'develop'
					}
					steps{
						sh 'id ubuntu'
					}
				}	
				stage('sub-job-dast'){
					when{
						branch 'feature'
					}
					steps{
						sh 'cal'
					}
				}
			}
		}
		stage('3-code-acceptance test'){
			steps{
				sh 'date'
			}
		}
		stage('4-code-deploy'){
			when{
				branch 'main'
			}
			steps{
				sh 'uptime'
			}
		}
		stage('5-deployment-test'){
			steps{
				sh 'sort -r /etc/passwd'
			}
		}
		stage('parallel-job2'){
			parallel{
				stage('sub-job-unit-test'){
					steps{
						sh 'pwd'
					}
				}
				stage('sub-job-final-test'){
					steps{
						sh 'id jenkins'
					}
				}
			}
		}
		stage('6-uat'){
			steps{
				sh 'uptime'
			}
		}
		stage('prod'){
			steps{
				sh 'wc -c /etc/passwd'
			}
		}
	}
}