# 1-Ambiente Virtual Linux/Windows

# Usando Requestlog

### Autor: Marco Sena :computer:

[githug](https://github.com/MarcoSena2210/web_empresa)

### Créditos: Professora Letícia Lima (Udemy)

# Criar o ambiente virtual Linux/Windows

## Windows

python -m venv .venv
source .venv/Scripts/activate # Ativar ambiente

## Linux  

## Caso não tenha virtualenv. "pip install virtualenv"

virtualenv .venv
source .venv/bin/activate # Ativar ambiente

## Instalar os seguintes pacotes Iniciais

pip install django
pip install pillow # tratamento de imagem

## Para criar o arquivo requirements.txt

### Cria o arquivo contendo todas asdependências do nosso projeto

pip freeze > requirements.txt

## Para criar as dependencias lendo o arquivo requirements.txt

### Usariamos

### pip install -r requirements.txt

### seria instalado as dependecias baseada nesse arquivo  

### Criando o projeto chamado Core

“core” é nome do seu projeto e quando colocamos um “.” depois do nome do projeto significa que é para criar os arquivos na raiz da pasta. Assim não cria subpasta do projeto

```
django-admin startproject core .
```

### Testar a aplicação

```
python manage.py runserver
```

### Criando a 1ª Branch do projeto

```
git checkout -b parte01_config_static
```

### Comitando

```
git add .
git commit -m "Configuração dos arquivos staticos" 
```

### Subindo o projeto para git

```
git push origin parte01_config_static
```

### Criando uma pasta collectstatic

 ```
python manage.py collectstatic  
 ```
