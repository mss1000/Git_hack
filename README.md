git config --global user.name 'user26'
git config --global user.email user26@apps.org

cat $HOME/.gitconfig
cat .gitignore

git init
git status
git add . // git status
git commit -m "Innital version"
git log // git status
git ls -files

changes in files:
git status
Discard uncommited changes: git checkout -- dir/files
Commit change: git commit -a -m "dir/file"
git log

Roll back to a previous commit point:
git reset --hard <orig SHA id>


GIT to share:

git init --bare
Add the bare repo as a remote repo for your local repo.
Run the commands:
git remote -v
git remote add origin git@192.168.1.22:/share/MA-Backend.git
git remote -v

Push the local repo to the remote repo.
Run the commands:
git remote show origin
git push origin master
git remote show origin

Clone the shared, remote repo to a local repo on your second development host. (New host)
Run the commands:
mkdir /root/Development
cd /root/Development
git clone git@192.168.1.22:/share/MA-Backend
git log
git status
git remote -v
git remote show origin

Fetch the remote repo to the first development host.
Run the command:
git fetch origin

Identify the files with differences between the local master and the remote origin master.
Run the command:
git diff --stat master origin/master  // git diff master origin/master README.md

git commit -a -m "Updated README.md to reflect code changes from user26 and user27."

Merge commits from both branches - favoring the local master for any files with conflicts.
Run the commands:
git log
git merge -s recursive -X ours origin/master
The -X ours flag used with the merge operation directs Git to favor the local master branch for any files with conflicts
between the two branches. This means your latest version of README.md that you just edited on this host will be
favored.

 git config --global push.default matching
git push --set-upstream origin 
git pull origin master
git push origin master

curl -u 'mss1000' https://api.github.com/user/repos -d '{"name":"Date_File","description":"Raspberry Pi - record date in file"}'
git remote add origin  https://github.com/mss1000/Date_File.git
git push origin master

…or create a new repository on the command line

echo "# Date_File" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/mss1000/Date_File.git
git push -u origin master
