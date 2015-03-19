Product: Integration tests for WSO2 ESB CodePlex Connector

Pre-requisites:

 - Maven 3.x
 - Java 1.6 or above
 - A CodePlex account


Tested Platform:

 - MacOs 10.9
 - WSO2 ESB 4.8.1

STEPS:

1. Make sure the ESB 4.8.1 zip file with latest patches available at {basedir}/repository folder. If you want to use another location edit the pom.xml as follows.

          <carbon.zip>
            ${basedir}/../test/wso2esb-${esb.version}.zip
          </carbon.zip>

2. Copy codeplex connector zip file (codeplex-connector-1.0.0.zip) to the location "Integration_Test/products/esb/4.8.1/modules/integration/connectors/repository/"

3. Make sure the codeplex test suite is enabled (as given below) and all other test suites are commented in the following file - "{basedir}/src/test/resources/testng.xml"

4. This section describes how to obtain an access token from the codeplex.

	i) 	 Login to your codeplex account, then navigate to url: https://www.codeplex.com/site/developers/apps and create new application.
	ii)  Needs get to authorized the account with application by sending a GET request to https://www.codeplex.com/oauth/authorize with client secret and state as parameters, you will get a code from codeplex.
	iii) In Order to get Access Token a POST request to https://www.codeplex.com/oauth/token with code obtained in above step.
    iv)	 After all you will have 4 properties which will be used to invoke authorization required operations with OAuth2

			clientId - client ID of the codeplex application
			clientSecret - client secret of the codeplex application
			refreshToken - refresh token obtained from codeplex oauth 2.0

	vi) By invoking getAccessToken.xml configuration, it will obtain the temporary access token using these property values. You need to invoke this operation before invoking authentication required operations.

5. From the base directory run the following command.
     $ mvn clean install

6. When testing you need to add repository directory in the codeplex root director and need to place esb 4.8.1 zip file inside to deploy proxy services and test operations in test automation process.

Notes:
More on codeplex authentication: https://www.codeplex.com/site/developers/api/authentication
