node {
  def verCode = UUID.randomUUID().toString()
 properties([
  pipelineTriggers([
   [$class: 'GenericTrigger',
    genericVariables: [
     [key: 'ref', value: '$.ref'],
     [
      key: 'https_url',
      value: '$.repository.clone_url',
     ]
    ],


    causeString: 'Triggered on $ref',

    token: verCode,
    tokenCredentialId: '',

    printContributedVariables: true,
    printPostContent: true,

    silentResponse: false,

    regexpFilterText: '$ref',
    regexpFilterExpression: 'refs/heads/master$|refs/heads/dev$|refs/heads/stage$'
   ]
  ])
 ])
}


def s = env.ref
git_branch = s.tokenize('/').last()

pipeline {
  
  agent any
  stages {
    stage('Some step') {
      steps {
        sh "Branch Name is echo $git_branch"
        sh "Repo URL is $clone_url"
      }
    }
  }
}
