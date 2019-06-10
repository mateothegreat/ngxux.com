---
description: Configurable Material Vertical Toolbar
---

# ngxux-mat-vertical-toolbar

![](../.gitbook/assets/image%20%285%29.png)

## Installing

```text
$ npm install @ngxux/mat-vertical-toolbar
```

## Usage

First we'll add our component to our template with:

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<ngxux-mat-vertical-toolbar></ngxux-mat-vertical-toolbar>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Next we'll inject the `NgxuxMatVerticalToolbarService` and configure our menu with:

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
public constructor(private ngxuxMatVerticalToolbarService: NgxuxMatVerticalToolbarService) {

    ngxuxMatToolbarService.menuItems = [

        new NgxuxMatToolbarItem({ icon: 'home', path: '/home', tooltip: 'Go home!', color: '#fff', hoverColor: 'red' }),
        new NgxuxMatToolbarItem({ icon: 'settings', path: '/settings', tooltip: 'Go settings!' }),

    ];

    ngxuxMatVerticalToolbarService.leftMenuItems = [

        new NgxuxMatVerticalToolbarItem({ icon: 'home', path: '/home', tooltip: 'Go home!' }),
        new NgxuxMatVerticalToolbarItem({ icon: 'settings', path: '/settings', tooltip: 'Go settings!' }),
        new NgxuxMatVerticalToolbarItem({ icon: 'supervised_user_circle', path: '/settings/users', tooltip: 'Go settings!' }),

    ];

    ngxuxMatVerticalToolbarService.click$.subscribe((item: NgxuxMatVerticalToolbarItem) => {

        console.log(item);

    });

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

