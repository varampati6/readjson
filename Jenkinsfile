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
	   when { expression { "${params.Environment}" == "azure" }  }
//	if ("${params.Azure_Parameters}" == "Azure")
	   steps {
            script {
		def projects = readFile(file: '/jenkins/4336/workspace/SINGULARITY_TEAM/Testing/readfiles/azure.json') 
		//def projects = readFile(file: "${env.WORKSPACE}/azure.json"  ) 
	//	    def projects = readFile file: "${env.WORKSPACE}/azure.json"
           //     if ("${params.Azure_Parameters}" == "Azure") {
                    echo "current workspace is ${env.WORKSPACE}"
		    sh "cat ${env.WORKSPACE}/azure.json"
		    if (manager.logContains('.*Master.*')) {
			    echo ' MasterData'
		    }
		     
                  //  echo "Project name is ${projects.projects.project[1].name}"
		 //   echo "Project name is ${projects.projects.project[1].name}"
		    
		     
                    }
             //   }
            } 
	}
  }
 }
