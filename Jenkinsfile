pipeline {
  agent { label '4336' }
//  environment {
 // def projects = readFile file: "${env.WORKSPACE}/azure.json"
//  def projects = readJSON file: '/jenkins/4336/workspace/SINGULARITY_TEAM/Testing/readfiles/azure.json'
//  }
  parameters {
	choice(name: 'Environment', choices: 'azure\nERL', description: 'What Config Environment Files should be used?')
	}
  stages {
   stage('Git Clone') {
        steps {
        git branch: 'master', changelog: true, url: 'https://github.com/varampati6/readjson.git'
        sh "ls"
		}
     }
  
   stage('Project Name') {
	   when { expression { "${params.Environment}" == "Azure" }  }
//	if ("${params.Azure_Parameters}" == "Azure")
	   steps {
            script {
		   def deployConfig = null
                def projects = readFile(file: '/jenkins/4336/workspace/SINGULARITY_TEAM/Testing/readfiles/azure.json') 
		//def projects = readFile(file: "${env.WORKSPACE}/azure.json"  ) 
	//	    def projects = readFile file: "${env.WORKSPACE}/azure.json"
           //     if ("${params.Azure_Parameters}" == "Azure") {
                    echo "current workspace is ${env.WORKSPACE}"
                  //  echo "Project name is ${projects.projects.project[1].name}"
		 //   echo "Project name is ${projects.projects.project[1].name}"
		    
		     echo "Readingg ${params['Environment']}.json"
		  try {deployConfig = readJSON file: "${params['Environment']}.json" }
		    catch (Exception e) {
            // sendErrorMessageToHipchat("Cannot read deploy_${params['CAMUNDA_ENV']}.json property: deployment<br>Error:<br>${e}")
            error("Cannot read ${params['Environment']}.json property: deployment\nError:\n${e}")
          }
                    }
             //   }
            } 
	}
  }
 }
