def generator = { String alphabet, int n ->
  new Random().with {
    (1..n).collect { alphabet[ nextInt( alphabet.length() ) ] }.join()
  }
}

pipeline {
  agent any
  triggers {
    GenericTrigger(
     genericVariables: [
      [key: 'ref', value: '$.ref']
     ],

     token: generator( (('A'..'Z')+('0'..'9')).join(), 16 ),
     
     causeString: 'Triggered on $ref',
     
     printContributedVariables: true,
     printPostContent: true,
    
     regexpFilterText: '$ref',
     regexpFilterExpression: 'refs/heads/master$|refs/heads/dev$|refs/heads/stage$'
    )
  }
  stages {
    stage('Some step') {
      steps {
        sh "echo $ref"
      }
    }
  }
}
