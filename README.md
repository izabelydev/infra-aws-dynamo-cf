# Tabela Candidatos

Esta tabela será utilizada para armazenar dados de candidatos a vagas de emprego. Os dados serão inseridos por uma função Lambda, que processará eventos enviados por uma aplicação Java.

## Pré-requisitos

- LocalStack rodando na sua máquina (`localhost:4566`)
- AWS CLI instalado e configurado com um perfil para LocalStack

## Criar tabela
```bash
aws cloudformation create-stack --stack-name candidatos-stack --template-body file://infra/DynamoDB_Candidatos.yml
```
## Verificar tabela criada
```bash
aws dynamodb describe-table --table-name candidatos --query "Table.{AttributeDefinitions: AttributeDefinitions, KeySchema: KeySchema}" --output table

```

### Saída esperada

```bash
---------------------------------------------------
|                  DescribeTable                  |
+-------------------------------------------------+
||             AttributeDefinitions              ||
|+-----------------------------+-----------------+|
||        AttributeName        |  AttributeType  ||
|+-----------------------------+-----------------+|
||  cand_cod_cand              |  S              ||
||  cand_nome_cand             |  S              ||
||  cand_sal_pret              |  N              ||
||  cand_ctt_email             |  S              ||
||  cand_ctt_celular           |  S              ||
||  cand_sel_res_prop_cod_vaga |  S              ||
||  cand_sel_res_prop_sal_base |  N              ||
||  cand_sel_res_prop_res      |  S              ||
||  cand_sel_res_prop_lig      |  S              ||
|+-----------------------------+-----------------+|
||                   KeySchema                   ||
|+----------------------------------+------------+|
||           AttributeName          |  KeyType   ||
|+----------------------------------+------------+|
||  cand_cod_cand                   |  HASH      ||
||  cand_sel_res_prop_cod_vaga      |  RANGE     ||
|+----------------------------------+------------+|
```