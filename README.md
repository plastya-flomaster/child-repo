`git remote add -f child-repo git@github.com:plastya-flomaster/child-repo.git`

`git checkout -b upstream/temp child-repo/master` 
#### вытаскиваем нужные изменения и склеиваем в один коммит
`git subtree split -q --squash --prefix=specs --rejoin -b merging/temp`

`git checkout master`

`git subtree add --prefix=specs --squash merging/temp`


Обновление:

#### switch back to tracking branch, fetch & rebase.
git checkout upstream/jsdoc
git pull jsdoc-upstream/master

# update the separate branch with changes from upstream
git subtree split -q --prefix=templates/default --annotate="[jsdoc] " --rejoin -b merging/jsdoc

# switch back to master and use subtree merge to update the subdirectory
git checkout master
git subtree merge -q --prefix=templates/default --squash merging/jsdoc
