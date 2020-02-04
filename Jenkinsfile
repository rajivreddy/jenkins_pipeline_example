node {
   stage("Clone Repo with $ref branch"){
      git branch: "${ref}", credentialsId: "gitaccess", url: "${ssh_url}"
   }
}
