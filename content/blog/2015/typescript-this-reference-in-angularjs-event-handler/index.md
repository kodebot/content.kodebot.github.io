---
title: "TypeScript - 'this' reference in AngularJS event handler"
date: 2015-04-27T00:00:00+00:00
publishdate: 2015-04-27T00:00:00+00:00
lastmod: 2015-04-27T00:00:00+00:00
tags: ["TypeScript", "AngularJS"]
disableNextPrev: true
hidden: true
comments: true
draft: false
---

<p>Let's have a look at how AngularJS 1.x controller is usually created in TypeScript before we go into details of how AngularJS event handler and how 'this' works in the AngularJS event handler context. </p>
<p>TypeScript encourages to type anything and everything to take full advantages of the type system and tool supports we get when working with any strongly typed language.</p><!-- more -->
<p>So, when using TypeScript with AngularJS 1.x, class is usually created to represent the implementation of the controllers. Here is an example of how this would look like</p>

```ts
// Controller using class
module App.Home {

    interface IHomeViewModel {
        title: string;
    }

    class HomeController implements IHomeViewModel {
        title: string = "Welcome!!!";

        static $inject = ["$location", "$rootScope"]
        constructor(
            private $location: ng.ILocationService,
            private $rootScope: ng.IRootScopeService) {
        }
    }

    angular.module("app")
        .controller("homeController", HomeController);
}
```

In this example, an interface called `IHomeViewModel` is created to represent the public members of the controller and a class `HomeController` is created which implements the interface.</p>

Dependencies are injected using static `$inject` member and injected dependencies are declared as private members.

<p>Finally, the controller is created using Angular module's controller method which takes name of the controller and constructor function (in this case, class) which represents the controller's implementation as parameters. </p>

<p>In AngularJS 1.x, events are one of the communication enablers among components. AngularJS itself raises various built in events and allows application to raise any custom events as well.</p>
<p>We can add handlers to these events to do something useful when the events are raised.</p>

Here is an example of how we will add handler to Angular's `$routeChangeStart` event which is raised when route change is initiated

```ts
// Event handlers
private hookEventHandlers():void {
        this.$rootScope.$on("$routeChangeStart", this.onRouteChangeStart);
}

private onRouteChangeStart():void {
        console.log(this.title);
}
```
The hookEventHandlers method is called from the constructor of the controller which adds handler to `$routeChangeStart` event and the handler simply logs `title` member of the class into console.

When this method is run, you would expect it to show 'Welcome!!!' in the console but it shows `undefined` instead.

This is happening because the caller of the method is NOT the instance of the class where it is defined, so `this` doesn't have a member named `title`.
<p>Fortunately, it is very easy to get around this problem in TypeScript using arrow function. Here is an example</p>

```ts
// Event handler using arrow function
private hookEventHandlers(): void {
        this.$rootScope.$on("$routeChangeStart",() => {
        this.onRouteChangeStart.call(this);
        });
}

private onRouteChangeStart(): void {
        console.log(this.title);
}
```
<p>Now, when this function is executed, 'Welcome!!!' is printed in the console window as expected.</p>

In this example, we have changed our event handler to be arrow function and the arrow function invokes `onRouteChangeStart` using call function and passing current instance of the class where it is defined as `this` reference.

But, how does arrow function has correct reference of `this`? When arrow function is created, `this` is lexically bound to the location where it is created. In this case, arrow function is created inside the member of a class where `this` represents the current instance of the class. So `this` reference inside the arrow function also represents the current instance of the class where it is created. That's it :)
<p>Full code example here,</p>

```ts
// Full code example
module App.Home {

    interface IHomeViewModel {
        title: string;
    }

    class HomeController implements IHomeViewModel {
        title: string = "Welcome!!!";

        static $inject = ["$location", "$rootScope"]
        constructor(
            private $location: ng.ILocationService,
            private $rootScope: ng.IRootScopeService) {

            this.hookEventHandlers();
        }

        private hookEventHandlers(): void {
            this.$rootScope.$on("$routeChangeStart",() =>; {
                this.onRouteChangeStart.call(this);
            });
        }

        private onRouteChangeStart(): void {
            console.log(this.title);
        }
    }

    angular.module("app")
        .controller("homeController", HomeController);
}
```