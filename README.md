# setup-conventional-commits

#### Este documento visa descrever as configurações necessárias para se realizar **commits** semânticos e padronizadoss de uma maneira contextualizada e simples utilizando três libs: [commitlint](https://github.com/conventional-changelog/commitlint), [commitizen/cli](https://github.com/commitizen/cz-cli) e a [husky](https://github.com/typicode/husky).

## Para saber mais sobre commits [semânticos](https://commitlint.js.org/#/).

A primeira coisa a se fazer após a construção da estrutura básica do seu projeto é inicializar o git:
```
git init
```
Após isto entra a nossa tão sonhada configuração para os commits semânticos de forma simples.

## Instalando o commitlint

### Gerenciador npm
```
npm install --save-dev @commitlint/config-conventional @commitlint/cli
```
### Gerenciador yarn
```
yarn add @commitlint/config-conventional @commitlint/cli -D
```

## Configurando commitlint para uso padrão dos conventionals commits
```
echo "module.exports = {extends: ['@commitlint/config-conventional']}" >> commitlint.config.js
```

## Instalando e configurando o Husky em seu projeto

### Gerenciador npm
```
npm install husky --save-dev 
```
### Gerenciador yarn
```
yarn add -D husky
```

Depois disto, você pode tanto criar o arquivo .huskyrc na raiz do projeto ou adicionar ao package.json o seguinte código:
```
"husky": {
    "hooks": {
      "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
    }
  }
```

Isso já bastaria para conseguirmos criar os nossos commits semânticos. Contudo, para deixar ainda mais completa essa config, iremos utilizar o commitizen/cli para deixar mais contextualizada e visual.

## Istalando e configurando o commitzen/cli

npm install commitizen -g

### Gerenciador npm
```
npm install commitizen -g

```
### Gerenciador yarn
```
yarn add commitizen -D
```

Em seguida: 

### Gerenciador npm
```
commitizen init cz-conventional-changelog --save-dev --save-exact
```
### Gerenciador yarn
```
commitizen init cz-conventional-changelog --yarn --dev --exact
```

Em seguida adicionar a seguinte linha no seu .huskyrc ou package.json no escopo do husky:
```
"prepare-commit-msg": "exec < /dev/tty && git cz --hook || true",
```
Ficando desta forma no arquivo:

```
 "husky": {
    "hooks": {
      "prepare-commit-msg": "exec < /dev/tty && git cz --hook || true",
      "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
    }
  }
 ```


# Referências

[Padronizando mensagens de commit do Git | Code/Drops #12](https://youtu.be/erInHkjxkL8)



@Italo Rayone



