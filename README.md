# Eslint + Prettier + VScode

This is a quick way to check your Javascript code and make it pretty too.

It uses Eslint to verify the code, but uses Prettier to format it, and brings the AirBNB Javascript style guide to make the code universally accepted.

You don't have to follow any of the rules and suggestions, but this is a good starting point, so you don't have to reinvent the wheel.

This is a a good tutorial on how to create your own file if you don't want to use this "standard" settings:
https://blog.echobind.com/integrating-prettier-eslint-airbnb-style-guide-in-vscode-47f07b5d7d6a

## The starting point

Let's assume you already have `npm` and `npx` installed. You will need these to complete your linter.

1. Using terminal or your favorite command line program, create a file `package.json` in the root of your project folder. An easy way to do that is to user the command `npm init`.

2. Download this repository to your computer.

3. Copy and paste the contents of the repository `package.json` into the `package.json` in the project folder you just created.

## The easy way

Now you have two options: The easy way is to simply run `npm i` in the directory where your `package.json` lives. npm will read the dependenciaes and install everything you need.

## The hard way

The hard way is to run the following commands on the terminal. You are installing all dependencies one by one. There is no difference here, but this method gives you the opportunity to know what you are installing and leave things out, or add things in. Your call.

```
npx install-peerdeps --dev eslint-config-airbnb
```

```
npm install -D eslint@5.6.0 prettier --save-dev
```

```
npm install -D eslint-config-airbnb eslint-plugin-jsx-a11y eslint-plugin-import eslint-plugin-react eslint-plugin-html babel-eslint --save-dev
```

```
npm install -D eslint-config-prettier eslint-plugin-prettier eslint-plugin-flowtype@2.50.3 eslint-config-react-app --save
```

```
npm install eslint-plugin-react-hooks@latest --save-dev
```

```
touch .eslintrc.json
```

```
echo '{
  "extends": [
    "airbnb", "prettier", "prettier/react", "react-app", "plugin:prettier/recommended"],
  "parser": "babel-eslint",
  "env": {
    "browser": true,
    "node": true,
    "jquery": true,
    "jest": true
  },
  "rules": {
    "prettier/prettier": ["error"],
    "jsx-a11y/href-no-hash": [0],
    "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }],
    "react-hooks/rules-of-hooks": "error",
    "react-hooks/exhaustive-deps": "warn",
    "prefer-const": ["error", { "destructuring": "all" }],
    "no-unused-expressions": [ 2, { "allowTaggedTemplates": true }],
    "import/prefer-default-export": 0,
    "space-before-function-paren": 0,
    "comma-dangle": 0
  },
  "plugins": [
    "html",
    "prettier",
    "react-hooks"
  ]
}' >> .eslintrc.json
```

```
touch .prettierrc
```

```
echo '{
  "printWidth": 100,
  "singleQuote": true
}' >> .prettierrc
```

Pay close attention to two files `.eslintrc.json` and `.prettierrc`. Notice that they start with a period, not a typo here This means they are invisible and reserved for the system. But we don't care about being left out. VSCode will see them, and you can modify them to fit your needs. This is where you change your rules that Eslint and Prettier will obey. Notice that they require a json format, so no single quotes, no skipping commas, etc.

I use React a lot, so I have some React and React Hooks rules, but feel free to modify them.

## VSCode Extensions

Now you have have it all running. You have to download and install Prettier and Eslint exentensions.

Click on the squareish icon on the Activity bar. Search and install ESLint, by Dick Bauemer and Prettier by Esben Petersen. After installing you might have to enable them in your editor.

![ESLint](/images/eslint.png)

and ...

![Prettier](/images/prettier.png)

## Running on command line

Use `npm run eslint` to verify your code or `npr run eslint-fix` to verify and correct your code.

## Running on VSCode

One more step: Under the VSCode User Settings, change the following line:

```
"editor.formatOnSave": true
```

Voila, now when you save your file, it is being error-corrected and prettiefied. Life doesn't get easier than that. Save this instructions and use them on all your future projects.
