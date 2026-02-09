# Freshline Mobile App Documentation

<p>
This file is used to store any documentation related to the project, such as setup instructions, architecture decisions, and any other relevant information that developers may need to know when working on the project.
</p>

---

# 1. Initial Setup

<p><strong>Step 1:</strong> Clone the repository</p>

```bash
git clone https://dhanu2@bitbucket.org/saketrtkmalik/freshline-mobile-app.git
```
<p><strong>Step 2:</strong> Create a new branch from main branch</p> <p><strong>Step 3:</strong> Initial setup of React Native referred through React Official Docs</p> <p> Follow all the steps mentioned in the document for app setup. </p> <p><strong>Step 4:</strong> Post successful installation of the app, maintain <code>.gitignore</code> file and push the changes to the branch.</p>
2. Architecture Setup
2.1 Environment Setup
<p><strong>Step 1:</strong> Go through React Native library and understand the steps</p> <p><strong>Step 2:</strong> Follow the steps mentioned in the library and do as directed</p> <p><strong>Step 3:</strong> Navigate to the below path and add environment config</p> <p><code>freshline-mobile-app/android/app/build.gradle</code></p>
project.ext.envConfigFiles = [
    development: ".env.development",
    staging :".env.staging",
    production:'.env.production'
]
<p><strong>Step 4:</strong> Create the following files in the root directory and add required environment variables</p> <ul> <li><code>.env.development</code></li> <li><code>.env.staging</code></li> <li><code>.env.production</code></li> </ul> <p><strong>Step 5:</strong> Post successful setup of environment variables, maintain <code>.gitignore</code> file and push the changes to the branch.</p> <p><strong>Step 6:</strong> Inside <code>package.json</code>, add the following scripts and install <code>cross-env</code> package</p> <p> Referred through React Native Config library documentation and some online resources for setting up scripts for bundling the app and cleaning build files. </p>
"scripts": {
  "android:uat": "cross-env ENVFILE=.env.staging react-native run-android --mode stagingDebug",
  "android:prod": "cross-env BABEL_ENV=production ENVFILE=.env.production react-native run-android --mode productionDebug",
  "bundle-android": "react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res",
  "build:android-debug": "react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/build/intermediates/res/merged/release/ && rmdir /s /q android/app/src/main/res/drawable-* && del android/app/src/main/res/raw/*.* /a /s && cd android && gradlew assembleDebug && cd ..",
  "build:android-release": "react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/build/intermediates/res/merged/release/ && rmdir /s /q android/app/src/main/res/drawable-* && del android/app/src/main/res/raw/*.* /a /s && cd android && gradlew assembleRelease && cd ..",
  "mac-build:android-debug": "react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/build/intermediates/res/merged/release/ && rm -rf android/app/src/main/res/drawable-* && rm -rf android/app/src/main/res/raw/!(*.mp3) && cd android && ./gradlew assembleDebug && cd ..",
  "mac-build:android-release:uat": "react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/build/intermediates/res/merged/release/ && rm -rf android/app/src/main/res/drawable-* && find android/app/src/main/res/raw -type f ! -name \"*.mp3\" -delete && cd android && cross-env ENVFILE=.env.staging ./gradlew assembleStagingRelease && cd ..",
  "mac-build:android-release:prod": "react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/build/intermediates/res/merged/release/ && rm -rf android/app/src/main/res/drawable-* && rm -rf android/app/src/main/res/raw/!(*.mp3) && cd android && cross-env ENVFILE=.env.production ./gradlew assembleProductionRelease && cd ..",
  "mac-bundle:android-release:uat": "react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/build/intermediates/res/merged/release/ && rm -rf android/app/src/main/res/drawable-* && rm -rf android/app/src/main/res/raw/!(*.mp3) && cd android && cross-env ENVFILE=.env.staging ./gradlew bundleRelease && cd ..",
  "mac-bundle:android-release:prod": "react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/build/intermediates/res/merged/release/ && rm -rf android/app/src/main/res/drawable-* && rm -rf android/app/src/main/res/raw/!(*.mp3) && cd android && cross-env ENVFILE=.env.production ./gradlew bundleProductionRelease && cd ..",
  "clean": "cd android && gradlew clean",
  "clean-mac-android": "cd android && ./gradlew clean",
  "start": "cross-env ENVFILE=.env.staging react-native start --reset-cache"
}
<p><strong>End of Documentation</strong></p> ```
