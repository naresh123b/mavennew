pipeline{
		 environment
			 {
			 WORKSPACE_FOLDER = "C:\\Users\\E004415\\jenkins\\ws" 
			 }
			 agent any
			     tools {
        maven 'maven'
        jdk 'javanew'
    }
			 
			 stages{
					stage('clean workspace'){
					steps {
					ws("${WORKSPACE_FOLDER}"){
						cleanWs()
						echo "WorkSpace Cleaned"}
					}
					}
							stage('Git Checkout') {
				 steps {
checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '61f67bff-a366-46ba-8350-9850dfef8d21', url: 'https://github.com/naresh123b/mavennew.git']]])
		}
					
				}
				stage('Build maven application'){
				   steps{
				         echo "Building as application"
				   }
				   }
				}
				}
