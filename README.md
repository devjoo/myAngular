# MyAngular

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 1.6.3.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `-prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).


### install CLI 

``` 
npm install -g @angular/cli
ng new myAngular
cd myAngular
ng serve -p 777 // 777
```

### ng generate component heroes
```
ng generate component heroes
```

## Component
 Angular core library에서 항상 Component를 import 한다.
```
import { Component, OnInit } from '@angular/core';
```

## @component
@Component 는 데코레이터 함수로 Angular metadata를 specify한다.

```
@Component({
    selector :  'app-heroes', //컴포넌트 element selector
    templateUrl : './heros.component.html', // 컴포넌트 templete file 위치
    styleUrls : ['./heros.component.css'] // 컴포넌트 private CSS style
})
```

## ngOnInit
The ngOnInit is a lifecycle hook Angular calls ngOnInit shortly after creating a component. It's a good place to put initialization logic.

ngOnInit  라이프사이클 hook다. 컴포넌트 생성 직후 ngOnInit을 호출한다. 초기화 로직을 넣는데 좋은 장소다.
```
export class HeroesComponent inplements OnInit {

    constructor(){
    }
    
    ngOnInit() {
    
    }
}
```

### 타입을 위한 클래스 생성
create hero.ts file and export.
* hero.ts
```
export class Hero {
    id : number,
    name : string
}
```
Refactor the component's hero property to be of type Hero
* heros.component.ts
```
import { Hero } from '../hero';
...
export class HeroesComponent implements OnInit {
  hero: Hero = {
    id: 1,
    name: 'Windstorm'
  };
```
The page no longer displays properly.
화면이 더이상 올바르게 표시되지 않는다. hero가 string에서 Object로 바뀌었기 때문에

## Format with the UppercasePipe |
pipe 연산자(operator) 는 built-in된 UppercasePipe를 activate 한다.
pipe 활용 - format strings, currency amounts, dates and other display data

## ngModel
ngModel은 유효한 Angular derective이지만 기본에 속하지는 않는다.
FormsModule 을 사용하도록 must opt-in to using it.

## AppModule
응용프로그램에 필요한 다른 파일, 라이브러리가 무엇인지 알아야한다. 이 정보를 metadata 라고 부른다.
일부 메타데이터는 컴포넌트 클래스에 추가한 @Component 데코레이터에 있다.
다른 중요한 메타데이터는 @ngModule 데코레이터에 있다.

가장 중요한 @ngModule 데코레이터는 가장 최상위 클래스인 AppModule에 있다

## Import FormsModule
* app.module.ts
FormsModule symbol from the @angular/forms library
```
import { FormsModule } from '@angular/forms';
```
## @NgModule의 imports
앱이 필요한 external 모듈 목록을 @NgModule의 imports에 등록한다.

## @NgModule의 declarations
```aidl
@NgModule({
    declarations: [
      AppComponent,
      HeroesComponent
    ],
    imports: [
      BrowserModule,
      FormsModule
    ],
```
## *ngFor
목록을 통해 반복할때 마다 hero는 현재 hero 오브젝트를 가지고 있다.
```aidl
<li *ngFor="let hero of heroes">
```

## *ngIf
selectedHero가 undefind일때는 노출안되고 selectedHero에 hero가 들러왔을때 display된다.
```aidl
<div *ngIf="selectedHero">
```

## [class.some-css-class]="some-condition"
클래스 바인딩은 조건부를 사용하여 추가 삭제를 용이하게 한다.
