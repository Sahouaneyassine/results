pipeline {
  agent {
    kubernetes {
      yaml '''
        apiVersion: v1
        kind: Pod
        metadata:
          name: owasppnew66
        spec:
          volumes:
            - name: task-pv-storage1
              persistentVolumeClaim:
                claimName: task-pv-claim3
          podRetention: "never"
          containers:
          - name: owaspppp
            image: yasssahouane/owasp_test:latest
            workspaceVolume: hostPathWorkspaceVolume(hostPath:"/home/jenkins/agent/remoting/test")
            command:
            - sleep
            args:
            - 99d
            imagePullPolicy: IfNotPresent
            ports:
            - containerPort: 9090
            volumeMounts:
                - mountPath: "/zap/wrk"
                  name: task-pv-storage1
        '''
    }
  }
  environment {
        GIT_PUSH_REPORT = credentials('k8s')
        
    }
  stages {
    stage('READ PROPERTIES'){
      steps{
        script{
          def props = readProperties file: './my.properties', text: 'other=Override'
        }
      }
    }
        stage('Run SCAN SCRIPT OWASP') {
          

            steps {
                 
       
        
            container('owaspppp') {
                
             script {
               
                    def props = readProperties file: './my.properties', text: 'other=Override'
                    def test = sh script : " echo ${props.auth_loginurl} "
                    def exitCode = sh script: """ zap-baseline-custom.py -r ${props.name_report} -g gen.conf -d -m 5 -t ${props.website} --auth_auto  --auth_loginurl ${props.auth_loginurl} --auth_username ${props.auth_username}   --auth_password ${props.auth_password}    --key_field_username ${props.key_field_username} --key_field_password ${props.key_field_password} --key_field_submit ${props.key_field_submit} --key_field_first_submit ${props.key_field_first_submit} --submit_button_input ${props.submit_button_input} --value_field_username ${props.value_field_username} --value_field_password ${props.value_field_password} --value_field_submit ${props.value_field_submit} --value_field_first_submit ${props.value_field_first_submit}  """, returnStatus: true
                    
                    if (exitCode == 2) {
                        sh 'echo "At least one WARN and no FAILs" '
                    }
                    else if (exitCode == 1){
                        sh 'echo "At least 1 FAIL"'
                    }
                    else if (exitCode == 3) {
                        sh 'echo "Any other failure"'
                    }
                    else if (exitCode == 0) {
                        sh 'echo "Nothing found"'
                    }
                    else {
                        currentBuild.result = 'FAILURE'
                        throw(error)
                    }
                    
                    
                }
                
             
}
               
               
              }
                   
        }
        stage('Get REPORT') {
            steps {
            container('owaspppp') {
                
                sh 'cp -R /zap/wrk /home/jenkins/agent/workspace/sdqs'
                sh 'cd /zap/wrk'
                sh 'ls'
                sh '''git config --global --add safe.directory /home/jenkins/agent/workspace/sdqs
                              git config --global user.email "sahouaneyassine1999@gmail.com"
                              git config --global user.name "yassine"
                              git init
                              git add .
                              git commit -m "second commit"
                              git checkout -b main
                              git branch -M main
                              git remote add origin1 https://github.com/Sahouaneyassine/results.git
                              git push -f --repo=https://Sahouaneyassine:$GIT_PUSH_REPORT@github.com/Sahouaneyassine/results.git --set-upstream https://Sahouaneyassine:$GIT_PUSH_REPORT@github.com/Sahouaneyassine/results.git main  
'''
                
                
                
                
            }
       
        
}
        }

  }
}
