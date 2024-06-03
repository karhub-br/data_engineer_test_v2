# :rocket: Desafio
O desafio consiste em desenvolver um ETL para processar arquivos que representam o orçamento do Estado de São Paulo de 2022 e armazená-los em um formato consistente para responder perguntas que ajudarão nosso time.

Os valores foram dolarizados com a cotação máxima do dolár do dia 22/06/2022.

## Tarefas

**Sobre os dados**

Disponibilizamos para você dois arquivos com os dados de Despesas e Receitas do Orçamento do Estado de São Paulo em 2022

| Dataset | Descrição      |
| :---  | :---      |
|[**gdvDespesasExcel**](./gdvDespesasExcel.csv) | Dados de despesas do Estado |
|[**gdvReceitasExcel**](./gdvReceitasExcel.csv) | Dados de receita do Estado |
|[**API cotação de moedas**](https://docs.awesomeapi.com.br/api-de-moedas#retorna-o-fechamento-de-um-periodo-especifico) | API que retorna cotação de uma moeda em um período especifico |


### Transformar e salvar os dados

**Regras de negócio**

* A tabela final deve conter as colunas ID da fonte de recurso, nome da fonte de recursos, total arrecadado e total liquidado.
    - Exemplo: a fonte de recurso `001 - TESOURO-DOT.INICIAL E CRED.SUPLEMENTAR` deverá ser salva como:

| ID Fonte Recurso | Nome Fonte Recurso| Total Liquidado | Total Arrecadado |
| :---  | :---      | :---  | :---  |
| 001 | TESOURO-DOT.INICIAL E CRED.SUPLEMENTAR | 9999.99 | 9999.99 |

* Os valores obitidos acima devem também ser exibidos na cotação do real no dia 22/06/2022 no formato decimal usando a api (https://docs.awesomeapi.com.br/api-de-moedas#retorna-o-fechamento-de-um-periodo-especifico) (lembrando que os valores das planilhas foram dolarizados)
* Adequar os tipos de dados para os mais apropriados.
* Para ajudar a identificar registros mais atualizados e para nosso controle de auditoria, precisamos que a tabela final tenha as colunas `dt_insert` que contenha data/hora de inclusão do registro
* Salvar esses dados em uma tabela, preferencialmente no BigQuery


### Utilizando consultas SQL responda as perguntas
* Quais são as 5 fontes de recursos que mais arrecadaram?
* Quais são as 5 fontes de recursos que mais gastaram?
* Quais são as 5 fontes de recursos com a melhor margem bruta?
* Quais são as 5 fontes de recursos que menir arrecadaram?
* Quais são as 5 fontes de recursos que menir gastaram?
* Quais são as 5 fontes de recursos com a pior margem bruta?
* Qual a média de arrecadação por fonte de recurso?
* Qual a média de gastos por fonte de recurso?


### Orquestração de Tarefas
O objetivo desse desafio é avaliar o conhecimento em automação do fluxo de dados, você tem a liberdade para demonstrar seus conhecimentos em orquestração, infraestrutura e conteinerização do projeto utilizando Docker.

### O que esperamos:
* Seu projeto deve estar hospedado em um repositório **git**.
* Crie uma documentação que explique como fez para chegar nos resultados obtidos, contendo as instruções para reproduzirmos suas análises, pode ser no **README** do git.
* A ferramenta de orquestração deve incluir cada etapa do ETL, sendo preferencialmente **Airflow**.
* Sinta-se à vontade para usar qualquer framework, bibliotecas e ferramentas que se sentir à vontade a única restrição é a linguagem de programação que deve ser **Python**

**Dicas**
* Usar encoding para ler arquivo sem erros
* Pandas para leitura de arquivos csv
* Se atentar as virgulas em campos que exibem valores
* Ler a documentação na api de moedas awesomeapi para utilizar o endpoint correto para obter da cotação do real

Boa sorte !
