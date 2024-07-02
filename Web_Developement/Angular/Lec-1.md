# README

This guide will walk you through setting up an Angular project with Material Design, Bootstrap, and additional components.

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

This completes the setup and initial configuration of your Angular project.