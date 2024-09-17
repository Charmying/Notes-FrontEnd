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

<br />

## .service 檔

用途： service 用於封裝和共享應用程式中的功能，例如：資料獲取、業務處理等。service 有助於保持組件的簡潔，促進程式碼的可重用性和可測試性。

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

<br />

## .route 檔

用途： route 檔案定義應用程式的 routing (路由) 配置，決定不同的 URL 對應哪個組件，實現單頁應用程式 (SPA )的導航。

- `.route.ts` 或 `app-routing.module.ts`

    功能： 定義 routing 陣列，設定 routing 路徑、對應的 component 和其他 routing 選項。

    內容： 包含 routing 配置，使用 Angular 的 RouterModule 進行導入和導出。

<br />

### `.route.ts` 和 `app-routing.module.ts` 的差異

- `.route.ts`

    比較簡單且常見的一種 routing 設定方式，通常是在專案中單獨的檔案內設定 routing 規則。

    通常適用於使用獨立元件 (Standalone Components)，可以在這個檔案中直接定義 routing 陣列，並在根組件中使用 `RouterModule.forRoot(routes)` 或 `RouterModule.forChild(routes)` 來進行配置。

    比較適合單一檔案配置，讓 routing 更集中、更簡潔。

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

    Angular 傳統的 routing 配置方式，通常是為了較大的專案而設計的。

    routing 配置會放在 AppRoutingModule 模組中，並使用 @NgModule 來管理和匯出路由設定。

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
    ];

    @NgModule({
        imports: [ RouterModule.forRoot(routes) ],
        exports: [ RouterModule ]
    })

    export class AppRoutingModule {}
    ```
    
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
