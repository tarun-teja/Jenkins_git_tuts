handleCheckout = {
    if (env.gitlabMergeRequestId) {
        sh "echo 'Merge request detected. Merging...'"
        def credentialsId = scm.userRemoteConfigs[0].credentialsId
        checkout ([
            $class: 'GitSCM',
            branches: [[name: "${env.gitlabSourceNamespace}/${env.gitlabSourceBranch}"]],
            extensions: [
                [$class: 'PruneStaleBranch'],
                [$class: 'CleanCheckout'],
                [
                    $class: 'PreBuildMerge',
                    options: [
                        fastForwardMode: 'NO_FF',
                        mergeRemote: env.gitlabTargetNamespace,
                        mergeTarget: env.gitlabTargetBranch
                    ]
                ]
            ],
            userRemoteConfigs: [
                [
                    credentialsId: credentialsId,
                    name: env.gitlabTargetNamespace,
                    url: env.gitlabTargetRepoSshURL
                ],
                [
                    credentialsId: credentialsId,
                    name: env.gitlabSourceNamespace,
                    url: env.gitlabSourceRepoSshURL
                ]
            ]
        ])
    } else {
        sh "echo 'No merge request detected. Checking out current branch'"
        checkout ([
            $class: 'GitSCM',
            branches: scm.branches,
            extensions: [
                    [$class: 'PruneStaleBranch'],
                    [$class: 'CleanCheckout']
            ],
            userRemoteConfigs: scm.userRemoteConfigs
        ])
    }
}
/*
testing scripted jenkins pipeline files
*/
node (){

stage ("checkout")
{
handleCheckout()
//checkout scm
sh "git branch -vv"
sh "cat testfile"
}
/* def MyImage = docker.build("test-image","./docker/vmanage/")
   * MyImage.inside{
   * sh 'cat /etc/*release*'
   * sh 'uname -a'*/

}
