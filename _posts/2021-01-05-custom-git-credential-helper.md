---
layout: post
title: Custom Git Credential Helper
---
Surprisingly Git makes it incredibly easy to create and use your own credential helper. There is a simple contract and if you follow it then literally in no time you can get it up & running. 🌟

For example, you can quickly put together `git-credential-from-env` bash script that pulls credentials from environment variables:

```
#!/bin/sh
echo "protocol=https"
echo "host=github.com"
echo "username=$(printenv GITHUB_USERNAME)"
echo "password=$(printenv GITHUB_TOKEN)"
```
Next you copy the script file into `/usr/bin` directory, make it executable and configure git to use this helper with the following command:

```
git config --global credential.helper from-env
```
This is it! Now your automation script can carry out any Git operation and seamlessly pass authentication handshake without a single line of code.

Done! ✅
