pipeline {
    agent any

    parameters {
        choice(
            choices: getAwsRegions(),
            defaultValue: 'ap-south-1'
            description: 'Select an AWS region',
            name: 'AWS_REGION'
        )
    }

    stages {
        // Your stages here...
                stage('print  region name'){
           steps{
               script{
                  def regions = getAwsRegions(params.AWS_REGION) 
               }
            //getAwsRegions()   
            
           }
        }
    }
}

def getAwsRegions(selectedRegion) {
    def awsRegions = []
    def awsSDK = new com.amazonaws.services.ec2.AmazonEC2Client()

    try {
        def describeRegionsResult = awsSDK.describeRegions()
        describeRegionsResult.getRegions().each { region ->
            def regionName = region.getRegionName()
            awsRegions.add(regionName)
            echo "AWS Region: ${regionName}"
        }

        // Print the selected region name
        echo "Selected AWS Region: ${selectedRegion}"
    } catch (Exception e) {
        echo "Failed to retrieve AWS regions: ${e.getMessage()}"
        awsRegions.add("Error")
    }

    return awsRegions
}

