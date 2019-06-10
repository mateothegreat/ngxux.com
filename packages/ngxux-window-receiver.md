---
description: Receive external method calls.
---

# ngxux-window-receiver

![](../.gitbook/assets/image%20%281%29.png)

## Introduction

The ngxUX Window Receiver Module allows you to easily expose external methods to the `window` object and observe method calls using subscriptions.

## Installation

Install the node module with npm:

{% code-tabs %}
{% code-tabs-item title="terminal command" %}
```bash
$ npm install @ngxux/window-receiver
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Bootstrapping

We need to add the `NgxuxWindowReceiver` module to our `app.module.ts` imports:

{% code-tabs %}
{% code-tabs-item title="app.module.ts" %}
```typescript
import { NgModule }                  from '@angular/core';
import { BrowserModule }             from '@angular/platform-browser';
import { NgxuxWindowReceiverModule } from '@ngxux/window-receiver';

import { AppComponent } from './app.component';

@NgModule({

    declarations: [

        AppComponent

    ],

    imports: [

        BrowserModule,

        NgxuxWindowReceiverModule

    ],

    providers: [],
    bootstrap: [ AppComponent ]

})
export class AppModule {}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Usage

You register your external functions by calling the `NgxuxWindowReceiverService.add(..)` method. This method will register your external function by name and returns an `Observable` which you can subscribe to anywhere, anytime.

### Injecting the Service

Before we can use external methods we need to inject the service. You do this by passing the following variable to your class constructor like so:

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
export class AppComponent {

    public constructor(private windowReceiverService: NgxuxWindowReceiverService) {

      ...

    }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Registering External Methods

Call the `.add(..)` method on the `NgxuxWindowReceiverService` passing an object with the property `methodName` which will become the external method exposed to `window`

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
this.windowReceiverService.add({

    methodName: 'myExternalFunction'

}).subscribe(args => {

    console.log('myExternalFunction called with arguments:', args);

});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Final Result

Patching things together we:

1. Include `NgxuxWindowReceiverModule` in our `app.module.ts` class.
2. Inject `NgxuxWindowReceiverService` in our `app.component.ts` class.
3. We add our external methods to the service by calling `.add(..)`.

{% code-tabs %}
{% code-tabs-item title="app.component.ts" %}
```typescript
import { Component }                  from '@angular/core';
import { NgxuxWindowReceiverService } from '@ngxux/window-receiver';

@Component({
    selector: 'app-root',
    templateUrl: './app.component.html',
    styleUrls: [ './app.component.scss' ]
})
export class AppComponent {

    /**
     * Inject the window reicever service.
     *
     * @param {NgxuxWindowReceiverService} windowReceiverService
     */
    public constructor(private windowReceiverService: NgxuxWindowReceiverService) {

        //
        // Add the external function by name and subscribe to the observable
        // that is returned.
        //
        this.windowReceiverService.add({

            methodName: 'myExternalFunction'

        }).subscribe(args => {

            console.log('myExternalFunction called with arguments:', args);

        });

    }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Now we can call the javascript function `myExternalFunction('Hello World!!');` externally. Give it a try in your web browsers developer console!

## Getting Help

Join us on our discord server at [https://discord.gg/programming](https://discord.gg/programming).

