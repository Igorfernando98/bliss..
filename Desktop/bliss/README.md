# BLISS Lambda Hello World

Projeto simples de Hello World usando AWS Lambda com Python.

## Estrutura do Projeto


.
├── app.py              # Código da função Lambda
├── requirements.txt    # Dependências (vazio para este exemplo simples)
└── .gitignore         # Arquivos ignorados pelo git


## Código da Função

Uma função Lambda simples que retorna "Hello, BLISS!" em formato JSON.

## Deploy

1. Criar o pacote de deploy:
bash
# Criar pasta para o pacote
mkdir package

# Copiar arquivo da aplicação
cp app.py package/

# Criar ZIP
cd package
zip -r ../deployment.zip .
cd ..


2. No console AWS Lambda:
   - Criar nova função
   - Runtime: Python 3.9
   - Arquitetura: x86_64
   - Upload do arquivo deployment.zip
   - Handler: app.handler

## Configuração do Lambda

- Memory: 128 MB
- Timeout: 30 segundos
- Function URL: Habilitada
  - Auth type: NONE (apenas para teste)
  - CORS: Enabled

## Teste

1. Via Function URL:
   - Acessar a URL fornecida pelo Lambda no navegador
   - Resposta esperada: {"message": "Hello, BLISS!"}

2. Via console Lambda:
   - Aba "Test"
   - Criar novo evento de teste:
json
{
  "httpMethod": "GET",
  "path": "/"
}


## Resposta da API

json
{
    "statusCode": 200,
    "headers": {
        "Content-Type": "application/json"
    },
    "body": "{\"message\": \"Hello, BLISS!\"}"
}