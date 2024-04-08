## Для чего
Что бы несколько разработчиков могли работать с одним проектом с использованием одних и тех же настроек Prettier (Стили форматирования кода) и писали максимально в одном стиле.

## Что для этого надо
#### Начинаем с нуля
В проекте в VSCode в папке с проектом: Файл → Сохранить рабочую область как .. / File →  Save Workspace As.. 

Сохраняем файл в корень проекта и копируем туда код ниже.

```json
{
  "folders": [
    {
      "path": "."
    }
  ],
  "settings": {
    "svg.preview.background": "transparent",
    "compile-hero.disable-compile-files-on-did-save-code": false,
    "editor.formatOnSave": true,
    "editor.formatOnPaste": true,
    "editor.insertSpaces": true,
    "editor.detectIndentation": false,
    "editor.wordWrapColumn": 100,
    "editor.wordWrap": "bounded",
    "editor.tabSize": 2,
    "[typescript]": {
      "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[javascript]": {
      "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[vue]": {
      "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[scss]": {
      "editor.defaultFormatter": "sibiraj-s.vscode-scss-formatter"
    },
    "[typescriptreact]": {
      "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[editorconfig]": {
      "editor.defaultFormatter": "EditorConfig.EditorConfig"
    },
    "[yaml]": {
      "editor.defaultFormatter": "redhat.vscode-yaml"
    },
    "[dockerfile]": {
      "editor.defaultFormatter": "ms-azuretools.vscode-docker"
    },
    "liveSassCompile.settings.watchOnLaunch": true,
    "liveSassCompile.settings.showOutputWindowOn": "None",
    "liveSassCompile.settings.formats": [
      {
        "format": "expanded",
        "extensionName": ".css",
        "savePath": "~/../css"
      }
    ],
    "liveSassCompile.settings.autoprefix": []
  },
  "extensions": {
    "recommendations": [
      "esbenp.prettier-vscode",
      "willjleong.nuxt-typescript-snippets",
      "syler.sass-indented",
      "glenn2223.live-sass",
      "sibiraj-s.vscode-scss-formatter",
      "Vue.volar",
      "Zignd.html-css-class-completion",
      "EditorConfig.EditorConfig",
      "redhat.vscode-yaml",
      "ms-azuretools.vscode-docker",
      "formulahendry.auto-rename-tag"
    ]
  }
}
```

Так же, создаем файлы в корне проекта:

**.editorconfig**

```js
root = true
 
# Unix-style newlines with a newline ending every file
[*]
end_of_line = lf
insert_final_newline = true
indent_style = space
indent_size = 2
```
**.prettierignore**
```js
node_modules
*.log*
*/.nuxt
**/.nuxt
**/.nitro
**/.output
**/.cache
**/.output
**/.env
**/dist
```

**.prettierrc**

```json
{
  "trailingComma": "es5",
  "tabWidth": 2,
  "semi": false,
  "singleQuote": true,
  "useTabs": false
}
```

в папке с фалом **package.json** устанавливаем пакеты:
```shell
yarn add --dev eslint
yarn add --dev prettier eslint-config-prettier eslint-plugin-prettier
yarn add --dev typescript @typescript-eslint/parser @nuxtjs/eslint-config-typescript
```

создаем файл:
**.eslintrc.cjs**

```cjs
module.exports = {
  root: true,
  env: {
    browser: true,
    node: true,
  },
  parser: 'vue-eslint-parser',
  parserOptions: {
    parser: '@typescript-eslint/parser',
  },
  extends: ['@nuxtjs/eslint-config-typescript', 'plugin:prettier/recommended'],
  plugins: [],
  rules: {
    'vue/no-multiple-template-root': 'off',
    'vue/no-unused-vars': 'off',
    'no-unused-vars': 'off',
    '@typescript-eslint/no-unused-vars': 'off',
    'no-console': 'off',
  },
}
```

в файле **package.json**
в блок Scripts добавляем

```json
"scripts": {
    ...
    "lint:js": "eslint --ext \".ts,.vue\" --ignore-path .gitignore .",
    "lint:prettier": "prettier --check .",
    "lint": "yarn lint:js && yarn lint:prettier",
    "lintfix": "prettier --write --list-different . && yarn lint:js --fix"
},
```