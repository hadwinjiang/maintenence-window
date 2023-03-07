# Welcome to ajust maintenance window
The workflow check the rds cluster maintenance window regularly. 
It will automatically push the maintenance window 3 days later when it might be within 3 days.
The operation will only target to Aurora version 2.09 and 2.10

* Deploy process
npm install     // Install the package
cdk bootstrap   // The first time you deploy an AWS CDK app into an environment (account/region), you can install a “bootstrap stack” 
cdk deploy      // Deploy the project
cdk destroy     // Delete the deployment

* Start the step function workflow
input example for step function
{
  "region": "us-west-2",
  "clusterIds": ["aurora-gdb-uswest2-test2", "aurora-gdb-uswest2-test3"]
}

* How to query the cluster list:
aws rds describe-db-clusters --region us-west-2 | jq -r ".DBClusters[] | {clusterId: .DBClusterIdentifier, engineVersion: .EngineVersion} "