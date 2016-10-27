---
title: How TapBookAuthor.com Helps Users Create Interactive Content with PhoneGap
date: 2016-06-15 00:00:00 Z
tags:
- Guest Post
- Community
author: Sondre Bjornebekk
---

This guest post is written by [Sondre Bjornebekk](https://www.linkedin.com/in/sondresb), the CEO of [TapBookAuthor.com](http://TapBookAuthor.com/).

The [TapBookAuthor.com](http://TapBookAuthor.com/) platform is used by educational and children's publishers all over the world to create interactive content for learning and entertainment. The company got a first international breakthrough when Samsung decided to use the platform in seven countries in South East Asia. Recently an Indie Edition of the platform, aimed at self publishers and small organizations, was launched and can be tested for free by anyone (to export and publish apps, a subscription is required).

The company is using PhoneGap for hybrid apps, mainly for iOS and Android. In this blog post, we'll highlight a few cool ways in which hybrid in general and PhoneGap in particular add value to their users. We'll look at:

- Offline mode
- Camera interactions
- APIs for using custom code
- Cross-store in-app purchases
- Drawing interactions
- Sound recording
- Reading Analytics

But before we jump to those features and look at the technical details behind them, let's give a quick overview of the platform itself.

## TapBookAuthor.com architectual overview

Basically TapBookAuthor.com gives users a visual editor where they can work on what we call scenes, and organize these in projects. In the simplest case, the scenes will be the sequential pages of a book in a single project.

Once the user is happy with his project, he can export - or build - in a variety of formats. Building to native apps is currently done with a set of servers that pick up the jobs and mix the HTML5 exported from the online visual editing platform as a zip file into a template that accepts this and variety of settings to control the appearance of the final app. We could be migrating this to [PhoneGap build](https://build.phonegap.com/) at some point, but there are/were some challenges in integrating our library of native features into that flow. Anyway, the picture below illustrates this overall flow:

![TapBookAuthor.com concept illustration](/blog/uploads/2016-06/tba_concept_sketch.png)

Now, let's jump in and have a look at how those 7 sample features are implemented to work smoothly on iOS and Android (and Windows, even if not officially released from our side at the time of writing). We'll start with a look at how the apps work smoothly even when offline.

## Offline mode

The kind of titles that lends itself to interactivity, animations and sounds that play when tapped works best if the resources are available locally. Often they are used in places like cabins, trains through tunnels and kindergartens with variable wifi capabilities. Thus, the offline mode is essential. How this works using PhoneGap is that a zip file is delivered to the app and unpacked locally. The screenshot below shows the progress of such a download into a bookshelf.

![Download progress](/blog/uploads/2016-06/downloadProgress.png)

A cool little detail here is how we implement versioning so that the user can download an updated version when it is available when he is online. We store a version id in _localStorage_ and if the user is online, we ask the server if a more recent version exists. The code below illustrates how we do this.

```js
 function downloadNewVersionIfNeeded(projectId, currentProjectId, successCallback, errorCallback) {
  var activeProjectId = getActiveProjectId(projectId, currentProjectVersionedIdMappingObjectLocalStorageKey); //extract from local storage active project ID
  if (downloadStatus == downloadStatuses.UN_DOWNLOADED && projectId != activeProjectId) {
    UserDialogs.showConfirmation(CAPTIONS.TITLE_UPDATE_MESSAGE, CAPTIONS.UPDATE_AVAILABLE, CAPTIONS.YES + "," + CAPTIONS.NO, function (buttonIndex) { //Ask user confirmation before starting downloading new version
        if (buttonIndex == 1) { // YES
          downloadProjectArchive(projectId, activeProjectId, successCallback, errorCallback);
        }});
  } else if (downloadStatus == downloadStatuses.DOWNLOADED_OLDER_VERSION) {
        UserDialogs.showConfirmation(CAPTIONS.TITLE_UPDATE_MESSAGE, CAPTIONS.UPDATE_AVAILABLE, CAPTIONS.YES + "," + CAPTIONS.NO, function (buttonIndex) {
          confirmationCallback(buttonIndex, projectId, activeProjectId, successCallback, errorCallback);
                    });
  } else if (downloadStatus == downloadStatuses.DOWNLOADED && (currentProjectId != activeProjectId)) { // if active project is already downloaded execute download success callback
    if (null != successCallback) {
      successCallback();
    }
  }
}

function downloadProjectArchive(projectId, activeProjectId, successCallback, errorCallback) {
  var relativePathPrefix = 'versionedProjects/';
  DownloadUI.displayDownloadBoxWithMessage(CAPTIONS.DOWNLOAD_WAIT_MESSAGE);
  setTimeout(function () {
  //call native plugin in order to download a new title
    window.plugins.FileDownloader.downloadFile(relativePathPrefix + activeProjectId, ProjectSettings.URLs.projectArchiveDownloadURL() + activeProjectId, null, function (message) {
      var downloadedProjectId = getDownloadedProjectId(projectId);
      if (downloadedProjectId) {
      //remove old version from storage folder using a native plugin
        window.plugins.FileDownloader.removeFileFromStorageFolder( relativePathPrefix + downloadedProjectId, function () {
          console.log("DownloadService: deleted old title after update downloaded");
        }, function () {
          console.log("DownloadService: failed to delete old title after update downloaded");
        });
      }
      //update local storage information with last downloaded project
      updateDownloadedProjectsMappingObject(projectId, activeProjectId);
      DownloadUI.removeUnzipSpinner();
      //Execute download success callback (in this case navigate to downloaded project)
      if (null != successCallback) {
        successCallback(true);
      }
    }, errorCallback);
  }, 500);
}
```

## Camera interactions

What if you could have stories for kids where the reader can fill in the blanks using the device camera and making the pictures part of the story? In fact, they can - through the use of the _Camera API_ of PhoneGap/Cordova. Below you see both the code to do it and the end result in one of the products using this.

```js
takePicture: function () {
//set camera options
  var options =
  {
    quality: 100,
    destinationType: destinationType,
    sourceType: Camera.PictureSourceType.CAMERA
  };
  //check if we need to stretch the picture in order to fit its parent
  if (that.cameraElementModel.get('isStreched')) {
    options['targetWidth'] = that.cameraElementView.$el.width();
    options['targetHeight'] = that.cameraElementView.$el.height();
  }
  //set which camera should be used
  if (!Camera.Direction) {
    Camera.Direction = {
      FRONT: 1,
      BACK: 0
    }
  }
  if (that.cameraElementModel.get('selectedCamera') == "Front Camera") {
    options['cameraDirection'] = Camera.Direction.FRONT;
  } else if (that.cameraElementModel.get('selectedCamera') == "Back Camera") {
    options['cameraDirection'] = Camera.Direction.BACK;
  }
  options['correctOrientation'] = true;
  //call the native side to make the picture
  navigator.camera.getPicture(this.onSuccessCameraPicture, this.onFailCameraPicture, options);
}
```

![Fireflies camera](/blog/uploads/2016-06/firefliesCamera.png)

In [Catching Fireflies](https://itunes.apple.com/us/app/catching-fireflies/id835812212?mt=8) this snippet helps creating a fun "this book belongs to"-page. When the user taps the camera icon shown in the screenshot, he can select from the library or take a new photo that will replace the camera in the page.

In our case in our tool, the camera interaction is made generically so that the user just draws the rectangle where the interaction is wanted in the title. But I think the code is sufficiently general that it might be useful for others. Do contact the author of this blog post if you would like a free copy of the scripts doing this with more detail than there is room to include here.

## APIs for using custom code

Even with a tool like [TapBookAuthor.com](http://TapBookAuthor.com/) that lets users add animations, hotspots for starting sounds and videos and even quizzes and non-linear stories with multiple layers, there are times when you want to code something truly unique by hand. The good news is that you can.

A full description of the API would be beyond the scope of this blog article, but look at the below example of usage and you will see we are using the messaging capability to send messages between custom code and our framework code. If you are interested in more details, start by having a look at our [blog post from when we launched the feature last summer](http://blog.tapbookauthor.com/?p=282) and the [hackathon where it was first used](http://blog.tapbookauthor.com/?p=308). Then the upcoming [API docs](https://tapbookauthor.atlassian.net/wiki/display/TCD/TBA+API) is a great next step when you want to get your hands dirty.

But we thought we'll also share a bit about the inner workings of the API. Below you see the call for subscribing to action complete event and a snippet on how this is implemented in the API.

```js
tbaApi.addEventListener(listener)
```

The above function receives a function as parameter. That function is executed when the API receives a message using the window.postMessage function. Below is some code that shows what is going on in detail:

```js
function _init() {
  window.addEventListener("message", _processMessage, false);
}
function _addEventListener(listener) {
  onMessageReceived = listener;
}

function _processMessage(e) {
  var messageData = e.data;
  if (typeof messageData == "object") { // this complies with messaging API
    if ("identifier" in messageData && "id" in messageData && "type" in messageData) {
      var identifier = messageData['identifier'], actionType = messageData['type'], parameters, actionId = messageData['id'];
      if (identifier == validIdentifier && actionType == actionsTypes.RESPONSE) {
        _executeCallback(actionId, messageData['parameters'], messageData['status']);
        _dispatchMessage(messageData);
      }
    }
  } else {
    _dispatchMessage(messageData);
  }
}

function _dispatchMessage(message) {
  if (null != onMessageReceived && typeof onMessageReceived == "function") {
    onMessageReceived(message);
  }
}
```

What happens in the above snippet is that the API subscribes to "message" event and each time a message is received, the `_processMessage` function is called. Each time a API call is made, a new action is created. Each action has a unique id, that is sent as parameter for execution and will be received in the message body when the action has finished (mandatory for async actions such as purchase). When the action is finished, based on its unique id success and error callbacks are identified (if any) and executed. After callback execution, the message is dispatched to the message handler sent from custom code (initialized using the call `tbaApi.addEventListener(listener)`, as shown above).

## Cross-store in-app purchases

In-app purchasing is used in many of our clients' bookshelves, for instance for reading training for early readers. To handle this without the need to manually code this every time, we have added the option to set product IDs in the visual editor and then this little code snippet takes care of selecting the relevant app store to interact with and act accordingly when the purchase is made.

The below code shows how we handle this.

```js
tbaApi.purchase("productId", successCallback, errorCallback)
```

Here the productId needs to be identical with the productId set on iTunes or Google Play. The successCallback and errorCallback functions will be executed when the purchase process succeeded or failed. Below is a slightly more complete example of how we do this, including the purchase call and the success and failure callbacks used in this case:

```js
/**
    * Call the native side for making the purchase of the product with the product id specified by the productId parameter
  * and quantity equals with one unity
  * @param productId  The product id for the product that will be purchased
  * @param successCallback The function executed if the purchase succeeded
  * @param errorCallback The function executed if the purchase failed
*/
this.makePurchase = function (productId, successCallback, errorCallback) {
  //if was already purchased it will directly execute the success callback
  if (wasPurchased(productId)) {
    if (null != successCallback) {
      successCallback(productId);
    }
  } else {
  //Will make the purchase call only if the device is online
    if (localStorage.getItem("isOnline") == "false") {
      UserDialogs.showAlert(CAPTIONS.NO_DOWNLOAD_OFFLINE);//"Oops, your device seems to be offline! Please connect to the Internet and try again.");
      return;
    }
    $("body").SpinnerProgressIndicator({showOnlySpinner: true});
    Chapter.isPurchaseActive = true;
    purchaseSuccessCallback = successCallback;
    purchaseFailCallback = errorCallback;
    //the call for purchasing product
    if (AppUtils.DeviceType.iOS) {
      window.plugins.inAppPurchaseManager.makePurchase(productId, 1);
    } else if (AppUtils.DeviceType.ANDROID) {
      window.plugins.inAppPurchaseManager.startAndroidIABForProduct(productId, null, null);
    }
  }
};

window.plugins.inAppPurchaseManager.onPurchased = function (productId) {
  console.log('JS purchased product: ' + productId);
  //Update in local storage purchased products
  updatePurchasedProjectsMappingObject(productId);
  $("body").SpinnerProgressIndicator("onComplete");
  //execute purchase success callback
  if (null != purchaseSuccessCallback) {
    purchaseSuccessCallback(productId);
  }
  Chapter.isPurchaseActive = false;
};

window.plugins.inAppPurchaseManager.onFailed = function (errNo, errText) {
  (null == errText) ? console.log('JS IAP failed with error') : console.log('JS IAP failed with error: ' + errText);
  $("body").SpinnerProgressIndicator("onComplete");
  //execute purchase error callback
  if (null != purchaseFailCallback) {
    purchaseFailCallback(errNo);
  }
  Chapter.isPurchaseActive = false;
};
```

## Drawing interactions

For children's books, it is cool to allow the user to sketch out drawings using his finger. We do this via a Canvas and store the PNG locally on the device. In addition, we have a feature to pick up the drawing in other parts of the story. A sample of this is shown below, where "canvas" clearly can have two interpretations... :)

![Drawing](/blog/uploads/2016-06/drawing.png)

![Drawing result](/blog/uploads/2016-06/drawingResult.png)

## Sound recording

When learning to read, being able to practice is important. That is why we added a simple recording inteaction to our set of interactions. Also, it can be really cool to record your own voice and being able to switch between this and a professional actor reading the same children's book. I know I have tried to convince my nephew that it is cooler to listen to me!

Below is a screenshot of the countdown to start a recording, as well as the Javascript snippet kicking this off:

![Recording](/blog/uploads/2016-06/recording.png)

```js
createAudioFileBeforeRecording: function () {
//get filename depending on current page number
  var audioFileName = this.getFileNameForRecording();
  //Create sound file
  window.plugins.FileDownloader.createFileInDocumentsFolder(audioFileName,
    function (successMessage) {
    console.log(successMessage);
    //Start recording
    SoundRecorder.preformAudioRecording(audioFileName);
  }, function (failMessage) {
    console.log(failMessage);
  });
}
```

## Reading Analytics

As a geek myself, I enjoy when we get to use new and cool technology. Our so called "Reading Analytics" solution for sure is one such area. Here we track for instance that the users that saw the video on page also spent long time reading page 10 before doing the end of chapter quiz. And almost literally everything in between... :)

I will just give a quick overview of the building blocks we have used for this, to provide some pointers to where you can start if you would like to create something similar - or maybe something very unlike it, but with common requirements. So here goes:

- We use JSON as a transport format
- A native DB to aggregate before we send the events to the server, support tracking even if reading offline
- The backend is a very simple Node.js endpoint running at a leading cloud provider in a "serverless fashion"
- The individual events end up being documents in ElasticSearch after processing - we interface with ES using the JSON protocol (test Sense in your Chrome browser when developing, it is great)
- Currently we are working on visualizations, hot candidate libraries here include [D3](https://d3js.org/), Charts.js and HighCharts - with the former having high potential, but also considerably more manual work than the two latter alternatives

That completes our walkthrough of the 7 samples of how PhoneGap helps our users create interactive content via TapBookAuthor.com. Hope it can be helpful for some of the readers. If you have great ideas for usage of our platform or want to play with the API, let me know. Also: If you have any corrections or comments to the above, do reach out! Looking forward to hearing from you.
