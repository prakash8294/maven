pipeline
{
   agent any
   stages
   {
       stage('contdownload')
       {
           steps
           {
               git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
       stage('contbuild')
       {
           steps
           {
               sh 'mvn package'
            }
        }
       stage('contdeployment')
       {
           steps
           {
               deploy adapters: [tomcat9(credentialsId: 'd5be3b33-4a45-441f-a7f1-ce7943047530', path: '', url: 'http://172.31.93.111:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
       stage('conttesting')
       {
           steps
           {
               git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
               
               sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
           
        }
        stage('contdelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'd5be3b33-4a45-441f-a7f1-ce7943047530', path: '', url: 'http://172.31.94.63:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
   }
} 
