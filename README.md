`git remote add -f child-repo git@github.com:plastya-flomaster/child-repo.git`
`git remote add -f specs-repo https://git.moscow.alfaintra.net/scm/moos/common-api-front-agent-specs.git`
#### создаем тестовую ветку для папки specs
`git checkout -b upstream/temp child-repo/master` 
#### вытаскиваем нужные изменения и склеиваем в один коммит
`git subtree split -q --squash --prefix=specs --rejoin -b merging/temp`

`git checkout master`

`git subtree add --prefix=swagger --squash merging/temp`

Обновление:

#### обратно
git checkout upstream/temp
git pull child-repo master

#### подтягиваем изменения
git subtree split -q --prefix=specs --rejoin -b merging/temp

#### переход на master и мерж
git checkout master
git subtree merge -q --prefix=swagger --squash merging/temp

----

## подключиться
git remote add -f child-repo git@github.com:plastya-flomaster/child-repo.git

git subtree add --prefix swagger child-repo master --squash

## апдейт
git subtree pull --prefix swagger child-repo master --squash

##  мерж
git subtree push --prefix swagger child-repo master

## внести изменения
git subtree push --prefix swagger child-repo master

