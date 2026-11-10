pipeline{
    agent none
    
    stages{
        stage('build'){
            agent{
                label'buildnode'
                
            }
            steps{
                deleteDir()
                
                sh'''
                git clone https://github.com/Fawaz-123-ctl/fawu.git
                ls -la
                '''
                stash name:'webpage',includes:'fawu/**'
                
            }
        }
        stage('deploy'){
            agent{
                label'deploynode'
                
            }
            steps{
                deleteDir()
                
                unstash'webpage'
                
                sh'''
                rm -rf /var/ww/html/*
                cp -r fawu/* /var/www/html
                ls -la /var/www/html/
                '''
                
            }
        }
    }
}
