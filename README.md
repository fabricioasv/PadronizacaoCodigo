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

## Escrita de um bom código

1. Classes devem ser escritas com PascalCase
2. Interfaces, preferencialmente, devem ter o indicador de interface 'I' seguido da classe que irá implementa-la
3. O nome do método deve ser um verbo significativo que deixe claro o objetivo do mesmo
4. A variável deve ser, preferencialmente, o mesmo nome do método que atribui seu valor sem o verbo. Caso não for possível, deve deixar claro o objetivo da mesma

```
private void escreverUmBomCodigo() {
  Fatura faturaDoCliente = ObterFaturaDoCliente();
}
```
```
private Fatura escreverUmBomCodigo() {
  Fatura faturaDoCliente = ObterFaturaDoClienteComRetencaoDeImpostosReferenteAOutroEstado();
  
  return faturaDoCliente;
}
```

> **Importante**: No segundo cenário, existia apenas uma variável do tipo Fatura. Caso existam mais, é aconselhável, que seja utilizada a primeira opção

5. Variáveis não devem ter apenas 1 letra - Ex: a, x, i -, mesmo que sejam auxiliares

```
private bool verificarSeExistemFaturasDoCliente(List<Fatura> faturas, string codigoCliente) {
  bool existemFaturasDoCliente = faturas.Any(fatura => fatura.CodigoCliente = codigoCliente);
  
  return existemFaturasDoCliente;
}
```
