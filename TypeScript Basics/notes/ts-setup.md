# TYPESCRIPT PROJECT CONFIGURATIONS

## REQUIREMENTS

**Dependencies/External Libraries Checklist:**

### NODE INSTALLATION

**NODE:**

- [ ] Node.js -- *Download to use the npm package manager -->* <https://nodejs.org/en/download>

### TYPESCRIPT/ESLINT INSTALLATION

**TYPESCRIPT:**

- [ ] TypeScript                -- **`npm install --save-dev typescript`**

**ESLINT w/ TYPESCRIPT INTEGRATION:**

- [ ] ESLint                    -- **`npm install --save-dev eslint`**
- [ ] TypeScript-ESLint Parser  -- **`npm install --save-dev @typescript-eslint/parser`**
- [ ] TypeScript-ESLint Plugin  -- **`npm install --save-dev @typescript-eslint/eslint-plugin`**

*OR simply run ...*

```bash
npm install --save-dev @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint typescript
```

### JEST INSTALLATION

**JEST:**

- [ ] Jest            -- **`npm install --save-dev jest`**

**JEST w/ TYPESCRIPT INTEGRATION:**

- [ ] TypeScript Jest -- **`npm install --save-dev ts-jest`**
- [ ] Jest Types      -- **`npm install --save-dev @types/jest`**

*OR simply run ...*

```bash
npm install --save-dev jest ts-jest @types/jest
```

## CONFIGURATION - INTEGRATING TYPESCRIPT, ESLINT LINTER, AND JEST TESTING FRAMEWORKS

**CONFIG FILE INIT COMMANDS (Initialize in the root project dir...):**

- [ ] Node Project Files

```bash
npm init                  # creates the node_module directory, package.json, and package-lock.json
```

- [ ] TypeScript Configuration file

```bash
tsc --init                # creates the TypeScript configuration file
```

- [ ] ESLint Configuration File

```bash
npm init @eslint/config   # create the ESLint configuration file
```

- [ ] Jest Configuration Files

```bash
jest init                 # creates the Jest configuration file
```

**IGNORE FILE COMMANDS (Add to the root project dir...):**

- [ ] ESLint Ignore File  

```bash
% touch .eslintignore
```

- [ ] Git Ignore File

```bash
% touch .gitignore
```

Files Structure:

**Root Directory**
/.github            *contains workflow configurations, pull request templates, etc...*
/node_modules       ***don't touch this!** -- contains everything needed to run node!*
/src                *contains source code directories/files...*
/tests              *contains test suite directories/files...*
.eslintrc.cjs       *ESLint configuration file*
.eslintignore       *ESLint configuration file*
.gitignore          *Github configuration file*
jest.config.ts      *Jest configuration file*
package.json        *Project configuration file*
package-lock.json   ***don't touch this!** --- contains project configuration information*
tsconfig.json       *TypeScript configuration file*
