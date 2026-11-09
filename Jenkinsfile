pipeline
{
	agent 
	{
	    label 'Jenkins'
	}
	stages
	{
		stage('ContinuosDownload')
		{
			steps
			{
				git 'https://github.com/IntelliqDevops/maven.git'
			}
		}
		stage('ContinuosBuild')
		{
			steps
			{
				sh 'mvn package'
			}
		}
		stage('ContinuosDeployment')
		{
		    steps
		    {
		        deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'b74740d7-58d3-43f5-be16-b4b2cee7ea85', path: '', url: 'http://172.31.20.216:8080/')], contextPath: 'decltest', war: '**/*.war'
		    }
		}
		stage('ContinuosTesting')
		{
		    steps
		    {
		        git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
		        sh 'java -jar testing.jar'
		    }
		}
		stage('ContinuosDelivery')
		{
		    steps
		    {
		        deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'b74740d7-58d3-43f5-be16-b4b2cee7ea85', path: '', url: 'http://172.31.29.41:8080')], contextPath: 'declprod', war: '**/*.war'
		    }
		}
	}	
}	

