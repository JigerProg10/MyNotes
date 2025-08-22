# Git & Github Notes

git is a software which makes copy of the current local repository, incremental that is only changes made.

to initialize git watching over project use:
`git init`
to make a git server repository locally use:
`git init --bare` , this is used to be as server , more in `git remote`

after initialize git local repo :
we need to add files to watched for changes
`git add <files> <folders>` , this way files and folders can be watched and put to staged mode.
use `git add . ` to add all the files.

if you want certain files and folders not to be watched or staged, make a `.gitignore` file in root directory and add names of files and folders
.env is hidden file and secrets/ is folder
.gitignore

```
.env
secrets/
```

then add this file in stage mode using`git add .gitignore`.
to unstage and untrack files if accidently staged them rather than to be ignored using .gitignore. use `git rm --cached <file>`, this removes file from staging as well as `--cached` ensures that its also removed from cached storage.

after all files are staged , we want its snapshot so we commit this changes.
`git commit -m "message here"`, with each commit we need to mention a message associated with it using flag `-m` followed by `""` and message inside it.

now that snapshot is taken you can review these snapshots using
`git log` or use `git log --oneline` for oneline for each commit. here head shows the current working snapshot.

if you want to review a specific snapshot/commit use `git checkout <hash>`, where hash represents uniquelly each commit.

to check difference between two commits use : `git diff <commit1hash> <commit2hash>`
or check difference between current and previous : `git diff HEAD HEAD-1`
to switch to a particular branch use: `git switch <branchname>`
to create as well as instantly switch to it use: `git switch -c <newbranchname>`

to list all branches use : `git branch`, use `-a` flag to also see remote branches as well.

by default github uses main as their main working branch while git uses master branch as working.
to resolve this we can move/rename current branch to another.using:
`git branch -m main`

to add a remote repository into our git repo sources list like github ones.
we use `git remote add origin <giturl.git>`, add flag add new remote connection origin is the name of that connection.
`git pull origin main` pulls the snapshot of remote repo branch main to local repo main
`git push origin main` pushes the snapshot changes of local repo branch main to remote repo branch main.

just to fork or get a copy of a repo we use : `git clone <giturl.url>`, this only makes copy and have no actual relation with giturl

for github to work properly and control flow(push and pull changes), we need to setup ssh keys of local machine to be allowed by github.
we use `ssh-keygen -t ed25519 -C "your_email@example.com"` here replace email with your github emailid.
if your machine doesnt support ed25519 encryption use `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`.

start your ssh client (use openssh or dropbear): `eval "$(ssh-agent -s)"`
then pass and activate your keys to ssh agent `ssh-add ~/.ssh/id_ed25519`, now ~/.ssh/id_ed25519 is usually where keys are stored but you can change depending on your keys.
this will generate a .pub file next to this key file. copy its content and paste it into github

1. if using setting (want to use in all projects/repos)
   Settings >(under Access) SSH and GPG keys > New SSH Key , give it a name or title and paste content of .pub file.

2. if want to use/access certain project
   Project > Settings tab > Deploy Keys > Add Deploy keys > here paste suitable name/title and paste .pub key. here you can choose if this key associated device is allowed to write to modify codebase or not.

this contents of ssh pub file looks like this

```
encryptiontype:hash email/username
```

like
`SHA256:hashcode email@email.com`
