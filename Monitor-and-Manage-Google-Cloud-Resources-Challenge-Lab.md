## Task 1 Create a bucket

Open Cloud shell and run the below to create the bucket (replace <BUCKET_NAME> with the lab value):
```
gcloud storage buckets create gs://<BUCKET_NAME>
```

Run the below to grant ```Storage Object Viewer``` to the secondary user (replace <PROJECT_ID> and <USER_ID> with the lab values):
```
gcloud projects add-iam-policy-binding <PROJECT_ID> \
    --member=user:<USER_ID> \
    --role=roles/storage.objectViewer
```

## Task 2 Create a Pub/Sub topic

Run the below command to create the pub/sub topic (replace <TOPIC_NAME> with the lab value):
```
gcloud pubsub topics create <TOPIC_NAME>
```

## Task 3 Create the thumbnail Cloud Function

Navigate to Cloud Functions and click ```Create Function```. On the first page fill in ```Function Name``` and update the trigger to Cloud Storage as per the below screenshot

![](https://drive.google.com/uc?export=view&id=1NhZ67GvKJYHznNRBBZtjo3eCdf46I_Rm)

Click save to move to the next screen, change the runtime to ```Node.js 14```, update the entrypoint to ```thumbnail``` and open the ```index.js``` and ```package.json``` files and respectively copy and paste the code provided by the lab. Deploy the function and wait on the screen until a green tick appears.

![](https://drive.google.com/uc?export=view&id=1Yp-8ezQ4sYiD6ElC7H6aKFrz7nv7SOvT)

To test the Cloud Function, navigate to Cloud Storage and click onto the Storage Bucket we created. Click ```upload files``` and select any JPG or PNG image. 

![](https://drive.google.com/uc?export=view&id=1Pj61D0Sz3lUtltsbELXl7Bs-uU-CX0_S)

Once uploaded refresh the Bucket until you see the thumbnail image appear

![](https://drive.google.com/uc?export=view&id=1mOAGdP_QujeHOwQU6CTw_Yyf7_hZxpap)
![](https://drive.google.com/uc?export=view&id=1rsgjuF0LTlYCVYUortq6p5A3sc0TvcB8)

## Task 4. Create an alerting policy

Navigate to alert and click ```create policy```. On this screen select the metric as per the below (untick ```Show only active resources & metrics``` otherwise it might not show up)

![](https://drive.google.com/uc?export=view&id=14fsfKky6xj6SUpuuu2gRkWxuhEWuqtB2)

Click ```configure triggers``` and set the threshold to 0.

![](https://drive.google.com/uc?export=view&id=1Bq5SfkM17Km-GNjjTu0MoaK5PqhKAsxP)

On the next screen untick ```Use notification channel```, name the policy as per the lab value and click ```Create Policy```

![](https://drive.google.com/uc?export=view&id=1GgPCGhU4Eb5rqPbtvnQ2WvmMsVVmwtfk)
![](https://drive.google.com/uc?export=view&id=1J7jna8Zkf4xykfE5MHTqpsvtXbpKGbxY)