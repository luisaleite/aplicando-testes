# aplicando-testes

(De 0 a 3) - Implementação dos 3 tipos de testes apresentados no artigo (1 ponto para cada tipo de teste implementado)

(De 0 a 2) - Explicação clara e objetiva sobre a aplicação dos testes

(De 0 a 2) - Organização do arquivo readme, com imagens dos testes e coerência dos textos.

# Xunit

## Primeiro caso de teste com essas informações:

```jsx
[Theory]
[InlineData(32, 0)]
[InlineData(47, 8.33)]
[InlineData(86, 30)]
[InlineData(90.5, 32.5)]
[InlineData(120.18, 48.99)]
[InlineData(212, 100)]
```

![Untitled](img/Untitled%20(7).png)

## Segundo caso de teste com essas informações:

```csharp
        [Theory]
        [InlineData(22, -5.56)]
        [InlineData(47, 8.33)]
        [InlineData(86, 30)]
        [InlineData(90.5, 32.5)]
        [InlineData(120.18, 48.99)]
        [InlineData(212, 100)]
```

![Untitled](img/Untitled%20(9).png)

*Foi trocado um valor intencionalmente para ver que os testes funcionam pois quando um valor da errado existe um erro sendo indicado

## Explicação

Este código é escrito em C# e usa a biblioteca de testes xUnit para testar a funcionalidade de conversão de temperatura de Fahrenheit para Celsius. Vou explicar cada parte do código:

1. **Namespaces e Usos**:
    
    ```csharp
    using System;
    using Xunit;
    
    ```
    
    - `using System;` importa o namespace System, que é a biblioteca básica do .NET.
    - `using Xunit;` importa a biblioteca de testes xUnit, que é usada para criar e executar testes unitários.
2. **Definição do Namespace**:
    
    ```csharp
    namespace Temperatura.Testes
    
    ```
    
    - Define um namespace chamado `Temperatura.Testes`. Namespaces são usados para organizar e agrupar classes relacionadas.
3. **Classe de Teste**:
    
    ```csharp
    public class TestesConversorTemperatura
    
    ```
    
    - Declara uma classe pública chamada `TestesConversorTemperatura` onde os métodos de teste serão definidos.
4. **Atributos [Theory] e [InlineData]**:
    
    ```csharp
    [Theory]
    [InlineData(32, 0)]
    [InlineData(47, 8.33)]
    [InlineData(86, 30)]
    [InlineData(90.5, 32.5)]
    [InlineData(120.18, 48.99)]
    [InlineData(212, 100)]
    
    ```
    
    - `[Theory]` é um atributo do xUnit que indica que o método de teste pode ser executado várias vezes com diferentes conjuntos de dados.
    - `[InlineData(...)]` fornece os dados de entrada para o método de teste. Cada chamada de `[InlineData]` passa dois valores, a temperatura em Fahrenheit e a temperatura esperada em Celsius.
5. **Método de Teste**:
    
    ```csharp
    public void TestarConversaoTemperatura(double fahrenheit, double celsius)
    {
        double valorCalculado = ConversorTemperatura.FahrenheitParaCelsius(fahrenheit);
        Assert.Equal(celsius, valorCalculado);
    }
    
    ```
    
    - `public void TestarConversaoTemperatura(double fahrenheit, double celsius)` é o método que realiza o teste.
    - O método recebe dois parâmetros: a temperatura em Fahrenheit e a temperatura esperada em Celsius.
    - `double valorCalculado = ConversorTemperatura.FahrenheitParaCelsius(fahrenheit);` chama o método `FahrenheitParaCelsius` da classe `ConversorTemperatura` para converter a temperatura de Fahrenheit para Celsius.
    - `Assert.Equal(celsius, valorCalculado);` verifica se o valor calculado é igual ao valor esperado. Se não for, o teste falha.
    
    # NUnit
    
    ## Primeiro caso de teste com essas informações:
    
    ```jsx
    [Theory]
    [InlineData(32, 0)]
    [InlineData(47, 8.33)]
    [InlineData(86, 30)]
    [InlineData(90.5, 32.5)]
    [InlineData(120.18, 48.99)]
    [InlineData(212, 100)]
    ```
    
    ![Untitled](img/Untitled%20(10).png)
    
    ## Segundo caso de teste com essas informações:
    
    ```jsx
            [Theory]
            [InlineData(22, 0)]
            [InlineData(47, 8.33)]
            [InlineData(86, 30)]
            [InlineData(90.5, 32.5)]
            [InlineData(120.18, 48.99)]
            [InlineData(212,00)]
    ```
    
    ![Untitled](img/Untitled%20(8).png)
    
    Este é um código de teste utilizando o framework NUnit para testar um conversor de temperatura de Fahrenheit para Celsius. 
    
    ```csharp
    using NUnit.Framework;
    
    ```
    
    Esta linha importa o namespace do NUnit, permitindo que você use as classes e métodos fornecidos pelo framework NUnit para escrever testes unitários.
    
    ```csharp
    namespace Temperatura.Testes
    {
        public class TestesConversorTemperatura
        {
    
    ```
    
    Aqui, estamos definindo um namespace chamado `Temperatura.Testes` e dentro dele uma classe chamada `TestesConversorTemperatura`. Esta classe irá conter todos os testes relacionados à conversão de temperatura.
    
    ```csharp
    [TestCase(32, 0)]
    [TestCase(47, 8.33)]
    [TestCase(86, 30)]
    [TestCase(90.5, 32.5)]
    [TestCase(120.18, 48.99)]
    [TestCase(212, 100)]
    
    ```
    
    Estes são os casos de teste. Cada caso de teste é marcado com o atributo `[TestCase]`, seguido dos valores de entrada e saída esperados. Por exemplo, `[TestCase(32, 0)]` indica que quando a temperatura em Fahrenheit é 32, esperamos que ela seja convertida em 0 Celsius.
    
    ```csharp
    public void TesteConversaoTemperatura(double tempFahrenheit, double tempCelsius)
    {
        double valorCalculado = ConversorTemperatura.FahrenheitParaCelsius(tempFahrenheit);
        Assert.AreEqual(tempCelsius, valorCalculado);
    }
    
    ```
    
    Este é o método de teste. Ele recebe os valores de temperatura em Fahrenheit e Celsius como parâmetros. Dentro do método, o código calcula a temperatura em Celsius usando o método `FahrenheitParaCelsius` do conversor de temperatura e armazena o resultado na variável `valorCalculado`. Em seguida, o método `Assert.AreEqual` é usado para verificar se o valor calculado é igual ao valor esperado `tempCelsius`. Se não for, o teste falhará.
    
    O objetivo desse código é garantir que a conversão de temperatura de Fahrenheit para Celsius esteja correta para os valores fornecidos nos casos de teste.
    
    # **MS Tes**t
    
    ## Primeiro caso de teste com essas informações:
    
    ```jsx
    [Theory]
    [InlineData(32, 0)]
    [InlineData(47, 8.33)]
    [InlineData(86, 30)]
    [InlineData(90.5, 32.5)]
    [InlineData(120.18, 48.99)]
    [InlineData(212, 100)]
    ```
    
    ![Untitled](img/Untitled%20(11).png)
    

## Segundo caso de teste com essas informações:

```csharp
        [DataRow(32, 0)]
        [DataRow(47, 8.33)]
        [DataRow(86, 30)]
        [DataRow(90.5, 32.5)]
        [DataRow(120.18, 48.99)]
        [DataRow(212, 0)]
        [DataTestMethod]
```

![Untitled](img/Untitled%20(12).png)

Este código é um exemplo de um teste unitário escrito usando o framework de testes Microsoft.VisualStudio.TestTools.UnitTesting. Ele é usado para testar a conversão de temperaturas de Fahrenheit para Celsius em uma classe chamada ConversorTemperatura.

Vamos quebrar o código:

1. O `using Microsoft.VisualStudio.TestTools.UnitTesting;` é uma declaração para importar os namespaces necessários para usar as classes e métodos fornecidos pelo framework de teste.
2. Em seguida, há uma declaração de namespace `namespace Temperatura.Testes { ... }`, que contém uma classe de teste chamada `TestesConversorTemperatura`.
3. Dentro dessa classe, há um método de teste chamado `TesteConversaoTemperatura`. Este método é decorado com os atributos `[DataRow]` e `[DataTestMethod]`. Isso indica que este método de teste deve ser executado várias vezes, uma vez para cada conjunto de dados fornecidos pelos atributos `DataRow`.
4. Cada atributo `DataRow` contém os parâmetros que representam uma temperatura em Fahrenheit e sua correspondente temperatura em Celsius.
5. Dentro do método `TesteConversaoTemperatura`, primeiro, a conversão da temperatura de Fahrenheit para Celsius é realizada chamando o método `ConversorTemperatura.FahrenheitParaCelsius()`, fornecendo a temperatura em Fahrenheit como parâmetro.
6. Em seguida, o método `Assert.AreEqual()` é usado para verificar se o valor calculado é igual ao valor esperado (a temperatura em Celsius fornecida no atributo `DataRow`).

Em resumo, este código realiza testes unitários para verificar se a conversão de temperaturas de Fahrenheit para Celsius na classe `ConversorTemperatura` está correta. Cada conjunto de dados fornecido pelos atributos `DataRow` é usado para testar diferentes casos de entrada.