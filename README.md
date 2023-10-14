# GIT : merge vs rebase

Git merge et git rebase sont tous les deux des commandes pour intégrer les modifications de deux branches différentes. Cependant, ils fonctionnent différemment.

## merge

Le git merge fusionne les modifications de deux branches en créant un nouvel "état fusionné" de ces branches. Cela se fait en créant un nouveau commit qui a des parents des deux branches. Cela crée une vue de l'historique contenant le développement de ces deux branches.

## rebase

Le git rebase fusionne les modifications de deux branches en réécrivant l'historique de la branche de déstination, comme si les commits de la branche source viens d'etre créés aprés les commits de la branche source. Le résultat final est une ligne de temps linéaire, plutôt qu'une fusion avec deux parents.

## Par points

### merge (`options par defaut`)

|         | merge (`par defaut`)                                                                                                         | rebase                                                                                      |
| ------- | ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| Code    | <pre># merge B to A<br/>git checkout A<br/>git merge B</pre>                                                                 | <pre># rebase B to A<br/>git checkout A<br/>git rebase B</pre>                              |
| Graph   | Jointure de deux lignes/branches                                                                                             | Une seule ligne tel que la branche **A** inclue **B**                                       |
| History | Un nouveau commit sera rajouter a la fin de la branche **A** tel que ses parents sont les derniers commits de chaque branche | Les commits de la branche **B** seront rajouter au debut du fork de la branche **A**        |
|         | Les ID's des anciens commits **Ne changent pas**                                                                             | Les ID's des commits de la branche **A** qui vienent apres les commits de **B**, changent ! |

### merge `--squash`

|         | merge `--squash`                                                                                           | rebase                                                                                      |
| ------- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| Code    | <pre># merge B to A<br/>git checkout A<br/>git merge --squash B<br/>git commit -m "squashed merge B"</pre> | <pre># rebase B to A<br/>git checkout A<br/>git rebase B</pre>                              |
| Graph   | Deux lignes/branches séparés, **A** et **B**                                                               | Une seule ligne tel que la branche **A** inclue **B**                                       |
| History | Un nouveau commit sera rajouter a la fin de la branche **A**                                               | Les commits de la branche **B** seront rajouter au debut de fork de la branche **A**        |
|         | Les ID's des anciens commits **Ne changent pas**                                                           | Les ID's des commits de la branche **A** qui vienent apres les commits de **B**, changent ! |
