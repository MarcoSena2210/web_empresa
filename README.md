# web_empresa
Curso de djando udemy

### Criando umanova branch stable

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
### Navegando para branch main 
git checkout main
