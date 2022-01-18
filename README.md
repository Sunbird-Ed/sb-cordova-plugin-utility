# sb-cordova-plugin-utility
Provides helper methods for Sunbird platform (mobile app). Supports Android only.

## Installation
Ionic

`ionic cordova plugin add sb-cordova-plugin-utility`

Cordova

`cordova plugin add sb-cordova-plugin-utility`

## Methods

|Method|
|--|
|getBuildConfigValue|Gets property value from `.properties` file| property | value |
|getBuildConfigValues|Gets property value from `.properties` file| property | values |
|rm|Deletes local files|
|openPlayStore|
|getDeviceAPILevel|
|checkAppAvailability|
|getDownloadDirectoryPath|
|exportApk|
|getDeviceSpec|
|createDirectories|
|writeFile|
|getMetaData|
|getAvailableInternalMemorySize|
|getUtmInfo|
|clearUtmInfo|
|getStorageVolumes|
|copyDirectory|
|renameDirectory|
|canWrite|
|getFreeUsableSpace|
|readFromAssets|
|copyFile|
|getApkSize|
|verifyCaptcha|
|startActivityForResult|
|getAppAvailabilityStatus|
|openFileManager|

#### getBuildConfigValue
Fetche dependency from `.properties` file. Argument should match the key as per the `build.config`.
```
window.sbutility.getBuildConfigValue('key', (v) => {
  return(v);
}, (err) => {
  return(err);
});
```

#### getBuildConfigValues
Fetche dependency from `.properties` file. Argument should match the key as per the `build.config`.
```
window.sbutility.getBuildConfigValues('key', (v) => {
  return(v);
}, (err) => {
  return(err);
});
```

#### rm
Deletes locally stored files from the device. `directoryPath` can be an array of file paths from where files need to be deleted.
```
window.sbutility.rm(directoryPath, directoryToBeSkipped, (entry: string) => {
    // Handle successful file deletion
}, err => {
    // Handle file deletion failure
});
```
#### openPlayStore
To open an external app in playstore, pass the `APPID` of the app need to open in playstore.

```
window.sbutility.openPlayStore(appId, successCallback, errorCallback);
```

#### getDeviceAPILevel
Provides current API level of device.
```
window.sbutility.getDeviceAPILevel((deviceAPI: string) => {
    console.log(deviceAPI);
}, err => {
    console.error(err);
});
```

#### checkAppAvailability
This requires `APPID` and checks if the app is installed o the device or not.
```
window.sbutility.checkAppAvailability(packageName, successCallback, errorCallack);
```

#### getDownloadDirectoryPath
This method provides the complete path to the Download directory of the device.
```
window.sbutility.getDownloadDirectoryPath((path: string) => {
  console.log(path);
}, error => {
  console.log(error);
});
```

#### exportApk
If you need to share the app APK, get the `.apk` file and save locally, pass the destination path you need to save the `.apk`. On success callback you'll get the path of the saved `.apk`.
```
window.sbutility.exportApk(destination, (apkPath: string) => {
    console.log(apkPath);
}, error => {
    console.error(error);
});
```

#### getDeviceSpec
For device specifications, like manufacturer, device model, Android version, app version etc. On success you'll get the object containing these set of information about the device.
```
sbutility.getDeviceSpec((deviceSpecifiaction: ) => {
    console.log(deviceSpecifiction);
}, error => {
    console.log(error);
});
```

#### createDirectories
Creates new directory locally to a given path, and returns the coplete path to the newly created directory on success.
```
window.sbutility.createDirectories(ContentUtil.getBasePath(parentDirectoryPath), listOfFolder,
    (entry) => {
        resolve(entry);
    }, err => {
        console.error(err);
        reject(err);
    });
```
    
#### getMetaData
```
window.sbutility.getMetaData([{path: filePath, identifier: 'ecar'}], (data) => {
    resolve(data.ecar.size);
}, err => {
    reject(err);
});
```

#### writeFile
Write on to file(s). Send array of files path on which to write.
```
window.sbutility.writeFile(fileMapList,
    (entry) => {
        resolve();
    }, err => {
        console.error(err);
        reject(err);
    });
```

#### getAvailableInternalMemorySize
Return the current device memory size.
```
window.sbutility.getAvailableInternalMemorySize((size) => {
    console.log(size);
}, (eror) => {
    console.log(error);
});
```

#### getUtmInfo
Get the UTM information parameters.
```
window.sbutility.getUtmInfo(response) => {
    console.log(reponse.val);
}, error => {
    console.log(error);
});
```

#### clearUtmInfo
Clears UTM parameters set on device.
```
sbutility.clearUtmInfo(() => {
    console.log('utm paramter clear');
}, err => {
    console.log(err);
});
```

#### getStorageVolumes
```
sbutility.getStorageVolumes((volumes) => {
    if (v.isRemovable) {
        // Handle external storage
    } else {
        // handle internal storage
    }
}));
```

#### copyDirectory
Copy directory to aspecified destination directory. Need to provide path of directory to be copied and the destination where to copy the directory.
```
sbutility.copyDirectory(sourceDirectoryPath, destinationDirectoryPath, () => {
    console.log('Copy operation succefull');
}, (e) => {
    console.log('Failed to copy directory');
});
```

#### renameDirectory
If you need to rename a spcific directory call `renameDirectory()`. first arg the directory which is to be renamed and 2nd argument the newname of the directory.
```
sbutility.renameDirectory(sourceDirectory, toDirectoryName, () => {
    console.log('Succefully renamed);
}, (e) => {
    console.log('Failed to rename direcory);
});
```

#### canWrite
Find out if a directory is writable or not.
```
sbutility.canWrite(directory, () => {
    console.log('Success');
}, (e) => {
    console.log('Error');
});
```

#### getFreeUsableSpace
Get free available space of a directory.
```
sbutility.getFreeUsableSpace(directory, (space) => {
    console.log('Success');
}, (e) => {
    console.log('Error');
});
```

#### copyFile
Copy a file from source to a destination path in device.
```
sbutility.copyFile(directoryPath, destinationFolder, fileName,() => {
    cosole.log('Success');
  }, err => {
    cosole.log('Error');
});
```

#### getApkSize
Apk size of the app.
```
sbutility.getApkSize((size: string) => {
    console.log('Apk Size ', size);
}, err => {
    console.log('Filed to get APK size');
});
```

#### verifyCaptcha
To veriffy captcha, you need to pass the GoogleCaptchaSiteKey as argument to verifyCaptcha method.
```
sbUtility.verifyCaptcha(captchaSiteKey).then((response) => {
  console.log('Captha Response ', response);
}).catch((error) => {
  console.error(error);
});
```

#### startActivityForResult
To open third party app from your app, pass the package id of th app you want to open as value of `package` key. You can pass other required data to `extras` key.
```
sbutility.startActivityForResult({
    package: packageId,
    requestCode: 101
}, (data) => {
    console.log('Success');
}, err => {
    console.log('Error');
});
```

#### getAppAvailabilityStatus
To check if the third party app is available or not, pass the `package` id as argument.
```
sbutility.getAppAvailabilityStatus(packageIds, (data) => {
    console.log(data);
}, error => {
    console.error(error);
});
```

#### openFileManager
On calling this method, device file manager opens up if succesfull.
```
sbutility.openFileManager((res) => {
    console.log('Success');
}, error => {
    console.error(error);
});
```