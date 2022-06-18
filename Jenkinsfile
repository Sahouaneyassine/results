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
            image: yasssahouane/owasp_weekly:latest
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
  stages {
        stage('Run SCAN SCRIPT OWASP') {
          
           def props = readProperties file: './my.properties', text: 'other=Override'

            steps {
       
        
            container('owaspppp') {
                
             script {
                    def exitCode = sh script: 'zap-baseline-custom.py -r 10testreport.html -g gen.conf -d -m 5 -t "${website}" --auth_auto --auth_loginurl "https://authenticationtest.com/simpleFormAuth/" --auth_username simpleForm@authenticationtest.com  --auth_password pa$$w0rd --auth_usernamefield simpleForm@authenticationtest.com  --auth_passwordfield pa$$w0rd --auth_submitfield submit ', returnStatus: true
                    
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
                              git push -f --repo=https://Sahouaneyassine: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@github.com/Sahouaneyassine/results.git --set-upstream https://Sahouaneyassine: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@github.com/Sahouaneyassine/results.git main  
'''
                
                
                
                
            }
       
        
}
        }

  }
}
