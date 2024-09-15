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
