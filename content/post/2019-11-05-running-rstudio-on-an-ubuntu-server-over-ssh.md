---
title: Running RStudio on an Ubuntu server over SSH
author: Arseniy Khvorov
date: '2019-11-05'
slug: running-rstudio-on-an-ubuntu-server-over-ssh
categories:
  - ubuntu-server
---

## The idea

RStudio server listens to port 8787 while it's running on the server.

We need to establish an SSH tunnel from a local port (e.g. 1234) to the remote server's port 8787.

Once that's done (instructions below), open a web browser, type it `localhost:yyyy` where `yyyy` is a local port the tunnel's been set up to forward to (e.g. 1234). RStudio login page will greet you. Use you server's username and password.

## Open SSH (linux, mac, windows 10)

```
ssh -f -N -L 1234:localhost:8787 username@xxx.xx.xxx.xx
```

Where `1234` is the local port, `8787` is the remote port, `username` is the username you use to login to the server and `xxx.xx.xxx.xx` is the server's IP address.

`-L` is the option that makes the tunnel.

`-f` and `-N` make ssh go into background. Without them you will also login to the server through the terminal (in addition to establishing the tunnel) but note that the tunnel will only live for as long as your terminal session does (since ssh is not in the background). Also note that these options work on windows but the terminal hangs, so you have to mercy-kill it (it won't kill the tunnel).

Open a web browser, type in `localhost:1234`

## Putty (windows)

* Session (Basic options for your PuTTY session)

  * Host Name: `username@xxx.xx.xxx.xx` where `username` is the username you use to login to the server and `xxx.xx.xxx.xx` is the server's IP address.
  
  * Connection type: ssh
  
* Connection-SSH-Tunnels (Options controlling SSH port forwarding)

  * Source port: `1234`
  
  * Destination: `xxx.xx.xxx.xx:8787` where `xxx.xx.xxx.xx` is the server's IP address

Once you open the session, the tunnel will be established. The tunnel will disappear once the Putty session ends.

Open a web browser, type in `localhost:1234`
