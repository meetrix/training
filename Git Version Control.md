Git is a free and open source distributed version control system designed to handle from small to very large projects with speed and efficiency.

1. Allow multiple users to collaborate on a single project.
2. Keep version handling and controlling in an organized manner and many many more.

Basic reference:
 1. https://git-scm.com/book/en/v2
 2. https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf
 
You can keep a remote git repository in GitHub, BitBucket or any other system for version controlling. Let us start with GitHub:

##### 1. CREATE A GITHUB ACCOUNT:
		       https://github.com
	 You also can create an account in BitBucket too.
		       https://bitbucket.org
	 Remember your username and password since they will be required frequently in the future.

Use Terminal from this point onwards to type commands.

##### 2. CLONE A REMOTE REPOSITORY:
		       git clone <url>
	 Here, 'url' is the url of the git repository.
	 This will clone (or copy) the repository and you can see inside the project using 'cd <repo-name>' and 'ls' in terminal too.

##### 3. DOING CHANGES IN A SEPARATE BRANCH:
	 This is the most important fact that should be considered. 
	 It is the best practice to change or add your features in a separate branch in git, instead of using 'master' branch. The 'master' is the main branch managed in a git repository. 
	     
         You can see your current branch (the highlighted one) and other branches:
		        git branch	
            
	 Create a new branch and move to that branch:
		        git branch <branch-name>
		        git checkout <branch-name>
	 Or you can achieve these both commands at once:
		        git checkout -b <branch-name>
	 The <branch-name> should be meanongful enough to understand the purpose of it and specially not a lengthy name.
	   
         To move to an already existing branch:
		        git checkout <branch-name>
            
	 Delete a branch:
		        git branch -d <branch-name>
	 
##### 4. COMMIT CHANGES:
	 Lists all new or modified files to be commited:
		        git status
            
	 Shows file differences not yet staged:
		        git diff
            
	 Add changed files:
	   	      git add <file-name>
	 The <file-name> is the name of the changed file.
       
	 You can use this to add all files:
		        git add -A
	 But the best practice is only adding changed files specifically.
       
	 Commit them with a commit message for clarification:
		        git commit -m <commit-message>

##### 5. SYNCHRONIZE CHANGES:
	 Uploads all local branch commits to GitHub:
		        git push origin <branch-name>
	 This will require to give your username, password.
       
	 Obtain updates of a specific branch from remote repository(To get updates by other contributors) :
	          git pull origin <branch-name>
            
	 Get all updates of the repository:
		        git fetch
            
	 Merging Branches:
		        git merge <branch-name> 
	 This will merge your current branch with the <branch-name> branch.
	  
##### 6. SAVE CHANGES:
		        git stash
	 This will temporarily store all the modified files by tracking the branch to last commit.

##### 7. REVIEW HISTORY:
	 List version history of current branch:
	  	      git log 
	 Type 'q' to exit.
       
	 Get changed files of a commmit:
		        git show <commit-num>
	 The <commit-num> can be obtained from 'git log'.
	  
         See the diffrence between two commits:
		        git diff <commit-1> <commit-2>
	   
##### 8. CREATE A REPOSITORY:
	 You can create a repository from your account by simply giving a name for it.
	 Initialize the Repository:
	 Go inside your project folder which you wanted to add on git, and type this:
		        git init
            
	 Then add files: 
		        git add -A
            
	 Commit initial files:
		        git commit -m "Initial Commit"
            
	 Add the remote repository to track changes:
		        git remote add origin <repo-url> 
            
	 Balance the changes:
		        git pull origin master
		        git push origin master

##### 9. ADD A README FILE:
	   It's the best practice to add README file for your repository in order to facilitate others and yourself later too.
	   The README can contain,
		        How to setup the project
		        Basic commands needed
		        Specific details about the features and changes

##### 10. ADD A .gitignore FILE:
	  The best practice is to specify intentionally untracked files that Git should ignore. This includes files created in IDE used, and other files created when building a project such as:
		        *.iml
		        .gradle
		        /local.properties
		        /.idea/*
		        node_modules/
		
	   Those file names should add in .gitignore file as above.	

##### 11. VIEW THE REMOTE REPOSITORY:
    		    git remote -v 
		
##### 12. RESOLVING CONFLICTS:
	  Conflicts occurred mostly when merging two branches or when pushing changes to the remote.
	  First, the conflicted file should be modified appropriately. 
	  Then add those changes:
		        git add <file-name>
		        git commit -m "Conflict Resolved"
