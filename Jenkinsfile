pipeline {
	agent {
		label 'master'
}
   
   parameters {
            choice(name: 'Azure_Parameters', choices:"Azure", description: "Do you whish to do Azure grab parameters?" )
			choice(name: 'Azure_Parameters', choices:"erl", description: "Do you whish to do erl grab parameters?" )
            
    }

 stages {
    stage('Git Clone') {
        steps {
        git branch: 'master', changelog: true, credentialsId: 'sanu-bitbucket-credentials', url: 'https://ustr-bitbucket-1.na.uis.unisys.com:8443/scm/~satyadas/read_json_file.git'
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
