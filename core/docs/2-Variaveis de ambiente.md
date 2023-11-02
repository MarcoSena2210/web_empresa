# Configurando variáveis de ambiente usando python-dotenv.
Dev: Marco Sena
Creditos: Professora Letícia Lima 
Email: leticialimacgi@gmail.com

Link: https://pypi.org/project/python-dotenv/

“Python-dotenv lê pares chave-valor de um  .env arquivo e pode defini-los como
variáveis de ambiente. Ajuda no desenvolvimento de aplicações seguindo os princípios
dos 12 fatores”
Da uma olhada nos 12 fatores é interessante.

## Precisa instalar essa biblioteca na aplicação.
´´´
pip install python-dotenv
´´´

## Criar um arquivo chamado “.env”.
Nesse arquivo vamos colocar as variáveis importantes como senha do banco de
dados, secret_key do django, api_key, chave cloud tudo que tem credenciais que
você não pode versionar etc…

Exemplo:
## Não precisa colocar "" aspas
## Não precisa colocar "" aspas
SECRET_KEY=django-insecure-q(ge$586x7o9n)3w+6d_^t(m!ib&9%_m8&6@=m=sy@^7qf)#*_
DEBUG=True
SUPER_USER=ADMIN
EMAIL=leticiateste@gmail.com
NAME_DB=db.sqlite3
USER_DB=root
PASSWORD_DB=
HOST_DB=localhost
PORT_DB=3306
EMAIL_HOST=smtp.office365.com
EMAIL_HOST_USER=email@hotmail.com
EMAIL_HOST_PASSWORD=sua_senha
EMAIL_PORT=587
EMAIL_USE_TLS=True
DEFAULT_FROM_EMAIL=email@hotmail.com
SERVER_EMAIL=DEFAULT_FROM_EMAIL

Sempre envio um arquivo exemplo (sem as informações reais) como esse exemplo
“_env” no commit. Assim quando eu abaixo o repositório eu preencho somente as
informações e renomeio o arquivo para “.env”. Lembrando o arquivo “.env” não vai nos
commits. Essa informação deve estar no .gitignore. Caso for um servidor real ai você
cria esse arquivo no servidor.

## Estrutura de pasta usada nesse projeto
projeto/
├── apps/
│ ├── base/
│ │ ├── migrations/
│ │ ├── static/
│ │ │ ├── css/
│ │ │ ├── js/
│ │ │ ├── fonts/
│ │ │ └── images/
│ │ ├── templates/
│ │ └── __init__.py
│ ├── myapp/
│ │ ├── migrations/
│ │ ├── templates/
│ │ └── __init__.py
│ └── __init__.py
├── core/
| ├── Docs/
│ ├── settings.py
│ ├── urls.py
│ ├── asgi.py
│ └── wsgi.py
├── manage.py
└── requirements.txt

## Configuração no core/settings.py

Nota que para chamar uma variavel no arquivo .env basta chamar a biblioteca
os.getenv('NAME_DB') e NAME_DB é nome da variavel que está no arquivo.

# importar a biblioteca
import os
import sys
from dotenv import load_dotenv

# Adicionar essa tag para que nosso projeto encontre o .env
load_dotenv(os.path.join(BASE_DIR, ".env"))

# Diz para Django onde estão nossos aplicativos
APPS_DIR = str(os.path.join(BASE_DIR,'apps'))
sys.path.insert(0, APPS_DIR)

# Chamar as variaveis assim
SECRET_KEY = os.getenv("SECRET_KEY")

# DEBUG
DEBUG = os.getenv('DEBUG')

# Aplicativos do django
DJANGO_APPS = [
'django.contrib.admin',
'django.contrib.auth',
'django.contrib.contenttypes',
'django.contrib.sessions',
'django.contrib.messages',
'django.contrib.staticfiles',
]
THIRD_APPS = [
...
]
PROJECT_APPS = [
'apps.base',
'apps.myapp',
]
INSTALLED_APPS = DJANGO_APPS + THIRD_APPS + PROJECT_APPS
# Banco de Dados.
DATABASES = {
'default': {
'ENGINE': 'django.db.backends.sqlite3',
'NAME': os.path.join(BASE_DIR, os.getenv('NAME_DB')),
#'USER':os.getenv('USER_DB')
#'PASSWORD': os.getenv('PASSWORD_DB')
#'HOST':os.getenv('HOST_DB')
#'PORT':os.getenv('PORT_DB')
}
}

# Se tiver configuração de email
EMAIL_HOST = os.getenv('EMAIL_HOST')
EMAIL_HOST_USER = os.getenv('EMAIL_HOST_USER')
EMAIL_HOST_PASSWORD = os.getenv('EMAIL_HOST_PASSWORD')
EMAIL_PORT = os.getenv('EMAIL_PORT')
EMAIL_USE_TLS = os.getenv('EMAIL_USE_TLS')
DEFAULT_FROM_EMAIL = os.getenv('DEFAULT_FROM_EMAIL')
SERVER_EMAIL = DEFAULT_FROM_EMAIL