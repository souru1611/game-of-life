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
					sh "docker run -d --name tomcatserver6 tomcat"
					sh "docker cp /mnt/game/gameoflife-web/target/gameoflife.war tomcatserver6:/usr/local/tomcat/wepapps "
					sh "chmod -R 777 /mnt/game/gameoflife-web/target/gameoflife.war "
					sh "docker exec tomcatserver6  /usr/local/tomcat/bin/./startup.sh "
					sh "docker exec tomcatserver6  chmod -R 777 tomcatserver6:/usr/local/tomcat "

				}

		}
	}
}
