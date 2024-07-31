pipeline {
    agent any
    stages {
        stage ('Parallel Stage') {
            parallel {
                stage ('Before CxSAST') {
                    steps {
                        echo "Before CxSAST"
                    }
                }
                stage ('CxSAST') {
                    steps {
                        step([$class: 'CxScanBuilder',
                              configAsCode: false,
                              filterPattern: '''!**/_cvs/**/*, !**/.svn/**/*, !**/.hg/**/*, !**/.git/**/*, !**/.bzr/**/*,
                                  !**/.gitgnore/**/*, !**/.gradle/**/*, !**/.checkstyle/**/*, !**/.classpath/**/*, !**/bin/**/*,
                                  !**/obj/**/*, !**/backup/**/*, !**/.idea/**/*, !**/*.DS_Store, !**/*.ipr, !**/*.iws,
                                  !**/*.bak, !**/*.tmp, !**/*.aac, !**/*.aif, !**/*.iff, !**/*.m3u, !**/*.mid, !**/*.mp3,
                                  !**/*.mpa, !**/*.ra, !**/*.wav, !**/*.wma, !**/*.3g2, !**/*.3gp, !**/*.asf, !**/*.asx,
                                  !**/*.avi, !**/*.flv, !**/*.mov, !**/*.mp4, !**/*.mpg, !**/*.rm, !**/*.swf, !**/*.vob,
                                  !**/*.wmv, !**/*.bmp, !**/*.gif, !**/*.jpg, !**/*.png, !**/*.psd, !**/*.tif, !**/*.swf,
                                  !**/*.jar, !**/*.zip, !**/*.rar, !**/*.exe, !**/*.dll, !**/*.pdb, !**/*.7z, !**/*.gz,
                                  !**/*.tar.gz, !**/*.tar, !**/*.gz, !**/*.ahtm, !**/*.ahtml, !**/*.fhtml, !**/*.hdm,
                                  !**/*.hdml, !**/*.hsql, !**/*.ht, !**/*.hta, !**/*.htc, !**/*.htd, !**/*.war, !**/*.ear,
                                  !**/*.htmls, !**/*.ihtml, !**/*.mht, !**/*.mhtm, !**/*.mhtml, !**/*.ssi, !**/*.stm,
                                  !**/*.bin,!**/*.lock,!**/*.svg,!**/*.obj,
                                  !**/*.stml, !**/*.ttml, !**/*.txn, !**/*.xhtm, !**/*.xhtml, !**/*.class, !**/*.iml, !Checkmarx/Reports/*.*,
                                  !OSADependencies.json, !**/node_modules/**/*, !**/.cxsca-results.json, !**/.cxsca-sast-results.json, !.checkmarx/cx.config,
                                  src/include/**/*''',
                              fullScanCycle: 10,
                              groupId: '2',
                              highThreshold: 0,
                              jobStatusOnError: 'FAILURE',
                              lowThreshold: 0,
                              mediumThreshold: 0,
                              preset: '0',
                              projectName: 'jsb-cxsast-jenkins-scan-subdirectory',
                              sastEnabled: true,
                              scaReportFormat: 'PDF',
                              sourceEncoding: '1',
                              vulnerabilityThresholdEnabled: true,
                              vulnerabilityThresholdResult: 'FAILURE',
                              waitForResultsEnabled: true
                        ])
                    }
                    post {
                        failure {
                            script {
                                currentBuild.rawBuild.@result = hudson.model.Result.SUCCESS
                            }
                            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                                sh 'exit 1'
                            }
                        }
                    }
                }
                stage ('After CxSAST') {
                    steps {
                        echo "After CxSAST"
                    }
                }
            }
        }
    }
}
