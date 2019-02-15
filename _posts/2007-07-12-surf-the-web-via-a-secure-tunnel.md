---
layout: post
title: 'Surf the web via a secure tunnel'
date: 2007-07-12 09:46
comments: true
categories : [Apple/OSX, Snippets]
---  

On occasion you may find yourself developing a site for a client who during the development phase will limit access to the site to a certain set of IP Addresses. This can be a real pain to deal with if your local IP is always changing.

To deal with this I always get the client to grant access to the damagestudios.net IP address (which is fixed and located in a cage in Santa Clara)

I then create a secure ssh tunnel and configure either Firefox or Camino to use the damagestudios.net site as a proxy.

Here’s what you need to accomplish this:
<ul>
<li>openSSH client (OS X has this built in)
<li>access to an openSSH server
<li>10 minutes
</ul>

First you need to create the tunnel. We need to know the name or IP address of the server you will be tunneling to, as well as your login name and password on that server.

<strong>For the example I'm using my information, you'll need to replace the username and servername with your information</strong>

Now fire up terminal or iTerm and enter the following into your terminal window.

<code>ssh -D 8080 -f -C -q -N fusion94@damagestudios.net</code>

You will then be prompted for your password, which you should enter. Your ssh tunnel is now in place.

Here's a quick overview of what those switches mean:

<strong>-D 8080</strong>: This basically does a lot of dynamic stuff and makes it behave as a SOCKS server. Of course you could use any non privileged port here (above 1023).
<strong>-f</strong>: This will fork the process into the background after you type your password.
<strong>-C</strong>: Turns on compression.
<strong>-q</strong>: Quiet mode. Since this is just a tunnel we can make it quiet.
<strong>-N</strong>: Tells it no commands will be sent. (the -f will complain if we don’t specify this).

So now that the tunnel is made we will need to configure Firefox or Camino to use this tunnel.

To do this open Firefox or Camino and type the following into the address bar:

<strong>about:config</strong>

This will bring up quite a bit of options but you can use the Filter: bar to filter out some of the results. To do this type in <i>proxy</i> into the filter bar.

There are 6 line items we need to deal with.
<ul>
<li>network.proxy.no_proxies_on : localhost, 127.0.0.1, 192.168.0.0/24, .damagestudios.net
<li>network.proxy.socks : 127.0.0.1
<li>network.proxy.socks_port : 8080
<li>network.proxy.socks.remote_dns : true
<li>network.proxy.socks_version : 5
<li>network.proxy.type : 1
</ul>

<strong>For the example I'm using my information, you'll need to replace the .damagestudios.net with your information</strong>

Once you made these changes you are set. You can confirm that you are serving from the fixed IP address by going to <a href="http://whatismyip.com">What is my IP</a>.

If you ever need to verify that the tunnel is up all you need to do is enter this into the terminal.

ps -aux | grep ssh

You should see a line similar to this:
fusion94   499   0.0 -0.1    29424   2576  ??  Ss    8:31AM   0:03.01 ssh -D 8080 -f -C -q -N damagestudios.net

There’s a lot more that can be done from here such as configuring things on the server for keeping the connection alive. You could also setup your server to allow a key based login so you could have your tunnel open when you start up your computer.

Regardless that's a blog posting for another day.

