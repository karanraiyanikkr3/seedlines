pipeline {
    agent any


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
