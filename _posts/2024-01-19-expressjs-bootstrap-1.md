---
layout: single
title:  "ExpressJS 2024: A Step-by-Step Guide for Building Your Backend - Part 1 of 4"
date:   2024-01-19 08:00:00 +0100
categories: coding 
tagline: "The ultimate guide on setting up an ExpressJS project in 2024. This guide will walk you through the initial setup of an ExpressJS project, integrating TypeScript, and implementing essential tools like ESLint and Prettier to ensure your code is clean, maintainable, and error-free."
header:
  overlay_image: /assets/images/posts/ExpressJS_2024.webp
  overlay_filter: 0.6 # same as adding an opacity of 0.5 to a black background
  teaser: /assets/images/posts/ExpressJS_2024.webp
---

Welcome to the ultimate guide on setting up an ExpressJS project in 2024. As the world of web development constantly evolves, staying updated with best practices and efficient project setups becomes crucial. This guide is designed to walk you through the initial setup of an ExpressJS project, integrating TypeScript, and implementing essential tools like ESLint and Prettier to ensure your code is clean, maintainable, and error-free. Whether you’re a seasoned developer or just starting out, this guide aims to provide clear, step-by-step instructions to help you create a robust ExpressJS application. Plus, to make things even easier, you can fork a fully set up and ready-to-go repository at [https://github.com/robiwells/bootstrap-express-ts-backend](https://github.com/robiwells/bootstrap-express-ts-backend). 

# Prerequisites

- [npm installed](https://www.npmjs.com)
- [node installed](https://nodejs.org/en)


# Initial setup

The initial setup of any project is foundational, impacting its future development, scalability, and ease of maintenance:

1. Create a folder called ```server```

    Keeping your server code in a dedicated directory is a best practice for organisation and helps in maintaining a clean project structure.

2. ```npm init```

    The command npm init is a crucial first step in setting up a new Node.js project, and it’s particularly essential when working with frameworks like ExpressJS. When you run this command in your project directory, it kick-starts the creation of a package.json file, which can be considered the blueprint of your project. This file holds important metadata about your project, such as its name, version, description, and dependencies. 

    You will be prompted to enter details like the project’s name, version, description, entry point (usually index.js), test command, repository link, keywords, author, and license. You can either fill in these details or press enter to accept the default values provided by npm. 

3. ```npm install express```

    This command downloads the Express framework and integrates it into your project as a dependency. This integration is reflected in your project's package.json file under the dependencies section. 


# Adding TypeScript

TypeScript has gained immense popularity in the development community for its ability to improve code quality, readability, and maintainability. We'll walk through the process of installing TypeScript and its dependencies, setting up the necessary configuration files, and organizing your project to take full advantage of TypeScript's features. 


1. ```npm install -D typescript ts-node @types/express @types/node```

	  This command installs TypeScript and its essential dependencies. TypeScript enhances JavaScript by adding static types, making your code easier to read and ts-node allows you to run TypeScript files directly. @types/express and @types/node are TypeScript declaration files for Express and Node.js, respectively, providing type definitions and enabling IntelliSense in your IDE.


2. ```npx tsc --init```
    
    This command generates a tsconfig.json file in your project, which is the TypeScript configuration file. This file specifies compiler options for your TypeScript project, allowing you to customise how your TypeScript code is compiled into JavaScript.


3. Open **tsconfig.json** and modify to match below:

    ```
    { 
      “compilerOptions”: { 
        “target”: “es6”, 
        “module”: “commonjs”, 
        “outDir”: “./dist”, 
        “strict”: true,
        “esModuleInterop”: true, 
        “skipLibCheck”: true, 
        “forceConsistentCasingInFileNames”: true 
      }, 
      “include”: [“src/**/*.ts”], 
      “exclude”: [“node_modules”]
    } 
    ```
    

    After creating the tsconfig.json file, customise its settings to match your project requirements. This includes setting the target JavaScript version, the module system, strict type-checking options, and more. One important setting is outDir, which specifies where the compiled JavaScript files will be placed. It’s recommended to set this to ./dist to keep your project organised.


4. Create **src** folder in your root folder. The will hold your source files.
5. Create **index.ts** file in your src folder:  
    ```
    import express, { Request, Response } from ‘express’; 
    const app = express();
    const port = process.env.PORT || 3000;

    app.get(‘/‘, (req: Request, res: Response) => {
        res.send(‘Hello there!’);
    });

    app.use((err: Error, req: Request, res: Response, _next
    : NextFunction) => {
        console.error(err.stack);
        res.status(500).send(‘Something went wrong’);
    });

    app.listen(port, () => {
        console.log(`Server running at http://localhost:${port}`);
    });
    ```

    This is the entry point of your application. It defines basic functionality, such as routing and error handling. The underscore before next in the error-handling middleware indicates to ESLint and other developers that this parameter is intentionally unused, which is a common pattern in Express applications.

6. Update **package.json** scripts section:

    ```
        “scripts”: { 
          “start”: “ts-node src/index.ts”, 
          “build”: “rm -rf dist/* && tsc”, 
          “serve”: “node dist/index.js” 
        } 
    ```

    Modify the scripts section of your package.json file to include commands for starting the development server, building the TypeScript files, and serving the compiled JavaScript files. This setup enhances the development experience by streamlining these common tasks.

# Loading Environment Variables from a File

In the development of web applications, particularly when using frameworks like Express.js, managing configuration settings securely and efficiently is paramount. By utilising the dotenv package, we can securely manage sensitive information such as database credentials, API keys, and other configuration settings. This approach not only enhances the security of our application by keeping sensitive data out of our codebase but also provides the flexibility to change settings without altering the code.

1. ```npm install dotenv```
		Dotenv is a zero-dependency module that loads environment variables from a .env file into process.env, making it easy to manage configuration settings. This step ensures that sensitive information like database passwords or API keys are not hardcoded into your application.

2.  Create a **.env** file in the project Root and add these variables:

    ```
    Copy codePORT=3000 
    APP_ENV=development 
    ```

		This file is where you’ll define your environment variables. For now, you can set the port number and the application environment.

    >  It’s crucial to add .env to your .gitignore file to prevent accidentally pushing sensitive data to your version control system.

3. Modify **index.ts** to use dotenv:

    ```
    import express, { Request, Response, NextFunction } from ‘express’;
    import dotenv from ‘dotenv’; // Add this
    dotenv.config(); // And this 

    // The rest of your Express server code… 
    ```

		In your index.ts file, import dotenv and invoke dotenv.config() at the top. This will load the environment variables defined in your .env file and make them accessible through process.env. 

Once you’ve set up dotenv, you can access the environment variables anywhere in your application using ```process.env.VARIABLE_NAME```. For example, ```process.env.PORT``` will give you the port number set in your .env file.    


# Integrate ESLint and Prettier

As our applications grow in complexity, ensuring code quality and consistency becomes a challenge. This is where tools like ESLint and Prettier come into play, transforming the way we write and maintain our code. 

ESLint is a powerful tool for identifying and fixing problems in JavaScript code, making it an indispensable asset for developers. When combined with TypeScript, it ensures your code not only follows best practices but also adheres to type safety. Prettier, on the other hand, takes care of formatting your code in a consistent style, taking the burden off of us to maintain a uniform codebase manually.

## ESLint Setup

1. Run ```npm install —D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin```

		This command installs ESLint along with the TypeScript parser and plugin. ESLint is a tool for identifying and reporting on patterns in JavaScript, with plugins available for TypeScript.

2.  ```npm install —save-dev eslint-plugin-node eslint-plugin-mocha eslint-plugin-require eslint-config-prettier eslint-plugin-import eslint-import-resolver-typescript```

		These additional packages enhance ESLint’s functionality with specific rules and integrations, like support for Node.js, Mocha, import statements, and compatibility with Prettier.

3. Create an **.eslintrc** file in the root folder and add:

    ```
    {
      “root”:true,
      “parser”:”@typescript-eslint/parser”,
      “parserOptions”:{
          “tsconfigRootDir”:”“./“”,
          “project”:[
            “./tsconfig.json”
          ]
      },
      “plugins”:[
          “@typescript-eslint”,
          “eslint-plugin-node”,
          “mocha”,
          “eslint-plugin-require”,
          “import”
      ],
      “extends”:[
          ““eslint”:”recommended””,
          ““plugin”:”@typescript-eslint/eslint-recommended””,
          ““plugin”:”@typescript-eslint/recommended””,
          ““plugin”:”node/recommended””,
          “prettier”
      ],
      “rules”:{
          “no-throw-literal”:”off”,
          “@typescript-eslint/no-throw-literal”:”error”,
          “node/no-missing-import”:”off”,
          “@typescript-eslint/no-unused-vars”:[
            “warn”,
            {
                “argsIgnorePattern”:”^_”
            }
          ],
          “node/no-unsupported-features/es-syntax”:[
            “error”,
            {
                “version”:“>=13.0.0”,
                “ignores”:[
                  “modules”
                ]
            }
          ],
          “node/no-unpublished-import”:[
            “error”,
            {
                “allowModules”:[
                  “module-alias”
                ]
            }
          ],
          “import/no-unresolved”:”error”
      },
      “settings”:{
          “import/parsers”:{
            “@typescript-eslint/parser”:[
                “.ts”,
                “.tsx”
            ]
          },
          “import/resolver”:{
            “typescript”:{
                “alwaysTryTypes”:true
            }
          }
      }
    }
    ```

    This configuration sets up ESLint for a TypeScript project. It includes parser settings, plugins, and extends various recommended ESLint configurations. The rules section customises specific linting rules, and settings help resolve module imports and TypeScript files.

    - root**:** Set to true, this indicates that this configuration is the root configuration file, and ESLint won’t look for other configuration files in parent directories.
    - parser**:** Specifies @typescript-eslint/parser as the parser, enabling ESLint to understand TypeScript syntax.
    - parserOptions**:** This section configures the parser. tsconfigRootDir is set to the current directory (“./“), and project points to the TypeScript configuration file (tsconfig.json). These settings help the parser understand the project’s TypeScript setup.
    - plugins**:** Lists ESLint plugins used in this project:
      - @typescript-eslint: Adds TypeScript-specific linting rules.
      - eslint-plugin-node: Provides rules related to Node.js.
      - mocha: Adds linting rules for Mocha test framework.
      - eslint-plugin-require: Enforces best practices for require statements.
      - import: Provides rules for ES6 import/export syntax.
    - extends**:** Determines the rulesets to extend. This configuration extends several recommended rule sets for ESLint, TypeScript, and Node.js. It also includes prettier to integrate Prettier formatting rules.
    - rules**:** Customizes specific linting rules:
      - Disables direct throwing of literals (no-throw-literal) but enforces this rule for TypeScript (@typescript-eslint/no-throw-literal).
      - Prevents errors being throw for unused variables if they start with an undescrore ‘_’.
      - Specifies settings for handling unsupported ES syntax features based on the Node.js version.
    - settings**:** Provides additional configuration for modules and parsers, particularly for resolving imports in TypeScript files (import/parsers and import/resolver). It ensures that the ESLint understands how to parse and resolve .ts and .tsx files.

4.  Create **.eslintignore** in root folder and add:    

    ```
    node_modules 
    dist
    ``` 
    
    This tells ESLint to ignore specified directories. Typically, node_modules and dist (the output directory) are not linted.

5. Add linting scripts to the scripts section of **package.json**:

    ```
    “scripts”:{
      “start”:”ts-node src/index.ts”,
      “build”:”rm -rf dist/* && tsc”,
      “serve”:”node dist/index.js”,
      “lint”:”eslint . --ext .ts”, // Add this
      ”lint:fix”: “eslint . --ext .ts —fix” // And this one
    }
    ```

    These scripts provide a way to run ESLint on your project. npm run lint checks for linting errors, and npm run lint:fix attempts to automatically fix them.

You can now run ```npm run lint:fix``` to diagnose and attempt to fix any linting errors in your project.

## Prettier Setup

1. ```npm install —D --save-exact prettier```
		
    This command installs Prettier, a code formatter that enforces a consistent style by parsing your code and reprinting it with its own rules.


2. Create **.prettierrc** file in root folder and add:
    
    ```
    { “semi”: true, “trailingComma”: “none”, “singleQuote”: true, “printWidth”: 90 } 
    ```		
    
    This configuration file for Prettier specifies the formatting rules, such as semicolon usage, single quotes, and maximum line width.

3. Create **.prettierignore** file in root folder and add:

    ```
    node_modules 
    dist 
    ```		
    
    Similar to .eslintignore, this file tells Prettier to ignore certain directories.

1. Add Prettier scripts to **package.json**:

    ```
    “scripts”: { 
      “start”: “ts-node src/index.ts”, 
      “build”: “rm -rf dist/* && tsc”, 
      “serve”: “node dist/index.js”, 
      “lint”: “eslint . —ext .ts”, 
      “lint:fix”: “eslint . —ext .ts —fix”, 
      “prettier”: “prettier \”**/*.{js,jsx,json,md,ts}\” —check”, // Add this 
      “prettier:fix”: “prettier \”**/*.{js,jsx,json,md,ts}\” —write” // And this 
    } 		
    ```

    These scripts enable you to check and fix formatting issues using Prettier across your project. ```npm run prettier``` checks for formatting issues, while ```npm run prettier:fix``` automatically fixes them.

By integrating ESLint and Prettier into your Express.js project, you’re taking significant steps towards maintaining a high code quality standard. ESLint helps in identifying and fixing problematic patterns or code that doesn’t adhere to certain style guidelines, while Prettier ensures your code is consistently formatted.

Both these tools are vital in a professional development environment, reducing the chance of errors and improving readability. They also play a crucial role in team collaborations by enforcing a consistent coding standard, making the codebase easier to understand and maintain for everyone involved.

# Running your Application
- Run ```npm start``` and visit http://localhost:3000/ to start the development server. Use Ctrl+C to stop the server.

- Use ```npm run build``` to compile TypeScript files into JavaScript. This will create a new dist folder containing the JavaScript code ready for distribution.

- Run ```npm run serve``` to start the server using the compiled JavaScript files, and again visit http://localhost:3000/.

# Wrapping Up 

By following the steps outlined in this guide, you’ll have the beginnings of a well-structured ExpressJS project, integrated with TypeScript, and fortified with ESLint and Prettier for optimal code quality. We hope this guide has empowered you to build ExpressJS applications from scratch with confidence.  If you prefer a head start, don’t forget to fork the complete project at [https://github.com/robiwells/bootstrap-express-ts-backend](https://github.com/robiwells/bootstrap-express-ts-backend). And there’s more good news – stay tuned for a follow-up post, where we will continue setting up our project. Happy coding!