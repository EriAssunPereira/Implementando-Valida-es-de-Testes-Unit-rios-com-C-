# Implementando-Valida-es-de-Testes-Unit-rios-com-C-
**Desafio de projeto:**

Para melhorar a qualidade do sistema, é uma excelente ideia adicionar testes unitários. Eles ajudam a garantir que o código funcione corretamente e a identificar problemas antes que eles afetem os clientes. Aqui estão algumas etapas que podemos seguir para escrever testes unitários eficazes:

1. **Identifique as partes críticas do sistema**: Comece analisando o código e identificando as áreas mais importantes. Isso pode incluir funções de validação, cálculos complexos, integrações com outras partes do sistema, etc.

2. **Escreva testes positivos e negativos**: Para cada parte crítica, crie testes que verifiquem o comportamento esperado (testes positivos) e também testes que verifiquem como o código se comporta quando recebe entradas inválidas ou inesperadas (testes negativos).

3. **Use estruturas de teste apropriadas**: No C#, você pode usar bibliotecas como NUnit, MSTest ou xUnit para escrever seus testes. Essas bibliotecas fornecem estruturas para criar e executar testes de maneira organizada.

4. **Execute os testes regularmente**: Configure um processo automatizado para executar seus testes regularmente. Isso pode ser feito como parte de um pipeline de CI/CD ou manualmente antes de enviar alterações para produção.

5. **Mantenha os testes atualizados**: À medida que o código muda, atualize seus testes para refletir essas mudanças. Isso garante que os testes continuem sendo relevantes e úteis.

Identificação das partes críticas do sistema:

1. **Identificação das partes críticas do sistema**:
   - Comece analisando as classes `ValidacoesLista` e `ValidacoesString` no projeto do tipo console. Quais são os métodos mais críticos nessas classes? Eles realizam validações importantes ou cálculos complexos?
   - Identifique também as áreas do código que interagem com outras partes do sistema ou que têm impacto significativo no funcionamento geral.

2. **Escreva testes positivos e negativos**:
   - Para cada método crítico identificado, crie testes que verifiquem o comportamento esperado (testes positivos). Por exemplo, se um método valida uma lista, teste com uma lista válida e verifique se o resultado é o esperado.
   - Além disso, crie testes que verifiquem como o código se comporta quando recebe entradas inválidas ou inesperadas (testes negativos). Por exemplo, teste com uma lista vazia ou com valores inválidos.

3. **Use estruturas de teste apropriadas**:
   - No projeto de testes com xUnit, crie classes de teste correspondentes para `ValidacoesLista` e `ValidacoesString`. Dentro dessas classes, implemente os métodos de teste para cada método crítico.
   - Use as estruturas fornecidas pelo xUnit para criar e executar os testes de maneira organizada.

4. **Execute os testes regularmente**:
   - Configure um processo automatizado para executar seus testes regularmente. Isso pode ser feito como parte de um pipeline de CI/CD ou manualmente antes de enviar alterações para produção.

5. **Mantenha os testes atualizados**:
   - À medida que o código muda, atualize seus testes para refletir essas mudanças. Isso garante que os testes continuem sendo relevantes e úteis.

Aqui está um exemplo de teste positivo para a classe `ValidacoesString`:

Suponhamos que temos um método chamado `IsPalindrome(string input)` na classe `ValidacoesString` que verifica se uma determinada string é um palíndromo (ou seja, lê-se da mesma forma da esquerda para a direita e vice-versa). Podemos escrever um teste positivo para esse método da seguinte forma:

```csharp
using Xunit;
using MeuProjeto.ConsoleApp;

namespace MeuProjeto.Testes
{
    public class ValidacoesStringTests
    {
        [Fact]
        public void IsPalindrome_ValidPalindrome_ReturnsTrue()
        {
            // Arrange
            string validPalindrome = "racecar";

            // Act
            bool result = ValidacoesString.IsPalindrome(validPalindrome);

            // Assert
            Assert.True(result);
        }
    }
}
```

Neste teste:
- **Arrange**: Criamos uma string válida de palíndromo ("racecar").
- **Act**: Chamamos o método `IsPalindrome` com a entrada válida.
- **Assert**: Verificamos se o resultado é `true`.

Lembre-se de implementar o método `IsPalindrome` na classe `ValidacoesString` para que esse teste seja bem-sucedido.

Vamos considerar um exemplo de teste negativo para a classe `ValidacoesLista`. Suponhamos que temos um método chamado `RemoveDuplicates(List<int> numbers)` que remove números duplicados de uma lista de inteiros. Veja como podemos escrever um teste negativo para esse método:

```csharp
using System.Collections.Generic;
using Xunit;
using MeuProjeto.ConsoleApp;

namespace MeuProjeto.Testes
{
    public class ValidacoesListaTests
    {
        [Fact]
        public void RemoveDuplicates_EntradaInvalida_RetornaListaOriginal()
        {
            // Arrange
            List<int> entradaInvalida = new List<int> { 1, 2, 3, 1, 4, 2 };

            // Act
            List<int> resultado = ValidacoesLista.RemoveDuplicates(entradaInvalida);

            // Assert
            Assert.Equal(entradaInvalida, resultado);
        }
    }
}
```

Neste teste:
- **Arrange**: Criamos uma lista com números duplicados (`entradaInvalida`).
- **Act**: Chamamos o método `RemoveDuplicates` com a entrada inválida.
- **Assert**: Verificamos se o resultado é igual à lista de entrada original.

O objetivo deste teste negativo é garantir que o método lide corretamente com entradas inesperadas (números duplicados) e não modifique a lista.

https://github.com/digitalinnovationone/trilha-net-testes-unitarios-desafio
