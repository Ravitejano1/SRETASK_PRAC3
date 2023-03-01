node{

                 stage('Clone repo'){
                    git branch: 'main', credentialsId: 'Githubcredentials', url: 'https://github.com/Ravitejano1/SRETASK_PRAC3.git'
                }

                stage('Maven Build'){
                    def mavenHome = tool name: "Maven-3.9.0", type: "maven"
                    def mavenCMD = "${mavenHome}/bin/mvn"
                    sh "${mavenCMD}/bin/mvn clean package"
                }
                
                stage('SonarQube analysis'){
                  withSonarQubeEnv('Sonar-Server-9.6'){
                    def mavenHome = tool name: "Maven-3.9.0", type: "maven"
                    def mavenCMD = "${mavenHome}/bin/mvn"
                   sh "${mavenCMD}/bin/mvn sonar:sonar'
                   }
       }
 }
