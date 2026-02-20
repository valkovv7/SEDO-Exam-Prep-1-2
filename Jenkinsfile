pipeline{
    agent {
		docker {
			image 'mcr.microsoft.com/dotnet/sdk:6.0'
		}
	}
    stages{
        stage("Restore dependencies"){
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps{
                sh 'dotnet restore'
            }
        }
        stage("Build the app"){
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps{
                sh 'dotnet build --no-restore'
            }
        }
        stage("Run the tests"){
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps{
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}