# Jenkins_git_tuts
A public repo to practice jenkins and git tutorials

This tutorial was created so that I can practice on this repo and become more familiar with git commands and jenkins tool


# Caveats
This repo was private at first and the checkout step in declarative pipeline fails. After some testing found out that git checkout was working fine on public repos.
so made this repo public for practising tutorials.
Will make this repo public after the issue is found

checkout([$class: 'GitSCM', branches: [[name: 'master']], 
     userRemoteConfigs: [[credentialsID: 'xyz', url: 'https://github.com/tarun-teja/Jenkins_git_tuts.git']]])

was used to test the git checkout in declarative pipeline
