---
title: "VS-TAC - Cordova version"
date: 2015-07-17T00:00:00+00:00
publishdate: 2015-07-17T00:00:00+00:00
lastmod: 2015-07-17T00:00:00+00:00
tags: ["Apps", "Apache Cordova"]
disableNextPrev: true
hidden: true
comments: true
draft: false
---

<p><a href="http://aka.ms/cordova" target="_blank">Visual Studio – Tools for Apache Cordova</a> is a great addition to Visual Studio. It allows us to develop <a href="http://cordova.apache.org/" target="_blank">Apache Cordova</a> applications while taking all the advantages of Visual Studio. I started using it with VS 2015 RC for one of the application I am developing using <a href="http://ionicframework.com/" target="_blank">Ionic</a>. </p> <p>Most of the work is done by visual studio using a new npm package called vs-tac, this package takes care of building and deploying your application using collection of cordova tools.<!--more--> The important thing to understand is that Visual Studio is not doing anything like MSBuild, instead it just uses core cordova tool to build and deploy your application.</p> <p>In the application I was developing, I wanted to use one of the Cordova plugin from npm.&nbsp; Cordova plugins are being migrated to npm and old plugins are also available <a href="http://cordova.apache.org/announcements/2015/04/21/plugins-release-and-move-to-npm.html" target="_blank">in cordova’s old registry.</a> If you want to use plugins from npm, your cordova cli version must be 5.0.0 or higher. VS 2015 RC currently uses version 4.3.0 which doesn’t support plugins from npm. So, you need to upgrade the version of cordova-cli Visual Studio uses.</p> <p>It is very simple to upgrade the version of cordova tools Visual Studio uses. All you need to do is, open up the config.xml in designer and update the cordova cli version in platforms tab</p> 

{{% img "images/image_3.png" %}}

<p>If you prefer, you can directly update the version you want to use in taco.json.</p>