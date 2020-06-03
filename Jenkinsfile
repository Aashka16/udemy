Skip to content
Search or jump to…

Pull requests
Issues
Marketplace
Explore
 
@Aashka16 
Learn Git and GitHub without any code!
Using the Hello World guide, you’ll start a branch, write comments, and open a pull request.


Aashka16
/
udemy
1
00
 Code
 Issues 0
 Pull requests 0 Actions
 Projects 0
 Wiki
 Security 0
 Insights
 Settings
udemy/Jenkinsfile
@Aashka16 Aashka16 Update Jenkinsfile
e669453 now
43 lines (39 sloc)  1.08 KB
  
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



