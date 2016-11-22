---
layout: post
title: make bittorrent go faster 
---
<p>I never realized this before, but you can in fact make bittorrent go a LOT faster if you are behind a NAT box by correctly configuring port forwarding. All you have to do is make sure that ports 6881-6899 (or if you like with newer versions, 6999) get forwarded to your local machine. You can get your local address, if you're on OS X, using the command ifconfig. </p><p>How to know it's working? Fire up Bram Cohen's version of BitTorrent, open the peer details window. If you see on the left column, any "r"s then it's working. If it's all "l"s then not working. L/R means the connection was started either Locally or Remotely. And only with NAT fixed can you get the remote ones. </p><p>Which basically means you can now talk to all of the other stupid people who are stuck behind a NAT and haven't fixed it yet (or can't) and you get tons more speed from them. </p>
