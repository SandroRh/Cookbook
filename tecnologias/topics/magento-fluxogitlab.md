# Fluxo do gitlab
1. Efetuar merge request com a branch `master`
2. Efetuar merge request com a branch `staging`

## Efetuar merge request com a branch master
Esse passo é realizado pela interface do gitlab.
- `ATENÇÃO:` NÃO APROVE O MERGE REQUEST.

## Efetuar merge request com a branch staging
```git
git fetch
git checkout staging
git reset --hard origin/staging
git merge origin feature/branch
git push origin staging
```