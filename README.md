# spotify-playlist-gpt-apple-shortcut
Shortcut for apple devices to use chatGPT and create a playlist on spotify using developer credentials

This work is an inspiration from [S-GPT](https://www.macstories.net/ios/introducing-s-gpt-a-shortcut-to-connect-openais-chatgpt-with-native-features-of-apples-operating-systems/) which is more powerful and useful. S-GPT only works with apple music and any shortcuts that already exists on the platform. I believe it is for a good reason as well. I started this as an effort to learn apple shortcuts eco system and using Spotify and OpenAI API's. There were several alternative thoughts to host the logic behind a webservice and abstract most of the developer nerdy stuff. But I had fun making this work only with shortcuts app and the available API's. I hope anyone uses this to play around or enhance will also enjoy doing so.

# Warning
These shortcuts heavily use spotify and openAI developer credentials like client ID, secerts and Keys. So please use caution to not misuse or be a victim of any hacks. Protecting developer keys and secrets are very important to keep you data safe, so never share them anywhere.

# Shortcuts download

| Shortcut | Download link|
| --- | --- |
|![Spotify referesh token gen](/images/spotify-refresh-token-gen-shortcut.png) | [icloud link to download spotify refresh token gen shortcut](https://www.icloud.com/shortcuts/046c31fd370945ea961f243e9b2cf382)|
|![Spotify playlist GPT](/images/spotify-playlist-gpt-shortcut.png)| [icloud link to download spotify playlist gpt shortcut](https://www.icloud.com/shortcuts/e5ba1ca663f844c28a34cc8b415d3f9a)|

# Developer credentials needed

## OpenAI API Key

| Account | Links |
| --- | --- |
|![openai key](/images/openai-api-key.png) | [Link to the account portal](https://platform.openai.com/account/api-keys)|


## Spotify Developer account

| Account | Links |
| --- | --- |
| ![spotify app cred](/images/spotify-developer-credentials.png) | [Link to account dashboard](https://developer.spotify.com/dashboard)|


# Onetime setup process
## Spotify refresh token gen
Spotify playlist gpt is the main shortcut which needs a `refresh_token` from the account api, which authorizes a developer app to be eligible to create and modify playlist on a users behalf. To get the `refresh_token` I tried to use the spotify refresh token gen shortcut which has no other connection except to facilitate obtaining this `refresh_token`. If you already have authorized a user with `scope` [playlist-modify-private](https://developer.spotify.com/documentation/web-api/concepts/scopes#playlist-modify-private) you can skip the spotify refresh token gen shortcut installtion.

1. Add spotify refresh token gen shortcut to your device from the above link
2. While adding a setup process will ask you for spotify developer app credentials `client ID` , `client secret` & `redirect uri` (which you need to create separately, kindly follow [spotify developer guide](https://developer.spotify.com/documentation/web-api/tutorials/getting-started) for the same)
3. After adding the shortcut run it to guide getting `refresh token`
4. The authcode gets generated from a weburl setup as your redirect uri in the developer portal, spotify after authorizing the user will append this onetime short lived code on the url.
5. Grab this code from the url and input to the shortcut as prompted (you will need to go back to the shorcut app for the prompt to show)
6. Once the authcode is provided and on successful api call, the `refresh token` will be copied to the clipboard. 
7. The `refresh token` has longer validity than the access token or any other token to my knowledge as per OAUTH 2.0 spec.

## Spotify playlist gpt
To get spotify playlist gpt shortcut working we need the `refresh token` obtained from the previous step, `client ID`, `client secret` and API key from OpenAI `secret key`. Upon adding the shortcut to your device these information will be requested to persit on your local device. So you do not have to keep entering them. But excersie caution while sharing as anyone inspecting the shortcut with your data filled can take advantage of them.

1. Add spotify playlist gpt shortcut to your device from the above link
2. While adding a setup process will ask you for spotify developer app credentials `client ID` & `client secret` (which you need to create separately, kindly follow [spotify developer guide](https://developer.spotify.com/documentation/web-api/tutorials/getting-started) for the same). The `refresh token` generated from previous step using the shortcut or by someother method. OpenAI `secret key` to call the v1/chat/compeletion api
3. Once the setup is done, it is expected to not need doing any of this everytime. But I could be wrong as the time of writing this I didn't have any problems. Hope people seeing this in future will have more context and knowledge to debug or fix as needed.

## Happy hacking!!!