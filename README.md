# qml-http-uploader

in main.ccp file:
```
qmlRegisterUncreatableType<HttpPostField>("HttpUp", 1, 0, "HttpPostField", "Can't touch this");
qmlRegisterType<HttpPostFieldValue>("HttpUp", 1, 0, "HttpPostFieldValue");
qmlRegisterType<HttpPostFieldFile>("HttpUp", 1, 0, "HttpPostFieldFile");
qmlRegisterType<HttpUploader>("HttpUp", 1, 0, "HttpUploader");
```

Now you can embed the uploader into the QML file by writing, e.g.:
```
import HttpUp 1.0
Item{
    HttpUploader{
        id: mpUploader
        onUploadStateChanged: {
            if( uploadState == HttpUploader.Done ) {
                console.log("Upload done with status " + status);
                console.log("Error is "  + errorString)
                console.log("response:" + mpUploader.responseText)
            }
        }
        onProgressChanged: {
            console.log("Upload progress = " + progress)
        }
    }
}
```
