---
layout: post
title: Connecting to SQL Server with Windows authentication from outside it's domain
published: true
---


I've configured all kinds of convoluted ways for connecting from A to B with SQL Server. SSH tunnels, proxies, VPNs and so on. Odd that I'd never until recently, needed to use Windows Auth across a network to get to SQL Server on  a a different Domain.  I'd usually be accessing via a bastion in the target domain or been using SQL Server level authentication.


SQL Server Management Studio, when using Windows authentication will want to use your native OS domain credentials. But there is a way to get it to use alternate domain credentials. It's a simple as starting SSMS from a cmd prompt like this:


`runas /user:TCP\timp /netonly ssms.exe`


_Where TCP\timp is my domain account and I'm assuming ssms.exe is in your local directory here (otherwise provide the full path)._



You'll get a prompt for your password. SSMS will then fire up. Give it the Server\Instance name you want and you are away. (Ignore the greyed out username)

