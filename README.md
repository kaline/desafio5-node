# Exercício 5 de node

Neste exercício você precisará:

- criar um projeto
- adicionar o projeto num repositório
- usar as funções de gravação de arquivo do node.js
- usar [esta biblioteca](https://www.npmjs.com/package/fft-js)

## problema a resolver

Crie um script em node js que receba um vetor de números e a partir deles faça uso da
transformada rápida de fourrier conforme o exemplo abaixo:

```javascript
var fft = require('fft-js').fft,
    fftUtil = require('fft-js').util,
    signal = [1,0,1,0];

var phasors= fft(signal);

var frequencies = fftUtil.fftFreq(phasors, 8000), // Sample rate and coef is just used for length, and frequency step
    magnitudes = fftUtil.fftMag(phasors); 

var both = frequencies.map(function (f, ix) {
    return {frequency: f, magnitude: magnitudes[ix]};
});

console.log(both);
```

## Orientações importantes:

O seu código deverá fazer duas coisas diferentes do código dado como exemplo:

- o vetor **signal** deverá ser lido a partir de process.argv seguindo regras a serem explicadas adiante
- a saída do cálculo de frequências não deve ser impresso via console.log, mas sim ser salvo num arquivo chamado **saida.json**
- crie um projeto com **npm init** e instale o **fft-js** como dependência
- colocar no .gitignore a node_modules

## Exemplo de uso

Este exemplo vai ler um vetor de 5 posições:

```bash
node index.js 5 1 1 0 2 4
```

O primeiro argumento é 5 para facilitar na hora de ler os demais argumentos.

Este exemplo vai ler 3 valores:

```bash
node index.js 3 4 6 9
```

Em ambos os casos é criado um vetor com estes elementos e aí os cáculos são realizados.

## Entregável

Um repositório no git com o nome node-exercicio-5 contendo o script capaz de criar o
arquivo contendo o valor da variável **both** apresentada no exemplo de código.

## Dica

Estudar o uso da função
[JSON.stringify](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)
e da 
[writeFileSync](https://nodejs.org/api/fs.html#fs_fs_writefilesync_file_data_options)