+++
author = "Ryan Plyler"
title = "SSH Tunneling"
date = "2020-09-16"
description = "How to do secure tunneling and local port fowarding with SSH"
tags = [
    "ssh",
    "shell",
    "bash",
    "security",
    "networking",
]
categories = [
    "networking",
]
#series = ["Themes Guide"]
#aliases = ["migrate-from-jekyl"]
+++

## SSH Tunneling (Port Fowarding)

*AKA, Poor-mans VPN Method*

**Use Case**

Let's say you have secret service running on port `4444` of you server `code.red.com` that, I don't
know, is a code scanner with a Web Interface. When you run that scanner, it fires up it's web GUI report
and listens on a local port `4444`

Now, you could open up port 4444 to to the world and just access it via `code.red.com:4444`. Or
you could remote in via VNC for instance, but that would require a graphical desktop and a VNC service
which can be frought with security issues.

Instead, you can create an SSH tunnel as long as you have SSH credentials and access that will let you
access that service on you local machine, via a forwarded, or tunneled port.

**Creating the Tunnel**

The following command will create an SSH tunnel from your machine, port 8080 to your server's *local*, not publically accessible
port `4444`.

```
ssh -L 8080:localhost:4444 root@code.red.com
```

If you have ssh access, this will log you in via SSH as usuall, BUT, it will also start listening on a local port `8080`.

**Explanation**

The `-L` instructs ssh to create a *local* port forward. Note, this is *local* to the remote machine, so that
can be a bit confusing at first.

`8080` is the port on your local machine that will listen for connections and foward them to port `localhost:4444` on your server.

`root@code.red.com` is the user account and domain of your server. You could easily use an IP address as well.

**Tunneling without a shell**

If you just want to forward the port, and dont need shell access, you can use the following command:

```
ssh -N -L 8080:localhost:4444 root@code.red.com
```

The `-N` just means, "no login" and ssh will continue to hold that connection until you `Ctrl-C` out of it.

### Conclusion

A nice perk of this methods is that your connection to whatever service is encrpted with the same security as an SSH connection. This allows you to securely access and potentially insecure service from the inside. There are also other kinds of SSH tunneling and port forwarding that I encourage you to look into, but those are beyond the scope of this little writeup.
