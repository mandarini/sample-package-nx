# My Library

This is the readme for my library.

## Installation

Once the `dist` folder is shared, the other team can install the library. Choose the method that corresponds to your preferred package manager:

### npm

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

### Yarn

1. Add the library to your `package.json` as shown in the npm section, or

2. Run the install command:

   ```bash
   yarn add file:/path/to/shared/dist
   ```

### pnpm

1. Add the library to your `package.json` as shown in the npm section, or

2. Run the install command:

   ```bash
   pnpm add file:/path/to/shared/dist
   ```

## Usage

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

## TypeScript Support

This library includes TypeScript declarations. TypeScript users will automatically get type definitions and autocompletion for the library's functions and classes.

## Updating

When a new version is available:

1. Share the updated `dist` folder with the other team
2. They should replace their existing copy with the new version
3. Run the installation command again to update the package
