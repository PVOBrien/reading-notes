## [Introduction to Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/dev/Introduction.html)

> "Amazon S3 has a simple web services interface that you can use to store and retrieve any amount of data, at any time, from anywhere on the web."

Amazon S3 works in "buckets". Buckets are the containers that store data, and buckets have a full complement of permissions control and standard interfaces (REST and SOAP, although SOAP is being deprecated and not available for new features). Updates are key based, and if you want one key to update based on another key, that functionality will need to be programmed per your needs. Amazon S3 has STANDARD, STANDARD_IA, and S3 Glacier for routinely accessed data, less-frequently used data, and infrequently used data access, respectively.

Storage Order: Region -> Bucket -> Objects -> Keys

## [Getting started with Amazon S3](https://docs.amplify.aws/lib/storage/getting-started/q/platform/android)

Provision via CLI

``` Java
amplify add storage

? Please select from one of the below mentioned services:
    `Content (Images, audio, video, etc.)`
? You need to add auth (Amazon Cognito) to your project in order to add storage for user files. Do you want to add auth now?
    `Yes`
? Do you want to use the default authentication and security configuration?
    `Default configuration`
? How do you want users to be able to sign in?
    `Username`
? Do you want to configure advanced settings?
    `No, I am done.`
? Please provide a friendly name for your resource that will be used to label this category in the project:
    `S3friendlyName`
? Please provide bucket name:
    `storagebucketname`
? Who should have access:
    `Auth and guest users`
? What kind of access do you want for Authenticated users?
    `create/update, read, delete`
? What kind of access do you want for Guest users?
    `create/update, read, delete`
? Do you want to add a Lambda Trigger for your S3 Bucket?
    `No`

// THEN:

amplify push
```

At which point ``` amplifyconfiguration.json ``` should be updated/provisioned per your setup.

Now, bring in the necessary dependencies for Gradle:
``` Java
dependencies {
    implementation 'com.amplifyframework:aws-storage-s3:1.4.1'
    implementation 'com.amplifyframework:aws-auth-cognito:1.4.1'
}
// Be sure to sync.
```

Within your onCreate() method you'll need to invoke S3:
``` Java
class MyAmplifyApp : Application() {
    override fun onCreate() { // Uncertain what this line is.
        super.onCreate()

        try {
            // Add these lines to add the AWSCognitoAuthPlugin and AWSS3StoragePlugin plugins
            Amplify.addPlugin(AWSCognitoAuthPlugin()) // NEW FOR S3
            Amplify.addPlugin(AWSS3StoragePlugin()) // NEW FOR S3
            Amplify.configure(applicationContext)

            Log.i("MyAmplifyApp", "Initialized Amplify")
        } catch (error: AmplifyException) {
            Log.e("MyAmplifyApp", "Could not initialize Amplify", error)
        }
    }
}
```

Now when wanting to upload content to the bucket:
``` Java
private fun uploadFile() {
    val exampleFile = File(applicationContext.filesDir, "ExampleKey")

    exampleFile.writeText("Example file contents")

    Amplify.Storage.uploadFile(
        "ExampleKey",
        exampleFile,
        { result -> Log.i("MyAmplifyApp", "Successfully uploaded: " + result.getKey()) },
        { error -> Log.e("MyAmplifyApp", "Upload failed", error) }
    )
}
```

And lastly, to download a file (because what good is having something uploaded if you can't download it?)
```
Amplify.Storage.downloadFile(
    "ExampleKey",
    File("${applicationContext.filesDir.toString()}/download.txt"),
    { result -> Log.i("MyAmplifyApp", "Successfully downloaded: ${result.getFile().name}") },
    { error -> Log.e("MyAmplifyApp", "Download Failure", error) }
)
// And as bonus,the below version incorporates the capability of a progress listener callback for use:
Amplify.Storage.downloadFile(
    "ExampleKey",
    File("${applicationContext.filesDir.toString()}/download.txt"),
    StorageDownloadFileOptions.defaultInstance(),
    { progress -> Log.i("MyAmplifyApp", "Fraction completed: ${progress.fractionCompleted}") },
    { result -> Log.i("MyAmplifyApp", "Successfully downloaded: ${result.getFile().name}") },
    { error -> Log.e("MyAmplifyApp", "Download Failure", error) }
)
```
Note: All quotes and code excerpted from Amazon documentation [here](https://docs.aws.amazon.com/AmazonS3/latest/dev/Introduction.html) or [here](https://docs.amplify.aws/lib/storage/getting-started/q/platform/android).
