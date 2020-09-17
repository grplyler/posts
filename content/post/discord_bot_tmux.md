+++
author = "Ryan Plyler"
title = "Run Discord Bot in tmux"
date = "2020-09-15"
description = "How to run discord bot in the background with tmux"
tags = [
    "tmux",
    "nodejs",
]
categories = [
    "sysadmin",
]
#series = ["Themes Guide"]
#aliases = ["migrate-from-jekyl"]
+++


**Log into server**

```
ssh root@myserver.dev -p 22000
```

**Navigate to folder**

```
cd /opt/tecbot
```

**Start tmux**

Creates a new tmux sesions with name "tecbot"

```
tmux new -s tecbot
```

**Pull git updates**

```
git pull
```

**Run Bot**

```
node index.js
```

**Disconnect from tmux session**

Hit Ctrl-B then D

**To Exist tmux session**

Hit Ctrl-D until the last window exists.

**List tmux sessions**

```
tmux list-sessions
tecbot: 1 windows (created Tue Sep 15 21:56:05 2020) [211x46]
```

**Reconnect to session by name**

```
tmux a -t tecbot
```

## A Better Solution: pm2

*Comming soon*

