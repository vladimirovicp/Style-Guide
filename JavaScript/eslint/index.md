

```bash
npm install --save-dev  eslint
npm install standard --save-dev
```

Явно обновите standard до v17+
```bash
npm install --save-dev standard@17
```

Создать файл .eslint.config.js

```
// eslint.config.js
import standard from 'standard/eslint-config.mjs';

export default [
  ...standard,
  {
    languageOptions: {
      ecmaVersion: 2024,
      sourceType: 'script', // или 'module', если используете ES modules
    },
  },
];
```