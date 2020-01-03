pipeline{
		 environment
			 {
			 WORKSPACE_FOLDER = "C:\\Users\\E004415\\jenkins\\ws" 
			 RUN_FOLDER       = "C:\\Users\\E004415\\jenkins"
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
				stage('Publish artifacts to remote server and run application'){
				   steps{
				   ws("${WORKSPACE_FOLDER}"){
				         sshPublisher(publishers: [sshPublisherDesc(configName: 'ansible', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '''cd /home/taxadmin/jenkinsnew/target
java -jar messageUtil-2.0-SNAPSHOT.jar > outout.txt &''', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'target/*.jar')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])}
                   
				}
				}
				}
				}
