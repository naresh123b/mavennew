pipeline{
		 environment
			 {
				 HOME = "E004415"
				 WORKSPACE_FOLDER = "C:\\Users\\env.HOME\\jenkins\\ws" 
			 RUN_FOLDER       = "C:\\Users\\env.HOME\\jenkins"
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
				 ws("${WORKSPACE_FOLDER}"){
checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '61f67bff-a366-46ba-8350-9850dfef8d21', url: 'https://github.com/naresh123b/mavennew.git']]])
		}
		}
					
				}
				stage('Build maven application'){
				   steps{
				   ws("${WORKSPACE_FOLDER}"){
				         echo "Building an application"
						 bat label: '', script: 'mvn install'}
				   }
				}
				stage('Move maven application'){
				   steps{
				   ws("${WORKSPACE_FOLDER}"){
				         echo "Moving an application"
						 bat label: '', script: '''cd ..
del messageUtil-2.0-SNAPSHOT.jar
cd ws\\target
move messageUtil-2.0-SNAPSHOT.jar C:\\Users\\E004415\\jenkins
'''}
                   
				   ws("${RUN_FOLDER}"){
				         echo "Running an application"
						 bat label: '', script: 'java -jar messageUtil-2.0-SNAPSHOT.jar &'
                   
				   }
				}
				}
				}
				}
