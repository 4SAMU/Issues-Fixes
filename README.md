# Issues and Fixes

# .gitignore

## unable to ignore files even after adding into **`.gitigore`** file

There could be several reasons why your `.gitignore` file is not ignoring certain files.
Here are a few possibilities:
-The files were already added to your repository before you added them to your `.gitignore` file. Adding files to `.gitignore` does not remove them from the repository. To remove them, you need to run git rm --cached <file> for each file.
-You may have specified the wrong path or filename in your `.gitignore` file. Double-check that the paths and filenames are correct, and that they match the files you want to ignore.
-Git may be ignoring your `.gitignore `file. Check that your `.gitignore` file is in the root of your repository and that its filename is spelled correctly. If Git is still ignoring your `.gitignore` file, you can force it to read the file by running git add -f `.gitignore`.
-The files you want to ignore may already be tracked by Git. In this case, you need to remove them from the repository and commit the changes. You can do this with the following commands:

```shell
git rm -r --cached .
git add .
git commit -m "Removed files from repository"

```

# Babel compiling & npm publishing

## JS

**`example you have this folder u want to compile:`**

```shell
MyModal
├── src
│   └── Modal.js
├── package.json
└── ...
```

First install with the command below

```shell
npm i @babel/cli @babel/core @babel/preset-env @babel/preset-react
```

### In the `package.json` add the following

```json
"devDependencies": {
    "@babel/cli": "^7.21.5",
    "@babel/core": "^7.21.8",
    "@babel/preset-env": "^7.21.5",
    "@babel/preset-react": "^7.18.6",
  },
"scripts": {
"build": "babel src --out-dir lib"
},
"babel": {
    "presets": [
      "@babel/preset-env",
      "@babel/preset-react",
      "@babel/preset-typescript"
    ]
  },

```

## TS

**`example you have this folder u want to compile:`**

```shell
MyModal
├── src
│   └── Modal.tsx
├── package.json
└── ...
```

First install with the command below

```shell
npm i @babel/cli @babel/core @babel/preset-env @babel/preset-react @babel/preset-typescript
```

### In the `package.json` add the following

```json
"devDependencies": {
    "@babel/cli": "^7.21.5",
    "@babel/core": "^7.21.8",
    "@babel/preset-env": "^7.21.5",
    "@babel/preset-react": "^7.18.6",
    "@babel/preset-typescript": "^7.21.5"
  },
"scripts": {
"build": "babel src --out-dir lib --extensions .ts,.tsx"
},
"babel": {
    "presets": [
      "@babel/preset-env",
      "@babel/preset-react",
      "@babel/preset-typescript"
    ]
  },

```

## After compiling run:

```shell
npm run build  #u will get a lib folder with all the compiled files
```

## Then to publish your package:

```shell
npm login #first authenticate yourself in the npm registry then:
npm publish
```

## Reloading Vscode

in vscode:

- `Ctrl+Shift+P`
- type `Reload`
- click `Developer: Reload Window`

