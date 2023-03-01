node{

                 stage('Clone repo'){
                    git branch: 'main', credentialsId: 'Githubcredentials', url: 'https://github.com/Ravitejano1/SRETASK_PRAC3.git'
                }

                stage('Maven Build'){
                    def mavenHome = tool name: "Maven-3.9.0", type: "maven"
                    def mavenCMD = "${mavenHome}/bin/mvn"
                    sh "${mavenCMD} clean package"
                }
                
                stage('SonarQube analysis'){
                  withSonarQubeEnv('Sonar-Server-9.6'){
                    def mavenHome = tool name: "Maven-3.9.0", type: "maven"
                    def mavenCMD = "${mavenHome}/bin/mvn"
                    mvn sonar:sonar \ 
                    -Dsonar.host.url=http://18.119.120.1:9000 \
                    -Dsonar.login="admin" 
                     Dsonar.password="admin123"\
                    -Dsonar.projectKey="SRETASK_PRAC3" --batch-mode --quiet 
                   }
       }
 }
