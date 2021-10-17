pipeline{
    agent {
    	label "worker"
    }
    tools {
        nodejs "nodejs"
    }
    stages{
        stage("Parallel compressing"){
            parallel{
                stage("UglifyJS"){
                    steps{
                        sh "ls www/js | xargs -I {} uglifyjs www/js/{} -co www/min/{}"
                        }
                   
                }
                stage("CleanCSS"){
                    steps{
                        nodejs(nodeJSInstallationName: "nodejs") {
                        sh "ls www/css | xargs -I {} cleancss -o www/min/{}"
                        }
                    }
                }
            }
        }
        stage("Make archives"){
            steps{
                sh "mkdir -p archives"
                sh "tar --exclude=Week2_CI_CD_tools --exclude=Week1 --exclude=.git* --exclude=www/js --exclude=www/css --exclude=archives -czvf archives/results.tgz ."
                archiveArtifacts artifacts: "archives/results.tgz", allowEmptyArchive: false, fingerprint: true, onlyIfSuccessful: true
            }
        }

        stage("Publishing"){
            steps{
                rtUpload (
                    serverId: "JFrog", spec:
                        """{
                            "files": [
                                {
                                "pattern": "archives/results.tgz",
                                "target": "default-generic-local/artifacts_${BUILD_ID}.tgz"
                                }
                             ]
                        }"""
                    )
           }
         }

    }
}