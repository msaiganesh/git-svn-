# pushing to git from svn 
If your SVN project uses the standard /trunk, /branches, and /tags directory layout, you can use the --stdlayout option instead of manually specifying the repository’s structure. Run the following command in the ~/GitMigration directory:

```git svn clone --stdlayout --authors-file=authors.txt
<svn-repo>/<project> <git-repo-name>
```

Non-standard SVN layouts

If your SVN repository doesn’t have a standard layout, you need to provide the locations of your trunk, branches, and tags using the --trunk, --branches, and --tags command line options. For example, if you have branches stored in both the /branches directory and the /bugfixes directories, you would use the following command:

```git svn clone --trunk=/trunk --branches=/branches
--branches=/bugfixes --tags=/tags --authors-file=authors.txt
<svn-repo>/<project> <git-repo-name>
```

initialise the git repository 
``` git init 
```
  
push 

```
git push origin refs/remotes/*:refs/heads/*

```
This command pushes all the remotes created during subversion to git migration, visible with git branch -a. Includes all deleted / merged branches / tags though!

## Else svn2git is a good tool

svn2git tool solves above two problems with native commands. Before we use this tool, we need to install it. It requires git, git-svn, and ruby installed. svn2git is a ruby wrapper around git’s native SVN support through git-svn. You can install the pre-requisites using below command.


```
$ sudo apt-get install git-core git-svn ruby

```
Once you have the necessary software on your system, you can install svn2git through rubygems, which will add the svn2git command to your PATH.

```
$ sudo gem install svn2git

```
Once svn2git is installed, use below commands to migrate SVN repository to Git.

First create the authors file using above command.
Find the initial svn revision from above svn log command.
Use below command to create local git project from svn repository.

```
svn2git URI/svn --authors authors.txt --revision 1

```

