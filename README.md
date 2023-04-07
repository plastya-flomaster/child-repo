`git remote add -f child-repo git@github.com:plastya-flomaster/child-repo.git`

`git checkout -b upstream/temp child-repo/master` 
// вытаскиваем нужные изменения и склеиваем в один коммит
`git subtree split -q --squash --prefix=specs --rejoin -b merging/temp`

`git checkout master`

`git subtree add --prefix=specs --squash merging/temp`

