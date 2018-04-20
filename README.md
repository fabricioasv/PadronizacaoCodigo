# PadronizacaoCodigo
Sugestão de padronização de código para a plataforma .NET

## CamelCase

CamelCase é a denominação em inglês quando se escreve palavras compostas ou frases. A primeira letra da primeira palavra é iniciada com minúscula e unidas sem espaços. É um padrão bastante utilizado em linguagens como Java, Ruby, PHP, Python onde sua principal utilização é em definições de Classes e Objetos. Já para o .NET sua utilização é mais abrangente em variáveis e membros (http://pt.wikipedia.org/wiki/CamelCase).

Ex: valorDaFatura, codigoDoCliente, valorDoImpostoRetido

## PascalCase

Denominaçao quando se escreve palavras compostas ou frases onde a primeira letra de cada palavra é iniciada com maiúscula. O padrão PascalCase é mais utilizado para nomear métodos e classes.

Ex: CalcularImposto(), EnvioEmail

## Usando CamelCase e PascalCase

| Estrutura  | Nomeclatura | Exemplo |
| ------------- | ------------- | ------------- |
| Classe  | PascalCase  | EnvioEmail  |
| Interface  | I + PascalCase  | IEnvioEmail  |
| Método  | PascalCase  | EnviarEmailParaClientePf()  |
| Variável  | CamelCase  | nomeCliente  |
| Membro Público/Privado | _ + CamelCase  | _ sobrenomeCliente |
| Constantes  | MAIÚSCULAS COM SUBLINHADO  | VALOR_DESCONTO  |
