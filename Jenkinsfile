pipeline {

		agent {
				label {
						label "built-in"
						customWorkspace "/mnt/project/"
				}
		}
		stages {
				stage ('cloning-project') {
								
								steps {
								
										sh "rm -rf *"
										sh "rm -rf /root/.m2/repository"
										sh "sudo git clone https://github.com/mahesh591w/project_login.git"
										
								}
				}
				stage ('build-war-file') {
								
								steps {
										sh "sudo cd /mnt/project/project_login"
										sh "sudo mvn clean install"
								}
				}
				stage ('deploy-war-on-newMachine') {
				
								steps {
								
										sh "sudo scp -o StrictHostKeyChecking=no -i /mnt/New-aws.pem /mnt/project/project_login/target/LoginWebApp.war ec2-user@172.31.39.21:/mnt/sever/apache-tomcat-9.0.87/webapps"
										
								}
				}
		}
}
