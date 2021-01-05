---
layout: post
title: Custom Git Credential Helper
---
Surprisingly Git makes it is incredibly easy to create and use your own credential helper. There is a simple contract and if you follow it in literally no time you can get it done.

For example, you can whip `git-credential-from-env` bash script that pulls credentials from environment variables:

```
#!/bin/sh
echo "protocol=https"
echo "host=github.com"
echo "username=$(printenv GITHUB_USERNAME)"
echo "password=$(printenv GITHUB_TOKEN)"

```
Next you install the script into /usr/bin directory and configure git to use this helper with the following command:

```
git config --global credential.helper from-env




```
This is it! Now your automation script can carry out any Git operation and seamlessly pass authentication handshake without a single line of code.

Done! ✅
