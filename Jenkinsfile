pipeline{
		 environment
			 {
			 WORKSPACE_FOLDER = "C:\\Users\\E004415\\jenkins\\ws" 
			 }
			 agent any
			 
			 stages{
					stage('clean workspace'){
					steps {
					ws("${WORKSPACE_FOLDER}"){
						cleanWs()
						echo "WorkSpace Cleaned"}
					}
					}
					
				}
				}
