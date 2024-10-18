# MyPackage

## Run tasks

To build the library use:

```sh
npx nx build my-lib
```

See outputs under [`packages/my-lib/dist`](packages/my-lib/dist).

See the library functions under [`packages/my-lib/src/lib`](packages/my-lib/src/lib). If you write a new function, make sure to export it from the barrel file [`packages/my-lib/src/index.ts`](packages/my-lib/src/index.ts).

## Sharing Privately with Another Team

This library is designed to be shared privately without publishing to a public package registry. Follow these steps to integrate it into your project.

### See sample usage

See this repository for a sample usage of this library: [sample-usage-of](https://github.com/mandarini/sample-usage-of).

### Sharing the Library

Before installation, you need to share the entire `dist` (`packages/my-lib/dist`) folder with the other team.

Ensure that the receiving team has access to the complete `dist` folder, including all its contents:

Example:

```tree
dist/
├── README.md
├── index.cjs.d.ts
├── index.cjs.js
├── index.esm.d.ts
├── index.esm.js
├── package.json
└── src
    ├── index.d.ts
    ├── index.d.ts.map
    └── lib
        ├── my-lib.d.ts
        ├── my-lib.d.ts.map
        ├── other-function.d.ts
        └── other-function.d.ts.map
```

### Installation

Once the `dist` folder is shared, the other team can install the library. Choose the method that corresponds to your preferred package manager:

#### npm

1. Add the library to your `package.json`:

   ```json
   "dependencies": {
     "my-lib": "file:/absolute/path/to/shared/dist"
   }
   ```

   Or use a relative path:

   ```json
   "dependencies": {
     "my-lib": "file:../relative/path/to/shared/dist"
   }
   ```

2. Run the install command:

   ```bash
   npm install
   ```

Alternatively, you can install directly from the command line:

```bash
npm install /path/to/shared/dist
```

#### Yarn

1. Add the library to your `package.json` as shown in the npm section, or

2. Run the install command:

   ```bash
   yarn add file:/path/to/shared/dist
   ```

#### pnpm

1. Add the library to your `package.json` as shown in the npm section, or

2. Run the install command:

   ```bash
   pnpm add file:/path/to/shared/dist
   ```

### Usage

After installation, you can import and use the library in your project:

For TypeScript or ES6+ projects:

```typescript
import { someFunction } from 'my-lib';

someFunction();
```

For CommonJS environments:

```javascript
const { someFunction } = require('my-lib');

someFunction();
```

### If you're using Typescript!!!!

Make sure to add the following to your `tsconfig.json` or `tsconfig.lib.json` file:

```json
  "compilerOptions": {
    ...
    "allowJs": true,
    "esModuleInterop": true
    ...
  }
```

### TypeScript Support

This library includes TypeScript declarations. TypeScript users will automatically get type definitions and autocompletion for the library's functions and classes.

### Updating

When a new version is available:

1. Share the updated `dist` folder with the other team
2. They should replace their existing copy with the new version
3. Run the installation command again to update the package
