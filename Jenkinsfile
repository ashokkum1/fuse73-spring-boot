def templateName = 'fuse-api'
pipeline {
    agent any
	 tools {
        maven 'M3' 
    }

	stages {
		stage('preamble') {
			steps {
				script {
					openshift.withCluster() {
						openshift.withProject('jboss') {
							echo "Using project: ${openshift.project()}"
						}
					}
				}
			}
		}
		
		
        stage('Build') {			
            steps {
				echo 'Building..'
				script {
					openshift.withCluster() {
						openshift.withProject('jboss') {
							sh 'mvn fabric8:deploy -Popenshift -Dfabric8.generator.from=registry.access.redhat.com/fuse7/fuse-java-openshift:1.3'
						}
					}
				}				
								
            }
        }
		
        
        
	}
}