##### JITSI LOCALLY SETUP IN YOUR COMPUTER

1. git clone [jitsi/jitsi-meet](https://github.com/jitsi/jitsi-meet)

2. sudo n lts (take the long term support version)

3. cd <project_folder>

4. npm install 

5. make


##### HOW TO DEPLOY JITSI MEET LOCALLY

###### start the server

./node_modules/.bin/webpack-dev-server  

###### compile css 

 ./node_modules/.bin/node-sass css/main.scss css/all.bundle.css && ./node_modules/.bin/cleancss css/all.bundle.css > 
css/all.css ; rm css/all.bundle.css

##### HOW TO RUN JITSI ANDROID

Go to your project folder using terminal and run following two commands same time using two terminals.

react-native run-android

react-native start

##### HOW TO CUSTOMIZE JITSI ANDROID

There are my blog post and script to run this as easy task.

[How to customize Jitsi – Meet](https://meetrix.io/2017/10/31/how-to-customize-jitsi-meet/)

[jitsi_android_customization.sh](https://gist.github.com/SupuniNimeshika/f423978a9407cbf4a2569df167bbecf1)


##### HOW TO CUSTOMIZE JITSI IOS APP

There is a script for that also.

[jitsi_ios_customization.sh](https://gist.github.com/SupuniNimeshika/a898e4baa257bb4d76df8fde72d0a2d5)

