# Next Starter

Tech Stack:

[Next.js](https://nextjs.org/) | [TypeScript](https://www.typescriptlang.org/) | [ESLint](https://eslint.org/) | [Prettier](https://prettier.io/) | [Tailwind CSS](https://tailwindcss.com/) | [pnpm]()

## How to re-create it

1.  You can create a TypeScript project with `create-next-app` using the `--ts`, `--typescript` flag. [Instructions here.](https://nextjs.org/docs/basic-features/typescript)

    ```shell
    pnpm create next-app --ts next-starter
    ```

1.  Install Tailwind. [Instructions here](https://tailwindcss.com/docs/guides/nextjs)

    Remember to use `pnpm` instead of `npm`

    Add automatic tailwind class sorting with prettier. [Instructions here](https://tailwindcss.com/blog/automatic-class-sorting-with-prettier)

    ```shell
    pnpm i -D prettier prettier-plugin-tailwindcss
    ```

1.  Configure Prettier. [See configuration.](./.prettierrc)

    Install `eslint-config-prettier`. [See more](https://prettier.io/docs/en/integrating-with-linters.html)

    ```bash
    npm install --save-dev eslint-config-prettier
    ```

    configuration (`.prettierrc`)

    Notes:

    Trailing commas improve developer experience. [See why](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Trailing_commas)

1.  Configure ESLint. [See configuration.](./.eslintrc.json)

    Install ESLint Plugin TypeScript. [Instructions here.](https://www.npmjs.com/package/@typescript-eslint/eslint-plugin)

    ```bash
    pnpm i @typescript-eslint/eslint-plugin @typescript-eslint/parser`
    ```

1.  Add Husky and lint-staged

    Install husky. [Instructions here.](https://typicode.github.io/husky/#/?id=install)

    ```bash
    pnpm i -D lint-staged husky
    pnpm dlx husky install
    pnpm dlx husky add .husky/pre-commit "pnpm dlx lint-staged"
    ```

    -   Add lint-staged configuration

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
