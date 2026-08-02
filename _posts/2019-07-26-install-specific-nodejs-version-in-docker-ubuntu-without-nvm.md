---
title: "Install specific NodeJS version in docker Ubuntu without nvm"
tags: [docker, nodejs, ubuntu]
description: "Let us say you want to install a specific version like 10.15.2 in Ubuntu docker. apt get will only serve whatever is on the Menu of Ubuntu repos. We can…"
original_date: 2019-07-26T05:44:25-07:00
---

Let us say you want to install a specific version like **10.15.2** in Ubuntu docker. **apt get** will only serve whatever is on the *Menu* of Ubuntu repos.

We can download a specific binary version from [https://nodejs.org/download/release/](https://nodejs.org/download/release/v10.15.2/node-v10.15.2-linux-x64.tar.gz)

Sample version will look like this:

<https://nodejs.org/download/release/v10.15.2/node-v10.15.2-linux-x64.tar.gz>

### **Step 1**

Download the binary

```
curl -O https://nodejs.org/download/release/v10.15.2/node-v10.15.2-linux-x64.tar.gz
```

### Step 2

Unzip the tar pack

```
tar xzf node-v10.15.2-linux-x64.tar.gz
```

### Step 3

Ensure node/bin is added to $PATH in Dockerfile

```
ENV PATH="/node-v10.15.2-linux-x64/bin:${PATH}"
```

or in terminal if not using docker

```
export PATH=/node-v10.15.2-linux-x64/bin:$PATH
```

### Step 4

Inside container/terminal should say

```
root@my-image-container-id:/# node -v
v10.15.2
```

### **Files & Stuff**

**Dockerfile**

```
FROM behance/docker-nginx:8.5
COPY /install-stuff.sh /.
RUN sh /install-stuff.sh
ENV PATH="/node-v10.15.2-linux-x64/bin:${PATH}"
```

**install-stuff.sh**

```
#!/bin/bash
set -e
apt-get -y update
apt-get install -y curl
curl -O https://nodejs.org/download/release/v10.15.2/node-v10.15.2-linux-x64.tar.gz
tar xzf node-v10.15.2-linux-x64.tar.gz
```

**Docker Commands**

```
docker build . -t my-image && docker run my-image
docker exec -it <my-image-container-id> /bin/bash
root@my-image-container-id:/# node -v
v10.15.2
```
