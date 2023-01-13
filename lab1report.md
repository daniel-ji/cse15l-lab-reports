# Week 1 Lab Report

This tutorial will cover how to log into a course-specific account on ieng6. 

## Installing VSCode
Visit [Visual Studio Code](https://code.visualstudio.com/) and install it on your computer. The site should look something like this: 

![Visual Studio Code Site](/vscodesite.png)

After downloading and opening VSCode, the application should look something like this: 

![Visual Studio Code](/vscode.png)

If the application opens and you see a similar screen, you are done installing VSCode. Congratulations! Feel free to explore VSCode and creating new files and folders or opening existing files and folders. If you want, you can create a folder for this CSE 15L class.

## Remotely Connecting
To remotely connect to ieng6, we will be using the terminal. Since we are using a Mac, we won't need to install Git Bash to connect and can just use the built-in `ssh` command in the Mac OS to connect. 

First, open a terminal on VSCode. On Mac, the shortcut is ``ctrl + ` ``. 

The terminal will appear on the bottom of the screen and look something like this: 

![VSCode Terminal](/vscodeterminal.png)

To connect, run the following command in the terminal: 

```
$ ssh cs15lwi23zz@ieng6.ucsd.edu
```

with `zz` replaced by whatever your username is for the course-specific account.

> Note: a prompt may appear regarding the authenticity of the host, asking if you want to continue to connect and you can just type `yes`. 

After entering your password for your account, you should be successfully connected!

Some text should be printed out to the terminal looking like this: 
```
Last login: Thu Jan 12 16:22:54 2023 from 100.81.34.164
Hello cs15lwi23avm, you are currently logged into ieng6-203.ucsd.edu

You are using 0% CPU on this system

Cluster Status 
Hostname     Time    #Users  Load  Averages  
ieng6-201   17:20:01   17  0.04,  0.12,  0.13
ieng6-202   17:20:01   14  0.01,  0.06,  0.07
ieng6-203   17:20:02   14  0.10,  0.18,  0.15

 
Thu Jan 12, 2023  5:20pm - Prepping cs15lwi23
```

## Trying Some Commands

Now that you have successfully connected to ieng6, it's time to run some commands. 

Feel free to try any commands from what we learned this week. Some commands you can try are: `cd`, `ls`, `pwd`, `mkdir`, `touch`, `mv`, and `cp`. Try to run them with some flags as well. For example, you should see something similar to the following image after running `ls -la`: 

![ls-la image](/lslaimage.png)

To exit the remote server, you can enter the following shortuct in the terminal: `ctrl + d` or type `exit`. 

## Conclusion

After completing the final step, you are now able to connect to ieng6 using `ssh` in a VSCode Terminal! Congratulations! 