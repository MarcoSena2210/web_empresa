# web_empresa
Curso de djando udemy
Dev: Marco Sena
Creditos: :Professora  Letícia Lima 
Email: leticialimacgi@gmail.com

### Criando uma nova branch stable

```
git checkout -b stable
```

Output
```
Switched to a new branch stable
```
### Enviando para branc stable do nosso repositório remoto
$
```
git push origin stable
```

Output
```
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
remote: 
remote: Create a pull request for 'stable' on GitHub by visiting:
remote:      https://github.com/MarcoSena2210/web_empresa/pull/new/stable
remote:
To https://github.com/MarcoSena2210/web_empresa.git
 * [new branch]      stable -> stable
```

### Fazendo o commit localmente
```
git add .
git commit -m "Primeiro commit" 
```
Output
```
[stable b0b1044] Primeiro commit
 2 files changed, 25 insertions(+)
 create mode 100644 primeiro_commit.txt
```

### Para saber qual branch estamos 

```
git status
```

### Para atualizar a branch main

```
 git merge stable 
 
```
Output

```
Updating bedd26d..943b3c1
Fast-forward
 README.md           | 41 +++++++++++++++++++++++++++++++++++++++++
 primeiro_commit.txt |  1 +
 2 files changed, 42 insertions(+)
 create mode 100644 primeiro_commit.txt
```
### Para enviar para repositorio remoto as atualizações da main
 ```
 git push
```
Output

Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/MarcoSena2210/web_empresa.git
   bedd26d..943b3c1  main -> main

```
### Ir para o repositorio main e verificar se atualizou
### Voltando para branck stable
```
git checkout stable
```
Output
Switched to branch 'stable' 