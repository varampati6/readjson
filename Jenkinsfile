pipeline {
  agent { label '4336' }
  environment {
  def projects = readFile file: "${env.WORKSPACE}/azure.json"
  }
  parameters {
	choice(name: 'Environment', choices: 'Azure\nERL', description: 'What Config Environment Files should be used?')
	}
  stages {
   stage('Git Clone') {
        steps {
        git branch: 'master', changelog: true, url: 'https://github.com/varampati6/readjson.git'
        sh "ls"
		}
     }
  
   stage('Project Name') {
	     when {
    expression {
    //    return env.BRANCH_NAME != 'master';
	    return "${params.Azure_Parameters}" == "Azure";
        }
    }
//	if ("${params.Azure_Parameters}" == "Azure")
	   steps {
            script {
          //      def projects = readJSON file: "${env.WORKSPACE}/azure.json"
           //     if ("${params.Azure_Parameters}" == "Azure") {
                    echo "current workspace is ${env.WORKSPACE}"
                    echo "Project name is ${projects.projects.project[1].name}"
                    
                    }
             //   }
            } 
	}
  }
 }
