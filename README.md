# S3-cross-replication

Implementing Cross-Account S3 Replication:
To enable cross-account replication in AWS S3, follow these steps:

Step 1:
First login 2 aws account Source s3 account and Destination s3 account.

In the source account create an s3 bucket here I created "multi-region-s3-sana" (this bucket I was created in ap-south-1)and destination I created a bucket in the name of "destination-bucket-sana"(this bucket I created in us-east-1)

Enable versioning on both the source and destination buckets. Versioning allows S3 to keep track of changes to objects and ensures accurate replication across accounts.





# Step-2:
In the source bucket create the replication rules for transferring data from different accounts to different regions.



click on the source bucket and go to the management, then create replication rule.



give replication rule id.



make sure your bucket region is in the replication rule.



Now in the replication rule destination, u can choose ur requirements like if you want to transfer the date within the account of different buckets of different regions. (or) if you want to transfer the data from different accounts of different regions.

Here I selected another account for that u have to destination account id and destination bucket name.



In the IAM role select create a new role for replication.



And save your replication settings



After clicking on save You will get a pop-up like this it means that if u have any existing objects to replicate to the destination bucket or not, I don't want to replicate existing objects to a destination bucket.

Based on your requirement you will select the options, here I am selecting "No, don't replicate existing objects".



# Step-3:
Now go to the destination bucket of 2nd aws account.



Now go to the permission option of the destination account of aws and edit the bucket policy of the destination bucket.



Copy and paste this policy.(https://docs.aws.amazon.com/AmazonS3/latest/userguide/replication-walkthrough-2.html)



Replace the "set permission for objects" to "1" & "2" in "sid" value and also replace the AWS iam arn value to your replication rule iam arn.

replace the bucket name destination bucket name.

To get the replication arn IAM policy, go to the replication rule of the source bucket click on IAM role and copy IAM arn role, and paste it into the destination bucket policy.





Replace this thing and save it



And finally, we did a replication of two different accounts of two different regions. Lets check if it will work or not.

For checking purpose I am uploading a few files in source bucket.

At present, in my source, nothing is there.









Here I uploaded one file to my source bucket. Now go to the destination bucket and refresh the page of the 2nd AWS account.



So, here we transfer the data from one account of s3 aws to another account os s3 aws.
