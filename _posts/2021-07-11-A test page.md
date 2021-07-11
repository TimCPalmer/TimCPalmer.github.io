---
layout: post
title: Connecting to SQL Server with Windows authentication from outside it's domain
published: true
---


I've had all kinds of messy contrived (but neccesary) ways in place for connecting from A to B, SSH tunnels, proxies, VPNs and so on. Odd that I'd never until recently needed to use Windows Auth across a network to get to SQL Server on Domain.  I'd usually be in there via a bastion in the domain , or perhaps using SQL Server level authentication (yeah I know - blame app vendors for that one most of the time!!)


Obviosuly by default SQL Server Management Studio, when using Windows authentication will want to naturally use your native OS credentials. But there is a way to get it to use alternate domain credentials. Fire up a cmd prompt and do the following


`runas /user:TCP\timp /netonly ssms.exe`


Where TCP\timp is my domain account and I'm assuming ssms.exe is in your local directory here (otherwise provide the full path).



You'll get a prompt for your password. SSMS will then fire up. Give it the Server\Instance name you want and you are away. (Ignore the greyed out username)

