import jenkins.model.Jenkins
import com.cloudbees.plugins.credentials.domains.Domain
import org.jenkinsci.plugins.plaincredentials.impl.StringCredentialsImpl
import com.cloudbees.plugins.credentials.CredentialsScope
import hudson.util.Secret

instance = Jenkins.instance
domain = Domain.global()
store = instance.getExtensionList(
  "com.cloudbees.plugins.credentials.SystemCredentialsProvider")[0].getStore()
def verCode = UUID.randomUUID().toString()
secretText = new StringCredentialsImpl(
  CredentialsScope.GLOBAL,
  env.JOB_NAME,
  "webhook token",
  Secret.fromString(verCode)
)

store.addCredentials(domain, secretText)

node {
 
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
    token: 'abc123',
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
        sh "Repo URL is $https_url"
      }
    }
  }
}
