pipeline {
	agent {
		label '4336'
}
   parameters {
        choice(name: 'Azure_Parameters', choices:"Azure\nERL", description: "Do you whish to do grab parameters?" )
        }

 stages {
    stage('Git Clone') {
        steps {
        git branch: 'master', changelog: true, url: 'https://github.com/varampati6/readjson.git'
        sh "ls"
    }
        
    }

    stage('Azure') {
	   steps {
            script {
            //    def projects = readJSON file: "${env.WORKSPACE}/azure.json"
		def projects = readFile(file: "${env.WORKSPACE}/azure.json")
                if ("${params.Azure_Parameters}" == "Azure") {
                    echo "current workspace is ${env.WORKSPACE}"
                   // echo "Project name is ${projects.projects.project[1].name}"
		     echo "Project name is ${projects.project.name}"
                    
                    }
                }
            } 
		}
    stage('ERL') {
	    
	   steps {
            script {
              //  def projects = readJSON file: "${env.WORKSPACE}/erl.json"
		def projects = readFile(file: "${env.WORKSPACE}/erl.json")
                if ("${params.Azure_Parameters}" == "ERL") {
                    echo "current workspace is ${env.WORKSPACE}"
                  //  echo "Project name is ${projects.projects.project[1].name}"
                    
                    }
                }
            } 
		}
	}

}
