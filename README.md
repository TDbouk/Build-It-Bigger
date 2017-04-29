# Build-It-Bigger

An Android app with multiple flavors that uses multiple libraries and Google Cloud Endpoints. More specifically, it includes a Java library that provides jokes, a Google Cloud Endpoints(GCE) project that serves those jokes, an Android Library containing an
activity for displaying jokes, and an Android app that fetches jokes from the GCE module and passes them to the Android Library for display.

## Getting Started
The below instruction will get you a copy of the project up and running on your machine for development and testing purposes.

### Prerequisites
Android Studio including SDK version 25 and build tools version 25.0.2.  
You can always update to the latest versions. 

### Running the tests
You can run an automated test that will hook up everything together including starting the backend, testing the app, and shutting down the back end using a Gradle task as follows:

`gradlew tieItAllTogether`

### Installing and Deployment
1. Import the project to your Android Studio  
2. Build the project

In the `doInBackground` method of GetJokeFromBackEndTask class, change the **rootUrl** to include your local IP or use 10.0.2.2 if you are testing against an emulator. 

```
MyApi.Builder builder = new MyApi.Builder(AndroidHttp.newCompatibleTransport(),
                    new AndroidJsonFactory(), null)
                    .setRootUrl("http:/my_computer_address:8080/_ah/api/")
                    .setGoogleClientRequestInitializer(new GoogleClientRequestInitializer() {
                        @Override
                        public void initialize(AbstractGoogleClientRequest<?> abstractGoogleClientRequest) throws IOException {
                            abstractGoogleClientRequest.setDisableGZipContent(true);
                        }
                    });

```

3. Select the backend run configuration and run it
2. Build the app and install the APK on your device or an emulator
                 
### Built With
[Android Studio](https://developer.android.com/studio/index.html) - The IDE used
[Gradle](https://gradle.org/) - Dependency Management

### Contributing 
Pull requests are gracefully accepted. 

### License
The project is licensed under the MIT License - see [LICENSE.txt](LICENSE.txt) file for detail.

### Acknowledgments
Setting up the GCE [tutorial](https://github.com/GoogleCloudPlatform/gradle-appengine-templates/tree/master/HelloEndpoints)
