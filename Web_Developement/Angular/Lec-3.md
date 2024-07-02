# README

This guide will walk you through setting up an Angular project with Material Design, Bootstrap, and additional components, as well as generating necessary modules, components, and services.

## Prerequisites

- Node.js installed on your computer

## Steps

### Step 1: Create a New Angular Project

```bash
ng new myproject
```

### Step 2: Install Necessary Packages

```bash
npm install bootstrap
npm install jquery
ng add @angular/material
ng add @ng-bootstrap/ng-bootstrap
npm install @iplab/ngx-file-upload --save
npm install ng2-file-upload
npm install ngx-toastr
npm install angular-sweetalert
```

### Step 3: Generate Modules and Components

```bash
ng generate module material
ng g m modules/login
ng g c modules/login
ng g m modules/home
ng g c modules/home
ng g m modules/view-reports
ng g c modules/view-reports
ng g m modules/modify-reports
ng g c modules/modify-reports
ng g m modules/search
ng g c modules/search

ng g m modules/modify-reports/components/modal-similarity
ng g c modules/modify-reports/components/modal-similarity
ng g m modules/modify-reports/components/container
ng g c modules/modify-reports/components/container
ng g m modules/modify-reports/components/tables
ng g c modules/modify-reports/components/tables
ng g m modules/search/components/container
ng g c modules/search/components/container
ng g m modules/search/components/tables
ng g c modules/search/components/tables
ng g m core/navbar
ng g c core/navbar
ng g m shared/material
ng g m shared/search
ng g c shared/search
ng g service core/services/searchData
```

### Step 4: Project Structure

Ensure your project structure resembles the following:

```plaintext
|-- app
     |-- modules
       |-- home
           |-- [+] components
           |-- home.component.css
           |-- home.component.html
           |-- home.component.spec.ts
           |-- home.component.ts
           |-- home.module.ts
       |-- reports
           |-- [+] components
           |-- reports.component.css
           |-- reports.component.html
           |-- reports.component.spec.ts
           |-- reports.component.ts
           |-- reports.module.ts
       |-- view-reports
           |-- [+] components
           |-- view-reports.component.css
           |-- view-reports.component.html
           |-- view-reports.component.spec.ts
           |-- view-reports.component.ts
           |-- view-reports.module.ts
     |-- core
       |-- navbar
           |-- navbar.component.css
           |-- navbar.component.html
           |-- navbar.component.spec.ts
           |-- navbar.component.ts
           |-- navbar.module.ts
       |-- [+] services
     |-- shared
          |-- material
           |-- material.module.ts
|-- assets
     |-- img
```

### Additional Instructions

- **Add Material Components to `material.module.ts`**:
  
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

- **Add MaterialModule to Other Modules**:
  
  Add `MaterialModule` to the imports array in other modules where Angular Material components are used.

### Sample Code for Core Components

#### `navbar.component.html`

```html
<mat-toolbar color="primary">
  <span>myproject</span>
</mat-toolbar>
```

#### `navbar.component.ts`

```typescript
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-navbar',
  templateUrl: './navbar.component.html',
  styleUrls: ['./navbar.component.css']
})
export class NavbarComponent implements OnInit {
  constructor() { }

  ngOnInit(): void {
  }
}
```

### Adding Bootstrap

Add the following lines to `angular.json` to include Bootstrap and jQuery:

```json
"styles": [
  "node_modules/bootstrap/dist/css/bootstrap.min.css",
  "src/styles.css"
],
"scripts": [
  "node_modules/jquery/dist/jquery.min.js",
  "node_modules/bootstrap/dist/js/bootstrap.min.js"
]
```

### Routing

To implement routing on button click, follow the guide on [StackOverflow](https://stackoverflow.com/questions/47010159/how-to-redirect-to-a-new-page-in-angular-4-through-button-click). Here's an example:

#### `app-routing.module.ts`

```typescript
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent } from './modules/home/home.component';
import { LoginComponent } from './modules/login/login.component';

const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'login', component: LoginComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```

#### `navbar.component.html`

```html
<button (click)="navigateToLogin()">Login</button>
```

#### `navbar.component.ts`

```typescript
import { Component } from '@angular/core';
import { Router } from '@angular/router';

@Component({
  selector: 'app-navbar',
  templateUrl: './navbar.component.html',
  styleUrls: ['./navbar.component.css']
})
export class NavbarComponent {
  constructor(private router: Router) { }

  navigateToLogin(): void {
    this.router.navigate(['/login']);
  }
}
```

This completes the setup and initial configuration of your Angular project.