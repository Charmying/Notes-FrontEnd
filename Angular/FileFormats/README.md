# Angular 檔案類型

在 Angular 中，`.component`、`.service` 和 `.route` 等檔案是開發過程中的核心結構之一，這些檔案類型和結構對於維護和組織程式碼非常重要，每一個都有其特定的用途。以下是針對這些檔案的介紹，以及其他常見的檔案和功能。

<br />

## .component 檔

用途： Component 是 Angular 應用程式的基本構建塊。每個組件負責管理應用程式中特定的視圖和相關的功能。

- `.component.ts`

    功能： 定義組件的類別和功能，包括資料綁定、事件處理等。

    內容： 包含 TypeScript 類別，裝飾器 `@Component` 用來指定組件的元資料，例如：模板 (template)、樣式 (css/scss)等。

- `.component.html`

    功能： 定義組件的模板，描述該組件在瀏覽器中如何呈現。

    內容： 除了包含 HTML 語法，也可能包含 Angular 的模板語法，例如：`*ngIf`、`*ngFor` 等。

- `.component.css/scss`

    功能： 定義組件專用的樣式。

    內容： 包含 CSS 或 SCSS 樣式，這些樣式通常只影響該組件本身。

- `.component.spec.ts`

    測試檔案

    用途： 包含單元測試程式碼，用於測試組件、服務等的功能。

    內容： 使用測試框架 (例如：Jasmine) 編寫的測試用例

TypeScript 檔案範例：

```
import { Component } from '@angular/core';

@Component({
  selector: 'app-example',
  standalone: true,
  templateUrl: './example.component.html',
  styleUrl: './example.component.scss',
  imports: []
})

export class ExampleComponent {
  title = 'Hello World';
}
```

Angular 組件通過 `.html`、`.scss`、`.ts` 結合起來 (不一定需要 `.spec`)，形成了一個完整的功能模塊。組件的設計理念是將應用程式分解成小型、可重用的部分，提高開發效率和程式碼的可維護性。

<br />

## .service 檔

用途： service 用於封裝和共享應用程式中的功能和操作，例如：資料獲取、業務處理等，並將這些功能操作與視圖 (組件) 分離。service 有助於保持組件的簡潔，促進程式碼的可重用性和可測試性。

- `.service.ts`

    功能：定義 service 的類別和相關方法。
    
    內容：包含帶有 @Injectable 裝飾器的 TypeScript 類別，該裝飾器允許 service 被 inject 到其他 component 或 service 中。

    ```
    // example.service.ts

    import { Injectable } from '@angular/core';
    import { HttpClient } from '@angular/common/http';

    @Injectable({
        providedIn: 'root'
    })

    export class ExampleService {
        constructor(private http: HttpClient) {}

        getData() {
            return this.http.get('https://api.example.com/data');
        }
    }
    ```
    
    - `@Injectable` 裝飾器用於標記這是一個 service，並告訴 Angular 可以被注入到其他組件或 service 中。

        `providedIn: 'root'` 表示該 service 在應用程式的根層級可用，也就是說，可以在應用程式的任何部分都可以被注入。

    - `HttpClient` 是 Angular 的內建 service，用於發送 HTTP 請求。這裡 `ExampleService` 使用 `HttpClient` 來向 API 發送 GET 請求並獲取資料。

Angular service 的設計理念是將應用程式的業務流程與視圖分離，從而提高程式碼的可重用性和可測試性。service 可以輕鬆被不同的組件共享，使其適合處理應用程式中的跨組件應用。

<br />

## .route 檔

用途： route 檔案定義應用程式的路由 (routing) 配置，決定不同的 URL 對應哪個組件，實現單頁應用程式 (SPA) 的導航。

- `.route.ts` 或 `app-routing.module.ts`

    功能： 定義路由陣列，設定路由路徑、對應的 component 和其他路由選項。

    內容： 包含路由配置，使用 Angular 的 RouterModule 進行導入和導出。

<br />

### `.route.ts` 和 `app-routing.module.ts` 的差異

- `.route.ts`

    比較簡單且常見的一種路由設定方式，通常是在專案中單獨的檔案內設定路由規則。

    通常適用於使用獨立元件 (Standalone Components)，可以在這個檔案中直接定義路由陣列，並在根組件中使用 `RouterModule.forRoot(routes)` 或 `RouterModule.forChild(routes)` 來進行配置。

    比較適合單一檔案配置，讓路由更集中、更簡潔。

    ```
    // app.routes.ts

    import { Routes } from '@angular/router';
    import { HomeComponent } from './home/home.component';
    import { AboutComponent } from './about/about.component';

    export const routes: Routes = [
        { path: '', component: HomeComponent },
        { path: 'about', component: AboutComponent },
    ];
    ```
    
    ```
    // app.component.ts

    import { Component } from '@angular/core';
    import { RouterOutlet } from '@angular/router';

    @Component({
        selector: 'app-root',
        standalone: true,
        imports: [ RouterOutlet ],
        templateUrl: './app.component.html',
        styleUrl: './app.component.scss'
    })

    export class AppComponent {}
    ```
    
    ```
    <!-- app.component.html -->

    <router-outlet />
    ```

- `app-routing.module.ts`

    Angular 傳統的路由配置方式，通常是為了較大的專案而設計的。

    路由配置會放在 AppRoutingModule 模組中，並使用 `@NgModule` 來管理和匯出路由設定。

    適合於非獨立元件 (使用模組系統的元件)，並且容易擴展和管理較大規模的專案。

    ```
    // app-routing.module.ts

    import { NgModule } from '@angular/core';
    import { RouterModule, Routes } from '@angular/router';
    import { HomeComponent } from './home/home.component';
    import { AboutComponent } from './about/about.component';

    const routes: Routes = [
        { path: '', component: HomeComponent },
        { path: 'about', component: AboutComponent },
        { path: '**', redirectTo: '' },   // 未匹配的路由導向至首頁
    ];

    @NgModule({
        imports: [ RouterModule.forRoot(routes) ],
        exports: [ RouterModule ]
    })

    export class AppRoutingModule {}
    ```
    
    - `RouterModule.forRoot(routes)`：用於設定應用程式的主要路由配置。

    - `path` 是 URL 路徑，component 是該路徑對應的組件。

    - `**` 表示所有未匹配的路徑，這裡配置為重新導向至首頁。
    
    ```
    // app.module.ts
    
    import { NgModule } from '@angular/core';
    import { BrowserModule } from '@angular/platform-browser';
    import { AppRoutingModule } from './app-routing.module';
    import { AppComponent } from './app.component';
    import { HomeComponent } from './home/home.component';
    import { AboutComponent } from './about/about.component';

    @NgModule({
        declarations: [
            AppComponent,
            HomeComponent,
            AboutComponent
        ],
        imports: [
            BrowserModule,
            AppRoutingModule
        ],
        providers: [],
        bootstrap: [ AppComponent ]
    })

    export class AppModule {}
    ```

<br />

## .module 檔

用途： Module 用於組織應用程式中的相關部分，將應用程式的功能分組，以便管理和加載。Module 通常包含 組件 (component)、指令 (directive)、管道 (pipe) 和服務 (service) 等，並組合成一個功能性單元。

- `.module.ts`

    功能： 定義一個 Angular 模組，指定其包含的組件、指令、Pipe，以及導入的其他模組。

    內容： 包含帶有 `@NgModule` 裝飾器的類別，定義模組的元數據。

    `@NgModule` 裝飾器：用於配置模組的元數據，包括組件、服務、指令和 Pipe 等的註冊。

    ```
    // app.module.ts

    import { BrowserModule } from '@angular/platform-browser';
    import { NgModule } from '@angular/core';
    import { AppComponent } from './app.component';
    import { ExampleComponent } from './example/example.component';

    @NgModule({
        declarations: [
            AppComponent,
            ExampleComponent
        ],
        imports: [
            BrowserModule
        ],
        providers: [],
        bootstrap: [ AppComponent ]
    })

    export class AppModule {}
    ```

    - `declarations`：指定該模組包含的組件、指令和管道。這裡註冊了 `AppComponent` 和 `ExampleComponent`。

    - `imports`：指定該模組依賴的其他模組。這裡導入了 `BrowserModule`，這是所有 Angular 應用程式的必需模組。

    - `providers`：指定服務提供者，通常用於註冊全局服務。

    - `bootstrap`：指定應用程式的根組件，這個組件是應用程式啟動時顯示的第一個組件。

Module 是 Angular 應用程式的基本結構單位，通過將組件、service 和其他功能組織在一起，幫助管理複雜的應用程式結構。

<br />

## .model 檔

用途： Model 用於定義應用程式中使用的資料結構和類型，提供強類型支持。

- `.model.ts`

    功能： 定義資料模型的介面或類別。

    內容： 包含 TypeScript 介面或類別，描述資料的結構和屬性。

    ```
    // user.model.ts

    export interface User {
        id: number;
        name: string;
        email: string;
    }
    ```

.model 檔為應用程式提供了資料結構的清晰定義，能夠幫助開發人員管理和操作資料，提高程式碼的可讀性和可維護性。
