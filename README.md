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
| Membro | _ + CamelCase  | _ sobrenomeCliente |
| Propriedade | PascalCase  | SobrenomeCliente |
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

## Indentação

1. Sempre utilize TAB para identação
2. Caso seja necessário utilizar mais de uma linha, deve haver apenas uma identação. As demais linhas devem seguir a primeira

```
public string ObterContatoPrincipal()
{
    string contatoPrincipal = _contatos.OrderByDescending(
        contato => contato).FirstOrDefault(
        contato => contato.Contains("principal"));

    return contatoPrincipal;
}
```

3. As chaves { } devem estar no mesmo nível da declaração. Início e fim

<table class="tg">
  <tr>
    <th class="tg-us36">Bom</th>
    <th class="tg-us36">Ruim</th>
  </tr>
  <tr>
    <td class="tg-us36">
	public void ObterContatoPrincipal()<br />
	{<br />
	}
    </td>
    <td class="tg-us36">
	public void ObterContatoPrincipal() {<br />
	}
    </td>
  </tr>
  <tr>
    <td class="tg-us36">
	foreach (Fatura fatura in faturas)<br />
	{<br />
	}
    </td>
    <td class="tg-us36">
	foreach (Fatura fatura in faturas) {<br />
	}
    </td>
  </tr>
</table>

4. Utilize 1 espaço antes e depois de cada operador (<; >;<=; =>; etc) e 1 espaço apenas depois de cada separador

<table class="tg">
  <tr>
    <th class="tg-us36">Bom</th>
    <th class="tg-us36">Ruim</th>
  </tr>
  <tr>
    <td class="tg-us36">
	for (int variavel = 0; variavel < 100; ++variavel)<br />
	{<br />
	}
    </td>
    <td class="tg-us36">
	for(int variavel=0;variavel<100;++variavel)<br />
	{<br />
	}
    </td>
  </tr>
</table>

## Boas práticas de programação

1. Evite métodos extensos. Caso o método possua mais de 30 linhas, opte por uma refatoração.
2. O método deve ser nomeado de modo a indicar sua função. O nome deve ser, preferencialmente, autoexplicativo.
3. O método deve executar "uma única tarefa", não desviando de sua responsabilidade.
4. Fique atento aos possíveis valores que um dado parâmetro pode assumir. Considere todas as possibilidades. 

<table class="tg">
  <tr>
    <th class="tg-us30">Bom</th>
    <th class="tg-us36">Ruim</th>
  </tr>
  <tr>
    <td class="tg-us36">
	if (tipoTarifa == Padrao) <br /> { <br /> 
	    &nbsp;&nbsp;&nbsp;&nbsp; // Padrao <br /> 
	    } <br /> 
	else if (tipoTarifa == Promocional) <br /> { <br /> 
	    &nbsp;&nbsp;&nbsp;&nbsp; // Promocional <br /> 
	    } <br />
	else <br /> { <br /> 
	    &nbsp;&nbsp;&nbsp;&nbsp; // Tipo inesperado lança uma exceção <br /> 
	    }
    </td>
    <td class="tg-us36">
	if (tipoTarifa == Padrao) <br /> { <br /> 
	    &nbsp;&nbsp;&nbsp;&nbsp; // Padrao <br /> 
	    } <br /> 
	else <br /> { <br /> 
	    &nbsp;&nbsp;&nbsp;&nbsp; // Promocional <br /> 
	    } <br />
	    // Se um novo tipo for incluido, não ocorrera diferenciacao com o Promocional. 
    </td>
  </tr>
</table>

5. Declare as constantes. Isso facilita o entendimento do código e, caso necessário, alterações no mesmo.

<table class="tg">
  <tr>
    <th class="tg-us36">Bom</th>
    <th class="tg-us36">Ruim</th>
  </tr>
  <tr>
    <td class="tg-us36">
	const int diasDeLocacao = 30; <br />
	const double precoPorDia = 10; <br />
	const double desconto = 0,1; <br /><br />
	const double precoFinal = precoPorDia * diasDeLocacao; <br />
	const double precoComDesconto = precoFinal * (1 - desconto);
    </td>
    <td class="tg-us36">
	const double precoFinal = 10 * 30; <br />
	const double precoComDesconto = precoFinal * (1 - 0,1);
    </td>
  </tr>
</table>

6. Utilize o recurso <b>enum</b> para indicar valores discretos.

```
	enum StatusPagamento
	     {
		 EmAberto;
		 Paga;
		 Vencida;
		 Renegociada;
	     }
	void EnviarEmail(string conteudoMensagem, StatusPagamento statusDePagamento)
	{
	     switch (statusDePagamento)
	     {
	         case StatusPagamento.EmAberto:
		     // manda email
		     break;
		 case StatusPagamento.Paga:
		     // manda email
		     break;
		 case StatusPagamento.Vencida:
		     // manda email
		     break;
		 case StatusPagamento.Renegociada:
		     // manda email
		     break;
	         default;
	     }
	}
```
7. Variáveis membros são declaradas como privadas e as propriedades podem ser public/protected.
8. Evite compartilhar variável de membro entre os métodos. Em tais situações, opte por declarar variáveis locais.
9. Não crie duas classes em um único arquivo, isso pode dificultar a localização de erros.
10. Evite criar arquivos grandes. É recomendável refatorar arquivos com mais de 1000 linhas.  
11. Capture exceções específicas.
12. Mensagens de erro devem direcionar o usuário ao problema, logo, insira uma mensagem clara e específica do erro.

## Ao iniciar uma aplicação

1. Faça uma verificação dos arquivos, das dependências necessárias e da conexão com o banco de dado. Garanta que esteja tudo pronto para começar.

