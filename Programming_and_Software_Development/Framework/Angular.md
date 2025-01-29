# Angular Cheat Sheet

## 📌 Introduction
Angular is a TypeScript-based open-source framework for building dynamic web applications. It provides tools for routing, HTTP requests, forms, dependency injection, and more.

---

## 🚀 Installation
```sh
npm install -g @angular/cli
ng new my-angular-app
cd my-angular-app
ng serve
```

---

## 🛠️ Angular CLI Commands
```sh
ng new project-name      # Create a new Angular project
ng serve                 # Run development server
ng generate component xyz  # Generate a new component
ng generate service xyz    # Generate a new service
ng build                 # Build the project
ng test                  # Run unit tests
ng e2e                   # Run end-to-end tests
```

---

## 🏗️ Project Structure
```plaintext
src/
 ├── app/
 │   ├── components/
 │   ├── services/
 │   ├── app.module.ts
 │   ├── app.component.ts
 │   ├── app.component.html
 │   ├── app.component.css
 ├── assets/
 ├── environments/
 ├── main.ts
 ├── index.html
```

---

## 🔹 Components
### Generate a Component
```sh
ng generate component component-name
```

### Example Component
```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-hello',
  template: '<h1>Hello, Angular!</h1>',
  styleUrls: ['./hello.component.css']
})
export class HelloComponent {}
```

### Component Binding
```html
<app-hello></app-hello>
```

---

## 🔹 Modules
```ts
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule],
  bootstrap: [AppComponent]
})
export class AppModule {}
```

---

## 🔹 Directives
- **ngIf** (Conditional Rendering)
```html
<p *ngIf="show">This is shown if 'show' is true</p>
```

- **ngFor** (Looping)
```html
<ul>
  <li *ngFor="let item of items">{{ item }}</li>
</ul>
```

- **ngClass** (Class Binding)
```html
<p [ngClass]="{'active': isActive}">Styled Text</p>
```

---

## 🔹 Services & Dependency Injection
### Generate a Service
```sh
ng generate service data
```

### Example Service
```ts
import { Injectable } from '@angular/core';

@Injectable({ providedIn: 'root' })
export class DataService {
  getData() {
    return ['Angular', 'React', 'Vue'];
  }
}
```

### Using a Service in a Component
```ts
import { Component } from '@angular/core';
import { DataService } from './data.service';

@Component({ selector: 'app-root', templateUrl: './app.component.html' })
export class AppComponent {
  items: string[];

  constructor(private dataService: DataService) {
    this.items = this.dataService.getData();
  }
}
```

---

## 🔹 Routing
### Enable Routing in `app.module.ts`
```ts
import { RouterModule, Routes } from '@angular/router';

const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'about', component: AboutComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule {}
```

### Using Router Links
```html
<a routerLink="/about">Go to About</a>
<router-outlet></router-outlet>
```

---

## 🔹 Forms
### Template-Driven Form
```html
<form #myForm="ngForm" (ngSubmit)="onSubmit(myForm)">
  <input name="username" ngModel required>
  <button type="submit">Submit</button>
</form>
```

### Reactive Form
```ts
import { FormGroup, FormControl } from '@angular/forms';

this.form = new FormGroup({
  username: new FormControl('')
});
```

---

## 🔹 HTTP Requests
### Import HttpClientModule
```ts
import { HttpClientModule } from '@angular/common/http';
@NgModule({ imports: [HttpClientModule] })
```

### Making an HTTP Request
```ts
import { HttpClient } from '@angular/common/http';

constructor(private http: HttpClient) {}

fetchData() {
  this.http.get('https://api.example.com/data').subscribe(data => {
    console.log(data);
  });
}
```

---

## 🎯 Useful Links
- [Angular Official Docs](https://angular.io/docs)
- [Angular CLI Documentation](https://angular.io/cli)
- [RxJS Documentation](https://rxjs.dev/)

---


