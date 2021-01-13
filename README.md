# AWS-CICD-CodeCommit-CodePipeline

CICD Pipeline that changes an Elastic Beanstalk App.

To start off we have created a web server in Elastic Beanstalk and we have used the sample application on Node.js. The code from AWS can be found here - https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/RelatedResources.html

We are simply going to change the background from green to blue and push this to EB via CodeCommit and CodePipeline.

![EB deployment](https://user-images.githubusercontent.com/68379635/104440911-dc038c80-558a-11eb-9f5b-855d30519623.PNG)

Now we are going to create a repo in CodeCommit and here we push our changes from our local machine back to CodeCommit, to set this up AWS have documentation here - 
https://docs.aws.amazon.com/codecommit/latest/userguide/how-to-connect.html

![CodeCommit Repo](https://user-images.githubusercontent.com/68379635/104441087-24bb4580-558b-11eb-8912-2a8b10e68990.PNG)

Once we have our repo and uploaded our changes we want to create a Codepipeline with the source being our CodeCommit repo.

![Pipeline](https://user-images.githubusercontent.com/68379635/104441471-a317e780-558b-11eb-9859-03313a864159.PNG)

For the deploy stage you want to select Elastic Beanstalk and we select our test environment. I'd suggest stopping the executuion for now as it will try to psuh the code from the repo to the EB app. 
So we have now used CodePipeline to hook our CodeCommit repo to our app.
Next we want to add a manual approval between our source and deployment, so any time we want to push changes to our application they need someone to manually approve the change.

![Manual Approval](https://user-images.githubusercontent.com/68379635/104442285-c1321780-558c-11eb-85a6-be4ece4094f5.PNG)

Now in our pipeline we want to execute our change so we select release change and se now see our change being pushed to our app.

![Executing](https://user-images.githubusercontent.com/68379635/104442554-20902780-558d-11eb-9668-454170f658ba.PNG)

Now we have to manually approve the change.

![Approval](https://user-images.githubusercontent.com/68379635/104442644-43bad700-558d-11eb-8c38-52fe8085bb29.PNG)

Once this is done we see our code being deployed and wait for everything to turn green to say it's been successful.

![Deployed](https://user-images.githubusercontent.com/68379635/104442760-6ea52b00-558d-11eb-89f7-f1e8baac8d97.PNG)

We now go to the URL of our EB app and we can see the change has been carried out.

![EB Blue](https://user-images.githubusercontent.com/68379635/104442878-97c5bb80-558d-11eb-9e00-a5df199389d6.PNG)
