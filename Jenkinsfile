node{

                 stage('Clone repo'){
                    git branch: 'main', credentialsId: 'Githubcredentials', url: 'https://github.com/Ravitejano1/SRETASK_PRAC3.git'
                }

                stage('Maven Build'){
                def mavenHome = tool name: "Maven-3.9.0", type: "maven"
                def mavenCMD = "${mavenHome}/bin/mvn"
                sh "${mavenCMD} clean package"
                }
                
                stage('SonarQube analysis') {
                withSonarQubeEnv('Sonar-Server') {
                def mavenHome = tool name: "Maven-3.9.0", type: "maven"
                def mavenCMD = "${mavenHome}/bin/mvn"
                sh "${mavenCMD} sonar:sonar"
                }
            }
}
