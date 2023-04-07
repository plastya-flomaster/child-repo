`git remote add -f child-repo git@github.com:plastya-flomaster/child-repo.git`
#### создаем тестовую ветку для папки specs
`git checkout -b upstream/temp child-repo/master` 
#### вытаскиваем нужные изменения и склеиваем в один коммит
`git subtree split -q --squash --prefix=specs --rejoin -b merging/temp`

`git checkout master`

`git subtree add --prefix=swagger --squash merging/temp`


Обновление:

#### switch back to tracking branch, fetch & rebase.
git checkout upstream/temp
git pull child-repo/master

#### update the separate branch with changes from upstream
git subtree split -q --prefix=specs --rejoin -b merging/temp

#### switch back to master and use subtree merge to update the subdirectory
git checkout master
git subtree merge -q --prefix=swagger --squash merging/temp
