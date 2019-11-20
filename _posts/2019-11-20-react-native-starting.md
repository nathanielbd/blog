---
layout: post
title: Let's write React Native: Getting started
categories: walkthrough
---

React Native is a mobile application framework. It is open-source and allows you to develop web, Android, and iOS applications by writing code that is essentially React Javascript.

This tutorial will walk you through how to get started with React Native as soon as possible with minimum environment requirements. It is meant to be accessible to complete beginners.

There are a couple options to choose from if you want to get started quickly.

#Snack

Snack is the easiest way to quickly get started with React Native. It only requires a browser and an internet connection. You can access it at [snack.expo.io](snack.expo.io). 

I've used online code editors such as CodeSandbox before. Snack seems to be one of the better ones as you can save projects to an easy-to-remember url, import github repositories, and test the app all within your browser. Like any online code editors, however, it has its pitfalls. At the very least, Snack is a great quick testing environment.

#Expo CLI

The command line (also called the 'terminal') is a program the accepts input from the user not from buttons and menus (graphical interfaces) but as text commands. There are other programs that can be run from inside the command line called command line interfaces (CLIs). On Windows, you can check out the terminal by pressing the Windows key and typing 'cmd.' On Ubuntu, press the Super key and type 'terminal.' On a Mac, type Command-Spacebar and search 'terminal.'

The company that created Snack also has an easy CLI that does not require Android Studio or Xcode to begin. The only requirement is a recent version of Node.js (at least 10 LTS). Node.js is a runtime environment for Javascript that allows you to execute it outside of a web browser (ex. on the command line or on a server). If you're not sure what version of Node.js you have installed, if any, run ``node -v`` in the terminal. To install Node, go to [https://nodejs.org/en/download/](https://nodejs.org/en/download/) and follow the instructions for your platform. The easiest way to upgrade your Node version on Windows is to simply reinstall Node with the desired version. On Linux and Mac, run ``sudo npm install n -g`` and ``sudo n stable`` in the terminal.

You now have Node on your computer! The last thing you need to do get the Expo CLI is run ``npm install -g expo-cli``.

For the next walkthough, you'll need to have a blank project. If you chose Snack, you'll start with blank project. It isn't much harder as you simply run ``expo init``.
