---
layout: post
title: "tutorials_version_manangement_svn"
date: 1970-01-01
---



SVN
svnadmin dump /svn/old_repos > ./repository.dump
svndumpfilter include path/to/docs –drop-empty-revs –renumber-revs –preserve-revprops < ./repository.dump > ./docs_only.dump
svnadmin load /svn/new_repos < ./docs_only.dump
svnadmin create –fs-type fsfs /var/svn/repos or bdb file system. Default is fsfs
svn log Day.txt
svn log --verbose Day.txt
svn diff Day.txt
svn co https://... checkoutdir --username username
scn co scn+ssh://... checkoutdir --username username
svn commit -m "Commit" Day.txt
svn update
svn resolved Day.txt
svn import -m "Importing" . https://.... 
svnserve --daemon --root /var/repos/
