node {
   
   pipelineTriggers([
					GenericTrigger(
						genericVariables: [
							[key: 'action', value: '$.action'],
							[key: 'ref', value: '$.pull_request.head.ref'],
							[key: 'statuses_url', value: '$.pull_request.statuses_url'],
							[key: 'title', value: '$.pull_request.title'],
						],
						causeString: 'Triggered on $ref',
						token: 'rsABLEpOMPuRomOS',
						printContributedVariables: true,
						printPostContent: false,
						silentResponse: false,
						regexpFilterText: '$action',
						regexpFilterExpression: '^(opened)|(synchronize)$'
					)
				])
   stage("Clone Repo"){
      git branch: "${ref}", credentialsId: "gitaccess", url: "${ssh_url}"
      echo "hello 123"
   }
}
