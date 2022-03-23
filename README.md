# Desafio QA BACKEND

# Sobre o desafio 

O desafio é composto por duas etapas:

A primeira etapa tem como objetivo avaliar a forma como é realizado o planejamento de casos de testes. O fluxo a ser considerado nesta etapa é o fluxo de Abertura de Conta de um app da empresa Start.

A segunda etapa tem como finalidade avaliar a automatização dos testes nos fluxos de Extrato, Saldo e Transferência Interna através da nossa API Pública.


## 1. Planejamento de Casos de Testes
A Start é uma fintech que quer oferecer um novo produto para os seus clientes: uma conta corrente. A conta corrente é direcionada para empresas e com ela a cliente consegue fazer transferências internas e externas, pagamentos de boleto, compras com o cartão de débito e emitir boletos de cobrança. As telas na imagem anexa mostram o fluxo de abertura de conta no app que a Start espera lançar para os seus clientes.

[IMAGEM](https://github.com/laspbr/DESAFIO_QA_BACKEND/blob/main/88742049-8429b400-d117-11ea-80a0-b86f26ed20ab.png)

Seu desafio nessa etapa é criar um planejamento dos casos de testes que você julgar necessário para ter o fluxo de abertura de conta bem testado. 

### Critérios de Avaliação

   - Qualidade dos cenários de testes;
   - Cobertura do fluxo;
   - Detalhamento e Organização.
   
### Informações sobre a etapa

   - Utilizar o formato Gherkin para a descrever os casos;
   - Os casos de testes devem ser commitados em formato .pdf;
   - As informações sobre o documento e sua localização devem estar no README na pasta raiz do repositório.


## 2. Automação dos testes de API

Sua missão é desenvolver alguns testes automatizados para a nossa API pública:

### Instruções iniciais

Para você desenvolver o desafio, utilize a seguinte conta que foi criada no nosso ambiente de Sandbox com dados fictícios.

- username - desafioqastone@gmail.com
- password - desafioqa

Você consegue acessar sua conta por esse link: https://sandbox.conta.stone.com.br/login.

Pronto! Você já está pronto para começar seu desafio.

Para se logar pela linha de comando, basta usar o seguinte comando:

```
curl https://login.sandbox.stone.com.br/auth/realms/stone_account/protocol/openid-connect/token \
	  -d 'client_id=admin-cli' \
	  -d 'username=YYYYYYYYY' \
	  -d 'password=ZZZZZZZZZ' \
          -d 'grant_type=password'
```

Isso te devolverá um `access_token`. Use-o para se autenticar nas chamadas para a API.

Você pode fazer transferências internas para essa conta:  
- Stone: 197  
- Agência: 0001  
- Conta: 475384


### Cenário

A Stone possui uma API de [OpenBanking](https://en.wikipedia.org/wiki/Open_banking) que estamos testando e evoluindo continuamente. O link para a documentação de referência é https://docs.openbank.stone.com.br/. 

Queremos que você use esta API para nos mostrar como iria automatizar as várias formas de se inferir qualidade das entregas.

Por exemplo: temos um endpoint para simular uma transação interna em `api/v1/dry_run/internal_transfers`. Queremos que você proponha uma solução de automação neste ambiente de "sandbox" da API. 

Espera-se que você faça a automação de 3 endpoints:

- Saldo: `GET api/v1/accounts/:id/balance`
- Extrato: `GET api/v1/accounts/:id/statement`
- Simulação de transferência interna: `POST api/v1/dry_run/internal_transfers`

Os dados para acesso serão detalhados mais abaixo.

### Como operar na API de sandbox da Stone OpenBanking?

Todos os endpoints possuem autenticação. Utilizamos OAuth2 e OpenID Connect como especificações de autenticação e autorização. Para o desafio de QA, criamos uma "client application" e um usuário para os testes:

- client_id: XXXXXXXXXX
- username: YYYYYYYY
- password: ZZZZZZZZ

Para conseguir o token de acesso, basta fazer um POST para o nosso IAM:

```
curl https://login.sandbox.stone.com.br/auth/realms/stone_account/protocol/openid-connect/token \
	  -d 'client_id=XXXXXXXXXX' \
	  -d 'username=YYYYYYYYY' \
	  -d 'password=ZZZZZZZZZ' \
          -d 'grant_type=password'
```
### Informações sobre a etapa

   - Utilizar o formato Gherkin para a descrever os casos;
   - Os casos de testes devem ser construídos através do Robot Framework;
   - O desafio deve conter, no mínimo, um projeto de código que instrumente o uso da API seguindo um conjunto de cenários que você mesmo irá criar para os 3 endpoints citados acima;
   - A execução deve retornar um status;
   - Ao término da execução deve ser gerado um relatório sobre as APIs testadas (cenários com sucesso/falha, timing, security e etc);
   - As instruções para executar o projeto devem estar no README na pasta raiz do repositório.

### Critérios de Avaliação

 Levaremos em conta os seguintes fatores:

  - Detalhamento e Organização;
  - Uso correto do Gherkin e Robot Framework;
  - Conhecimento de APIs;
  - Ferramentas de automação de análise de qualidade;
  - Escrita de cenários sobre os endpoints;
  - Geração de relatórios/métricas de qualidade;


# Envio do Desafio

 Você deve disponibilizar seu código no Github e manter o repositório como privado. Quando finalizar, favor entrar em contato com a sua recrutadora, para disponibilizarmos os usuários que deverão possuir acesso para realizar a avaliação.


O repositório deve ser facilmente executável! E lembre-se, a organização e o nível de detalhamento da entrega serão cruciais nesta avaliação!

Bom desafio! 
