# Deployment using CloudFormation

This is a CloudFormation template to deploy in AWS the Lambda function taking care of:

- Necessary IAM roles and policies
- Schedule configuration

Advantages are this is easier to follow, less prone to human error and also easier to update.

# Setup

## Step 1. Deploy CloudFormation Template
 1. Sign up to the AWS console here https://aws.amazon.com
 2. Select the right region in the top right corner, same as where your LightSail servers are.

 Your instance name and region can be found here (see image): 
http://take.ms/3KOAo

 3. Put CloudFormation in the search field or go to https://console.aws.amazon.com/cloudformation
 4. Click CREATE STACK
 5. Select "Upload a template file", upload ***stack.yaml*** and click NEXT
 6. Give it a stack name, for example ***lambda-lightsail-snapshots*** and click NEXT
 7. Click NEXT in "Configure stack options".
 8. Tick the Capabilities acknowledge at the end and click CREATE STACK

## Step 2. Upload the Lambda function

 1. Go to the https://aws.amazon.com again
 2. Put the Lambda in the search field
 3. In AWS Lambda click in FUNCTIONS, you should see the function you created in step 1, click it
 4. Paste and replace in the 'Function Code' field the code from here (the index.js contents in this repository)
 https://raw.githubusercontent.com/vidanov/lambda-nodejs-lightsail-backup/master/index.js
 Change the name of the ***instanceName*** in the function and set up the frequency of the backups
 
  <pre><code>
        
        const backupDaysMax = 7; // keep at least 7 daily backups 
        
        const backupWeeksMax = 4; // keep at least 4  weekly  backups
        
        const backupMonthsMax = 3; // keep at least 3  monthly  backups
</code></pre>        

Set the name and the region accordingly to your settings in the line
 <pre><code>
      const instanceName = "LAMP_Stack-2GB-Frankfurt-1"
      AWS.config.update({ region: 'eu-central-1' });
</code></pre>

 5. Push SAVE button at the top right

Jump to Step 4 in the main [README.md](../README.md)
