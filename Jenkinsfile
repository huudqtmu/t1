pipeline {
 agent any
 
 stages {
	stage('clone'){
		steps {
			echo 'Cloning source code'
			git branch:'main', url: 'https://github.com/huudqtmu/t1.git'
		}
	} // end clone
    stage ('Publish') {
		steps {
			echo 'public 2 runnig folder'
		//iisreset /stop // stop iis de ghi de file 
			bat 'xcopy "%WORKSPACE%" /E /Y /I /R "c:\\t1"'
 		}
	}
 
    stage('Deploy to IIS') {
            steps {
                powershell '''
               
               
                Import-Module WebAdministration
                if (-not (Test-Path IIS:\\Sites\\t1)) {
                    New-Website -Name "t1" -Port 88 -PhysicalPath "c:\\t1"
                }
                '''
            }
        } // end deploy iis

  } // end stages
}//end pipeline
