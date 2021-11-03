# map-nextjs

## Pre-requisitos 
- Node.js
- Yarn 

## Setup

```bash
//Inicialização
yarn create next-app
```
Feito isso irá instalar as depedências fundamentais do Next
- React
- React DOM
- Next

```bash
cd boilerplate
yarn dev
```

### Configurando o TypeScript no NextJS
- Na raiz do projeto é preciso criar um arquivo tsconfig<br>
Esse arquivo ts.config é um arquivo de compilação do compilador do ts<br>
E depois rodar o comando yarn dev

```bash
touch tsconfig.json

yarn dev
```
Mostra um erro: Precisamos instalar os pacotes necessários:
- typescript - responsável pela compilação
- @types/react
- @types/node

types/react e types/node, irão facilitar o autocomplete do intellisense

```bash
yarn add --dev typescript @types/react

yarn dev
```

Ao rodar _yarn dev_ ele já consegue entender o typescript. Ele identificou e populou o tsconfig<br>
E foi criado um novo arquivo _next-env.d.ts_, onde tá declarado alguns tipos.


### [EditorConfig](https://editorconfig.org/)
Definir regras do seu editor, assim toda vez que você crie um novo arquivo ele siga essas regras.
Que pode ser:
- Tamanho da indentação 
- Se você vai usar tabs ou spaces
- Se você vai pular uma linha no final do arquivo
- ...

Na raiz do projeto:
```bash
touch editorconfig
```
