
![Git](Images/GitLogo.png)

# **Git Tutorial:**

- ## **What is Version Control?**

Version Control is a system that allows you to revisit various versions of a file or set of files by recording changes. Through version control, one can revert a file or project to a previous version, track modifications and modifying individuals, and compare changes. By utilizing a Version Control System (**VCS**), mistakes with files can easily be rectified.

 **There are 3 types of version control:**

 1. #### ***Local Version Control:***

A Local **VCS** entails one database on the hard disk that stores changes to files.

 2. #### ***Centralized Version Control:***

 The need for collaboration within a developer team on a single file or set of files led to the advent of the Centralized Version Control System (**CVCS**). This system entails a single server storing all changes and file versions, which can be accessed by various clients. This allowed programmers to have more knowledge of team members’ activities with certain files, and gave administrators much more control over divvying up revision privileges.

 3. #### ***Distributed Version Control:***

 A Distributed Version Control systems (**DVCS**) addresses the major vulnerability of the **CVS**: the server as a single point of failure. If a **CVS** goes down, collaborators cannot work with each other on a file or save changes and new versions. Also, in the event of corruption of a central database’s hard disk — with the absence of backups — all work will be lost, except for any portions on local machines.

To prevent this a **DVCS** allows clients to create mirrored repositories. These data backups can be easily be placed on the server to replace any lost information.

- ## **What is Git ?**

Git is a **DVCS** that stores data in a file system made up of snapshots. Each time you save a changed version of your project — called commit — Git creates a snapshot of the file and stores a reference to it.



Git mostly relies on local operations because most necessary information can be found in local resources. Eliminating the need to fetch history information from the server, and allowing one to continue work on a project even when not online or on a **VPN**.

- **Git states:**

Git has three main states:

1. #### **Commited:** 
Data is securely stored in a local database.
2. #### **Modified:**
File has been changed but not committed to the database.
3. #### **Staged:**
Flagged a file’s changed version to be committed in the next snapshot.


- ## **Importing:**

To import an existing project or directory into Git, follow these steps using the Terminal or Command Line:

Switch to the target project’s directory

Example:
    

       $ cd test (cd = change directory)


       Use the git init command

       $ git init


Note: At this stage, you have created a new subdirectory named .git that has the repository files. Tracking has not commenced.

 To start tracking these repository files, perform an initial commit by typing the following:


       $ git add *.c

       $ git add LICENSE

       $ git commit -m “any message here”


- ## **Cloning:**

You can also create a copy of an existing Git repository from a particular server by using the **clone** command:

       $ git clone https://github.com/test

By cloning the file, you have copied all versions of all files for a project. The command  automatically checks out — or retrieves for editing — a copy of the newest version of the project.

- To clone a repository into a directory with another name of your choosing, use the following command format:

       $ git clone https://github.com/test mydirectory


- **The Life Cycle of File Status**



1. After we edit a file, Git flags it as **modified** because of changes made after the previous commit.

2. We stage the **modified** file.

3. Then, we commit staged changes.


- ## **Check File Status**


- To determine the state of files, we use:

       $ git status


- **Tracking and Staging a New File**

- Single File

Track one file only by using the following format:

       $ git add filename

- All Files

Track all files in a repository by using the following command:

       $ git add *

- After using these commands, files are tracked and staged for committing.


- **Committing a File**

After staging one or multiple files, you should commit the changes and record what you did within the commit message:

       $ git commit -m “made change x,y,z”

- This step has committed changes for the file or files (you can have one commit message for multiple files, if applicable) to the HEAD.

- **Committing All Changes**

       $ git commit -a

- This command commits a snapshot of all modifications to tracked files in the working directory.

- **Pushing Changes** 

![Car](Images/CatCoding.webp)

Next, you would push changes to a remote repository.

- Example:

       $ git push origin master

- This command pushes changes from the local **“master”** branch to the remote repository named **“origin”**.

- For cloned repositories, Git will automatically give the name **“origin”** to the server from which you cloned and the name **“master”** to your local repository. However, these names can be changed by the user.

- **Stashing Changes:**

When we are not ready to commit changes but do not want to lose them either, we use :

      $ git stash

- This command temporarily removes changes and hides them, giving us a clean working directory. When you are ready to continue working on the changes, to retrieve the hidden changes,
we simply use :

       $ git stash apply 
       
- ## **Remote Repositories**


In order to collaborate on Git projects, we must interact with remote repositories, versions of a project residing online or on a network. You can work with multiple repositories, for which you can have ***read/write*** or ***read-only** privileges. Teams can use remote repositories to push information to and pull data from.

- **Cloned Repositories**

As mentioned earlier, for cloned repositories, Git will automatically give the name **“origin”** to the server from which you cloned and the name **“master”** to your local branch.
Seeing Your Remotes

 We can view the short names, such as **“origin,”** of all specified remote handles by running the:

       git remote command
 


By using ***git remote -v***, we can view all the remote URLs next to their corresponding short names:

       $ cd example

       $ git remote -v

       remote1 https://github.com/remote1/example (fetch)

       remote1 https://github.com/remote1/example (push)

       remote2 https://github.com/remote2/example (fetch)

       remote2 https://github.com/remote2/example (push)

       remote3 https://github.com/remote3/example (fetch)

       remote3 https://github.com/remote3/example (push)


## [Main page](https://amjadmesmar.github.io/reading-notes/)