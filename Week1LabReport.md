# Week 1 Lab Report
*How I, Haesol Jung, was able to log into a course-specific account on ieng6*
## 1. Installing Visual Studio Code
Go to the official Visual Studio Code [website](https://code.visualstudio.com) and download the correct version of VS Code\
according to your operating system. Follow the instructions to complete the installation and when finished, you should\
be able to open a tab that looks like the image below:\
\
<img width="508" alt="vscode installation" src="https://user-images.githubusercontent.com/110417501/212202826-969a8f8c-55eb-495a-9689-ed1d0af5babe.png">
\
## 2. Resetting your CSE 15L Account
First find your course-specific account for this course at this [website](https://sdacs.ucsd.edu/~icc/index.php).\
Then from there a link that allows you to reset your password should appear.\
From this point on everything should be fairly intuitive but if not, feel free\
to use this [tutorial](https://docs.google.com/document/d/1hs7CyQeh-MdUfM9uv99i8tqfneos6Y8bDU0uhn1wqho/edit) to help navigate the process!

## 3. Remotely Connecting your terminal to UCSD CSE
> If you are on Mac, please skip to step number 3.

1. Install **git** for Windows using this [download link](https://gitforwindows.org)
2. Change your default terminal to use the just-installed **git bash** in Visual Studio Code using these [instructions](https://stackoverflow.com/questions/42606837/how-do-i-use-bash-on-windows-from-the-visual-studio-code-integrated-terminal)
3. To use ssh, open a new terminal in VS Code by pressing **Ctrl(Windows) or Command(Mac) + `**
4. In the terminal, type the following comand except with "zz" replaced by your individual course-specific account's letters.\
`ssh cs15lwi23zz@ieng6.ucsd.edu`
5. After pressing enter, you should receive a message not unlike the one below:
```
⤇ ssh cs15lwi23zz@ieng6.ucsd.edu
The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```
6. Now, type "yes" in the terminal and right after, when prompted for a password, enter the new password you made previously\
in the section "Resetting your CSE 15L Account". If you have succesfully logged in, you should see a message similar to this:
<img width="468" alt="succesfullogin" src="https://user-images.githubusercontent.com/110417501/212238877-aae30eab-f929-4a56-ba6c-4f5c01b8574e.png">

> NOTE: there will be no visible characters when typing out your password but it is a common terminal feature that is used\
> to protect your privacy.

**Congrats!** You have successfully connected your computer(the client) to a computer in the CSE Basement(the server).\
Any commands you run now will run on that server. How exciting!
## 4. Running Commands on Terminal
**Some important commands you should try implementing are:**
1. cat <path1> <path2> ... - Used to print the contents files given by the paths
2. ls <path> - “List” Used to list the files/folders in the given path
3. pwd - “Print working directory” Used to display the current working directory
4. cd <path> - “Change Directory” Used to change the current working directory to the given path\

**Below is an example of what some sample command inputs and outputs look like:**

<img width="500" alt ="samplecommands" src="https://user-images.githubusercontent.com/110417501/212436525-42c78ae3-c704-4d6f-bc34-ff81eed6f005.png">

> Remember that when you are done testing commands on the remote server, you can also try running these commands on\
  your own computer as well. To leave the remote server, simply run the command `exit`.
