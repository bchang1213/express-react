1. Using terminal, `mkdir` your project name and then once `cd`-ing into that project folder, run `npm init`.

2. Press enter through the `npm init` prompts and give the relevant info where you see fit.

3. Using your favorite text editor, open up the package.json file and let’s create our development environment command:
Edit your package.json's script object as such:
```
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "clean": "rm -rf ./dist",
    "build:client": "webpack --mode production --config webpack.prod.js",
    "build:server": "babel -d ./dist/server ./server -s",
    "build": "npm run clean && npm run build:server && npm run build:client",
    "start:prod": "npm run build && DEBUG='express:*' NODE_ENV='production' node ./dist/server/index.js",
    "dev:server": "nodemon --exec babel-node ./server/index.js",
    "dev:client": "webpack-dev-server --mode development --open --config webpack.dev.js",
    "start": "concurrently --kill-others-on-fail \"npm run dev:server\" \"npm run dev:client\""
  },
```
4. Based on the modules utilized in those 'commands' above, we will now begin to form this application by importing those modules into the application package.json and project's automatically created `npm_modules` folder.

5. `npm import express cors body-parser dotenv compression aws-sdk cookie-parser express-winston helmet http-status fg-loadcss joi multer morgan multer-s3 winston redis`

6. Inside your project root folder, create `server/config`, `server/controllers`, `server/routes`. Create `server/index.js`.