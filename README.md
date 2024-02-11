# Frontend

## Changes that must be taken into account
1. ngIf
<!-- Angular 16 and previous versions -->
<div *ngIf="showTable; else showList">
  <table>
    <!-- full table -->
  </table>
</div>

<!-- Angular 17 -->
@ngIf (showTable) {
  <table>
    <!-- full table -->
  </table>
}

2. ngFor
<!-- Angular 16 and previous versions -->
<div *ngFor="let item of items; let i = index;">
  <p>{{ item }}</p>
</div>

<!-- Angular 17 -->
@for (item of items; track item.id) {
  <p>{{ item }}</p>
}

3. ngSwitch
<!-- Angular 16 and previous versions -->
<div [ngSwitch]="color">
  <app-color *ngSwitchCase="red"/>
  <app-color *ngSwitchCase="blue"/>
  <app-default-color *ngSwitchDefault/>
</div>

<!-- Angular 17 -->
@switch (color) {
  @case ('red') {
    <app-red-color />
  }
  @case ('blue') {
    <app-blue-color />
  }
  @default {
    <app-default-color />
  }
}
4. Stable Application Builders : ng new my-app --ssr
5. Deferred Loading Blocks : 

<button (click)="load = true" #showProfileBtn>
  Load my profile
</button>

@defer (on interaction(showProfileBtn); when load == true) {
  <my-profile />
} @placeholder (minimum 300ms) {
  <!-- placeholder -->
} @loading (after 300ms; minimum 1.5s) {
  <loading-component /> <!-- loading section -->
} @error {
  <p>Something went wrong, please try again... </p> <!-- handle error msg -->
}