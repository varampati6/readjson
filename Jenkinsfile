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
        git branch: 'master', changelog: true, url: 'https://ustr-bitbucket-1.na.uis.unisys.com:8443/scm/~satyadas/read_json_file.git'
        sh "ls"
    }
        
    }

    stage('Project Name') {
	    
	   steps {
            script {
                def projects = readJSON file: "${env.WORKSPACE}/azure.json"
                if ("${params.Azure_Parameters}" == "Azure") {
                    echo "current workspace is ${env.WORKSPACE}"
                    echo "Project name is ${projects.projects.project[1].name}"
                    
                    }
                }
            } 
		}
		
	    stage('Project Name') {
	    
	   steps {
            script {
                def projects = readJSON file: "${env.WORKSPACE}/erl.json"
                if ("${params.Azure_Parameters}" == "erl") {
                    echo "current workspace is ${env.WORKSPACE}"
                    echo "Project name is ${projects.projects.project[1].name}"
                    
                    }
                }
            } 
		}
	}

}
