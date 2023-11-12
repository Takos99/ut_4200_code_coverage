<h3>Part 1:</h3>
	1. From the repository provided by instructor, fork it, this can be done using the *gh repo fork* command or through the Github GUI by going to the repository and simply clicking "Fork"
	2. Creating the config file requires quite a bit of documentation consulting but basically for this assignment consists of the following:
	   
	   Version (ex. 2.1)
	   
	   Jobs (name of job(s) ex. build)
	   Image (Which node or OS will be used. For this assignment it was a docker container)
	   
	   Steps (Basically the commands that will be ran), for this one we used 'Checkout' to select the repository, 'npm install' and 'npm test' to both install and run tests on a given package aka the forked repository to acquired all the required components for it to be able to run properly, then finally stored those results as artifacts using circleci command 'store_artifacts'.*
	   
	   Workflows (list of jobs to run, in this case it was just 'Build')

\*Stored artifacts and results can be useful for testing, as they can show how "well" your code/pipeline is working, and can show if new additions or deletions cause the code to not work anymore  or if it still functions, code coverage part shows what parts of the code are actually being utilized by the tests so you can know if you have similarities to 'Rule Shadowing' like on a firewall. Finally they can be useful for sharing code with a team, if a problem pops up you can share the test results with the team and more easily find solutions.
<h3>Part 2:</h3> 
	1. Create a CircleCI API Token, this can be done from the CircleCI dashboard by clicking on your profile icon and going to: Personal API Tokens > Create New Token (Make sure you copy it and save it somewhere safe because after you close it, you will NOT be able to see it again.)
	2. Study the CircleCI documentation as needed, it can be found [Here](https://circleci.com/docs/api/v2/)
	3-5. Create a script that utilizes the API token we created, grabs stored artifacts and stores them locally. In the script you will have the following:
	   
	   API_TOKEN (Paste your API token you generated here in this key)
	   PROJECT_USERNAME (Key for your CircleCI/Github username)
	   PROJECT_NAME (Key for the repository name in this case it was ut_4200_code_coverage)
	   
	   then using <curl> it authenticates with CircleCI using the token, grabs the requested artifacts (coverage report and test results) and stores them locally here is an example of one instance used in the script:
	
	curl -u $API_TOKEN: \ "https://circleci.com/api/v2/project/github/$PROJECT_USERNAME/$PROJECT_NAME/workflow/$WORKFLOW_RUN/job?name=store-artifacts-coverage" \ -o coverage.zip

