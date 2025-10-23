# AWS STEP FUNCTIONS
CRIAÇÃO STEP_FUNCTIONS

# Descrição do Desafio

Este laboratório tem como objetivo consolidar seus workflows automatizados com AWS Step Functions. O entregável é um repositório organizado contendo anotações e insights adquiridos durante a prática, servindo como material de apoio para os seus estudos e futuras implementações.

# Objetivos de Aprendizagem 

Ao concluir este desafio, você será capaz de: 
- Aplicar os conceitos aprendidos em um ambiente prático; 
-  Documentar processos técnicos de forma clara e estruturada;
- Utilizar o GitHub como ferramenta para compartilhamento de documentação técnica.

# DESAFIOS ENCONTRADOS

Durante a criação e execução do AWS Step Functions, alguns erros comuns foram abordados e solucionados, com foco na configuração de permissões e no entendimento de como os dados são processados entre os estados. Aqui estão os pontos principais discutidos:

1. Erro de Permissões (lambda:InvokeFunction)
Problema: A Step Function não tinha permissão para invocar a função Lambda. O erro retornado foi 403 - "User is not authorized to perform: lambda:InvokeFunction".

Solução: Foi necessário adicionar uma política de permissão à role associada à Step Function, permitindo a ação lambda:InvokeFunction sobre a função Lambda específica.

2. Erro Invalid path '$.status' no Estado Choice
Problema: O erro "Invalid path '$.status': The choice state's condition path references an invalid value" ocorreu porque o caminho $.status não estava correto ou o valor não estava sendo passado entre os estados.
Solução: Foi necessário verificar o retorno da função Lambda, garantir que ela estava retornando o valor de status no formato correto (ex: { "status": "Aprovado" }) e revisar o caminho de acesso no estado Choice.
Ação: Foi validado que o retorno da função Lambda deveria ser um objeto contendo a chave status para que a Step Function pudesse processá-lo corretamente.

3. Erro de Sintaxe com exports em Módulo ES6
Problema: A função Lambda estava sendo desenvolvida com a sintaxe CommonJS (exports.handler), mas o arquivo estava sendo tratado como um módulo ES6 (.mjs), o que causou o erro "exports is not defined in ES module scope".
Solução: A sintaxe foi alterada para export const handler, que é a maneira correta de exportar funções em módulos ES6.

4. Permissões de Role para Invocar Funções Lambda
Problema: A Step Function não conseguiu invocar a função Lambda devido à falta de permissões de lambda:InvokeFunction.
Solução: A política de permissão foi configurada corretamente para permitir que a role da Step Function invocasse a função Lambda específica, corrigindo o erro de autorização. 

O fluxo da Step Function mostrado na imagem envolve um workflow de aprovação de documentos, com o objetivo de automatizar o processo de decisão baseado em um valor de status.

<img width="1788" height="830" alt="image" src="https://github.com/user-attachments/assets/e4a7f237-b2be-418d-99d7-e8288d6bd73c" />


