### For CNS

### Install Angular ESLint
 ```bash
ng add @angular-eslint/schematics
ng g @angular-eslint/schematics:convert-tslint-to-eslint
```

### Install Prettier and Prettier-ESLint dependencies
```bash
npm i prettier prettier-eslint eslint-config-prettier eslint-plugin-prettier -D
```

### ESLint configuration configura en tu en eslint.config.js -> rules @typescript-eslint/member-ordering
Filename: `eslint.config.js`
```bash
// https://github.com/angular-eslint/angular-eslint#notes-for-eslint-plugin-prettier-users
module.exports = tseslint.config(
  {
    files: ["**/*.ts"],
    extends: [
      eslint.configs.recommended,
      ...tseslint.configs.recommended,
      ...tseslint.configs.stylistic,
      ...angular.configs.tsRecommended,
    ],
    processor: angular.processInlineTemplates,
    rules: {
      "@angular-eslint/directive-selector": [
        "error",
        {
          type: "attribute",
          prefix: "app",
          style: "camelCase",
        },
      ],
      "@angular-eslint/component-selector": [
        "error",
        {
          type: "element",
          prefix: "app",
          style: "kebab-case",
        },
      ],
      "@typescript-eslint/member-ordering": [
        "error",
        {
          default: [
            "public-static-field",
            "protected-static-field",
            "private-static-field",
            "#private-static-field",
            "public-decorated-field",
            "protected-decorated-field",
            "private-decorated-field",
            "public-instance-field",
            "protected-instance-field",
            "private-instance-field",
            "#private-instance-field",
            "public-abstract-field",
            "protected-abstract-field",
            "public-field",
            "protected-field",
            "private-field",
            "#private-field",
            "static-field",
            "instance-field",
            "abstract-field",
            "decorated-field",
            "field",
            "static-initialization",
            "public-constructor",
            "protected-constructor",
            "private-constructor",
            "constructor",
            "signature",
            "call-signature",
            "public-static-accessor",
            "protected-static-accessor",
            "private-static-accessor",
            "#private-static-accessor",
            "public-decorated-accessor",
            "protected-decorated-accessor",
            "private-decorated-accessor",
            "public-instance-accessor",
            "protected-instance-accessor",
            "private-instance-accessor",
            "#private-instance-accessor",
            "public-abstract-accessor",
            "protected-abstract-accessor",
            "public-accessor",
            "protected-accessor",
            "private-accessor",
            "#private-accessor",
            "static-accessor",
            "instance-accessor",
            "abstract-accessor",
            "decorated-accessor",
            "accessor",
            "public-static-get",
            "protected-static-get",
            "private-static-get",
            "#private-static-get",
            "public-decorated-get",
            "protected-decorated-get",
            "private-decorated-get",
            "public-instance-get",
            "protected-instance-get",
            "private-instance-get",
            "#private-instance-get",
            "public-abstract-get",
            "protected-abstract-get",
            "public-get",
            "protected-get",
            "private-get",
            "#private-get",
            "static-get",
            "instance-get",
            "abstract-get",
            "decorated-get",
            "get",
            "public-static-set",
            "protected-static-set",
            "private-static-set",
            "#private-static-set",
            "public-decorated-set",
            "protected-decorated-set",
            "private-decorated-set",
            "public-instance-set",
            "protected-instance-set",
            "private-instance-set",
            "#private-instance-set",
            "public-abstract-set",
            "protected-abstract-set",
            "public-set",
            "protected-set",
            "private-set",
            "#private-set",
            "static-set",
            "instance-set",
            "abstract-set",
            "decorated-set",
            "set",
            "public-static-method",
            "protected-static-method",
            "private-static-method",
            "#private-static-method",
            "public-decorated-method",
            "protected-decorated-method",
            "private-decorated-method",
            "public-instance-method",
            "protected-instance-method",
            "private-instance-method",
            "#private-instance-method",
            "public-abstract-method",
            "protected-abstract-method",
            "public-method",
            "protected-method",
            "private-method",
            "#private-method",
            "static-method",
            "instance-method",
            "abstract-method",
            "decorated-method",
          ],
        },
      ],
    },
  },
  {
    files: ["**/*.html"],
    extends: [
      ...angular.configs.templateRecommended,
      ...angular.configs.templateAccessibility,
    ],
    rules: {},
  }
);
```


### Prettier Configuration crea el archivo '.prettierrc' y '.prettierignore' en la raiz de tu proyecto y agrega el siguiente contenido
Filename: `.prettierrc`
```json
{
  "semi": false,
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "all",
  "arrowParens": "avoid",
  "printWidth": 100,
  "endOfLine": "auto",
  "bracketSameLine": true
}
```

Filename: `.prettierignore`
```
dist
node_modules
```


### VSCode extensions recomendadas en tu vsc:
```
dbaeumer.vscode-eslint
esbenp.prettier-vscode
```

### Ajusta las siguientes configuracion en .vscode/settings.json file  (crtl + shift + p) para abrir el .vscode/settings.json:
```
{
  "[html]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.codeActionsOnSave": ["source.fixAll"],
    "editor.formatOnSave": false
  },
  "[typescript]": {
    "editor.defaultFormatter": "dbaeumer.vscode-eslint",
    "editor.codeActionsOnSave": ["source.fixAll"],
    "editor.formatOnSave": false
  },
},
"editor.suggest.snippetsPreventQuickSuggestions": false,
"editor.inlineSuggest.enabled": true
```

### Agregue el comando Fix Lint and Prettier errors en package.json
`"lint:fix": "ng lint --fix"`
