# Instalar Vercel CLI

```
npm i -g vercel
```

# Iniciar tu proyecto

```
mkdir my-api
cd my-api
npm init private
npm install @vercel/node
```

# Instalar typescript y adicionar tsconfig.json

```
npm install --save-dev typescript
```

# Luego adicionar el tsconfig.json:

```
curl -o tsconfig.json https://gist.githubusercontent.com/vdelacou/1954a25d720f702b4af011ba2773001b/raw/tsconfig.json
```

# Es hora de codificar nuestra función!

Vercel considerará todos los archivos en la carpeta api como una función para implementar.
Cree una carpeta api y cree un archivo user.ts

```
mkdir api
cd api
```

# Crear user.ts

y copia en user.ts el código a continuación

```
import { VercelRequest, VercelResponse } from '@vercel/node';
export default (req: VercelRequest, res: VercelResponse): void => {
  res.json({ name: 'Johne', email: 'john@example.com' });
};
```

# Implementar nuestra función

Inicie sesión en Vercel, necesitará su correo electrónico que puede encontrar aquí: https://vercel.com/account

```
vercel login
```

# Siga las instrucciones para iniciar sesión y luego ejecute el comando

```
vercel
```

Entonces, su API ahora está implementada en varias ubicaciones y se puede llamar con la $ URL que se muestra en su consola.

```
curl --request GET $URL/api/user
```

# Probar y desarrollar nuestra función a nivel local

Solo lanzar

```
vercel dev
```

Y luego puede probar localmente y recargar en vivo durante el desarrollo

```
curl --request GET http://localhost:3000/api/user
```

# Add Linter

```
curl -o .gitignore https://gist.githubusercontent.com/vdelacou/1954a25d720f702b4af011ba2773001b/raw/.gitignore
curl -o .prettierrc https://gist.githubusercontent.com/vdelacou/58484f1c11af70aaa457f4e5c289e893/raw/.prettierrc
mkdir .vscode
curl -o .vscode/extensions.json https://gist.githubusercontent.com/vdelacou/c5f3fd74c5e836706c0adaeb0d383bd0/raw/extensions.json
curl -o .vscode/settings.json https://gist.githubusercontent.com/vdelacou/c5f3fd74c5e836706c0adaeb0d383bd0/raw/settings.json
curl -o .editorconfig https://gist.githubusercontent.com/vdelacou/58484f1c11af70aaa457f4e5c289e893/raw/.editorconfig
npm install @typescript-eslint/eslint-plugin @typescript-eslint/parser --save-dev
npm install eslint-config-airbnb-typescript --save-dev
npx install-peerdeps --dev eslint-plugin-prettier
npm install eslint-config-prettier --save-dev
curl -o .eslintrc.json https://gist.githubusercontent.com/vdelacou/1954a25d720f702b4af011ba2773001b/raw/.eslintrc.json
```

# Proyecto a producción

Y luego puede llevar a producción el proyecto correr este comando.

```
vercel --prod
```

y luego ver en consola la $URL

```
curl --request GET $URL/api/user
```
