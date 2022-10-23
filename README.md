# Next Starter

Tech Stack:

[Next.js](https://nextjs.org/) | [TypeScript](https://www.typescriptlang.org/) | [ESLint](https://eslint.org/) | [Prettier](https://prettier.io/) | [Tailwind CSS](https://tailwindcss.com/) | [pnpm]()

## How to re-create it

1.  You can create a TypeScript project with `create-next-app` using the `--ts`, `--typescript` flag. [Instructions here](https://nextjs.org/docs/basic-features/typescript)

    ```
    pnpm create next-app --ts next-starter
    ```

1.  Install Tailwind. [Instructions here](https://tailwindcss.com/docs/guides/nextjs)

    - Remember to use `pnpm` instead of `npm`

    - Add automatic tailwind class sorting with prettier. [Instructions here](https://tailwindcss.com/blog/automatic-class-sorting-with-prettier)

      ```
      pnpm install -D prettier prettier-plugin-tailwindcss
      ```

1.  Prettier configuration (`.prettierrc`)

    - Trailing commas improve developer experience. [See why](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Trailing_commas)

    - Use double quotes to be consistent with HTML

    ```js
    {
      "useTabs": true,
      "singleQuote": false,
      "trailingComma": "es5",
      "printWidth": 100
    }
    ```

1.  ESLint configuration

    - Extend these extra rulesets
    - Add `parserOptions.project` and `ignorePatterns` to fix some bugs

      ```js
      // .eslintrc.cjs

      module.exports = {
         ...
         extends: [
         "eslint:recommended",
         "plugin:@typescript-eslint/recommended",
         "plugin:@typescript-eslint/strict",
         "plugin:@typescript-eslint/recommended-requiring-type-checking",
         "prettier",
         ],
         parserOptions: {
            sourceType: "module",
            ecmaVersion: 2020,
            project: "./tsconfig.json",
         },
         ignorePatterns: ["*.cjs", "playwright.config.ts", "svelte.config.js"],
      }
      ```

1.  Add Husky and lint-staged

    - Instructions to install husky [here](https://typicode.github.io/husky/#/?id=install)

    ```bash
    pnpm i -D lint-staged husky
    pnpm dlx husky install
    pnpm dlx husky add .husky/pre-commit "pnpm dlx lint-staged"
    ```

    - Add lint-staged configuration

    ```json
    // .lintstagedrc.json

    {
    	"**/*.{html,js,svelte,ts}": ["pnpm lint:fix", "pnpm lint", "pnpm check"]
    }
    ```

1.  Add vscode settings & extensions

    ```json
    // .vscode/settings.json

    {
    	"editor.codeActionsOnSave": [
    		"source.addMissingImports",
    		"source.fixAll",
    		"source.organizeImports"
    	],
    	"editor.defaultFormatter": "esbenp.prettier-vscode",
    	"editor.foldingImportsByDefault": true,
    	"editor.formatOnSave": true
    }
    ```

    ```json
    // .vscode/extensions.json

    {
    	"recommendations": [
    		"svelte.svelte-vscode",
    		"bradlc.vscode-tailwindcss",
    		"dbaeumer.vscode-eslint",
    		"esbenp.prettier-vscode"
    	]
    }
    ```

1.  Add common utils

    ```
    src/
    ├ lib/
    ├ utils/
    │ └ classes.ts
    ```
