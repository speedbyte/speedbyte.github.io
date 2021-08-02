---
layout: post
title: "Command Reference"
date: 1970-01-01
---

      init [--] [<path>...]
           Initialize the submodules recorded in the index (which were added and committed elsewhere) by setting submodule.$name.url in .git/config. It uses the same setting from .gitmodules as a
           template. If the URL is relative, it will be resolved using the default remote. If there is no default remote, the current repository will be assumed to be upstream.

           Optional <path> arguments limit which submodules will be initialized. If no path is specified and submodule.active has been configured, submodules configured to be active will be
           initialized, otherwise all submodules are initialized.

           When present, it will also copy the value of submodule.$name.update. This command does not alter existing information in .git/config. You can then customize the submodule clone URLs in
           .git/config for your local setup and proceed to git submodule update; you can also just use git submodule update --init without the explicit init step if you do not intend to customize
           any submodule locations.

           See the add subcommand for the definition of default remote.

       deinit [-f|--force] (--all|[--] <path>...)
           Unregister the given submodules, i.e. remove the whole submodule.$name section from .git/config together with their work tree. Further calls to git submodule update, git submodule foreach
           and git submodule sync will skip any unregistered submodules until they are initialized again, so use this command if you don’t want to have a local checkout of the submodule in your
           working tree anymore.

           When the command is run without pathspec, it errors out, instead of deinit-ing everything, to prevent mistakes.

           If --force is specified, the submodule’s working tree will be removed even if it contains local modifications.

           If you really want to remove a submodule from the repository and commit that use git-rm(1) instead. See gitsubmodules(7) for removal options.



GeneralCommands

visudo
username ALL=(ALL) NOPASSWD: /bin/login
root ALL=(ALL:ALL) ALL


NetworkManager

etc -> run -> ust/lib -> NetworkManager.conf



    In Device Manager, right-click on the Intel card and select Properties
    Then click on the Advanced tab.
    You will see an option called Wireless mode. Set the mode from 802.11a/b/g to just 802.11b/g.
        This will prevent the card from scanning or accessing the 5Ghz 802.11a band and just leave you with the 2.4Ghz b/g band to work with.



wget "publickey"
sudo apt-key add "publickey"
add a new file in /etc/sources.list.d/example.list

git submodule update --init
git submodule foreach git checkout tags/boost-1.67.0


Disk partitioning.

lsblk uses 1024 to calculate GB and parted uses 1000 and hence there is a difference in the reported size.

rsync include/ does not copy include
rsync include copies include
cp include/ copies include

pgrep -P #id
ps -opid,pcpu --sort=-pid

Themes

~/.config/gtk-3.0/
@define-color base_color #000000;
NautilusWindow * .view {
 background-color: #000000;
}


pushing all branches

for remote in `git branch -r`; do git branch --track $remote; done
git fetch --all
git pull --all

Now you can see all the branches:

git branch

To push all the branches try:

git push --all


    git diff -C #checks for renames.
    git diff --word-diff -U0
    git config -f .gitmodules submodule.xxx.ignore dirty
    git config submodule.xxx.ignore all
    xclip -selection c
    git config --global credential.helper 'cache --timeout=2628000'

====== Synaptic, Mouse ======


cat /sys/bus/serio/devices/serio1/protocol

make sure synaptic_drv.so is present in the /usr/lib
xorg configuratin files should be present in /usr/share/X11/xorg.conf.d
synclient would throw no synpatics drivers loaded error, if the drivers are not loaded

sudo modprobe -r psmouse
sudo modprobe psmouse
xinput --list
xinput enable <id> 
xinput disable <id>


====== Seafile  ======

    xclip -selection c
    readelf --debug-dump=decodedline filename
    sudo ip link set dev mydev address  02:23:45:67:89:ab
    sudo ip tuntap add dev mydev mode tap

    sudo showkey -s
    sudo showkey -k

     
    apt-config dump | grep Dir::Ignore-Files-Silently::
    dead key - circumflex ( circonflexe ) - hat dad because noting happens when you press them by themselves, until you press another key.


====== FFMPEG / EXIFTOOL ======

    identify -format '%[EXIF:*]' DSC_0169.jpg
    exiftool -a -u -g1 image.jpg
    exiftool -p '$filename has date $dateTimeOriginal' -q -f dir
    find ./  -type f -exec md5sum {} \;
    exiftool -b -ThumbnailImage 2014-10-26\ 14.26.28.jpg
    exiftool -s -ImageSize -ExposureTime b.jpg
    exiftool -T -createdate -aperture -shutterspeed -iso dir > out.txt
    find ./ -type f -name '*.jpg' -exec sh -c 'exiftool -b -ThumbnailImage {} > ../thumbs/{}'

    ffmpeg -r 10 -i 0000000%03d.png -vcodec libx264 -crf 25 test.mp4
    ffmpeg -i input.wmv -ss 30 -c copy -t 10 output.wmv
    ffmpeg -i input.wmv -c copy -t 35 output.wmv  % This starts from 0
    recordmydesktop -o /local/tmp/out.ogv --fps 10 --channels 1 --freq 22050 --v_quality 63 --s_quality 10 --workdir
    /local/tmp --on-the-fly-encoding –compress-cache

====== GITLAB ======

    apt-get install gitlab-ce
    /etc/gitlab/gitlab.rb
    gitlab-reconfigure

    sudo gitlab-ctl reconfigure
    DROP DATABASE IF EXISTS "gitlabhq_production
    gitlab-ctl tail # all logs

    ================================================================================
    Error executing action `run` on resource 'execute[create gitlab database user]'
    ================================================================================

    sudo gitlab-rake gitlab:setup

    PG::ConnectionBad: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/var/opt/gitlab/postgresql/.s.PGSQL.5432"?

    netstat -pant | grep postg
    sudo vim /var/opt/gitlab/gitlab-rails/etc/database.yml


    vagrawal@itlx3354:/var/opt/gitlab$ sudo gitlab-ctl status
    run: gitlab-workhorse: (pid 1177) 466078s; run: log: (pid 1173) 466078s
    run: logrotate: (pid 14122) 1675s; run: log: (pid 1180) 466078s
    run: nginx: (pid 1178) 466078s; run: log: (pid 1175) 466078s
    down: postgresql: 1s, normally up, want up; run: log: (pid 1169) 466078s
    run: redis: (pid 1170) 466078s; run: log: (pid 1168) 466078s
    run: sidekiq: (pid 20296) 27s; run: log: (pid 1172) 466078s
    run: unicorn: (pid 1181) 466078s; run: log: (pid 1174) 466078s


/var/log/gitlab/postgresql/current

2017-03-27_09:36:05.16192 FATAL:  could not create shared memory segment: Invalid argument
2017-03-27_09:36:05.16194 DETAIL:  Failed system call was shmget(key=5432001, size=2167676928, 03600).
2017-03-27_09:36:05.16194 HINT:  This error usually means that PostgreSQL's request for a shared memory segment exceeded your kernel's SHMMAX parameter.  You can either reduce the request size or reconfigure the kernel with larger SHMMAX.  To reduce the request size (currently 2167676928 bytes), reduce PostgreSQL's shared memory usage, perhaps by reducing shared_buffers or max_connections.
2017-03-27_09:36:05.16195       If the request size is already small, it's possible that it is less than your kernel's SHMMIN parameter, in which case raising the request size or reconfiguring SHMMIN is called for.
2017-03-27_09:36:05.16195       The PostgreSQL documentation contains more information about shared memory configuration.



apt-get install gitlab-ce
/etc/gitlab/gitlab.rb
gitlab-reconfigure
git submodules, git subtree git subrepo
git config --global credential.helper 'cache --timeout=3600'
git ls-files --



stage | grep 160000
find . -type d -empty -not -path "./.git/*" -exec touch {}/.gitkeep \;

vim /opt/gitlab/embedded/service/gitlab-rails/config/environments/production.rb

sudo gitlab-rails console production
u = User.where(id: 1).first
u.admin = true
u.save!
exit


git pull -X theirs

git fetch --all ; fetches without complaining about local changes.


Gitlab

    curl https://packages.gitlab.com/gpg.key  | sudo apt-key add – 
    sudo apt-get update 
    sudo apt-get install  debian-archive-keyring 
    sudo apt-get install -y apt-transport-https  

Create a file named /etc/apt/sources.list.d/gitlab-ce.list deb https://packages.gitlab.com/gitlab/gitlab-ce/ubuntu/ trusty main deb-src https://packages.gitlab.com/gitlab/gitlab-ce/ubuntu/  trusty main sudo apt-get update sudo apt-get install gitlab-ce gitlab:  To configure and start GitLab, RUN THE FOLLOWING COMMAND: sudo  gitlab-ctl reconfigure GitLab should be reachable at http://server.domain.de  Otherwise configure GitLab for your system by editing  /etc/gitlab/gitlab.rb file and running reconfigure again. For a  comprehensive list of configuration options please see the Omnibus  GitLab readme https://gitlab.com/gitlab-org/omnibus-gitlab/blob/master/README.md

In /etc/gitlab/gitlab.rb add: external_url “http://gitlab.example.com:4554&#8221;  Disable nginx nginx[‘enable’] = false Give apache user privileges to  listen to GitLab web_server[‘external_users’] = [‘www-data’] Then run  sudo gitlab-ctl reconfigure.
Then add the apache vhost along with the others, taken from this repo, download https://gitlab.com/gitlab-org/gitlab-recipes/raw/master/web-server/apache/gitlab-apache2.4.conf
The settings you need to replace are:
–  change the port to say 4554 ServerName gitlab.example.com – replace  with the domain with which you reach from outside ProxyPassReverse http://gitlab.example.com/ – replace with ProxyPassReverse http://yourdomain.com:4554/  Change to DocumentRoot /opt/gitlab/embedded/service/gitlab-rails/public  Fix the log paths at the end of this conf Then as you already know, add  Listen 4554 to /etc/apache2/ports.conf and restart apache.  Documentation: https://gitlab.com/gitlab-org/omnibus-gitlab/blob/master/doc/settings/nginx.md#using-a-non-bundled-web-server  Unicorn is listening on 8080 (you can check this with sudo netstat  -pant | grep unicorn) Your document root is  /opt/gitlab/embedded/service/gitlab-rails/public You can create a new  vhost for gitlab in apache with the following configuration: ServerName  gitlab.example.com ServerSignature Off ProxyPreserveHost On Order  deny,allow Allow from all ProxyPassReverse http://127.0.0.1:8080 ProxyPassReverse http://gitlab.example.com/ RewriteEngine on RewriteCond %{DOCUMENT_ROOT}/%{REQUEST_FILENAME} !-f RewriteRule .* http://127.0.0.1:8080%{REQUEST_URI}  [P,QSA] # needed for downloading attachments DocumentRoot  /opt/gitlab/embedded/service/gitlab-rails/publicThe minimum settings in  the gitlab.rb file should be: cat /etc/gitlab/gitlab.rb | grep “^[^#]”  external_url ‘http://gitlab.example.com&#8217; web_server[‘external_users’] = [‘www-data’] nginx[‘enable’] = false ci_nginx[‘enable’] = false
sudo  netstat -pant might not show you unicorn but config.ru sudo gitlab-ctl  reconfigure sudo service apache2 restart Type the server name configured  above in your browser and then Username: root Password: 5iveL!fe
gitlab-rake gitlab:setup

====== AFS ======

find ./ -type d -exec fs setacl -dir {} -acl system:anyuser none \; -print
fs la


====== GIT ======

    git diff -C #checks for renames.
    git diff --word-diff -U0
    git config -f .gitmodules submodule.xxx.ignore dirty
    git config submodule.xxx.ignore all
    git config --global credential.helper 'cache --timeout=2628000'

    git config --local include.path ../.gitconfig

git log master..origin/master
git diff master..origin/master
git diff origin/master # implicitly means difference between the local branch and origin/master

git fetch --dry-run
git push --dry-run

 git diff stash@{0} -- _posts/2017-09-13-scratch.md

deinit to remove the entry from .git/config
rm --cached to remove the entry from index
rm -rf to remove the submodule directory
submodule add again ( the presence of this submodule in .gitmodules is not a problem )
git submodule uupdate --force --depth 10

git log --all --full-history -- ./main.cpp
git log -p --all --full-history -- ./main.cpp

git update-index --chmod=+x <file>
git ls-files
git ls-tree

8,5G    ./copied_dataset
3,0G    ./PriorityGraphSensors_small
du: cannot read directory './project/libs': Permission denied
859M    ./project
9,4G    ./PriorityGraphSensors_temp
11G ./MotionFlowPriorityGraphSensors_done
34G ./PriorityGraphSensors
4,2M    ./bin
7,2G    ./MotionFlowPriorityGraphSensors
964K    ./PriorityGraphSensors.git.bfg-report
4,8G    ./PriorityGraphSensors.git
78G .


So, start with cloning, and then init submodules and finally update submodules.

    git clone --depth 10 <repo>
    git submodule init
    git submodule update --depth 10

In case of error - error: Server does not allow request for unadvertised object SHA, increase the depth for this particular module for example 100.

    git submodule update --depth 100 <submodule> # for those modules, whose depth doesnt match. try with different depths.

When successful, continue with default

    git submodule update --depth 10

git submodule deinit libs/ffmpeg
git submodule update --init --recursive --depth 10

without build - all submodules downloaded with depth.


BFG 
git reflog expire --expire=now --all && git gc --prune=now --aggressive

I am answering my own question, after a little bit of research, that might be helpful to the others:

It is a big pain to understand git submodules, but once you get it, everything starts making sense !

The following post shows:

 - adding submodules and letting others sync with your submodules.
 - updating submodules and letting others sync with your submodules.
 - removing submodules and letting other sync with your submodules.
 - updating the removed submodules.

**Adding submodules**

   – (minus) when submodule is not initialized.
   + when top of the tree commit-id does not match with what is saved in index file.

   git submodule add -b <branch> <serverurl> <localpath>

The entry in .gitmodules ( name, path, url, branch ) downloads the respective submodule by

    git submodule update --init

This does three important thing, the first two of which are hidden from the user:

1. updates .git/config with an extra entry ( submodules )

2. downloads a repository in bare form under .git/modules. That means, there is .git inside a .git.

3. checks out the git submodule from the .git/modules into the parent directory.

Now, on Day 2, the commiter, who commited the submodule realises, that he should change the submodule to some other commit and not the HEAD. So, he would go to his local repository and then go the submodule path and then checkout the commit that he wants by simply invoking

    git checkout <hash>
    cd <parent dir>
    git submodule status

At this point, the git submodule status still does not shows the new hash. The new hash will only be visible when the changes are staged. Now, the commiter, just needs to stage ( add ), commit and push the changes, so that it is visible to all the other developers.

**Updating the added submodule**

On Day 3, the other developers, would update their repository by just invoking the command

    git pull # this is to get the latest commit of the parent git repository.
    git submodule update # update the submodule with latest hash

Basically, here the point is simple: The submodule does not react until and unless it is told to do so. Just doing git pull, wont update the git submodule. The developers can continue to work on their local submodules and not sync them to the one on the server "forever". The submodule update would happen on explicitly invoking the git submodule update command.

**Removing submodule**

Now, on Day4, the committer, decides to remove the git submodule completely. Here the steps are also not simple, because there is nothing called  git submodule rm that should have been equivalent to git submodule add. This can be done only and only if the following sequence is followed:

    git submodule deinit submodulename

1. this deletes the .git/config entry.

2. this clears the submodule directory !! You will see nothing in the submdoule directory after this command.

3. But the contents of the submodule are still available under .git/modules

Hence a git status -u here will still show that Everyting is upto date !

So show the removals,

    git rm submodulepath

At this point git status will return that .gitmodules has been changed ( the submodule has been deleted ) and the submodule path has been deleted. Commit and push the changes.

**Updating with removed submodule**

On Day5, the developers want to delete the submodules "automatically" like it did with git submodule update. So they do first a git pull, which succesfully removes all indices to the git submodules

     git submodule status # shows nothing

BUT, the .git/config still contains valid submodule entry and the submodule folder is there with all its contents and the bare repository under .git/submodules !  There is no command to delete them. All of them must be explicitly removed via hand..( Please correct me if I am wrong )

Ignoring submodules

    git config -f .gitmodules --remove-section "submodule.$submodule_name
    git submodule deinit -f "$submodule_name"
    git config submodule.<name> ignore=all
    git config status.submodulesummary 1




git submodule update --remote
git submodule update --remote --rebase
git push --recurse-submodules=check

git config status.submodulesummary 1
git config --global diff.submodule log


unstage:
git checkout -- .
git ls-files -u ; only show unstaged files


GIT

git log --diff-filter=D --summary
Git is a version management tool. gitg is a light weight GUI based client and git-sh is a lightweight console based git client.
git reset--hard SHA
git push origin HEAD --force ; after a reset has been done.
git config --global push.default simple ; push only the current branch
git config --global push.default matching
git init –bare ~/new-bare.git
cd ~/new-bare.git
git symbolic-ref HEAD refs/heads/trunk
Then push the temp repository to the new bare repository.
cd ~/temp
git remote add bare ~/new-bare.git
git config remote.bare.push ‘refs/remotes/*:refs/heads/*’
git push bare
cd ~/new-bare.git
git branch -m trunk master
Git config –global http.sslVerify false
The below is to get the git repository without the ssh key stored inside the computer.
Ssh -T agrawal@atreus.informatik.uni-tuebingen.de is needed to authenticate the host.
gitexcludes
gitignore

man gitcli; This gives an overview of the basic structure of git command line interface.

GIT MERGE

git checkout –ours filename
grep -lr ‘<<<<<<<‘ . | xargs git checkout –theirs
You have to do git add to mark the resolution of the merge. Also git status will show you unmerged files.

GIT TREE

git ls-tree HEAD;
commit is a submodule; blob is a file; tree is a directory.

GIT LOG

git log
git log — filename
git log — directoryname
git log –pretty=oneline -6



GIT CONFIG

git config –list

GIT SUBMODULE

Entries in .gitmodules
[submodule “rainfilter”]
path = rainfilter
url = git@atreus.informatik.uni-tuebingen.de:testcase-generation/rainfilter.git
After a git submodule init, the contents of the .gitmodule is read and it is copied to the .git/config.
After that do a git submodule update to get all the submodules. In case any of the submodules does not work, then maybe the url is broken. Do git submodule sync to correct the error or do git submodule sync — A to update the url of only module A.

First time preparation:

git submodule add nameoftherepo path
By default, submodules will add the subproject into a directory named the same as the repository, in this case “nameoftherepo”. You can add a different path at the end of the command if you want it to go elsewhere. The above command also makes a .gitmodule and uses the same format as described above.
git diff –cached –submodule
git diff –cached Nameoftherepo
git clone –recursive path ; skips the git submodule init and git submodule update commands.
git status –ignore-submodules

Git submodule at normal operation

git fetch or git merge  ;but to do it you need to be in the directory
Another way is the command git submodule update –remote
git config -f .gitmodules submodule.nameoftherepo.branch somebranch ; in case you want to add another branch and not the default master
git config status.submodulesummary 1

git show –name-only
diff -iwy –brief Dir1 Dir2
git diff –name-only
git diff branch1..branch2
git diff branch1…branch2
git diff b1..b2, show you what is in b2 that is not in b1. So git diff b1..b2 and git diff b2..b1 will not have the same output. On the contrary, git b1…b2, show you what is in b1 XOR b2 (either b1 or b2 but not both). So git b1…b2 is equal to git b2…b1

diff –side-by.side –supress-common-lines
diff -c ( suppress commong lines
git clear -dn unversioned file
git clear -dnx also ignored file
git rm –cached nameoffile [will delete the file from the git repo]
git reset nameoffile [removes tracking, but not delete ]
git commit -i filename
git ls-files -u
git show:1:filename
git stash show -p
Number of printers can be seein in the group policy.
git remote show origin
git instaweb –httpd=webrich
REPOS:
gitweb conf -> /etc/gitweb.conf
install dir /usr/share/gitweb
In apache2 /conf.d/gitweb
git config –global –edit
git commit –amend –reset=author
system-config-firewall
install gitweb, httpd, git-core

GIT FETCH

fetch fetches in the .git and pull pulls it as human readable
git remote add temp (url or path to the .git)
git fetch temp master

GIT CLEAN

remove all the files untracked, tracked etc.
git clean –



GIT STASH

git stash ; explicitly the command is git stash save.
git stash list
git stash apply
git stash apply –index ; this will bring the same thing as  before. including reapplying the indexes in .git
git stash pop ; applies and drops
git stash show -p and then pipe it with git apply -R; this is to show the patch between the stash{0} and the parent when the stash was done and subsequently apply the patch reversely to the current state. This means basically we are unapplying the patch that we just did.
stash@{0} is the way how the stashed file is looked for.
git stash branch testchanges ; this checks out the position in a branch called testbranch when the file was stashed, applies the said stash and drops the stash if it works peoperly. This way your master branch is not corrupted in case things are not working the way it should have been.

GIT SPARSE

git config core.sparsecheckout true
echo directorypath | tee -a .git/info/sparse-checkout
git pull origin master
If a repo already exisits, then a pull is not needed and it can be done by
git read-tree -mu HEAD
http://schacon.github.io/git/git-read-tree.html#_sparse_checkout

GIT FILTER

git clone git@github.com:ssp/pazpar2.git pazpar2g
git filter-branch –prune-empty –subdirectory-filter etc — –all ; keep only etc subfolder
git filter-branch -f –prune-empty –index-filter ‘git rm –cached –ignore-unmatch `git ls-files` | grep -v “tmarc.xsl\|check-pazpar2.sh”)’ ; remove all files other than the ones you want to keep (tmarc.xsl, check-pazpar2.xsl)

GIT FS:
refs/head – all branches

GIT CONFIG

git config –global http.sslVerify false
gitexcludes  : ~./gitexcludes
gitignore
git config user.name “VA”
git config user.email “df”

GIT RESET

git reset –hard origin/master
git reset –hard HEAD~4
git reset –soft HEAD^

GIT FETCH,COMMIT,PUSH:

git pull . master
git pull . topullfrom
git merge master
git merge topullfrom
git remote add -f origin url
git init
git clone url foldername; if you omit the foldername it creates one with the name of the repo
git commit -m “first commit”
git commit
git commit -a
git commit –amend –reset-author
git add filename
git add . ( for first time addins )
git add -a ( for next addins )
git fetch -a origin master
git push –all origin
git push -u origin master
git push -all ( branches )
git push –tags ( tags )

SSH
HTTPS: https://domain/agrawal/repo.git
SSH: git@domain:agrawal/repo.git
If there is a SSL certificate issue, then the error would be SSL certifcate problem:self signed certificate.
In windows the ssh public key should be present in users/.ssh folder
In Linux in home/user/.ssh folder
The below is to get the git repository without the ssh key stored inside the computer.
Ssh -T agrawal@atreus.informatik.uni-tuebingen.de is needed to authenticate the host.

GIT TAG, BRANCH:
git tag “name”
git tag ; shows the status of the current tag
git branch; shows the status of the current branch
#Remove all local
git branch | grep -v “master” | xargs git branch -D
Remove all remote branches that has been merged to master in one go.
git branch -r –merged master | awk -v master | sed -e ‘s/\//:/’ | xargs -n2 git push
git push origin –delete <branch>  # Git version 1.7.0 or newer
git branch -r -d <remote>/<branch> # Shorter
git branch -d <branchname>    # deletes local branch
git push origin :<branchname> # deletes remote branch
git branch -f master HEAD

GIT REMOTE:
git remote add origin url
git remote  rm origin
git remote add -f old_repo old_repo_url
git remote set-url origin url
git remote -v

git pull --all --no-commit
git config --global --edit
git commit --amend --reset=author
git remote show origin
git instaweb --httpd=webrich
git ls-files -u
git show:1:filename
git stash show -p
git clear -dn unversioned file
git clear -dnx also ignored file
git rm --cached nameoffile [will delete the file from the git repo]
git reset nameoffile [removes tracking, but not delete ]
git commit -i filename
git diff --name-only
git show --name-only


Remove all local
git branch | grep -v "master" | xargs git branch -D

Remove all remote branches that has been merged to master in one go.
git branch -r --merged master | awk -v master | sed -e 'S/\// :/' | xargs -n2 git push

git push origin --delete <branch>  # Git version 1.7.0 or newer
git branch -d <branch> # Shorter version
git branch -dr <remote>/<branch> # Shorter
git branch -d <branchname>    # deletes local branch

or
git pull . branchname
git merge branchname
git push origin :<branchname> # deletes remote branch
git branch -f master HEAD
git push -all ( branches )
git push --tags ( tags )
git diff
git commit -a
git commit --amend --reset-author
git reset --hard origin/master
git reset --hard HEAD~4
git copy username "VA"
git config user.email "email id"
git remote add origin https://...
git push -u origin master
git push -all ( branches )
git push --tags ( tags )
git diff
git ocmmit -a
git commit --amend --reset-author
git reset --hard origin/master
git reset --hard HEAD~4
git config usern.ame "VA"
git config user.email "df"
git mergetool
git add
git commit
git checkout --ours filename or .
git checkout --theirs filename or .
patch -p1 < path to patch file
patch foo.c < patch.diff ; just the foo.c will be patched.
git apply -v apply.patch
patch -R ( reverse the patch ) < path to patch file
diff -u oldfile-name-here newfile-name-here > patch.diff ; to create a unified diff patch.
git format-patch branch1 master --stdout >
git diff branch1...branch2 >
git diff --cached ; to see all diffs ready to be commited.
git diff --staged ;
git checkout featurebranch paths
git cherry-pick
git checkout --patch branch filename
git config --global alias.hist "log --pretty=oneline"
git am --signoff < fix_empty_poster.patch
git format-patch master --stdout > fix_empty_poster.patch
git am --abort
git apply --stat
git apply --check
cat ddd | colordiff | less -RNS
git apply --whitespace=fix patchname
git commit --author="Weikas <speedbyte>"
git diff | vim -R -
git diff --color | less -R


GIT Submodule update

    git clone --recursive URL


====== Audio/Sound ======

ppa:osmoma/audio-recorder
pulseaudio
alsamixer
pacmd list-sinks

pactl list sources
pacmd "set-source-port 1 analog-input-microphone-front" ; The source port can be found out by the above command
if all was successful we can now put that at the end of your /etc/pulse/default.pa file as such: pacmd "set-source-port 1 analog-input-microphone-front"

iPhone Veikas 58:55:CA:C1:8B:DD
JBL B8:69:C2:5A:1A:4A
Belkin 00:19:0E:02:D1:61
hcitool dev - shows current bluetooth
sudo apt-get install pavucontrol


#/etc/bluetooth/asound.conf

pcm.btheadset {
   type plug
   slave {
       pcm {
           type bluetooth
           device 00:19:0E:08:2A:CD
           profile "auto"
       }
   }
   hint {
       show on
       description "BT Headset"
   }
}
ctl.btheadset {
  type bluetooth
}


#/etc/bluetooth/audio.conf

[General]

Enable=Source,Sink,Media,Socket


====== Software ======


Adminer, KPhotoAlbum, Piwigo, Lychee
gthumb
.config/nautilus/accel



====== Hardware ======


system bios related information

dmidecode

System Activity Information

    sar -bdp 1 # gives the current read and write of a usb stick or a hard disk
    sudo dmsetup info /dev/dm-0
    cat /proc/cpuinfo, hostnamectl, lscpu, lshw, lspci etc.

SystemManagement Bus – SMBUS which is a simple two wire bus like i2c.

    kernel.shmmax = 17179869184
    nproc
    getconf _NPROCESSORS_ONLN
    page_size=`getconf PAGE_SIZE`
    phys_pages=`getconf _PHYS_PAGES`
    shmall=`expr $phys_pages / 2`
    shmmax=`expr $shmall \* $page_size`
    echo kernel.shmmax = $shmmax
    echo kernel.shmall = $shmall
    ipcs -l # infomration about semaphores
    sysctl --system # restart sysctl after changin the values.


====== Networks ======


    cat /etc/NetworkManager/NetworkManager.conf

managed=false if you do not want the ifupdown to be managed by the Network manager.

    -P /var/run/wpa_supplicant/-.. /wlan0.pid
    -D nl80211,wext
    -C /var/run/wpa_supplicant

Find process from port

    lsof -i:8080 -n

Find port from process

    netstat -lnp | grep 1483

Find process id from process name

    pgrep -f jenkins

Find process name from id

    ps -ef |grep id


SIP
GPRS, EGPRS , UMTS / 3G and, HSPDA / 3.5 G( High Speed Downlink Packet Access ) Push To Talk ( Is like a Walkie Talkie )


Computer Networks

The class A addresses are when the first octet is fixed, and the rest of the octets can be adjusted by the company.
class B addresses have first two octets fixed and the rest can be adjusted by the company.
class C addresses have first three octets fixed and the last octet can be adjusted by the company.

  * The first octet in class A ranges from 0-127
  * The first octet in class B ranges from 128-191
  * The first octet in class C ranges from 192-223
  * 223-239 is multicast

The class A network have a default mask of 255.0.0.0
Class B network have a default mask of 255.255.0.0
Class C network have a default mask of 255.255.255.0
Default mask means only 1 subnet and the rest are hosts. However it is upto the system admin how many subnets and hosts can be made out of the available addresses.

The net ID is the corresponding bit set to 1 and the host ID is the corresponding bit set to 0
So, the network id and host id of 192.168.10.10 / 255.255.255.0 is network ID = 192.168.10 and Host ID = 10.

Now have a look at the last octet in 255.255.255.0. 0 is equivalent to 1, that means only 1 subnet can be made.
If it would have been 255.255.255.128 then the last octet has one 1 which means 2 subnets can be made.
Similarly 192 leads to two 1's and hence four subnet and 224 leads to 111 which means 8 subnets. In this case the remaining bits are 5 and hence 11111 which means 32 hosts.
The other notation to write this is prefix/length.
In the case of 192.168.10.30 with subnet of 255.255.255.224 the prefix / length notation is 192.168.10.30/27
The prefix tells us how many 1s are present in the whole subnet mask.

If the company has a class C address, then it can configure 256 servers. These 256 servers ofcourse should not be seen by everyone. That means for example 10 of them are only for development and 5 for finance people.
That means, the companys net should be divided into two subnets. Which means a subnet mask of 255.255.255.128 will divide the network into two subnets with each subnet having their own broadcast address and subnet id - example: 192.168.10.0 and 192.168.10.128 for a class C network of 192.168.10.0  and additionally 127 hosts each. The broadcast address would be then 192.168.10.127 and 192.168.10.255. So, the company has to buy a router to divide the two departments.
A development team person ( 192.168.10.10 ) cannot access a finance server (192.168.10.137 ) because they are in two different subnets. The router blocks any kind of message between the two subnets.


To find all the ip addresses and mac addresses in the network use

   arp -av
   arp-scan network/length
   nmap -sL network/length
   arp -n
   ip route add -net 10.0.0.0 netmask 255.255.255.0 dev eth0 src 10.0.0.10 table rt2
   ip route add 10.10.0.0/24 dev eth1 src 10.10.0.10 table rt2
   ip route add default via 10.10.0.1 dev eth1 table rt2

The first command says that the network, 10.10.0.0/24, can be reached through the eth1 interface. The second command sets the default gateway.

Routing Rules

So that the system knows when to use our new routing table, two rules must be configured.

    ip rule add from 10.10.0.10/32 table rt2
    ip rule add to 10.10.0.10/32 table rt2

These rules say that both traffic from the IP address, 10.10.0.10, as well as traffic directed to or through this IP address, should use the rt2 routing table.

    sudo ip route flush table main
    ip route flush dev wlan0

switches transfer packets based on their MAC addreesses, hence they inteface two LANS.
Routers transfer packets based on their destination addresses, hence they interface two WANS
Repeaters and hubs are at a physical level and just replicates messages from one LAN to another.

====== CURL/WGET ======


curl/wget
Both are bidirectional and to get data from the websites

    -c continue
    -O directory plus the name of the new file
    --no-check-certificate
    -P directory_prefix

    wget fileurl 
    dig www.amazon.com 
    host domain.de 
    host ip-address
    curl www.google.de --interface wlan0
    wget google.de #curl has much more features than wget


====== Networking ======

To check a connection to a port

    nc -vz server.domain.de 22
    telnet ldap.domain.de 389
    nmap -S 192.168.22.100/24

See all listening ports

    netstat -lpantu -A inet
    netstat -an
    tcpdump  -n -i eth0 tcp port 22 and host [IP address of client]
    tcpdump -i -nn eth0 -c 500 : this shows the 500 bytes and closes  automatically

  - WEP : Wireless Encryption Protocol
  - WPA : Wifi Protected Access
  - WPA2 : Wifi Protected Access 2
  - WPS:

Networking  is a mean to connect your computer to another computers. This is done  through a router. The router is a device that is an interface between  your computer and other computers in the world or in other words it is  called a gateway. To be able to connect to other computers, you need  access to this router first and then this router will authenticate you  and if you are authenticated, then you can talk to the rest of the  world. So, first of all one needs to find the interface to talk to the  router. There are two very well known interfaces – ethernet and the  wifi. Your computer is always connected to the router either through the  ethernet or the wifi. The reason one cannot connect itself to the other  computers in the world is because your router did not authenticate you  or the link in of the interface ( ethernet or wifi ) is not ready. In  either the cases, there would be no entry of a default gateway in your  system. So, the key is if you want to know if your computer is able to  contact other computers, then simply look for the entries in the routing  table. This can be done by the command route -n

One can find if  the interface is UP by invoking a commmand

    ethtool eth0
    ethtool wlan0

If the answer is “Link detected: no”, then the link is not ready.  One can also see the list of ready links by invoking the command

    ifconfig -a.

All the available interfaces are displayed. However, they  are just available and not ready. To make the interfaces ready, one has  to bring the interface up. This is done by

    sudo ip link set dev eth0 up.

Now ifconfig should even show the interface that you just switched on.
Once  the link is up, then you can get the ip address by by invoking the  command

    sudo dhclient eth0.

One can also get the ip address by invoking  the command

    sudo ifup eth0

which reads the /etc/network/interface file  and looks for the interface eth0. Normally it is enough to write the  rule “iface eth0 inet dhcp” there. Internally, the command dhclient  would be invoked and your computer would get the desired ip address.

To automate the process, you can write the commands in the rc.local file which would be run during the start up process.
The  question is what when the interface is ready, but there is no ethernet  wire connected for example in a train etc and you want to start your  computer. That is not a problem, because the command ip link set dev  eth0 up, just tells the kernel that in case a ethernet wire is  connected, then it should be automatically registered. After that a mere  dhclient eth0 should suffice to get the IP Address.

If you are  still lazy, then it is enough to just invoke dhclient eth0. This would  start the interface if not started and get the IP Address.

The  above applies for wlan0 interfaces too. However, the wlan is a little  tricky, because there are lot of protocols to authenticate with the wlan  router. In case of ethernet, you are obliged to connect your computer  to the ethernet sockets in the wall and hence do not need any special  authentication. The authentication is that your computer is connected to  the ethernet socket. However, you are not authorized to use the router,  because your MAC Address might not be in the database of the allowed  computers in the router.
So, to configure the wlan interface, one  also needs to uplink the interface and call dhclient to get the ip  address. The uplinking is simple if you have a wlan chip, but contacting  the dhcp to get the ip address needs some more lines in the network  interface file.
First of all, you need to know if the router that  you want to connect to is found by the kernel. This can be done by

    iwlist scan | grep -i “essid”.

If the router is found, then one has to  make the wpa-supplicant file to start the authentication. It is also  possible to write the information in the interface file like

    iface wlan0  inet dhcp
        wireless-essid name of the router
        wireless-mode Managed
        wireless-key password
    iface wlan0 inet dhcp
        wpa-conf  path-to-wpa-supplicant-file
        wpa_passphrase myssid  my_very_secret_passphrase
    iface  wlan0-home inet dhcp
        wpa-ssid myssid
        wpa-psk  ccb290fd4fe6b22935cbae31449e050edd02ad44627b16ce0151668f5f53c01b
    ifup  wlan0=wlan-home

wpa_supplicant can be used as a roaming daemon and you  have two options to exploit this possibility

1) Having  /etc/network/interfaces handle wpa_supplicant’s networks
Within  wpa_supplicant.conf, you can assign a value to the ‘id_str’ variable for  each network={…} block in order to uniquely identify each network. Once  this is done the value of this variable can then be used within  /etc/network/interfaces to have each wpa_supplicant network  activated/configured automatically. If the ‘id_str’ variable is not  explicitly defined for a given network in wpa_supplicant.conf, then the  variable defaults to ‘default’.

The following line specified in  /etc/network/interfaces will activate and configure each ‘default’  network in wpa_supplicant.conf with DHCP upon a successful connection to  an access point: iface default wlan0 dhcp

To check the wpa_supplicant file:

    sudo killall -HUP wpa_supplicant && sudo wpa_cli reconfigure
    sudo wppa_cli identity "edimax" password "ddddd"

WPS

    wpa_cli wps_pbc 11:22:33:44:55:66

and then press the WPS button on the accesspoint.

So,  there are two methods to initiate ( it doesnt mean that the initiation  will be successful ) the connection. One is the network-manager ( sudo  apt-get install network-manager ) or the wpa-supplicant ( sudo apt-get  install wpa-supplicant ). The network-manager stores all the information  of this router, its authentication protocol, passwords etc in the  location /etc/Network-Manger/system-connections/. The configuratio file is under /etc/NetworkManager/NetworkManager.conf.

The wpa-supplicant is  more flexible and the wpa-supplicant.conf file that contains the all the  information of this router, its authentication protocol, passwords etc.  can be put anywhere in the computer. The information where the  wpa-supplicant can be found is done through the file called  /etc/network/interfaces. One has to write a command wpa-conf and the  location of the wpa-supplicant file.

When you have a router at a  home, you dont know what kind of protocols etc is it looking for. And  ofcourse, hence you cannot make any entries in the Network-Manager or  wpa-supplicant. The information can be found by issuing a command iwlist  scan or iwconfig. This will contact the various routers in the vicinity  over ethernet as well as wifi and tell you what are they looking for.

dhclient  should be avoided, because ifup and ifdown scripts take care of the  dhclient. Basically, one does not know about the other. Hence if you  invoke dhclient to obtain the ip address and then do ifdown, you will  get an error message that the wlan0 is not configured.

    elinks http://www.google.de

To  add/delete a route:

    sudo ip route del default via 192.158.15.254
    sudo ip addr add 192.168.1.14/24 dev eth0
    sudo ip route add default via  192.168.1.1
    sudo route del -net 0.0.0.0 gw 192.168.178.1 netmask 0.0.0.0  dev eth0
    sudo route add default gw 192.168.22.9 eth2
    sudo route add default gw 192.168.1.1 dev wlan0
    sudo ip route del default via 192.158.15.254
    sudo route add -net 192.168.178.0 netmask 255.255.255.0 dev wlan0
    sudo route del -net 192.168.178.0 netmask 255.255.255.0
    sudo ip route flush table all
    sudo ip route delete dev eth0
    sudo ip route add dev eth0 via 134.2.15.254
    sudo ip link set dev eth0 down
    sudo dhclient eth0 -> this will bring eth 0 up using DHCP.
    sudo ip addr add 192.168.1.14/24 dev eth0
    sudo ip link set dev eth0 up
    sudo ip route add default via 192.168.1.1
    sudo ip addr flush interface-name



The leases can be renewed by first deleting: </var/lib/dhcp/*.leases>
    dhcpclient -r
    dhcpclient #get the lease

dnsmasq  is a tool which speeds up the dns queries because it caches the  entries. Normally it is already started by the network-manager tool  listening on the port 53. Nevertheless, if you want to start on your  own, you can do it using the command

    dnsmasq -d –all-servers. This also logs onto the syslog.

    netstat -pant ( all )
    netstat -plnt ( only  listen )
    netstat -an -o -p TCP
    nc -ul localhost  port_number  #listen on a udp port
    Nc -l port number
    echo -n “hello” | nc -u -w1 localhost 5000 #Send datapacket over udp every 1 second
    socat
    netcat
    nmap
    wget google.de #curl has much more features than wget
    ipconfig /renew ipconfig /release /home/agrawal/host
    wget fileurl
    dig http://www.amazon.com
    host domain.de
    host ip-address
    sudo iwlist wlan0 scan | grep -i  “ESSID”
    sudo iwconfig wlan0 essid “network-essid”
    sudo iwconfig wlan2  mode master

    apt-cache depends owncloud
    ifconfig obselete ipaddr
    ifconfig obselete iplink hostname
    hostname newname
    cat /etc/hosts would need to  be changed because sudo requires DNS lookups in certain cases and it  cannot resolve your newly sset hostname. echo newname | sudo tee  /etc/hostname ls /sys/class/net or ip addr
The above two is  equivalent to writing in the /etc/network/interfaces. The  /network/interfaces is permanent but the above commands are just for  that session.

Resolving DNS: sudo vi /etc/resolv.conf enter: search example.com domain example.com nameserver 192.168.1.1
cat  ssl_request_log cat access_log cat ssl_error_log cat error_log tail -c  100000 secure | less TLS – Transport Security Layer is a replacement of  SSL. But still SSL is more popular.
EAP-TTLS Extensive Authentification Protocol
Entry for /etc/network/interface
    auto wlan0
    iface wlan0 inet dhcp
    wpa-ssid Agrawal, Vikas
    wpa-psk guars0468

    iface eth0 inet static
    address 198.51.100.5/24
    gateway 198.51.100.1

    arp -a
    netstat -r
    nmap -sP 10.0.0.4/24

curl/wget      Both are bidirectional and to get data from the websites -c continue -O  the name of the downloaded file will be put in this folder  –no-check-certificate

MTA Mail transport agent exim sendmail postfix telnet localhost 25 sudo lsof -n -i:25
host url host ip_address

iptables:  A firewall rule specifies criteria for a packet and a target. If the  packet does not match, the next rule in the chain is
examined; if it  does match, then the next rule is specified by the value of the target,  which can be the name of a user-defined chain, one of the targets  described in iptables-extensions(8), or one of the special values  ACCEPT, DROP or RETURN.
wget -r -np -k http://&#8230;..  nd (no directories): download all files to the current directory -e  robots.off: ignore robots.txt files, don’t download robots.txt files -A  png,jpg: accept only files with the extensions png or jpg -m (mirror):  -r –timestamping –level inf –no-remove-listing

SSH: tail -c 10000 0  secure| less TLS is a replacement of SSL. However people keep saying  SSL rsa should be used, because dsa is not so good implemented

Network  Interfaces Edit /etc/network/interfaces with static Ip (

    iface eth0  inet static
    address “x.x.x.x”
    netmask “x.x.x.x”
    gateway “x.x.x.x”
    /etc/init.d/networking  restart
    sudo ifconfig eth1 192.168.22.160/24

This will route all the  traffic with the ip address 192.168.22.x via eth1.

Check this with route  –n and tcpdump –n –I eth1 –c 500. It is very likely that the interface  eth1 abrupty closes because a connection is closed like tcpdump etc.

If eth1 exists in the routing table, then you can add a route for eth0. You have to do ifdown for eth0, then add the route for eth0 and then do  ifup for eth1. Otherwise you will get an error RTLinkError: File exist.

Tested curl www.google.de --interface wlan0

iwlist is deperecated and obselete. The newer challenger is iw. iwlist scan provides much lesser output than iw scan

Display the third line from a text file
ls | sed '3,3!d' 
ls | sed -n '3,3p'

Attaching WLAN to LInux

    openssl version -a
    wget fileurl dig www.amazon.com host domain.de host ip-address curl ( baap of wget )
    sudo iwlist wlan0 scan | grep "ESSID" sudo iwconfig wlan0 essid "network-essid"
    iwlist sudo iwconfig wlan2 mode master apt-cache depends owncloud
    ifconfig obselete ipaddr ifconfig obselete iplink
    sudo yum install wireshark sudo yum install wireshark-gnome
    lsusb WIN netsh whal show drivers
    import screenshot.png display screenshot.png
    mc firefox -P

hostname  hostname newname cat /etc/hosts would need to be changed because sudo  requires DNS lookups in certain cases and it cannot resolve your newly  sset hostname. echo newname | sudo tee /etc/hostname

ls  /sys/class/net 
or ip addr sudo etc/init.d/NetworkManager stop sudo  /etc/init.d/NetworkManager start sudo chmod +x etc/init.d/NetworkManager  sudo chmod -x etc/init.d/NetworkManager sudo update-rc.d -f  NetworkManager remove sudo update-rc.d -f NetworkManager defaults 50  sudo apt-get install NetworkManager sudo apt-get purge NetworkManager


The  above two is equivalent to writing in the /etc/network/interfaces. The  /network/interfaces is permanent but the above commands are just for  that session.
Resolving DNS: sudo vi /etc/resolv.conf enter: search example.com domain example.com nameserver 192.168.1.1



====== XWindow ======

    wmctrl -m

    sudo mokutil --enable-validation
    sudo mokutil --enroll-key

    window manager : xdg_current_desktop
    display manager : /etc/X11/default-display-manager
    desktop envirionment

    dpkg-reconfigure xserver-xfree86

    xserver-xorg-driver-nouveau has to be deleted
    you can do this using additional drivers.
    Select nvidia.

    modprobe -v module
    modprobe -r module

    list of all modules integrated in the kernel lsmod
    list of all modules ; ls /lib/modules/$(uname -r)/kernel/drivers/; ls /lib/modules/$(uname -r)

    dpkg-reconfigure kdm
    DISPLAY=:0 compiz --replace

    Alt PrntScreen K kills your Display manager.

    dconf reset -f /org/compiz/
    nohup setssid unity

    nohup compiz --reset
    nohup unity --replace

    Alt PrntScreen K kills your Display manager.
    dconf reset -f /org/compiz/nohup setssid unity

    /etc/X11/default-display-manager
    /usr/bin/\*session

    XDG_CURRENT_DESKTOP
    wmctrl -m
    echo $DESKTOP_SESSION
    import os
    os.get.environment('​CURRENT_DESKTOP')

    exo-preferred-applications
    initctl restart unity-panel-service
    xdg-mime under .local/share/applications
    desktop-file-install \*.desktop

    command line tool for querying information about file type handling and adding descriptions for new file types

    XDG_CURRENT_DESKTOP : current desktop environment.

    DISPLAY-MANAGER:

    cat /etc/X11/default-display-manager
    ls /usr/share/xsessions/
    Alt F2 – Open a program
    gnome-do gconf_editor&
    rdesktop -g 1680\*1050 -u agrawal ork-win
    sudo apt-get install gnome-tweak-tool
    import os; print os.environment.get('DESKTOP_SESSION')

Graphics Driver
    blacklist nouveau in /etc/modprobe.d to avoid nouveau to be loaded.

Gpu test
 
    lshw -class video
    watch -d nvidia-smi

Download GpuTest : \url{http://www.geeks3d.com/20140304/gputest-0-7-0-opengl-benchmark-win-linux-osx-new-fp64-opengl-4-test-and-online-gpu-database/#download}
    
    ./GpuTest /test=fur /width=1024 /height=640
 
Switching between graphic cards:

There is only one graphic card in the VIRES PC. Hence there is no chance of switching between graphic cards. The only thing one can do is switch between drivers. One is the nouveau provided by xfreedesktop.org and the other is directly from nvidia. Both of them use different OpenGL drivers.

    dkms status
    vim /usr/src/nvidia/dkms.conf
    lspci -vv ( this shows the kernel driver available and kernel driver in use. If no kernel driver line is available, that means this driver is not at all used)
 
    sudo prime-select nvidia
    sudo prime-select intel

    boot parameter disablemodules=nouveau
    
    nouveau.noaccel=1
    nouveau.modeset=0

    sudo update-alternatives --config packagename
    sudo dkpg --configure --all


====== Virtual ======

execute the command by ./vmware-install.pl and everything will be automatically done.
Too  check if it works, please restrt the virtual machine and see if you get  a full screen or you can drag and drop a folder. if yes, everything  worked.

p
====== Power Management ======

tp_smapi

sudo apt-get install acpi acpi-fakekey acpi-support acpi-support-base acpid pm-utils 

acpi -v

cat /sys/class/power/... 

Check availability of thinkpad_acpi module

lsmod | grep thinkpad_acpi.

To check what are the supported values, modinfo thinkpad_acpi. fan_control should be there, otherwise there is no need to add the value in the .conf file.

sudo vim /etc/modprobe.d/thinkpad_acpi.conf :

options thinkpad_acpi fan_control=1.

Reload module

modprobe -r thinkpad_acpi && modprobe thinkpad_acpi.

If kmod is running as a sevice ( systemctl status kmod ) , putting anything under modprobe.d will automatically parse it i.e. no  need to issue any command like modprobe etc.

modprobe -c triggers the reloading of modules. Ofcourse if the file thinkpad_acpi file is not present, then one has to create one under /etc/modprobe.d. To check, if the thinkfan is really controlling your fans, you can start and stop the service thinkfan by doing

pm-suspend

pm-hibernate.

shutdown ‘now’

reboot

Control the fans

Disable fancontrols : echo disable >  /proc/acpi/ibm/fan # This is only possible in root shell. Hence sudo also wont help. The inbuilt fan controls are disabled automatically as soon as the thinkfan daemon starts successfully. Please see below.

file /proc/acpi/ibm/fan

Find temperature sensor

find /sys/devices -type f -name “temp\*\_input”

sudo apt-get install thinkfan

The corresponding values needs to be put in the thinkfan.conf file, so that the module knows where to find the temperatures.

<code>
hwmon /sys/devices/virtual/thermal/thermal_zone0/temp
hwmon /sys/devices/platform/coretemp.0/hwmon/hwmon1/temp1_input
hwmon /sys/devices/platform/coretemp.0/hwmon/hwmon1/temp2_input
hwmon /sys/devices/platform/coretemp.0/hwmon/hwmon1/temp3_input

#(FAN_LEVEL, LOW, HIGH)
(0,     0,      50)
(1,     48,     60)
(2,     50,     61)
(3,     52,     63)
(4,     56,     65)
(5,     59,     66)
(7,     63,     32767)

</code>

First start thinkfan -n # to check for temperatures. If all is good, then

/etc/default/thinkfan.conf START=yes

Additional startup parameters

 DAEMON_ARGS=”-q”

systemctl start thinkfan.service

To check if the inbuilt fan control has been disabled, then do, cat /proc/acpi/ibm/fan and the first line should show disabled.

sudo apt-get install laptop-mode-tools # is an excellent power management tools for laptop.

The story behind the whole: coretemp module provides information about the current temperatures in the cpu, harddisk etc. This can be seen by invoking the command sensors ( sudo apt-get install lm-sensor ). The coretemp is connnected to the ISA bus and procures three temperatures.

<code>
thinkpad-isa-0000
Adapter: ISA adapter
fan1:        2824 RPM

acpitz-virtual-0
Adapter: Virtual device
temp1:        +47.0°C  (crit = +200.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +48.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:         +43.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:         +46.0°C  (high = +100.0°C, crit = +100.0°C)

</code>


The sensors does not give you the temperature of the hard disk.

To get the temperature of the harddisks, install the hddtemp package.

There are options under Disk→Settings and standby mode, Acoustics etc can be changed.

To configure the backlight, put the value in the following file

echo 53 > /sys/class/backlight/intel_backlight/brightnes

 in /etc/rc.local and then restart.

  Fresh drivers from upstream, currently shipping Nvidia.

## Current Status

Current long-lived branch release: `nvidia-430` (430.40)
Dropped support for Fermi series (https://nvidia.custhelp.com/app/answers/detail/a_id/4656)

Old long-lived branch release: `nvidia-390` (390.129)

For GF1xx GPUs use `nvidia-390` (390.129)
For G8x, G9x and GT2xx GPUs use `nvidia-340` (340.107)
For NV4x and G7x GPUs use `nvidia-304` (304.137) End-Of-Life!

Support timeframes for Unix legacy GPU releases:
https://nvidia.custhelp.com/app/answers/detail/a_id/3142

## What we're working on right now:

- Normal driver updates
- Help Wanted: Mesa Updates for Intel/AMD users, ping us if you want to help do this work, we're shorthanded.

## WARNINGS:

This PPA is currently in testing, you should be experienced with packaging before you dive in here:

Volunteers welcome!

### How you can help:

## Install PTS and benchmark your gear:

    sudo apt-get install phoronix-test-suite

Run the benchmark:

    phoronix-test-suite default-benchmark openarena xonotic tesseract gputest unigine-valley

and then say yes when it asks you to submit your results to openbechmarking.org. Then grab a cup of coffee, it takes a bit for the benchmarks to run. Depending on the version of Ubuntu you're using it might preferable for you to grabs PTS from upstream directly: http://www.phoronix-test-suite.com/?k=downloads

## Share your results with the community:

Post a link to your results (or any other feedback to): https://launchpad.net/~graphics-drivers-testers

Remember to rerun and resubmit the benchmarks after driver upgrades, this will allow us to gather a bunch of data on performance that we can share with everybody.

If you run into old documentation referring to other PPAs, you can help us by consolidating references to this PPA.

If someone wants to go ahead and start prototyping on `software-properties-gtk` on what the GUI should look like, please start hacking!

## Help us Help You!

We use the donation funds to get the developers hardware to test and upload these drivers, please consider donating to the "community" slider on the donation page if you're loving this PPA:

http://www.ubuntu.com/download/desktop/contribute
 More info: https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa
Press [ENTER] to continue or Ctrl-c to cancel adding it.



Laptopmode

One has to have an active acpid service. Install laptop-mode-tools. Other recommended are hddtemp, thinkfan, tlp-stat, tlp-rdw, sensors-detect, lm-sensors, sensors FAN

sudo add-apt-repository ppa:linrunner/tlp

/sys/devices/platform/thinkpad_hwmon/fan1_input

sensors-detect # This program will help you determine which kernel modules you need to load to use lm_sensors most effectively. It is generally safe and recommended to accept the default answers to all questions, unless you know what you’re doing. /etc/module – boot time module load.


To check for available sensors through a package, download fancontrol and run pwmconfig. It will show everything which is connected via the pwm signals ( usually motors are controller thru pwm )

System D commands:

    systemctl reboot hibernate suspend shutdown

====== Init.d ======


Debian  has a init process called System V which has runs scripts whose links  are available under the corresponding runlevels and the actual script is  available under /etc/init.d

All the scripts are present under  /etc/init.d.

If you want to have your commands started at the beginning,  simply type the command or the script under /etc/rc.local.

This file is  called via the starting runlevels for example rc2.d or rc3.d. The  runlevels itself have many scripts which are symbolic links to the  /etc/init.d directory.

If you want to remove a script or add a script, then you have to run the update-rc.d command.

The comnand simply renames  the file to K ( which means kill ) or S ( which means start ) in the  run levels. If defaults is used then update-rc.d will make links to  start the service in runlevels 2345 and to stop the service in runlevels  016.

As a rule of thumb start number is 100 minus the kills number.  Insert links using the defaults: update-rc.d foobar defaults sudo  update-rc.d -f foobar defaults 50 Equivalent command using explicit  argument sets: update-rc.d foobar start 20 2 3 4 5 . stop 20 0 1 6 .  Remove all links for a script (assuming foobar has been deleted  already): update-rc.d foobar remove #When invoked with the remove  option, update-rc.d removes any links in the /etc/rcrunlevel.d  directories to the script /etc/init.d/name. The script must have been  deleted already. If the script is still present then update-rc.d aborts  with an error message unless used with -f option.

Enable: update-rc.d  foobar enable

#This just disables the script by writing K instead of S  in all the runlevels. The script itself remains untouched.

Disable:  update-rc.d foobar disable

command runlevel tells you the default runlevel.

command telinit and then the runlevel takes you to that runlevel.

For example telinit 6 will reboot.

The default runlevel is written in /etc/init/rc-sysinit.conf.

/etc/rc.local and /etc/crontab have user commands that needs to be started during start up. /etc/rc.local is run in the end.

The  other strategy is the UpStart / Systemd from Ubuntu. The rc.d strategy is from  the SystemV days.

In the upstart if you want to disable a service temporarily, just type manual in a file /etc/init/servicename.override.

    echo manual | sudo  tee /etc/init/servicename.override.
    echo start | sudo tee  /etc/init/servicename.override.


If you want to start/disable the service later, then  just

    systemctl disable thinkfan
    systemctl start servicename


Two kind of buses: system bus and session bus ( after login )

The --system and --session options direct dbus-send to send messages to
       the system or session buses respectively. If neither is specified,
       dbus-send sends to the session bus.


Init
  * 0 : shutdown
  * 1 : single user mode
  * 2 : multi user mode
  * 3 : full multiuser mode
  * 4 : nothing
  * 5 : graphic
  * 6 : reboot


Status all

The main command used to introspect and control systemd is systemctl. Some of its uses are examining the system state and managing the system and services. See man systemctl for more details.


    service --status-all
    systemctl status enable disable restart start stop
    systemctl daemon-reload
    systemctl list-units
    systemctl list-unit-files

Logging method

    journalctl -xe

====== GRUB ======

install Grub

Type the following command to install GRUB on the USB device:

grub-install –root-directory=/media/usb /dev/sdb
if UEFI
sudo grub-install --efi-directory=/boot/efi /dev/sda

Create grub.conf:

cd /media/usb

mkdir -p boot/grub


Grub command line
default=0
timeout=5
root (hd1,0)
title Fedora Linux
kernel /vmlinuz
initrd /initrd.img

mkfs.fat -I /dev/sdX
It is typical for fixed disk devices to be partitioned so, by default, you are not permitted to create a filesystem across the entire device.  mkfs.fat will complain and tell you that it refuses
           to work.  This is different when using MO disks.  One doesn't always need partitions on MO disks.  The filesystem can go directly to the whole disk.  Under  other  OSes  this  is  known  as  the
           'superfloppy' format.  This switch will force mkfs.fat to work properly.

isohybrid isofile.iso --entry 4 --type 0x1c

dd from to

Now your stick is ready to be booted.






======  PRINTING ======


All printing is done by the command lpr

To print a document to pdf, install a package cups-pdf. To read the pdf sudo

apt-get install zathura

Issue a command ls | lpr -P PDF to check if the pdf is generated in your home folder ~/PDF/.

A useful hint is the tab. Once you write lpr -P and press the TAB, a list of printers would be generated and one can choose which one to use. However, it could be that the printer is not accepting requests etc. For that it is useful to see the complete status before issuing the print request. This can be done via the command lpstat -t.

lpr -P PDF hello.txt would generate the hello.pdf in the above folder. However, with the word document, the above didnt work. I got a blank page.

LPR Options

lpr -P PDF -o columns=2

    -o media=A4
    -o landscape
    -o page-ranges=1,10 #1-4,7,9
    -o cpi=10 # character per inches
    -o page-left=20
    -o page-bottom=20
    -o page-right=20
    -o page-up=20
    -o lpi=6 # lines per inches
    -o scaling=50
    -o prettyprint
    -o number-up=4 # number of pages in one page
    -o wrap # no wrap disables wrapping.
    -o sides=two-sided-long-edge -#1 # number of prints
    -o output-order=normal # reverse for printer with facedown printing
    -o job-sheets=topsecret,topsecret
    -o page-set=odd # prints only odd pages
    -o page-border=none # double, single, single-thick
    -o number-up-layout=lrtb #
    -o fit-to-page name-of-the-file-to-print
    -o page_ranges=
    -o sides=two_sided_long_edge
    -o number_up=2
    -o number_up_layout=lrtb


To create a printer instance, as a user issue the command:

lpoptions -p printer/set1 -o option1=value -o option2=value

To delete a printer instance issue the command:

lpoptions -x printer/set1

lpr -P printer/set1 filename # stat with lpstat

To see the queue one can do the following command:

lpstat -W all / completed / not-completed

lpstat -l gives the information about the status of the printer



====== Regular expressions ======

    find ./project/ -name *.h  -exec sed -i 's!gnuplot/!gnuplot-iostream/!g' {} \;
    find $FFMPEG_PWD/../ffmpeg-install/lib/pkgconfig -name '*.pc' -exec sed -i 's!/local/git/PriorityGraphSensors/libs/ffmpeg/../ffmpeg-install$!/usr/local!' {} \;

A good site to test your regular expression is regex101.com.

Some  of the important keywords are ^, (), {}, [], \w, \b, +, \*. If you know  what these keywords do, then you can very well decode a lot of regular  expressions. Optional keywords such as i, m, g etc. are also important.

In  python, the module is re and the regular expression needs to be  compiled first using re.compile(the re string, re.MULTILINE ). To be able  to use the regular expression, you have to apply it by using for example  re.findall(the compiled regularexpression, your test string). Many  actions can be done once the regular expression is compiled.

I  tend to use -regex instead of -iname in the find command. Although, it  is a little bit more complicated, it helps me practise the regular  expressions. There are many flavors of regular expression and on the  linux machine, I use posix-extended. This can be done by passing the  option -regextype posix-extended to the find command.

* - 0 or more times the preceeding character
+ - 1 or more times the preceeding character
? - 0 or 1 time the preceeding character

    echo LS_COLORS | sed ‘s/01=34/01=35/’
    echo "hi there" | sed 's/hi/hello/'

    quiet suppresses lines that wont be changed. p just prints but does not act.
    xargs sed --quiet 's!gnuplot/!gnuplot-iostream/!gp'

p in sed is very powerful because it prints the name of the original and  the name of the changed thing. This can be then piped to xargs with -n2  i.e

    sed ‘p;s/pattern/replacement’ | xargs -n2 mv

Ofocurse the sed  command itself has to have an input and this comes from another pipe  such as

    ls | sed
    echo “dfds” | sed

    su – password



====== Shell ======


    IFS=$'\n' files=($(find . -name '*.sh'))
    
while
do
done
$VTD_ROOT/Runtime/Core/SimServer/simServer $CONFIG_FILE 3>&- &
(echo "$!" >&3 &)
exec 3>&-

to compare numbers use -gt -le -eq

Command Substitution $()
and Process Substitution : arguments will look like /dev/fd/3 and /dev/fd/4: they are file descriptors corresponding to two pipes created by bash.
echo <(echo) <(echo)
Last command !-1 
Last but one command !-2

$! - pid of the last backgrounded process in that specific shell.
$$ - pid of the main shell.
$? - return value of the script
$@ - all the parameters, like argv
$0 - the first value and so on..

-e (exists)
-eq (equal)
-gt (greater)
for i in `seq 1 10`; do echo $1; done

BASH:

To read a linenumber from one file and print that line from another file.
sed 's/$/p/' linesfile | sed -n -f - datafile

AWK is to check column oriented lines like tables etc.

awk 'NR==5 || NR==9' 

sed 'NUMq;d' file
tail -n+NUM file | head -n1

rsync folder/ copies the contents of the folder but not the folder itself
cp folder/ copies the folder/

#!/bin/bash
count=0
while (( $count < 20 ))
    do
    printf -v website "htps://..." $count
wget $website
    count=$(($count+1))
done

Redirection: command > all.log 2>&1

The  most irritating and intelligent language. The syntax of bash is very  tight bound. The assignment of variables and their manipulation etc. is  not a piece of cake. For arithmetic operations, always use double  paranthesis. This is because is each paranthesis is its own shell.  ans=((1+2)) ;echo answillgiveus3here.Anotherexampleisans=(ans+1). Similarly compare operations in while loop such as while ((ans<5))willwork.Similiarlyifif[ans -ge 3 ]; or if (( ans<=5));willwork.Thearraysareassignedbyarray1=(“hello”,“world”).Anotherfactoristhespaces.Onealwaysneedsaspaceafter[andbefore].Thisisimportantinifconditionssuchasif[−ddirectoryname].Duringassignmentitisalsoimportantthatthereisnospacebetweenthevariablesand=.Onereadstheinputinthevariableusingreadvariablenameandnotreadvariablename foo="Hello" echo a((a+=12))echoa printf -v foo_new "%s World" $foo
count=$(($count+1))
Backquotes are used to assign the ouput of the command. Like abc=ls -l. This can also be done as abc=(ls−l)Comparingisachallengeinbash.Tocomparenumbersuseif[i -eq 5 ], comparing strings if [ "$x" == "valid" ]; then
Arrays can be accessed and initialsed : array = ( “one” “two” ) ${array[0]}
So,  I wrote my first complex bash string and the content will display the  lpoptions of a printer. The lpoptions is an option to set the option of  the printer when you print a page. Like how many pages etc.
string=(lpoptions−pPDF);i=1;whiletrue;dores=‘echostring | cut -fi−d‘‘‘;echores; if [ “res”==”];thenbreak;fi;i=((i+1)); done; find ./ -iregex ‘._.(doc|pdf)′−execechofind./−typef−iregex‘.∗.(doc|pdf)’  -cp echo {} ../\; -o means OR -a means and find . -type f ( -path dir1  -o -path dir2 -o -path dir3 ) -prune -o -name ‘_.js’ -o -print find  build -not ( -path build/external -prune ) -not ( -path build/blog  -prune ) -name ‘_.js’ -o -print find /var/repos/LABOR -type d -maxdepth 1  -printf ‘%T@ %P\n’ | sort -n | awk ‘{print 2}
 find dir1 dir2 dir3 -name “*.c”0 the first positional parameter, equivalent to argv[0] in C, see the first argument FUNCNAMEthefunctionname(attention:insideafunction,0 is still the 0oftheshell,notthefunctionname)1 … 9theargumentlistelementsfrom1to9{10} … Ntheargumentlistelementsbeyond9(notetheparameterexpansionsyntax!)_ all positional parameters except 0,seemassusage@ all positional parameters except 0,seemassusage# the number of arguments, not counting $0
; to execute all commands & to execute when previous successful
cat /etc/shells echo $0 env | grep SHELL whereis bash which bash locate bash
printenv set ( the current shell value )
export TEST_VAR echo TESTVARexport−nTESTVAR(justforprintenv)unset/etc/profilexclip−o−ddisplayechoDisplay
export  -n TEST_VAR undoes from env varible to shell variable. unset TEST_VAR  unsets it completely if the environment varialbe, needs to be permanent,  it has to be kept in the .bashrc. But to make it effective, either  close the shell and restrat or simply type source .bashrc printenv |  grep LS_COLORS LS_COLOR_MINE=echo $LS_COLORS | sed ‘s/di=01;34:/di=01;35:/’ backtick ` is used to assign the output of a command to the variable.
.zshrc autoload -u prompt promptinit oh-my-zsh/themes. ZSHTHEMES=
set | echo $HOME
setxbmap -option grp:alt-shift-toggle us_en
shopts -s dotglob
If  the command has atleast one mandatory optins then it is not required to  write a minus sign in front of the options. such as tar cf
Use Alt o and Alt l Ctrl o for panels

bash source extenral functions
if [ -f functions.sh ]
/path/functions.sh
fi


    grep -r --include='*.tex' -lZ '{fig/.*}' . |  xargs -r0 sed -i.back 's:\({fig/[^}]*\)}:\1.png}:g'

    grep --include=*.{c,h} -r *

    mogrify -format png *.jpg

diff -qr ~peter ~george  |sort ; diff different files but not the contents recursively

diff  ~peter ~george  |sort ;just diff different files including the contents

chmod +t /usr/local/tmp or chmod 1777 /usr/local/tmp

diff -rq directory1 directory2 | sort | less

diff -iBc file1 file2

tar -xvjf tar -xvzf tar -cvzf directory


chkconfig --list

shutdown -c ( cancel ) -k ( send message ) -r ( reboot ) -h ( halt ) -t time delay like now or +15m

DISPLAY=:0 ccsm&

export DISPLAY=:0

sudo dconf reset -f /org/compiz

unity --reset_icons & disown

Key Management
EAP
Phase 2

grub2-install --reached /dev/sdX
update-grub2
root path in /mnt
boot path in /mnt/boot


arp -a  | grep cups

ip link set dev wlan0 up
lshw --class network
lsmod | grep driver

screen
Ctrl A "
Ctrl A c
Ctrl A :
Ctrl A Shift A
Ctrl A Shift S
Ctrl A Shift X
screen -S name
Ctrl A d; detach
screen -r; resume
screen -X -S [session] quit

Generating locales:

sudo locale-gen
dpkg-reconfigure locales
dpkg-reconfigure tzdata
locales --a


ntpq -p
sudo ntpd -qg
sudo hwclock -w


allow-hotplug forces a call to ifup and hence the network interface file is read again. If there are
wpa entries, then the wpa_supplicant and wpa_cli would be called automatically.


new, buffer, bn, bp, b name of the file, set hidden, set confirm, wincmd kjhl.

kemgmt, eap, subject/domain, auth are mandatory. cipher information is not mandatory.

sudo grub-install --target=i386-pc --force --no-floppy --boot-directory=/media/agrawal-local/MULTIBOOT /dev/sdb

sudo mkfs.vfat -F32 -n "label" /dev/sdb
sudo mkfs.ext3 -n "label" /dev/sdb"

mlabel to label a partition


wodim dev=/dev/scXX -v systemrescuecd-x86-x.y.z.iso


iso and then post process with isohybrid and then dd to usb stick and then run


set prefix=(hd0,msdos9)/boot/grub
insmod (hd0,msdos9)/boot/grub/linux.mod
The above two command will put grub in regular command mode. This is
the extra step you need in case of GRUB2. The below three steps are
options, it may be needed – I am not sure.
insmod part_msdos
insmod ext2
insmod gzio
Now continue with GRUB2 commands.
set root=(hd0,msdos9)
linux /boot/vmlinuz-3.19.0-43-generic root=UUID=0278bf38-1115-4f62-ab63-39d6bedd6b18 ro quiet splash $vt_handoff
initrd /boot/initrd.img-3.19.0-43-generic
boot


fsarchiver probe


====== CMAKE ======



Yes, there is:

File -> Settings... -> Build, Execution, Deployment -> Toolchains -> CMake executable

Then set the custom path.

Note that I do not know if this will solve your specific problem.



====== Fritz box ======


Attaching a USB printer.
Basically,  the USB printer can be used as a network printer. This is done using  the port number 9100. If you want to see if this port number is  supported by the router, Then type nc -zv router_ip 9100. The connection  should be successful. If the connection is not successful, it means any  program is already blocking tis port. The 9100 is a raw data port which  means, the data which is sent to this port is forwarded one to one to  the usb port.
nmap -sP 192.168.1.0/24 will scan all the devices in  the network. You nevertheless need to install the printer driver for  the printer.
http://169.254.1.1/http://192.168.1.3/login.lua?page=/home/home.lua&sid=0419ad3a629b719bhttp://192.168.1.3/login.lua
The  printer also might not work, if the printer is not recognised as a  printer. The fritz box should recognise the connected decice As a  printer and not a usb storage and hence start the printer server which  will start accepting print commands from the client.
To activate printer server, please click on the print fucntion check box in the usb fernanschluss.

====== SSH ======

Ssh-2 Rsa Encryption: aes256-cbc
To check if you already have a key type Cat /home/username/.ssh/id_rsa.pub
If it doesn’t exist generate it. SSH generate ssh-keygen -t rsa -C ” vikas.agrawal@iao.fraunhofer.de ” Passphrase :…
To  extract the generated public key use the following command: Use code  below to copy your public key to the clipboard. Depending on your OS  you’ll need to use a different command: Xclip -sel clip <  ~/.ssh/id_rsa.pub
Generate PGP key: Gpg –key-gen Encrypt: Gpg -e file Decrypt: Gpg -o filename -d filename
One  must have the fingerprint of the remote computer in the file called  known_hosts. If not, then the finger print would be tried to be stored.  However, if the fingerprint was already there, then the ssh connection  would not take place. In order to make this successful, it is important  to delete the entry of the remote computer from the known_hosts file.  This is done via the command ssh-keygen -f /home/name/.ssh/known_hosts  134.2.1.4.181
SSH RSA should be used. DSA is an old protcol and is  obselete. DSA has many security issues. The server key should be kept  in the authorised key or known_hosts so that the authentication takes  place automatically without the user intervention to type in yes.
To  access gitrepos from Jenkins for example, you would change the entry in  the .ssh folder: cat ~git/.ssh/authorized_keys  command=”/home/git/gitServer/gitolite/src/gitolite-shell  jenkins”,no-port-forwarding,no-x11-forwarding,no-agent-forwarding,no-pty  ssh-rsa jenkins@arrakis and then invoke the command ssh -T ( no pseudo  tty ) i.e the method is just for authentication and not for getting a  terminal.
ssh-keygen -t rsa -C “emailid” xclip -sel clip < ~/.ssh/id_rsa.pub
generate  rsa key; put in file .ssh folder ssh-copy-id -i ~/.ssh/id_rsa.pub  username@server.domain.com The id_rsa ( private key ) convert  into ppk and then add to paegent. Put the keys in the authorized keys  The id_rsa ( private key ) ocnvert into ppk and then add to the paegent.  SHA Sha256sum -c “shasum” “filename”
xclip -sel clip | filename ssh-keygen -t rsa -C “email id”
openssl version -a
pscp id_dsa username@server.domain.com


====== Makefile ======

install prefix
make install --prefix=
make install DEST_DIR=
$^ all inputs

$< first inout

This is also the same in Linux

$@ : output
    $($(objects): .o=.c) is a shorthand for $(patsubst %.o,%.c,$objects))

ar rcs – create a library/archive -c options says not to  run the linker i.e
just compile -L is the path to the library files. -l  libraryname

FORCE in the recipe will always run that is the same as  .PHONY: clean or clean : FORCE FORCE:

ELF relocatable file executable file shared object file

ELF  Header, Program Header, Section header SEgments: Text,(code)

Data(initialised read write data),
BSS(uninitialised data) Sections:  .symtab, .strtab, .shstrab, .debug, section headertable

readelf, size, file, objdump -i

ldd to determine the dependancies for the dynamic link library. .a is static, .so is shared object ( dynamic )

jre 1.6.0 in /usr/lib/jvm

run but not develop java programs – JRE develop – JDK

gcc, i385-all, make

Debugging  and flashen is parallel to one another. Most of the devices which can  flash can also be debugged at the same time. The examples are

There  are various debug formats called as dwarf-2 stab gdb1 gdb2 gdb3

In  computing, the Executable and Linkable Format (ELF, formerly called  Extensible Linking Format) is a common standard file format for  executables, object code, shared libraries, and core dumps.

Today  the ELF format has replaced executable formats such as a.out and COFF  Type of format for ELF: Binary, executable, object, shared libraries,  core dump
ELF COFF HEX OUT

Install Prefixes
    cmake CMAKE_INSTALL_PREFIX=dir ..; make; make install
    ./configure --prefix=dir; make; make install

There are two major open source assembler, YASM and GAS. GAS uses AT&T assembler syntax and YASM uses Intel assembler syntax. However it is possible to use AT&T assembler syntax or viceversa by passing appropriate flags such as yasm -p gas while compiling the file.

I agree that pkg-config should be avoided IF a Find\*.cmake exists, but that still isn't the case for the latest version of cmake in 2016.

====== Further linux Commands ======

    rename 's/txt$/md/' *
    ls | grep \.png$ | sed 'p;s/\.png/\.jpg/' | xargs -n2 mv
    convert -resize 50% *.jpg or *.pdf
    convert -density 200 -resize 50% -quality 80 *.jpg or *.pdf
    Sudo useradd -G shadow tomcat7

Virtual machine Ubuntu:  /lib/modules/3.2.0-33-generic/build/include /usr/bin/gcc Fusion or  Workstation virtual environment between guestos and host os by running  vmware-config-tools.pl you can again configure vmware tools. Thinprint  is driver free printing. vmware tools can be run by inviling  /usr/bin/wmware-toolbox-cmd manually start /usr/bin/vmware-user. To used  the vmxnet driver,

Restart networking using the following commands  /etc/init.d/networking stop rmmod pcnet32 rmmod vmxnet modprobe vmxnet  /etc/init.d/networking start
sudo add-apt-repository ppa:user/ppa-name
ppa:gwendal-lebihan-dev/cinnamon-stable and then apt-get update
ldd  to determine the dependancies for the dynamic link library. .a is  static, .so is shared object ( dynamic ) df -aTh /dev/sdb1 gives the  size, filesystem etc of the usb disk.
cat /proc/cpuinfo gives the info about the CPU
cat /proc/mounts gives a list of filesystem in your present container
mount gives a list of mounted filesystems
Manually  changing files: /etc/vim/ /opt/eclipse/cpp-mars/eclipse /local/agrawal/  /usr/share/applications/eclipse ~/.bashrc ~/.vimrc.local  /usr/local/bin/arm-* ~./gitexcludes
chsh change shell
usermod -s /bin/bash agrawal
.profile will be read as soon as your profile is loaded.  add exec /bin/bash --login sudo dpkg-reconfigure keyboard-configuration  corrected my problem with the keyboard. install dconf-editor for date  time settings etc in the console. sudo apt-get install console-common  and then run the command sudo kbd-config. This will fix your keymap.
copy  bashrc from /etc into home folder and this can be edited If a user is  deleted with userdel -r username and still files are present, then the  files user change into his UID because this user is notavailable  anymore. The UID is a continous process and would be never allocated any  previous UID with adduser. This is prevent getting access to files that  has been left by the previous user. password=hello EOF reading input  sudo passwd username password confirmpaassword sudo passwd vagrawal  << EOF passwordpassword EOF find -name '.wsdl' | xargs emacs {} find -name '.wsdl'  -exec emacs {} \; find ./ -name config.xml -ok sed -i  's/itlx3301/itlx3301/gc' {} \; instead of -exec above in case you want  to append your own parameter after xargs then it should be done like  this: xargs -I {} cp {} 1_{} This replaces the string {} into nothing  and hence what remains are really the arguements. The arguements are  also done linewise and not all in a single line.
find ./ -name "main.h" | xargs  basename -s .h | xargs -I{} sh -c "expand '{}.h' > '{}-spaces.h'"
The  {} is replaced with the file name found by find. This would execute the  command for every found file. If you want to execute a command with all  found files as arguments use a + at teh end like this:
find -name '*.wsdl' -exec emacs {} +
ps -aux has VSZ RSS ( sizes ) and then state ( S is in interrupted sleep which means it is waiting for an event )
cut -d: -f1 /etc/passwd
To log off the user. skill -KILL -u vivek
ipconfig /renew
mount -t vboxsf sha
    ipconfig /releasere /home/agrawal/host
    automount /etc/rc.local
    addser -n ( do not create a home directory ). Here if you want to never have a home directory, then one can edit the file /etc/adduser.conf
Add a  user to a group 
    usermod -a -G group user 
Remvoe a user from a group If  no user exists, then 
    deluser user group 
If the user exits, then 
    usermod  -G "" username 
    adduser user group 
    groupdel userdel -r user ( delete with  home directory ) 
Entries in the vipw -g is automatically deleted when a  user is deleted. His remaining files are marked with his uid ( a number ). Hence the unix system never automatically assigns the same uid which  had been already used once.
find /home -user tomcat find /home -group tomcat
cut -d: -f1 /etc/passwd vipw vipw -g
/etc/passwd : atributes of users /etc/shadow : attributes of users password /etc/groups : atributes of groups
keepnote
yum list all | installed yum history yum history info "id" ; to execute all commands & to execute when previous successful
repoquery --list "packagename"
yum groupinstall -y "DEvelopment" "Development Tools"
du -hc screen
configure --enable-win64 make make install
/etc/yum.conf /etc/yum.repos.d /var/log/yum.log
sudo yum install 'ls | grep rpm'
cat ssl_request_log cat access_log cat ssl_error_log cat error_log
tail -c 100000 secure | less
TLS - Transport Security Layer is a replacement of SSL. But still SSL is more popular.
sudo occ files: scan all
config autostart cat /etc/rc.local cat /etc/crontab
xclip -sel clip < filename ssh-keygen -t rsa -C "emailid"
HOTSPOT
switch workspaces : Ctrl Alt Arrow
ifconfig -a
Printing is on the downside of the paper
yum repolist
set | echo $HOME
setxbmap -option grp:alt-shift-toggle us_en
watch -n 0.1 "dmesg | tail -n $((LINES-6))"
psep id_dsa username@server.domain.com
scnadmin create /var/repos/master_Exams chgrp groupname directory or filename sudo grep heli /etc/groups
chown owner:group directory / filename
chown -hR
rsa should be used and dsa is not so good implemented
Generate  rsa. Put in the .sh filder ssh-copy-id -i ~/.ssh/id_rsa.pub  username@server.domain.com The id_rsa ( private key ) convert  into ppk and then add to paegent.
sudo yum repolist all sudo yum-config-manager --disable "name" sudo yum-config-manager --add-repo "URL"
sudo yum list available
cat /etc/shells
echo $0 env | grep SHELL
whereis bash which bash locate bash
grep -A5 -B5 supported
services.msc sfc netsh shutdown /s
6.6 3.2.29 ftp://ftp.scientifilinux.org/linux/scientific/6.6/x86_64
rpm -Uvh http://download.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm
Yum repolist.
Epel shud appear. xclip -sel clip < ~/.ssh/id_rsa.pub
Sudo mount -t vboxsf -o uid=UID,gid=(id -g) share ~/host /os
[sl] [sl-security] [sl-source]
EAP-TTLS Extensive Authentification Protocol
import key shop -s dotglob
jre 1.6.0 in /usr/lib/jvm
run but not develop java programs - JRE develop - JDK
rpm -e remove rpm -Uvh rpm -ql jdk.x86_64
lsof - lists open files umount -l /media/.. ( lazy )
fuser find uers processes fuser -v /media/
certmgr.msc
Alt F2 - Open a program gnome-do gconf_editor& rdesktop -g 1680*1050 -u agrawal ork-win
Df  is for disk space. The command is df -h ( h means human readable )  Vmstat if for memory. The command is vmstat -Sm ( m means mega byte )
Others are du and ls. Du is for diskusage.
Du ./ -h | grep '50K'
find ./ -name "own*" Find ./ -size "1M>"
Cd /etc/yum.repos.d To start a program automatically, put ur file executables in
Wget "the url with the data"
To install wine Wget Configure Make Make install
Command to install linux source Command to download is apt-get source linux-image-$(uname -r)
Packages required: Downloading Dpkg-dev
Fakeroot is the command to build the kernel.
Installed git, subversion, git-core Svn checkout svn://developer.berlios.de/socketcan/trunk
Git clone git://kernel.ubuntu.com/ubuntu/ubuntu-maverick.git
Fakeroot debian/rules clean Dh_testdir
Distro: Lsb_release -a Uname -r
Package manager: vi /etc/apt/sources.lst Apt-get update this updates the package and the release.
Apt-get install "packetname" Apt-get update Apt-get
Vmware: Vmware-config-tools.pl Vmware-hgfsclient : lists the shared folders
ELDK: Sudo apt-get install ia32-libs ( for running for eldk on 64 bit hosts )
SHA Sha256sum -c "shasum" "filename"
find ./ -name "*.c"
mount -t iso9660 /dev/hdc /media/cdrom Umount /dev/hdc
Cat /etc/mtab
Apt-get source kernel-source-2-4-27 Or Apt-get install kernel-source-2-4-27
Apt-get source linux-headers-$(uname -r)
Ncftp ftp.sunet.se Wget ftp://ftp.sunet.se/pub/linux.....
CDs
Download the iso image using wget and the url Then mount the iso image using the command mount -t iso9660 /
Making an iso image
mkisofs
-A "ELDK-4.2 -- Target: PowerPC -- Host: x86 Linux" \ -publisher "(C) date "+%Y" DENX Software Engineering, www.denx.de " \ -p "id -nu@hostname -- date" \ -V ppc-linux-x86 \ -l -J -R -o eldk-ppc-linux-x86.iso ppc-linux-x86/distribution
Mount -o loop "isoimage" destination directory.
Directory structure for the apt
Archive.debian.org/debian main sarge
Which means pick up the the sarge distribution ( it should be a folder in the dists directory ) and then go the folder main.
Tar -xjvf .bz2 archive
Tar -xzvf .tar archive
Tar -cf directory



patch -p0 < patchname

Iwlist scan
Entry for /etc/network/interface
auto wlan0
Iface wlan0 inet dhcp
Wpa-ssid Agrawal, Vikas
Wpa-psk guars0468

iface eth0 inet static
    address 198.51.100.5/24
    gateway 198.51.100.1

Sudo add-apt-repository ppa:kivy-team/kivy


/etc/rc.local
Put the mount command in mount -t vboxsf share /home/agrawal/host
automount /etc/rc.local

userdel user
/etc/passwd - attribs of users
/etc/shadow - attribs of user password
/etc/group - attribs of group


openssl version -a

wget fileurl

dig url
host url
host ip_address

sudo iwlist wlan0 scan | grep "ESSID"

sudo iwconfig wlan0 essid network-essid

iwlist
sudo iwconfig wlan2 mode master
apt-cache depends owncloud
ifconfig obselete ipaddr ip link

sudo yum install wireshark
sudo yum install wireshak-gnome
lsusb
netsh wlan show drivers


shared clipboard
import screenshot.png
display screenshot.png
mc
firefox -P
keepnote
yum list all | installed
yum history, yum history info "id"
; to execute all commands
& to execute till the first failed.

raspberry --list "package name"
yum groupinstall -y "Development Tools"

import site; site.getsite packages

Lockhunter

du -d1 -hc
screen

configure --enable-win64
make
make install

/etc/yum.conf
/etc/yum/repos.de
/var/log/yum.log

sudo yum install 'ls| grep rpm'

cd httpd
{
cat ssl_request_log
cat access_log
cat ssl_error_log
cat error_log
}

tail -c 10000 0 secure| less

TLS is a replacement of SSL. However people keep saying SSL

sudo occ files_scan all

config autostart
cat /etc/rc.local
cat /etc/crontab

xclip -sel clip | filename
ssh-keygen -t rsa -C "email id"
hotspot

ifconfig -a

yum repolist
set; echo $HOME
    setxbmap -option grp:alt_shift_toggle us_en
    watch -n 0.1 "dmesg | tail -n $((LINES-6))"

pscp  id_dsa username@server.domain.com

svnadmin create /var/repos/master-exams
chgrp groupname directory/filename


chown user:group directory/filename
chown -hR

rsa should be used, because dsa is not so good implemented

Put the keys in the authorized keys

generate rsa key; put in file .ssh folder

ssh-copy-id -i ~/.ssh/id_rsa.pub username@server.domain.com

The id_rsa ( private key ) ocnvert into ppk and then add to the paegent.

sudo yum repolist all
sudo yum-config-manager --disable "reponame"
sudo yum-config-manager --add-repo "URL/enable.repo"

sudo yum list available

cat /etc/shells

echo $0
env | grep SHELL

location
whereis bash
which bash
locate bash

grep -A5 -B5 filename

services.msc
sgc
netsh
shutdown /s

[sl]
[sl-security]
[sl-source]

install group

EAP_TTLS
Extensible Authentication protocol
import key
shopts -s dotglob

Run but not develop Java programs: JRE
Develop : JDK

rpm -e <packagename> remove
rpm -Uvh
rpm -ql jdk.x86_64
lsof : list all open files umount -l /media/...
fuser find user process
fuser -v /media/..

certmgr.msc
Roaming /microsoft/system/certificates

rpm -ivh --testrpm
rpm -qpr rpm

install yum --nogpgcheck localinstall prackagename
yum-config-manag3er --add-repo ucl.repo
yum-dowloader --resolve package

Esc Tab -  autocomplete


minicom
profiles in /etc/minicom

setsend /dev/ttyS1 autoconfig
minicom -s
groups agrawal
usermod -a -G groupname username
sudo setsend /dev/ttyS0 -V autoconfig
diff -iwy --brief Dir1 Dir2
diff --side-by.side --supress-common-lines

diff -c ( suppress commong lines



====== VIM ======

    vim :e file, :b1, :v, :y, :p, :d
    :windo diffthis
    :windo diffoff

    set tabstop=4
    set expandtab
    retab
    set list

    count number of occurences of a pattern - %s/pattern//gn. If you have already searched using /, then simply :%s///gn

    vim test.yml, windo diffthis, vert diffsplit test_original.yml, read test.yml, delete first line, diffoff, windo 
    diffthis, checktime
    ls, bnext, bprev, bfirst, blast, bdelete, badd
    new, vnew
    vsplit
    split
    C-w - close, open, w,


You can learn the ASCII or Unicode value of the character under the cursor by pressing ga in command mode or :as / :ascii on the command line . This displays the value of the current character in decimal, hex and octal. (Think "get ascii.")

Select all ggvG

Copy All %y+

    "*yy #copy to clipboard

    "+yy

:%!xxd

vim -b ( reveals everything )


shell: startup
netsh
schtasks

curl/wget

Both are bidirectional and to get data from the websites
-c continue
-O the name of the downloaded file will be put in this folder

--no-check-certificate

mtab will contain the enry to the usb stick

nc -ul localhost 48772
socat, netcat, nmap
echo -n "hello" | nc -u -w1 localhost 5000


lpstat -a
lpstat -H
lpr "Hello"  goes to the default printer

arp -a
netstat -r

nmap -sP 10.0.0.4/24

set defaut printer and send.


lpr "filename"


Number of printers can be seein in the group policy.


printenv
set ( the current shell value )

export TEST_VAR
echo $TEST_VAR
    export -n TEST_VAR ( just for printenv )
    unset
    /etc/profile
    xclip -o -d display
    echo $Display

export -n TEST_VAR undoes from env varible to shell variable.
unset TEST_VAR unsets it completely
if the environment varialbe, needs to be permanent, it has to be kept in the .bashrc. But to make it effective,
either close the shell and restrat or simply type source .bashrc
printenv | grep LS_COLORS
LS_COLOR_MINE=`echo $LS_COLORS | sed 's/di=01;34:/di=01;35:/'`
backtick ` is used to assign the output of a command to the variable.

/usr/share/vim/vim74/colors  ( vim74 is the vimversion )
in /usr/share/vim/vimrc write color desert
or you can also write in /etc/vim/vimrc.local simply one line color desert.
This line however should be read by /etc/vim/vimrc ---> you have to check here.

REPOS:

gitweb conf -> /etc/gitweb.conf
install dir /usr/share/gitweb
In apache2 /conf.d/gitweb
system-config-firewall install gitweb, httpd, git-core
/home/trackplus/plugins/portal-5.0/config.php



netstat -fulpn | grep 80
/etc/init.d/httpd start
This reads from /etc/httpd/conf.d
httpd -v

/etc/sysconfig/httpd
uncomment /usr/sbin/httpd.worker
test with 127.0.0.1

.zshrc
autoload -u prompt
promptinit
oh-my-zsh/themes. ZSHTHEMES=
sudo fdisk -l | less
mkfs
hdparam
mount


MTA Mail transport agent exim sendmail postfix
telnet localhost 25
locate master.cf
sudo lsof -n -i:25
netstat -pant ( all )
netstat -plnt ( only listen )


dircolors -b > .dircolors
change the first line to export and remove the second line.

if [ -f ~/.dircolors ]; then
    . ~/.dircolors
fi

On linux you can use either command line tools such as cdrecord/wodim or graphical tools such as k3b, brasero or xfburn.
source .bashrc

Partition:


Writing the ISO image file to a CDRom

To use wodim or cdrecord run the following command in a console:

mount a iso file in a real cd

cdrecord systemrescuecd-x86-x.y.z.iso

mount a iso file virtual cd:
 mount -o loop,exec /path/to/systemrescuecd-x86-x.y.z.iso /tmp/cdrom

mount a usb:
mount /dev/sdb2 /media/usbdisk ( implicit auto or otherwise -t filesystemname )
the file system is read from /proc/filesystems

To see the whole partition in gui - gnome-disk-utility
in console, parted or gparted or fdisk

make the disk bootable: Startup Disk Creator, Unetbootin
or command line:
1. syslinux /dev/sdb1: syslinux is a boot loader for the Linux operating system which operates off an MS-DOS/Windows FAT filesystem.
OR

Install Grub

If nothing works, simply remove, purge grub and install grub2.
grub-mkconfig uses tempates from /etc/grub.d and /etc/default/grub
aand then writes into /boot/grub/grub.cfg
Type the following command to install GRUB on the USB device:
# grub-install --root-directory=/media/usb /dev/sdb
Create grub.conf:
# cd $/media/usb
# mkdir -p boot/grub
Edit the grub.conf file

default=0
timeout=5
root (hd1,0)
title Fedora Linux
kernel /vmlinuz
initrd /initrd.img


sudo apt-get install gnome-tweak-tool



grub4dos download
boot disk creator
diskpart is a powershell utility to create a bootable  usb in windows. It is formatted into any filesystem and set active by  simple commands. Also another way is the Windows USB/DVD Download tool  Also another way is the Fedora Live USB creator Also another way is the  Startup Disk Creator in GNOME Ubuntu I am using Unetbootin
The method to write the image onto a SD card is using the Win32DiskImager
you will find an extensive list here: http://www.howtogeek.com/127377/the-best-free-tools-for-creating-a-bootable-windows-or-linux-usb-drive/?PageSpeed=noscript


====== Linux ======


acpitool  -> it reads the /proc/cpu and /sys/class and displays in human  readable format. sudo lshw -short -C disk sudo lshw -class disk -class  storage smartctl -d ata -a -i /dev/sda ( gives an overview of the  diagnostics hdd ) hdparm -S 1 ( multiple of 5 seconds for timeout to  turn off the spindle motor ) hdparm -y ( force in standby mode ) hdparm  -t / -T ( read from hard disk / memory to determine reading powre )  iotop iostat -pxd Result code :UHD01V000-BL7V1K
./grub-mkconfig -o  /boot/grub/grub.cfg grub-install --root-directory=/ /dev/sda The  --root-directory=/x option tells grub where to look for the grub  directory during the installation process. dd if=/dev/sda  of=host1-sda.mbr count=1 dd if=host1-sda.mbr of=/dev/sda count=1
dd  if=host1-sda.mbr bs=1 count=444 > new.mbr # only the mbr and not the  partition table, because we dont want to disturb the partition table.  dd if=/dev/sda bs=1 skip=444 count=68 >> new.mbr dd if=new.mbr  of=/dev/sda count=1
sudo ifup -a --allow=auto
sudo add-apt-repository ppa:relan/exfat sudo apt-get install fuse exfat-utils
debootstrap trusty trusty-chroot
SHOTWELL_LOG=1 gdb shotwell 2>&1 | tee shotwell.gdb

    --include=*.txt  

job.FileMontor needs libjnotify.so in /usr/lib


===== Hard disk formatting =====


The hard disk is divided into tracks and each track is further divided into sectors. A group of sectors ( normally 512 bytes ) is called a cluster.
A cylinder is a group of sectors on different platters and thus giving an impression of a cylinder.
The cylinders has a significant meaning because the magnetic head can access many platters at the same time and hence if the corresponding data is stored in
the same sector number but in different platters, then the access to the data is much more efficient.



====== DIA ======

First step after installing DIA is to go to File->DiagramProperties and do the settings there.

Figure 1: [fig:example] This is an example of figure included using LaTeX commands.
In  the Grid section, use 0,5 and 0,5 for Spacing and 1,1 for Visible  Spacing. The visible spacing is just to show the lines, whereas Spacing  is important for the blocks to snap on the grid.
The Diagram  Properties is just for that Diagram. In case you want to make your  changes permanent, the above settings needs to be done in the File ->  Preferences. Some other changes are Magnify which will set a default  value of the magnification of one page
Antialiasing to fix the exported diagram size.
Align – Alt-Shift-M to straighten the connected arrows between the obhects

====== Music ======


I  had organised all my music with a software called media monkey. It also  has an inbuilt player to play the audio and video files. However, as a  native application, I prefer VLC Media player. Another player is called  mplayer. In Linux, one can stream audio files directly from the url  using a packet called livestreamer.It can be downloaded via sudo apt-get  install livestreamer. One can also directly play streaming by
mplayer2 http://listen.radionomy.com:80/CaretoFUN
livestreamer –player=mplayer http://www.youtube.com/watch?v=U4Pw3ofFWgs 360
You can search the music here: http://www.xatworld.com/radio-search/


====== QT ======

Install  qt5-default. Check if the  /usr/lib/x86_64-linux-gnu/qtchooser/default.conf has qt5 entries. We can  also get to qmake by typing qmake -qt=qt5
libav ( avconv ) and ffmpeg ( ffmpeg ) are competitors but finally ffmpeg wins and is included in the ubuntu versions.
wget https://www.ffmpeg.org/releases/ffmpeg-2.8.5.tar.bz2 then ./configure then make all and then make install



====== APT ======

If broken packages

sudo dpkg -i --force-overwrite /var/cache/apt/archives/libjline-java_1.0-1_all.deb


deb [locationurl] [os] main contrib non-free
It  is impossible to work without tools and to download the tools one needs  more tools and that is the apt. Locations are /etc/apt/source.list  /etc/apt/source.list.d/
    dpkg-query -l, dpkg-query -L packet name,  aptitude show packetname, apt-get install –simulate, sudo apt-get  install -f, sudo apt-add-repository -r ppa:username/ppaname or without  -r to add, sudo apt-get remove or purge packetname, sudo apt-get update  are some basic commands.

The softwares that have been installed or  were installed are seen at /var/lib/dpkg/packages. The command  dpkg-query looks under this directory. The fetched packages are seen at  /var/lib/apt/lists/. The command apt-cache search looks into this  directory.
    Add: sudo apt-add-repository ppa:username/packagename  Remove: sudo apt-add-repository -r ppa:username/packagename This will  make an entry under /etc/apt/source.list.d

Purge: Purging a  PPA means, downgrading the packages in the selected PPA to the version  in the official Ubuntu repositories and disabling that PPA. PPA Purge  does exactly that. To install PPA Purge run the following command: sudo  apt-get install ppa-purge

    sudo apt-get -o  Debug::pkgProblemResolver=yes dist-upgrade 
    sudo apt-get -u dist-upgrade  
    sudo apt-get -f install 
    sudo apt-get clean
    apt-cache search –full .  | grep ‘^Package’ would give the list of all the packets found under the /var/lib/dpkg/lists. This list as described above is created by  running apt-get update which parses the source.list file and  source.list.d
    dpkg-query -l provides all the packets that are  installed. However if you do 
    dpkg-query -l ‘*’, it lists all the  packages that are installed and not installed.
    sudo apt-get purge  foobar #means that it is identical to remove except that packages are  removed and purged (any configuration files are deleted too).

Adding  a repository to ubuntu: The etc/source.lst file consists of the  repositories where ubuntu looks for the files. The branches are main,  restricted, universe and At the server side, following directory  structure should be present.
Directory structure for the apt  Archive.debian.org/debian main sarge Which means pick up the the sarge  distribution ( it should be a folder in the dists directory ) and then  go the folder main.
–dists –pool –project –tools
    apt-cache depends owncloud






====== TODO2 ======


Color grep
apt-cache search --full password | grep --color=always Package | less -RNS




apt-get install open-vm-tools-desktop fuse instead of vmware tools.
apt-get install packetkit

gpg-zip -c -o file.gpg dirname
gpg-zip -d file.gpg


thermald
linux-tool-common gives cpupower  and cpufreq options
intel_pstate needs to be activated and can be checked
intel_pstate=enable in grub after quiet splash

select-default-ispell
setupconf


git merge -e --no-ff --stat

exo-preferred-applications

vfat auto,users,uid=1000,gid=100,dmask=000,fmask=111,utf8

# dpkg-reconfigure xserver-xfree86

xserver-xorg-driver-nouveau has to be deleted
you can do this using additional drivers.
Select nvidia.

modprobe -v module
modprobe -r module

list of all modules integrated in the kernel lsmod
list of all modules ; ls /lib/modules/$(uname -r)/kernel/drivers/; ls /lib/modules/$(uname -r)


dpkg-reconfigure kdm
DISPLAY=:0 compiz --replace

Alt PrntScreen K kills your Display manager.

dconf reset -f /org/compiz/
nohup setssid unity


nohup compiz --reset
nohup unity --replace

/etc/X11/default-display-manager

/usr/bin/*session

XDG_CURRENT_DESKTOP
wmctrl -m
echo $DESKTOP_SESSION

sudo update-manager -d


i8kutils - dell fan utils
thinkfan - lenovo fan utils
/etc/thinkfan
/etc/i8kmon

/etc/modules _ kernel modules to be loaded during boot time.
/etc/modprobe.d/options .. options



apt-get install gitlab-ce
/etc/gitlab/gitlab.rb
gitlab-reconfigure

mkswap -f partition
swaplabel -L "<abel" partition
mkfs.ext4
mkfs.ext4 -L "volume"

\usepackage[export]{adjustbox}


mobaxterm. apt-cyg
git submodules, git subtree git subrepo
bizcare.co quadrocopter
Pandoc
Qemu
-m 256M

qemu-kvm
-net nic -net user
-net none

qemu-img --help  . convert disk images

openvs
dreiceck, viereck , gesselschaft
raspberry zero


xserver-xorg-driver-nouveau has to be deleted
you can do this using additional drivers.
Select nvidia.

modprobe -v module
modprobe -r module

list of all modules integrated in the kernel lsmod
list of all modules ; ls /lib/modules/$(uname -r)/kernel/drivers/; ls /lib/modules/$(uname -r)


dpkg-reconfigure kdm
DISPLAY=:0 compiz --replace

Alt PrntScreen K kills your Display manager.

dconf reset -f /org/compiz/nohup setssid unity

nohup compiz --reset
nohup unity
--replace

/etc/X11/default-display-manager

/usr/bin/*session

XDG_CURRENT_DESKTOP
wmctrl -m
echo $DESKTOP_SESSION

sudo update-manager -d


i8kutils - dell fan utils
thinkfan - lenovo fan utils
/etc/thinkfan
/etc/i8kmon

/etc/modules _ kernel modules to be loaded during boot time.
/etc/modprobe.d/options .. options



mkswap -f partition
swaplabel -L "<abel" partition
mkfs.ext4
mkfs.ext4 -L "volume"

\usepackage[export]{adjustbox}


mobaxterm. apt-cyg

bizcare.co quadrocopter
Pandoc
Qemu
-m 256M

qemu-kvm
-net nic -net user
-net none

qemu-img --help  . convert disk images

openvs
dreiceck, viereck , gesselschaft
raspberry zero



====== Mails ======

Thunderbird is a very good email  client with almost everything. I have been using this email client for  quite some time now. The best thing about it, is that everything is  under one folder. If you are migrating to some other computer, you just  need to copy this folder ( called the profile folder ), and paste it  into your new computer. You wont find a difference at all in working  with your emails. All Addons, settings, accounts, address books, local  folders etc. are there as before.
The only thing one needs to  think about is the command thunderbird -P This is a very powerful  command and lets you choose the location of the profile folder.
It  is also possible to read and write emails over the command line. This  is useful for example, if you are in the shell and want to extract an  attachment like pictures etc sent by one of your friends. The command  line arguement for the same is :

====== STRINGS and FOLDERS ======

grep  -i ( case insensitive ), locate, updatedb, tree, less / is look forward  ? is look backward, & displays only those lines where the pattern  is matched. The difference between less and grep is that grep displays  only those lines with the matches, whereas less displays the whole file  and highlights the matches.
Know your computer
One  of the cool things are monitoring your computer in Linux. One needs  many tools to do that like htop, watch -d -n 1 “sensors && lpq  -P PDF”, multitail /var/log/syslog /var/log/kern.log
Using  commands such as hostnamectl, localectl, lshw, lscpu, and lots of other  ls’es, sensors and lots of commands ending with ctl like apachectl etc.  you can have a tons load of information about your computer.

====== Apache ======


.htaccess  wird jedes mal gelesen, conf.d is only during the startup.  /var/www/index.html is the first interaction with the apache. Error log  can be set borh in apache2.conf and sites-enabled/000-default
The  apache2.conf is the entry point. It contains the server root, the time  outs of the server, the location of the log file, log level, the various  modules and conf files that are enabled, list of the ports which is  configured to be listened, the directories in the filesystem, that are  allowed to be accessed, the acccess file name .htaccess that can be kept  in each directory, optinal includes from conf-enabled and site-enabled.  The modules load the shared library and the conf has the configuration  to the shared library. After the configuration is changed, the apache  needs to be restarted in order to build the object file with the new  configuration. sudo a2enmod module_name sudo a2dismod module_name to see  the enabled modules: apachectl -M
in mods-enabled in dav_svn.conf  write the location of the svn-auth.htpasswd and the location of the  SVNParentPath and the access url to the repository in /etc/apache2 :  AuthUserFile svn-auth-htpasswd with the entry
First time: use -c  to create the file Use -m to use MD5 encryption of the password, which  is more secure htpasswd -c -m /etc/svn-auth.htpasswd harry
Processes
PGREP
pgrep -a -u username; all processes with names pgrep -n -u username ; newest process with name


====== Socket communication ======


Most  important things in socket communication: a server needs to bind to a  socket a client needs to send the data on this socket.
I have  tried the approach of reverse programming, which helps me to include  things as I write.So, here is how I write a socket program. The below  line tells me everything and now one can create the whole C file by  reverse tracing.
Client:
s = send((int)clientsocket, (void *)message, (size_t)sizeof(message), 0, (struct sockaddr *)&serversocket, (size_t)sizeof(serversocket));
A client Socket () Connect () Write() Read()
A Server
Socket() Bind() Listen() Accept() Read() Write() Close()
IP : 10.0.0.100 Gateway : 10.0.0.1 Subnet : 255.255.255.0
Install Telnet in Windows using command line. pkgmgr /iu:”TelnetClient”
The first thing tht the Bdi looks for is the cfg file and it should be present in the Tftp directory




====== MySql ======

mysql  -u admin -p Enter password: Welcome to the MySQL monitor. Commands end  with ; or \g. Your MySQL connection id is 5340 to server version:  3.23.54
Type 'help;' or '\h' for help. Type '\c' to clear the buffer.
mysql> CREATE DATABASE databasename; Query OK, 1 row affected (0.00 sec)
mysql>  GRANT ALL PRIVILEGES ON databasename.* TO  "wordpressusername"@"hostname" IDENTIFIED BY "password"; Query OK, 0  rows affected (0.00 sec)
mysql> FLUSH PRIVILEGES; Query OK, 0 rows affected (0.01 sec)
mysql> EXIT Bye


A very good hands on guideline is written here: https://codex.wordpress.org/Installing_WordPress






====== Disks ======

du  -d1 -h df -H mount -t ext4 /dev/sda1 /local mount -t ext4 -o ro  /dev/sda1 /local mount rw,remount /dev/sda1 umount /dev/sda1 blkid ; all  the uid label lsblk ; all the partitions fdisk -l
/etc/fstab:  static file system information. Use ‘blkid’ to print the universally  unique identifier for a device; this may be used with UUID= as a more  robust way to name devices that works even if disks are added and  removed. See fstab(5).
<file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=0278bf38-1115-4f62-ab63-39d6bedd6b18 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=0beeb2e6-29e4-41ad-956a-e611e8aeb7b8 none            swap    sw              0       0
#/local
UUID=ed9084b9-79d2-4512-93a3-821d3d1a3279 /local          ext4    errors=remount-ro 0       1
#/matlab
UUID=2f56f83c-5366-4272-82df-000b8ecbdfde /matlab         ext4    errors=remount-ro 0       1

e2label /dev/sda1 “xxx”
gparted
fdisk -l /dev/sda # lists the format type
ntfs-3g /dev/sda1 /mnt/mountlocation
mkfs.ext4 -f -L “label” /dev/sda9
A very useful place is /dev/disk and the entries there are sorted according to what one needs.
All the supported fs by your linux kernel is available here: /lib/modules/2.6.18-5-686/kernel/fs/
cat /proc/mounts gives a list of filesystem in your present container mount gives a list of mounted filesystems
mount -o loop,exec isofile /tmp/cdrom mount -t vboxsf sha Sudo mount -t vboxsf -o uid=UID,gid=(id -g) share ~/host/os umount -l /media/.. ( lazy )
Df  is for disk space. The command is df -h ( h means human readable )  Vmstat if for memory. The command is vmstat -Sm ( m means mega byte )
Others are du and ls. Du is for diskusage. Du ./ -h | grep ’50K’
mount -t iso9660 /dev/hdc /media/cdrom Umount /dev/hdc
Cat /etc/mtab
Download the iso image using wget and the url Then mount the iso image using the command mount -t iso9660 /
Making an iso image
mkisofs
-A “ELDK-4.2 — Target: PowerPC — Host: x86 Linux” \ -publisher “(C) date “+%Y” DENX Software Engineering, http://www.denx.de ” \ -p “id -nu@hostname — date” \ -V ppc-linux-x86 \ -l -J -R -o eldk-ppc-linux-x86.iso ppc-linux-x86/distribution
Mount -o loop “isoimage” destination directory.
/etc/rc.local Put the mount command in mount -t vboxsf share /home/agrawal/host
automount /etc/rc.local Writing the ISO image file to a CDRom
To use wodim or cdrecord run the following command in a console:
mount a iso file in a real cd
sudo fdisk -l | less mkfs hdparam mount
cdrecord systemrescuecd-x86-x.y.z.iso
mount a iso file virtual cd: mount -o loop,exec /path/to/systemrescuecd-x86-x.y.z.iso /tmp/cdrom
mount  a usb: mount /dev/sdb2 /media/usbdisk ( implicit auto or otherwise -t  filesystemname ) the file system is read from /proc/filesystems
To see the whole partition in gui – gnome-disk-utility in console, parted or gparted or fdisk
make the disk bootable: Startup Disk Creator, Unetbootin or command line:
syslinux  /dev/sdb1: syslinux is a boot loader for the Linux operating system  which operates off an MS-DOS/Windows FAT filesystem.
On  linux you can use either command line tools such as cdrecord/wodim or  graphical tools such as k3b, brasero or xfburn. source .bashrc
sudo  apt-get install ntfsprogs To know witch filesystem you have on a device  the command is: Code: file -s /dev/sdb1 mkntfs /dev/xxx mkfs -t ntfs  /dev/xxx mkfs.ntfs /dev/xxx
After that you need to enter the drive into the fstab by typing fsck -f -y /dev/xxx again replacing the letters.
sudo  lshw -C disk hwparm /dev/xxx dconf-editor blockdev –setrw hwparm -r 0  /dev/sdb1 ls -li # find the inode find . -inum -delete # delete the  inode
COPY IMAGE TO SD
Sudo dd if=”firmwareimage” of=/dev/sdb



====== User  Accounts ======



chmod -R g=u *


passwd vipw -g adduser username sudo groups vagrawal : to see  what groups the user belongs to chmod r+x directory or filename. chgrp  groupname directory or filename. Sudo useradd -G shadow tomcat7
chsh  change shell usermod -s /bin/bash agrawal .profile will be read as soon  as your profile is loaded. add exec /bin/bash –login sudo  dpkg-reconfigure keyboard-configuration corrected my problem with the  keyboard. install dconf-editor for date time settings etc in the  console. sudo apt-get install console-common and then run the command  sudo kbd-config. This will fix your keymap. If a user is deleted with  userdel -r username and still files are present, then the files user  change into his UID because this user is notavailable anymore. The UID  is a continous process and would be never allocated any previous UID  with adduser. This is prevent getting access to files that has been left  by the previous user. ps -aux has VSZ RSS ( sizes ) and then state ( S  is in interrupted sleep which means it is waiting for an event ) cut -d:  -f1 /etc/passwd skill -KILL -u vivek # To log off the user. find /home  -user tomcat find /home -group tomcat cut -d: -f1 /etc/passwd vipw vipw  -g /etc/passwd : atributes of users /etc/shadow : attributes of users  password /etc/groups : atributes of groups userdel username
EOF reading input password=hello sudo passwd username password confirmpaassword sudo passwd vagrawal << EOF passwordpassword
import screenshot.png display screenshot.png
getent  passwd Supported databases: ahosts ahostsv4 ahostsv6 aliases ethers  group gshadow hosts initgroups netgroup networks passwd protocols rpc  services shadow cat /etc/nsswitch.conf EOF
find ./ -name “own” Find ./ -size “1M>” find -name ‘.wsdl’ | xargs emacs {} find -name ‘.wsdl’  -exec emacs {} \; find ./ -name config.xml -ok sed -i  ‘s/itlx3301/itlx3301/gc’ {} \; instead of -exec above The {} is replaced  with the file name found by find. This would execute the command for  every found file. If you want to execute a command with all found files  as arguments use a + at the end like this: find -name “.wsdl” -exec emacs {} +
Disk Size df -aTh /dev/sdb1 gives the size, filesystem etc of the usb disk.
lsusb screen xclip -sel clip < filename
watch  -n 0.1 “dmesg | tail -n $((LINES-6))” grep -A5 -B5 supported lsof –  lists open files fuser find uers processes fuser -v /media/
lsof : list all open files fuser find user process fuser -v /media/..
groups agrawal usermod -a -G groupname username
du  -d1 -h | cut -f1 -d’.’ will give you the sizes. –output-delimiter=$’\n’  # this will print the outputs in new lines, otherwise in a single line.  sed ‘s/\s+/ /g’

====== Fonts ======


Unicode is a character  set or character data and utf-8 and utf-16 are the encodings for this  character set. Each character is mapped to a bytesequence which can be  translated from the application.
Each code page is represented by a  code page identifier. For example 1252 is a code page identifier and is  handled by the Unicode and character set API function. A windows  operating aystem always has one currently active windows code page.
The list of fonts can be found here: fc-list

download fonts from internet in the form of .ttf and store in .local/share/fonts/
Now run fc-list to see if the font is available


====== TODO3 ======


readlink -f $(which java)
whereis java
mvn install:install-file -Dfile=lib/VciJava.jar -DgroupId=VciJava -DartifactId=VciJava -Dversion=1.0 -Dpackaging=jar

docker pull kenntwasde/raspi_baseimage-docker:jessie
docker images -q
#!/bin/bash# Delete all containers
docker rm $(docker ps -a -q)# Delete all images
docker rmi $(docker images -q)

docker run -it --rm -p 80:80 nginx
and then localhost from the browser.


ffmpeg -ss 60 -i input.wmv -vframes 1800 -acodec copy -vcodec copy output.wmv

ffmpeg -i input.flv -ss 00:00:14.0 -vframes 50 out_%d.png


nautilus-open-terminal and then nautilus -q
Add a template in ~/Template/ and it will appear in the right click.


glxgears
xclock



====== Encryption and Certificates ======

There are 4 kinds of certificates:
Security certificates
Personal certificates
Certificate trusted websites
Device certificates
The  server sends a certificate when the website is called, and then it is  compared with the certificate on the device. Wenn the certifcate is not  trusted or the certificate on the device is invalid, then you get an  information. The certificate can be downloaded from the website and  stored into your device. This avoids to be connected to malicious  websites. The certificate is tested for its signature and their  validity. The signature is in form of a fingerprint. The saved  certificates in your device must be trusted before it can be used to  verify the signature of the downloaded certifcates.
Encryption
GPG  key has two keys: one is a private key and the other is a public key.  The private key and the public key can be generated by invoking the  command gpg2 --gen-key. Various options are RSA or DSA and 2048 bit or  1024 bit encryption. Data, strings, emails or anything which is are bits  and bytes can be encrypted using the GPG public key. Only someone  possessing the private key can decrypt the message. One always encrypts  using the public key and decrypts using the private key.
secring  is obselete and the private key is stored under the folder private-key  under the .gnupg folder. The gpg-agent is responsible for the management  of the private key and is automatically invoked when there is need to  access the private key. Ofcourse, the gpg-agent needs your passphrase to  access the contents of the private-key. There is no support for PGP-2  keys because of their flaws and hence any public PGP2 key would be  rendered useless. The difference between GPG2 and PGP keys can be seen  by their fingerprints. GPG2 has a 20 double hexadecimal fingerprint  while PGP2 has 16 double hexadecimal fingerprint.
To start  encrypting data with the public key of other people, you need to import  their public key. Assuming the public key of the user is available, it  is imported using the --import option. The key is then imported in the  pubring.gpg file. The key is but not yet trusted. This is an additional  step and if you sign the public key of the other user with your  fingerprint then, the key goes into the the trustdb.gpg.
GPG is  used not only to send the data from one person to another person. It can  also be used to send your data to the whole world. Ofcourse you have to  distribute your public key to the whole world. The data is signed with  your private key. The fingerprint itself is sent with the data and it  can be verfied at the other end using --verify option. The data can be  signed either in clear text using --clearsign option or in binary  compressed form using --sign option or with separate data and signature  file using --detach-sig. If the file has been tampered at the other end,  then a Bad Signature message appears otherwise the gpg --verfify exits  with Good Signature. It is also possible to encrypt and sign at the same  time.
All the private key handling is done by the gpg-agent  utility. The configuration is stored in the .gpg-agent.conf file.  Restarting of the daemon is necessary after completing the configuration  process. There are various ways how the passphrase is asked. It could  be done either via gtk or on the shell. This configuration is done using  pinentry-program also stored in the .gpg-agent.conf. If  gnome-keyring-daemon is active, then the gpg-agent has got no effect.  Its like if nm-applet is active, the network-manager has got no effect.  Using dconf-editor, the cache timing for the gpg password can be  configured. The gnome keyring daemon needs to be restarted.



gpg --gen-key
gpg --list-keys
gpg --delete-secret-key <ID>

gpg -c filename ; encrypt
gpg filename ; decrypt
gpg --export --armor "User Name" > public.key
gpg --export-secret-key --armor "Weikas" > private.key

gpg --import testuser.publickey
ggp --edit-key "Testuser"
fpr -> sign -> list etc.

gpg-zip --encrypt --output test1 --gpg-args  -r Bob mydocs
gpg --output secrets_to_testuser --encrypt secrets
gpg --output secrets_to_testuser --encrypt --armor secrets
gpg --output secret_to_testuser --sign --encrypt secrets
gpg --output program_to_wholeworld_and_signature.sig --sign program
gpg --output program_to_wholeworld_and_signature.sig --clearsign program
gpg --output just_signature.sig --detach-sig program

gpg --output secrets_from_weikas --decrypt secrets_to_testuser
gpg --output program --verify program_to_wholeworld_and_signature.sig
gpg --output program --verify just_signature program

default-cache-ttl 3600 # value in .gpg-agent.conf
gpg-connect-agent reloadagent /bye
dconf-editor
gnome-keyring-daemon -r -d
Pass
This utility under the name  "pass" in the Ubuntu packet manager is used to store passwords encrypted  using the GPG key. The public GPG key is provided during the init  phase. After that all the corresponding data can be encrypted with the  supplied key at the init phase. If the pass data folder is initialised  as a repository, then by simply changing the data folder leads to a git  commit automatically. The pass folder can be initialised via the  command:
pass git init
pass init "Username"
pass insert EMAIL/email@email.com
pass edit EMAIL/email@email.com
pass -c EMAIL/email@email.com

zip file.zip file
zip -r directory.zip directory
zip --encrypt file.zip.enc file # prompt for password
zip --encrypt -r directory.zip.enc directory # prompt for password

unzip directory.zip.enc
#Beware if any directory is present with the same name as the zipped file, then it would be overwritten. Hence I normally send the contents to another directory.

unzip directory.zip.enc -d directory-new # prompts for password



====== LUKS ======

Linux Unified Key Setup

Adding a key

cryptsetup luksAddKey <device> ~/keyfile

Addung a passphrase

cryptsetup luksAddKey <device>

Removing a key

cryptsetup luksRemoveKey <device>

Preparing a LUKS formatted myEncryptedStick

sudo cryptsetup luksFormat /dev/sdf1

Mount the virtual file system

sudo cryptsetup luksOpen /dev/sdf1 myEncryptedStick

This will put an entry into /dev/mapper

sudo mkfs.vfat /dev/mapper/Stick -n myEncryptedStick

Mount the filesystem

sudo mount /dev/mapper/myEncryptedStick /media/username

Umount the virtual file system

sudo cryptsetup luksClose myEncryptedStick

Unmount the file system

sudo umount /media/username



====== Sound ======


ppa:osmoma/audio-recorder
pulseaudio
alsamixer
pacmd list-sinks

pactl list sources
pacmd "set-source-port 1 analog-input-microphone-front" ; The source port can be found out by the above command
if all was successful we can now put that at the end of your /etc/pulse/default.pa file as such: pacmd "set-source-port 1 analog-input-microphone-front"

====== OpenVpn ======

/etc/default/openvpn
AUTOSTART="none"


<code>
# HE Version 3.0
# /etc/openvpn/client.conf
client
dev tun
remote openvpn.domain.de
#remote openvpn-backup.domain.de
; Für HfS-Wohnheimbewohner
; remote 10.42.0.9
port 1194
pull
auth-user-pass
tun-mtu 1500
mssfix 1400
# Hier den Namen des Certificats eingeben
# cryptoapicert "SUBJ:Openvpn"
# Optional, wenn nicht MS-Zertifikatsspeicher verwendet wird
script-security 3
ca /etc/openvpn/ca.crt
cert /etc/openvpn/cert.txt
key /etc/openvpn/key.txt
comp-lzo
keepalive 10 60
nobind
float
cipher BF-CBC
route-method exe
route-delay 2
up /etc/openvpn/update-resolv-conf
#down /etc/openvpn/update-resolv-conf
daemon

</code>




freeing SMP memory



====== GUI ======

    svn checkout http://thotkeeper.googlecode.com/svn/trunk/ thotkeeper-read-only
    sudo apt-get install python-wxgtk2.6

