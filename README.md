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
2. O método deve ser nomeado de modo a indicar sua função. O nome deve sempre ser autoexplicativo.
3. O método deve executar "uma única tarefa", não desviando de sua responsabilidade.
4. Fique atento aos possíveis valores que um dado parâmetro pode assumir. Considere todas as possibilidades. 

<table class="tg">
  <tr>
    <th class="tg-us36">Bom</th>
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

5. Declare as constantes. Isso facilita o entendimento do código e, caso necessário, alterações no mesmo. Valores soltos no código não são claros.

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
 
 6. Use String.Empty em substituição de "".
 
 <table class="tg">
  <tr>
    <th class="tg-us36">Bom</th>
    <th class="tg-us36">Ruim</th>
  </tr>
  <tr>
    <td class="tg-us36">
	if (nome == String.Empty) <br />
	{<br /> 
	    &nbsp;&nbsp;&nbsp;&nbsp; // ... <br />
	}
    </td>
    <td class="tg-us36">
	if (nome == "") <br />
	{<br /> 
	    &nbsp;&nbsp;&nbsp;&nbsp; // ... <br />
	}
    </td>
  </tr>
</table>
 
 7. Ao fazer comparações de strings, converta para minúsculas, maiúculas e/ou retire os espaços do início e do fim. Isso garante que a string irá corresponder, mesmo se estiver escrita de forma diferente. 
 
<table class="tg">
  <tr>
    <th class="tg-us36">Bom</th>
    <th class="tg-us36">Ruim</th>
  </tr>
  <tr>
    <td class="tg-us36">
	if (nome.ToLower() == "contrato") <br />
	{<br /> 
	    &nbsp;&nbsp;&nbsp;&nbsp; // ... <br />
	}
    </td>
    <td class="tg-us36">
	if (nome == "contrato") <br />
	{<br /> 
	    &nbsp;&nbsp;&nbsp;&nbsp; // ... <br />
	}
    </td>
  </tr>
  <tr>
    <td class="tg-us36">
	if (nome.ToUpper() == "AGENCIA") <br />
	{<br /> 
	    &nbsp;&nbsp;&nbsp;&nbsp; // ... <br />
	}
    </td>
    <td class="tg-us36">
	if (nome == "AGENCIA") <br />
	{<br /> 
    	&nbsp;&nbsp;&nbsp;&nbsp; // ... <br />
	}
    </td>
  </tr>
  <tr>
    <td class="tg-us36">
	if (nome.trim() == "Cliente") <br />
	{<br /> 
	    &nbsp;&nbsp;&nbsp;&nbsp; // ... <br />
	}
    </td>
    <td class="tg-us36">
	if (nome == "  Cliente  ") <br />
	{<br /> 
    	&nbsp;&nbsp;&nbsp;&nbsp; // ... <br />
	}
    </td>
  </tr>
</table>

8. Utilize o recurso <b>enum</b> para indicar valores discretos.

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
9. Fique atento aos tipos de acesso (public / private / protected / internal). Variáveis, classes, membros devem ser declarados de forma correta de acordo com o seu uso e nível de acesso.
10. Evite compartilhar variável de membro entre os métodos. Em tais situações, opte por declarar variáveis locais.
11. Não crie duas classes em um único arquivo, isso pode dificultar a localização de erros.
12. Evite criar arquivos grandes. É recomendável refatorar arquivos com mais de 1000 linhas.  
13. Mensagens de erro devem direcionar o usuário ao problema, logo, insira uma mensagem clara e específica do erro.

## Exceções

1. Existem diversos tipos de exceções já definidas no .Net. Antes de criar uma exceção, verifique se já não existe uma que se enquadra para sua situação (https://docs.microsoft.com/pt-br/dotnet/standard/design-guidelines/using-standard-exception-types).
2. Caso sua exceção for de negócio, crie, capture e lance suas próriprias exceções. Nunca utilize a exceção genérica "Exception" para todos os casos.
3. Use try-catch na camada de dados para capturar as exceções do banco de dados. Após gravar a exceção, ela pode ser lançada para que uma outra camada da aplicação possa tomar as medidas adequadas.
4. Ao capturar um erro não tratado/esperado, SEMPRE utilize apenas o "throw" e nunca "throw EXCEÇÃO".

<table class="tg">
  <tr>
    <th class="tg-us36">Bom</th>
    <th class="tg-us36">Ruim</th>
  </tr>
  <tr>
    <td class="tg-us36">
	try<br />
	{<br />
		&nbsp;&nbsp;&nbsp;&nbsp; // Seu código<br />
	}<br />
	catch (ExcecaoNegocio excecao)<br />
	{<br />
		&nbsp;&nbsp;&nbsp;&nbsp; LogarExcecao(excecao);<br />
		<br />
		&nbsp;&nbsp;&nbsp;&nbsp;throw;<br />
	}<br />
	catch<br />
	{<br />
		&nbsp;&nbsp;&nbsp;&nbsp;throw;<br />
	}<br />
    </td>
    <td class="tg-us36">
	try<br />
	{<br />
		&nbsp;&nbsp;&nbsp;&nbsp;// Seu código<br />
	}<br />
	catch(Exception excecao)<br />
	{<br />
		&nbsp;&nbsp;&nbsp;&nbsp;throw excecao;<br />
	}<br />
    </td>
  </tr>
</table>

## Ao iniciar uma aplicação

1. Se um valor errado for encontrado no arquivo de configuração, a aplicação deve informar ao usuário, por meio de uma mensagem de erro, quais são os valores corretos.
2. A aplicação deve ser capaz de criar um arquivo com valores padrão para o caso de algum arquivo de configuração necessário não for encontrado.
3. Faça uma verificação dos arquivos, das dependências necessárias e da conexão com o banco de dado. Garanta que esteja tudo pronto para começar.

## Arquitetura

1. Use arquitetura em camadas: Camada web, business e data access.
2. Utilize uma camada específica para acesso ao banco de dados. Nunca execute uma tarefa relacionada ao acesso do BD por meio das páginas de interface do usuário.
3. Separe a aplicação em assemblies. Agrupe as classes de utilitários independentes em uma biblioteca de classe separada. Todos os arquivos relacionados ao banco de dados podem estar em uma outra biblioteca de classes.

## Comentários

1. Escreva comentários sempre que necessário.
2. Evite comentar cada linha de código. Se os nomes das variáveis e métodos estão autoexplicativos, não há a necessidade de comentar tudo.
3. Sempre verifique os comentários. Garanta que a ortografia esteja correta e que a escrita esteja suficiente para o entendimento do código.
