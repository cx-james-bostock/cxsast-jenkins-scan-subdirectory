pipeline {
    agent any
    stages {
        stage ('CxSAST') {
            steps {
                step([$class: 'CxScanBuilder',
                      comment: '',
                      configAsCode: false,
                      credentialsId: 'checkmarx-user',
                      customFields: '',
                      excludeFolders: '',
                      exclusionsSetting: 'job',
                      failBuildOnNewResults: true,
                      failBuildOnNewSeverity: 'LOW',
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
                      groupId: '1',
                      highThreshold: 0,
                      jobStatusOnError: 'FAILURE',
                      lowThreshold: 0,
                      mediumThreshold: 0,
                      preset: '0',
                      projectName: 'cxsast-jenkins-scan-subdirectory',
                      sastEnabled: true,
                      scaReportFormat: 'PDF',
                      serverUrl: 'http://ip-172-35-1-213.ec2.internal',
                      sourceEncoding: '1',
                      username: '',
                      vulnerabilityThresholdEnabled: true,
                      vulnerabilityThresholdResult: 'FAILURE',
                      waitForResultsEnabled: true
                ])
            }
        }
        stage ('Test') {
            steps {
                echo "Test stage"
            }
        }
    }
}
