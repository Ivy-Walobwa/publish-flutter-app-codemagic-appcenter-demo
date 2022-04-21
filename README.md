# Counter App
[![Codemagic build status](https://api.codemagic.io/apps/62614885eb4a9ade4d72e9f4/62614885eb4a9ade4d72e9f3/status_badge.svg)](https://codemagic.io/apps/62614885eb4a9ade4d72e9f4/62614885eb4a9ade4d72e9f3/latest_build)

Demo app. 

## Publishing to App Center

Additional script to be added to your Workflow editor between **build** and **publish** as a **post-build script**.

The script publishes app to app-center. 


```
echo 'Installing App Center CLI tools'
npm install -g appcenter-cli
echo "Publishing $aabPath to App Center"
appcenter distribute release \
    --group "Beta testers" \
    --file $aabPath \
    --release-notes 'App submission via Codemagic' \
    --app ivywalobwa/Counter-App \
    --token $APP_CENTER_TOKEN \
    --quiet
```  

- `Beta testers` is the name of your group. 
-  `$aabPath` is set as an environment variable in the workflow editor. It's the path to your .apk/.aab/.ipa artifacts. eg; build/app/outputs/bundle/release/app-release.aab
-  `$APP_CENTER_TOKEN` is set as an environment variable in the workflow editor. It's the token obtained from user settings in App Center.
-  `ivywalobwa/Counter-App` is username/appname. App name on app center should match android app name. 


## Publish Images
![Screenshot (589)](https://user-images.githubusercontent.com/49009293/164490446-8cc452ce-def6-4540-9720-b4ae34dbb09f.png)


![Screenshot (588)](https://user-images.githubusercontent.com/49009293/164490660-71195049-db6e-42c9-892e-da7fb84dfbf1.png)


## Resources:
[Publish app artifacts to App Center](https://docs.codemagic.io/knowledge-base/publish-app-artifacts-to-app-center/)

