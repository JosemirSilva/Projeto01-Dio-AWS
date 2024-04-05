<!--
title: 'AWS Simple HTTP Endpoint example in NodeJS'
description: 'This template demonstrates how to make a simple REST API with Node.js running on AWS Lambda and API Gateway using the traditional Serverless Framework.'
layout: Doc
framework: v2
platform: AWS
language: nodeJS
authorLink: 'https://github.com/serverless'
authorName: 'Serverless, inc.'
authorAvatar: 'https://avatars1.githubusercontent.com/u/13742415?s=200&v=4'
-->

# API Node.js com Serverless Framework em ambiente AWS 

Fiz o fork do Cassiano, e alteração do código foi realziada afim de apresentar o resultado de meu trabalho, no entanto, vou melhorá-lo, pois este tem como como objetivo a entrega de uma infraestrutra em nuvem AWS com API Gateway, DynamoDB, AWS Lambda e AWS CloudFormation utilizando o framework Serverless para o desenvolvimento baseada em Infraestrutura as a Code.

service: meu-servico

provider:
  name: aws
  runtime: nodejs12.x
  stage: dev
  region: us-east-1

functions:
  minhaFuncao:
    handler: handler.minhaFuncao
    events:
      - http:
          path: minha-rota
          method: get
          cors: true

resources:
  Resources:
    MinhaTabelaDynamoDB:
      Type: 'AWS::DynamoDB::Table'
      Properties:
        TableName: MinhaTabela
        AttributeDefinitions:
          - AttributeName: id
            AttributeType: S
        KeySchema:
          - AttributeName: id
            KeyType: HASH
        ProvisionedThroughput:
          ReadCapacityUnits: 1
          WriteCapacityUnits: 1

