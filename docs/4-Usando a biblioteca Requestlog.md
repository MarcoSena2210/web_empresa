# Usando Requestlog

### Autor: Marco Sena :computer:
[Github](https://github.com/MarcoSena2210/web_empresa)
### Créditos: Professora Letícia Lima (Udemy)

# Django-requestlogs
O pacote django-requestlogs permite a gravação de logs de requisições HTTP em um
banco de dados. Isso pode ser útil para análise de desempenho e solução de
problemas. O pacote também fornece uma interface web para visualização dos logs.

Precisamos Instalar essa biblioteca.
Documentação: <https://pypi.org/project/django-requestlogs/>

## 1. Criando a 3ª Branch do projeto
```
git checkout -b parte03_config_cors_cookies
```

## Instalar a biblioteca Django-requestlogs
```
pip install django-requestlogs
```

### Recriar o requiriments(Atualizar)
pip freeze > requirements.txt

## Adicionar no core/settings.py
MIDDLEWARE = [
...
'requestlogs.middleware.RequestLogsMiddleware',
]

REST_FRAMEWORK={
...
'EXCEPTION_HANDLER': 'requestlogs.views.exception_handler',
}

Documentação: <<https://docs.djangoproject.com/en/4.1/topics/logging/#topic-loggingparts-loggers>>

# Logs

LOGGING = {
    'version': 1,
    'disable_existing_loggers': False,
    'handlers': {
        'requestlogs_to_file': {
            'level': 'INFO',
            'class': 'logging.FileHandler',
            'filename': 'info.log',
        },
    },
    'loggers': {
        'requestlogs': {
            'handlers': ['requestlogs_to_file'],
            'level': 'INFO',
            'propagate': False,
        },
    },
}

REQUESTLOGS = {
    'SECRETS': ['password', 'token'],
    'METHODS': ('PUT', 'PATCH', 'POST', 'DELETE'),
}

## LOGS 2
No primeiro bloco de código, LOGGING , estão sendo definidos os parâmetros do logger
de informações para as requisições, que será gravado em um arquivo chamado
info.log .

No segundo bloco, REQUESTLOGS , estão sendo definidas as opções de gravação de logs
para as requisições, como as informações que devem ser ocultadas e quais
métodos HTTP devem ser registrados. exemplo senhas, token de cliente/sistema.
Quando precisamos gerar log em alguma rota, script qualquer função em expecifico
podemos chamar essa biblioteca logger e receber as informações no arquivo de .log
que configuramos.

Por exemplo. Na view podemos fazer um tratamento assim, cria uma Exception para
tratar os erros e enviar para nosso arquivo de log.

import logging
error_logger = logging.getLogger()

def sendmail(data):
...
...
try:
data = response.data
sendmail(data)
except Exception as e:
error_logger.error(str(e) + "|" + str(data))
...

Outro detalhe, em produção o arquivo info.log quando voce criar ele no linux
precisa ter permissões.
```
sudo chmod -R 777 path/info.log
```
