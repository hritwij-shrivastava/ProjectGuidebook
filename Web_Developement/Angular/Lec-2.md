# README

This guide will walk you through setting up an Angular project with Material Design, Bootstrap, and additional components, as well as incorporating services and routing.

## Prerequisites

- Node.js installed on your computer

## Steps

### Step 1: Install NodeJS

Ensure NodeJS is installed on your computer. If not, download and install it from [Node.js official website](https://nodejs.org/).

### Step 2: Install Angular CLI

```bash
npm install -g @angular/cli
```

### Step 3: Configure PowerShell for Script Execution (Windows)

Run the following commands in PowerShell:

```powershell
set-ExecutionPolicy RemoteSigned -Scope CurrentUser
Get-ExecutionPolicy
Get-ExecutionPolicy -list
```

### Step 4: Handle Node.js Error (if any)

If you encounter issues, use the following command:

```powershell
$env:NODE_OPTIONS = "--openssl-legacy-provider"
```

### Step 5: Create a New Angular Project

```bash
ng new athena
```

### Step 6: Serve the Angular Project

```bash
ng serve
```

### Step 7: Install Bootstrap

```bash
npm install bootstrap
```

### Step 8: Install jQuery

```bash
npm install jquery
```

---

**Always generate components after creating the corresponding module.**

---

### Step 9: Add Angular Material

Follow the guide on [Angular Material Getting Started](https://material.angular.io/guide/getting-started) and run:

```bash
ng add @angular/material
```

### Step 10: Generate Material Module

```bash
ng generate module material
```

### Step 11: Modify `material.ts` as follows

```typescript
import { NgModule } from '@angular/core';

@NgModule({
  imports: [],
  exports: []
})
export class MaterialModule { }
```

### Step 12-15: Generate Modules for Components

```bash
ng g m MyComponents/navbar
ng g m MyComponents/sidebar
ng g m MyComponents/searchs
ng g m MyComponents/tables
```

### Step 17-20: Generate Components

```bash
ng generate component MyComponents/searchs
ng generate component MyComponents/navbar
ng generate component MyComponents/sidebar
ng generate component MyComponents/tables
```

### Step 21: Update `material.ts` with Angular Material Modules

```typescript
import { NgModule } from '@angular/core';
import { MatToolbarModule } from '@angular/material/toolbar';

const material = [
  MatToolbarModule
];

@NgModule({
  imports: [material],
  exports: [material]
})
export class MaterialModule { }
```

**Add `MaterialModule` under imports in all modules (`searchs`, `navbar`, `sidebar`).**

### Step 22: Update `searchs.module.ts`

```typescript
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';
import { MaterialModule } from 'src/app/material/material.module';

@NgModule({
  declarations: [],
  imports: [
    CommonModule,
    MaterialModule
  ]
})
export class SearchsModule { }
```

### Step 23: Update `navbar.module.ts`

```typescript
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';
import { MaterialModule } from 'src/app/material/material.module';

@NgModule({
  declarations: [],
  imports: [
    CommonModule,
    MaterialModule
  ]
})
export class NavbarModule { }
```

### Step 24: Update `sidebar.module.ts`

```typescript
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';
import { MaterialModule } from 'src/app/material/material.module';

@NgModule({
  declarations: [],
  imports: [
    CommonModule,
    MaterialModule
  ]
})
export class SidebarModule { }
```

### Step 25: Update `table.module.ts`

```typescript
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';
import { MaterialModule } from 'src/app/material/material.module';

@NgModule({
  declarations: [],
  imports: [
    CommonModule,
    MaterialModule
  ]
})
export class TableModule { }
```

### Step 26: Add Angular Bootstrap

```bash
ng add @ng-bootstrap/ng-bootstrap
```

### Step 27: Generate Modal Similarity Module and Component

```bash
ng g m MyComponents/modal-similarity
ng generate component MyComponents/modal-similarity
```

### Step 28: Implement Angular Material Toolbar

Visit [Angular Material Toolbar Examples](https://material.angular.io/components/toolbar/examples). Copy the HTML, TypeScript, and CSS from the example and paste them into the corresponding files for the `navbar` component:

- `navbar.component.html`
- `navbar.component.ts`
- `navbar.component.css`

### Step 29: Generate a Service

Generate a new service to handle data fetching:

```bash
ng g service services/searchData
```

### Step 30: Implement File Upload with Angular, Node, and Express

Follow the tutorial on [Angular Node Express JS File Upload](https://www.positronx.io/angular-node-express-js-file-upload-tutorial/).

### Step 31: Add Bootstrap to Angular Project

For integrating Bootstrap into your Angular project, follow the instructions on [StackOverflow](https://stackoverflow.com/questions/37649164/how-to-add-bootstrap-to-an-angular-cli-project):

1. Check Angular CLI version:

    ```bash
    ng v
    ```

    If your Angular CLI version is greater than `1.0.0-beta.11-webpack`, follow these steps:

2. Install `ngx-bootstrap` and `bootstrap`:

    ```bash
    npm install ngx-bootstrap bootstrap --save
    ```

    In case of an error, run:

    ```bash
    npm config set legacy-peer-deps true
    ```

### Step 32: Implement Routing on Button Click

To implement routing on a button click, follow the guide on [StackOverflow](https://stackoverflow.com/questions/47010159/how-to-redirect-to-a-new-page-in-angular-4-through-button-click).