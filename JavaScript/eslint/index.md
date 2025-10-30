

Запуск встроенный ESLint внутри standard

Не устанавливайте eslint, потому что standard уже включает нужную версию ESLint внутри себя.

```bash
npm install standard --save-dev
```

Добавляем в package.json

```
  "scripts": {
    "lint": "standard",
    "lint:fix": "standard --fix"
  },
```

Команды запуска

```bash
  npm run lint
  npm run lint:fix
```

Так же для vscode существует плагин StandardJS - JavaScript Standard Style