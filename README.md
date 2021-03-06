JSON API for Yelp


#AWS Lambda and API Gateway
I wanted to learn that tech and here is how I use it:

#Step 1: Setup AWS Lambda

1. Download and Install Apex:

  `curl https://raw.githubusercontent.com/apex/apex/master/install.sh | sh`

2. Download and Install AWS-CLI `brew install awscli` - sorry windows users, just use the browser :-)

3. Create IAM user in AWS Console and give permissions to IAM and Lambda (
Apex will need to create a IAM role and be able to execute/deploy to Lambda).
Caution: If you give it FUllAcccess Policy to IAM and Lambda make sure, you remove it afterwards to avoid any security problems.

4. Run `aws configure`
setup your user with AWS_ACCESS_KEY & AWS_SECRET_KEY.
I used `us-east-1`

5. Run `apex init`

6. Make sure you can deploy. Run `apex deploy`

7. If it is successful, you can run `apex invoke hello`

8. Now, do `git clone ` this repo into `functions/hello` folder

9. `cd functions/hello `

10. `npm install`

11. `cd ../..`

12. apex deploy

------------------

To test it out that it's working do the following:

```
echo {"business_url"    : "http://api.yelp.com/v2/business/","consumer_key"    : "CONSUMER_KEY","consumer_secret" : "COSUMER_SECRET","oauth_token"     : "OAUTH_TOKEN","oauth_secret"    : "OAUTH_SECRET"} | apex invoke hello
```

you should get JSON response from Yelp API

Step #2 Integrate with AWS API Gateway: 

.....
Business URL should be in format: http://api.yelp.com/v2/business/BUSINESS_ID
Your business id looks something like aurora-construction-and-design-sarasota
https://tpbqwidt0h.execute-api.us-east-1.amazonaws.com/prod/get-reviews?business_url=BUSINESS_URL&consumer_key=CONSUMER_KEY&consumer_secret=CONSUMER_SECRET&oauth_token=OAUTH_TOKEN&oauth_secret=OAUTH_SECRET