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


### Editor Config
[EditorConfig](https://editorconfig.org/), define as regras do seu editor, assim toda vez que um arquivos for criado, ele siga essas regras.
Que pode ser:
- Tamanho da indentação 
- Se você vai usar tabs ou spaces
- Se você vai pular uma linha no final do arquivo
- ...

Na raiz do projeto:
```bash
touch .editorconfig
```

### ESLint
[ESLint](https://eslint.org/), analisa o código conforme vamos escrevendo para identificar problemas. Ex. Criação de variáveis que não estamos utilizando.

```bash
npx eslint --init
```
Arquivo criado: .eslintrc.json

Plugin:
- Necessário para analisar os hooks 
- [Instalação](https://www.npmjs.com/package/eslint-plugin-react-hooks)

```bash
yarn add eslint-plugin-react-hooks --dev
```

- Adicionando mais regras:
```json
{
  ...
  "react/prop-types": "off", //para não ter conflito com o typescript, pois o ts será o responsável pelos tipos
  "react/react-in-jsx-scope": "off", //ao utilizar o jsx, precisa importar o React. Só que no Next o React 
                                    //já é definido globalmente, então não preciso ficar importando, já  que ele tá
                                    //importado globalmente em todos os arquivos.
  "explicit-module-boundary-types": "off" //é quando precisamos tipar tipos implícitos, nesse caso o ts reconhece, infere
                                          //o tipo
}
```

- Detectando a versão do React
No arquivo _.eslintrc.json_ add:
```json
"settings": {
  "react": {
    "version": "detect"//ao rodar eslint ele não irá avisar que não tem a versão do react
		}
},
```

### Prettier
- O [prettier[(https://prettier.io/) serve para formatação visual do código:
  - Se tá usando aspas simples ou duplas
  - Espaçamento
  - ...

```bash
yarn add --dev --exact prettier
```
configurar o arquivo .prettierrc.json
```bash
echo {aqui terá as regras}> .prettierrc.json
```
Regras:
```json
{
  "trailingComma" : "none", //virgula no final da linha do obj
  "semi": false, //ponto e virgula 
  "singleQuote": true //aspas simples
}
```

Instalar o [eslint-plugin-prettier](https://github.com/prettier/eslint-plugin-prettier)

```bash
yarn add --dev eslint-plugin-prettier eslint-config-prettier
```

No arquivo .eslintrc.json no "extends" add "plugin:prettier/recommended"

```json
{
  "extends": ["plugin:prettier/recommended"]
}

```
Por ultimo, crie uma pasta na raiz .vsCode e o arquivo .settings.json
```json
{
  "editor.formarOnSave": false,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```