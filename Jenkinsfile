pipeline {	
	agent {
		label {
			label "built-in"
			customWorkspace "/mnt/game"	
		}
	}
	stages {
		stage ("wsp-1") {

				steps {
					sh "mvn clean install"
					sh "systemctl start docker "
					sh "docker run -d --name tomcatserver1 tomcat"
					
					sh "docker cp /mnt/game/gameoflife-web/target/gameoflife.war tomcatserver:/usr/local/tomcat/wepapps "
					sh "chmod -R 777 /mnt/game/game-of-life "
					sh "docker exec tomcatserver bash /usr/local/tomcat/bin/startup.sh "
					sh "docker exec tomcatserver bash chmod -R 777 /usr/local/tomcat "


				}

		}
	}
}
