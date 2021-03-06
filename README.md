# php-api

## Índice
* [Informações gerais](#informações-gerais)
* [Gerador de CPF](#geraCPF)
* [Validador de CPF](#validaCPF)
* [Gerador de CNPJ](#geraCNPJ)
* [Validador de CNPJ](#validaCNPJ)
* [Cálculo de Financiamento PRICE](#calculaPRICE)
* [Cálculo de Financiamento SAC](#calculaSAC)
* [Cálculo de Prestação](#calculaPAGTO)
* [Cálculo de Valor Futuro](#calculaVF)
* [Cálculo de Valor Presente](#calculaVP)
* [Setup](#setup)

## Informações Gerais
* Toda a biblioteca foi desenvolvida em PHP com foco em cálculos financeiros
* Chamadas e saídas em formato JSON
* APIs para uso público

## geraCPF
* Arquivo: geraCPF.php
* Gerador de CPFs válidos para uso em teste de aplicações
* URL: http://.../geracpf.php
* Body => JSON
```
{ "authKey":"", "param": [#]} onde # é a quantidade de CPFs a serem gerados
```
* Method: GET
* Retorno:
```
{
    "statCode": "<status code>",
    "statMsg": "<status message>",
    "result": ["###########","###########"] onde ########### são CPFs gerados
}
```
* Os stat codes e messages podem ser vistos em include/std_messages_api_php.php

## validaCPF
* Arquivo: validaCPF.php
* Verificador de número de CPF
* URL: http://.../validacpf.php
* Body => JSON
``` 
{ "authKey":"", "param": ["###########","###########"]} onde ########### são CPFs a serem validados
```
* Method: GET ou POST
* Retorno:
```
{
    "statCode": "<status code>",
    "statMsg": "<status message>",
    "result": [#,#] onde # = 0 para CPF inválido e 1 para CPF válido 
}
```
* Os stat codes e messages podem ser vistos em include/std_messages_api_php.php

## geraCNPJ
* Arquivo: geraCNPJ.php
* Gerador de CNPJs válidos para uso em teste de aplicações
* URL: http://.../geracnpj.php
* Body => JSON 
```
{ "authKey":"", "param": [#]} onde # é a quantidade de CNPJs a serem gerados
```
* Method: GET
* Retorno:
```
{
    "statCode": "<status code>",
    "statMsg": "<status message>",
    "result": "result": ["###########","###########"] onde ########### são CNPJss gerados
}
```
* Os stat codes e messages podem ser vistos em include/std_messages_api_php.php

## validaCNPJ
* Arquivo: validaCNPJ.php
* Validador de número de CNPJ
* URL: http://.../validacnpj.php
* Body => JSON
```
{ "authKey":"", "param": ["###########","###########"]} onde ########### são CNPJs a serem validados
```
* Method: GET ou POST
* Retorno:
```
{
    "statCode": "<status code>",
    "statMsg": "<status message>",
    "result": [#,#] onde # = 0 para CNPJ inválido e 1 para CNPJ válido 
}
```
* Os stat codes e messages podem ser vistos em include/std_messages_api_php.php

## calculaPRICE
* Arquivo: calculaPRICE.php
* Calculo de financiamento por tabela PRICE - Sistema Frances de Amortizacao
* URL: http://.../calculaPRICE.php
* Body => JSON
```
 { "authKey":"", "param": [vl, i, n]} Ex.: { "authKey":"", "param": [1000, 1.5, 12]}
```
* onde vl = valor financiado / i = taxa de juros / n = numero de periodos
* Method: GET ou POST
* Retorno:
```
{
    "statCode": "<status code>",
    "statMsg": "<status message>",
    "result": [
        [
            ###,        Numero da parcela
            ###.##,     Vl. da Prestação
            ###.##,     Vl. da Amortização
            ###.##,     Vl dos Juros
            ###.##      Saldo devedor
        ],[...]
        ]
}
```
* Os stat codes e messages podem ser vistos em include/std_messages_api_php.php

## calculaSAC
* Arquivo: calculaSAC.php
* Calculo de financiamento por tabela SAC
* URL: http://.../calculaSAC.php
* Body => JSON
```
{ "authKey":"", "param": [vl, i, n]} Ex.: { "authKey":"", "param": [1000, 1.5, 12]}
```
* onde vl = valor financiado / i = taxa de juros / n = numero de periodos
* Method: GET ou POST
* Retorno:
```
{
    "statCode": "<status code>",
    "statMsg": "<status message>",
    "result": [
        [
            ###,        Numero da parcela
            ###.##,     Vl. da Prestação
            ###.##,     Vl. da Amortização
            ###.##,     Vl dos Juros
            ###.##      Saldo devedor
        ],[...]
        ]
}
```
* Os stat codes e messages podem ser vistos em include/std_messages_api_php.php

## calculaPAGTO
* Arquivo: calculaPAGTO.php
* Cálculo financeiro para valor de Prestação
* URL: http://.../calculaPAGTO.php
* Body => JSON 
```
{ "authKey":"", "param": [vl, i, n]} Ex.: { "authKey":"", "param": [1000, 1.5, 12]}
```
* onde vl = valor financiado / i = taxa de juros / n = numero de periodos
* Method: GET ou POST
* Retorno:
```
{
    "statCode": "<status code>",
    "statMsg": "<status message>",
    "result": #####.## correspondente ao valor da prestação
}
```
* Os stat codes e messages podem ser vistos em include/std_messages_api_php.php

## calculaVF
* Arquivo: calculaVF.php
* Cálculo financeiro para Valor Futuro
* URL: http://.../calculaVF.php
* Body => JSON 
```
{ "authKey":"", "param": [vp, i, n]} Ex.: { "authKey":"", "param": [vp, i, n]}
```
* onde vp = valor presente / i = taxa de juros / n = numero de periodos
* Method: GET ou POST
* Retorno:
```
{
    "statCode": "<status code>",
    "statMsg": "<status message>",
    "result": ####.## correspondente ao valor futuro
}
```
* Os stat codes e messages podem ser vistos em include/std_messages_api_php.php
 
## calculaVP
* Arquivo: calculaVP.php
* Cálculo financeiro para Valor Presente
* URL: http://.../calculaVP.php
* Body => JSON
```
{ "authKey":"", "param": [vf, i, n]} Ex.: { "authKey":"", "param": [vf, i, n]}
```
* onde vf = valor futuro / i = taxa de juros / n = numero de periodos
* Method: GET ou POST
* Retorno:
```
{
    "statCode": "<status code>",
    "statMsg": "<status message>",
    "result": ####.## correspondente ao valor presente
}
```
* Os stat codes e messages podem ser vistos em include/std_messages_api_php.php

## Setup
* Basta copiar os arquivos para uma pasta de scripts PHP