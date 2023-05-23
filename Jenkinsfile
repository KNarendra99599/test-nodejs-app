pipeline { 
  
   agent {
        docker {
            cloud('my-docker-cloud') {
                dockerHost('tcp://10.0.2.72:2375')
                // Server credentials - none -
                testConnection(true)
                errorDuration(300)
                exposeDockerHost(true)
                containerCap(5)
            }
            
            // Docker agent templates
            customWorkspace('/home/jenkins')
            label('docker')
            idleMinutes(1)
            remoteFsRoot('/home/jenkins')
            exclusive(false)
            dockerImage('jenkins-docker-slave')
            registryCredentials('jenkins/******')
            hostKeyVerificationStrategy('Non verifying Verification Strategy')
            stopTimeout(10)
            removeVolumes(false)
            pullStrategy('Never pull')
            pullTimeout(300)
        }
    }

   stages {
   
     stage('Install Dependencies') { 
        steps { 
           sh 'npm install' 
        }
     }
     
     stage('Test') { 
        steps { 
           sh 'echo "testing application..."'
        }
      }

         stage("Deploy application") { 
         steps { 
           sh 'echo "deploying application..."'
         }

     }
  
   	}

   }
