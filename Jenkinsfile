pipeline {
    agent any

    parameters {
        choice(
            choices: getAwsRegions(),
            description: 'Select an AWS region',
            name: 'AWS_REGION'
        )
    }

    stages {
                stage('print  region name'){
           steps{
               script{
                  def regions = getAwsRegions(params.AWS_REGION) 
               }
           }
        }
    }
}
