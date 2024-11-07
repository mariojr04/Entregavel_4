#  Como Rodar o Projeto
## 1. Clonando o Repositório

Primeiro, clone o repositório para sua máquina local:

````bash
git clone https://github.com/seu-usuario/seu-repositorio.git
````

## 2. Instalando Dependências
Dentro do diretório do projeto, instale as dependências usando o npm:

````bash
cd seu-repositorio
npm install
````
Este comando irá instalar o Jest (e outras dependências) necessárias para rodar os testes unitários.

## 3. Executando os Testes
Com as dependências instaladas, você pode rodar os testes unitários com o comando:

````bash
npm test
````
O Jest irá procurar por arquivos de teste no diretório `/tests` e executar os testes definidos nos arquivos com o sufixo `.test.js`.


## Exemplo de Saída
Ao rodar os testes, você verá uma saída semelhante a esta no terminal:

```` bash
PASS  ./tests/soma.test.js
✓ soma de 1 + 2 deve retornar 3 (5 ms)
✓ soma de -1 + 2 deve retornar 1
✓ deve lançar erro quando parâmetros não forem números
````
Se algum teste falhar, o Jest vai mostrar o erro, facilitando a depuração.

# Como Adicionar Novos Testes

Para adicionar novos testes, crie um arquivo no diretório `/tests` com o sufixo `.test.js`, e defina os testes utilizando o framework Jest. Por exemplo:
````bash
// tests/soma.test.js
const soma = require('../src/soma');

test('soma de 1 + 2 deve retornar 3', () => {
  expect(soma(1, 2)).toBe(3);
});

test('deve lançar erro quando os parâmetros não forem números', () => {
  expect(() => soma('a', 2)).toThrow('Ambos os parâmetros devem ser números');
});
````
Cada teste deve ser definido usando a função `test()`, e você pode usar várias funções de asserção do Jest (como `toBe()`, `toEqual()`, `toThrow()`, etc.) para verificar o comportamento esperado.

# Boas Práticas de Programação
Este projeto segue algumas boas práticas de Clean Code e Programação Defensiva:

## 1. Validação de Entrada
Validação de entradas é feita para garantir que a função não quebre em caso de parâmetros inválidos:

javascript
Copiar código
// Exemplo de validação de entrada
function soma(a, b) {
  if (typeof a !== 'number' || typeof b !== 'number') {
    throw new Error('Ambos os parâmetros devem ser números');
  }
  return a + b;
}
## 2. Tratamento de Erros

Erros são tratados adequadamente, garantindo que a aplicação não falhe de maneira inesperada:

````bash
try {
  soma('a', 2);
} catch (error) {
  console.error(error.message);  // Ambos os parâmetros devem ser números
}
````
## 3. Nomes Significativos para Funções e Variáveis

As funções e variáveis são nomeadas de forma clara e intuitiva para facilitar a leitura e a manutenção do código.

````bash
function calcularSoma(numero1, numero2) {
  return numero1 + numero2;
}
````
## Dicas de Uso
- **Rodar um Teste Específico**: Se você quiser rodar um teste específico, pode usar o comando `npm test nome-do-arquivo`, como por exemplo:

````bash
npm test soma.test.js
````
- **Testes em Paralelo**: O Jest já executa os testes em paralelo, o que acelera o processo de execução de testes.

- **Cobertura de Testes**: Você pode rodar os testes com a cobertura de código (para ver quais partes do código foram testadas) utilizando o comando:

````bash
npm test --coverage
````
Isso vai gerar um relatório sobre a cobertura de testes do seu código.

