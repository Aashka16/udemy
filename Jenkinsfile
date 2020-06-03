pipeline {
   agent any

   stages {
      stage('maven build') {
         steps {
             script{
             def maven= tool 'M2_HOME'
             sh """
                echo $maven
                cd webapp;$maven/bin/mvn clean test package
             """
             }
         }
      }
	  stage ('sonarq test) 
	    steps {
                build job: 'project sonarqube_test'
				}
      stage('upload the artifactory'){
            steps{
                script{
                    sh """
                    pwd
                    """
                        retry(3){
                            
                            rtUpload (
                            serverId: "jfrog-server",
                            spec:
                                """{        
                                "files": [
                        {
                             "pattern": "webapp/target/*.war",
                                "target": "MyProject"
                               }
                            ]  
                        }"""
                               )
                       }
                    }
                }    
            }
        }
    }



