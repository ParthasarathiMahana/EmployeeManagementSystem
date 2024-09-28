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

- Command to create a turbo rep: npx create-turbo@latest

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
