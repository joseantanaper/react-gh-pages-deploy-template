# React GitHub Pages Deploy Template

1. Create an empty repository.
2. Create a new branch "development" and set it as Default branch.
3. Create a new React App.

   ```sh
   npm create vite@latest -- --template react-gh-pages-deploy-template
   ```

4. Add "base" to **vite.config.ts**:

   ```json
   base: "",
   ```

5. Install **gh-pages** as a development dependency.

   ```sh
   npm install gh-pages --save-dev
   ```

6. Edit **package.json**

   - Add "homepage" property:

     ```json
     "homepage": "https://{**USERNAME**}.github.io/react-gh-pages-deploy-template"
     ```

   - Add deployment scripts to **package.json**

     ```json
     "scripts": {
      "predeploy": "npm run build",
      "deploy": "gh-pages -d build",
     }
     ```

7. Add a "remote" that points to the GitHub repository (???).

   ```sh
   git remote add origin https://github.com/{**USERNAME**}/react-gh-pages-deploy-template.git
   ```

   ??? error: remote origin already exists.

8. Add

---

# React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type aware lint rules:

- Configure the top-level `parserOptions` property like this:

```js
export default tseslint.config({
  languageOptions: {
    // other options...
    parserOptions: {
      project: ["./tsconfig.node.json", "./tsconfig.app.json"],
      tsconfigRootDir: import.meta.dirname,
    },
  },
});
```

- Replace `tseslint.configs.recommended` to `tseslint.configs.recommendedTypeChecked` or `tseslint.configs.strictTypeChecked`
- Optionally add `...tseslint.configs.stylisticTypeChecked`
- Install [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) and update the config:

```js
// eslint.config.js
import react from "eslint-plugin-react";

export default tseslint.config({
  // Set the react version
  settings: { react: { version: "18.3" } },
  plugins: {
    // Add the react plugin
    react,
  },
  rules: {
    // other rules...
    // Enable its recommended rules
    ...react.configs.recommended.rules,
    ...react.configs["jsx-runtime"].rules,
  },
});
```
