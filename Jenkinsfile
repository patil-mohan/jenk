node{

   def tomcatWeb = 'C:\\Users\\mohan.patil\\Desktop\\my_jenkins\\demo_app\\ebix_asg_sb'
   def jbossBin = 'C:\\IndusJDE\\jboss-eap-7.1\\bin'
   /* def tomcatStatus = '' */
   stage('SCM Checkout'){
     git 'https://github.com/patil-mohan/demo_app.git'
       withCredentials([gitUsernamePassword(credentialsId: 'git_credentials_2023', gitToolName: 'Default')]) {
  bat 'git submodule update --init --recursive'
	}
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      bat "${mvnHome}/bin/mvn package"
      }
   /*
   stage('Deploy to Jboss'){
     bat "copy target\\JenkinsWar.war \"${tomcatWeb}\\JenkinsWar.war\""
   }*/
 
   stage('Deploy to JBoss') { 
            steps {
                sh 'cp C:/Users/mohan.patil/.jenkins/workspace/demo_pipeline/ebixproject.war C:/IndusJDE/jboss-eap-7.1/standalone/deployments/ebixproject.war'
            } 
        }
   stage ('Start JBoss Server') {
         sleep(time:5,unit:"SECONDS") 
         bat "${jbossBin}\\standalone.bat"
         sleep(time:100,unit:"SECONDS")
   }
        
   }
