# Monorepo:
- Monolithic Repository: BE, FE, Common, External sources we are hitting
- folder structure: 
    1. repo:
        - apps
            - backend
            - web / ui
        - packages (AKA helper packages)
        - infra
- why monorepo?
    1. ans: If our services(e.g. react, nodejs, etc...) need to import or use each other (shared code reuse)
    2. optimized ci/cd (remote caching)
    3. centralized tooling and config: eslint
    4. collaboration

- monorepo framework in nodejs
    1. learna
    2. nx
    3. turbo repo (monorepo framework + more feature)
        - e.g - npm workspace + extra stuff
    4. yarn / npm workspace
- build system:
    - e.g : vite, typescript compiler
    - we can say compilers are build system
    - build system do transpilation, minification, running tests
- monorepo framework:
    - provides tools and conventions to manage projects that contains multiple packages/app.
    e.g : dependency management
- build system orchestrator:
    - e.g : turbo repo
    - using turbo repo we can define tasks that can call transpiler etc to do the job.
    - dependency management and caching during builds

- Command to create a turbo repo: npx create-turbo@latest

- turbo repo folder structure:
    - apps
        - web
        - docs
    - packages
        - eslint-config
        - typescript-config
        - ui
         - src
         - turbo
- If I want to create a form that can be used in web and docs, then the steps are: (without generator)
    - in src folder of ui present inside packages create form.tsx and write the code
    - in the package.json of ui folder export the same
    - use it in web and docs.
- Using generator:
    - package >> ui in terminal run "npm run generate:component"
- add react app in a turbo repo:
    - go to app folder and run : 'npm create vite@latest'
    - go to parent folder and run "npm i" (we can do it inside the app, but if we do it in parent folder it takes care of all the apps we have like our react app)
-------- 
### Week-2
- add an express app in turbo repo:
    - go to app folder and create "backend" folder
    - do npm init.
    - install express : npm i express
    - add build script in package.json.
    - in tsconfig.json add:
    ```js 
    {
        "extends":"@repo/typescript-config/base.json",
        "compilerOptions": {
            "rootDir": "./src",
            "outDir": "./dist",
            "lib": ["ES2015"],
            "module": "NodeNext"
        },
        "exclude": ["node_modules"],
        "include": ["."]
    }
    ```
- add a common folder which will contain code that will be shared among both font-end and back-end code.
    - in "packages" folder add a "common" folder to keep the common code.
    - do npm init --> create package.json
    - create "src" folder to keep the sharable files.
    - add ts.config and add:
    ```js
    {
        "extends":"@repo/typescript-config/base.json"
    }
    ```
    - do npm i in root folder. so that the common folder will be there in "node_modules" and thus will be availabl for BE and FE.
    - now using import statement add  the common code to BE and FE.