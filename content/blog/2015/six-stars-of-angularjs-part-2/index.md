---
title: "Six stars of AngularJS - Part 2"
date: 2015-03-24T00:00:00+00:00
publishdate: 2015-03-24T00:00:00+00:00
lastmod: 2015-03-24T00:00:00+00:00
tags: ["JavaScript", "AngularJS"]
comments: true
draft: false
---

<p>In <a href="../six-stars-of-angularjs-part-1" target="_blank">part 1</a>&nbsp;of this series, we have briefly seen how <code>$provide</code> and <code>$injector</code> work and we also took a deep dive on how we create a service using provider function of <code>$provide</code> service.</p><!-- more -->
<p>Lets continue our journey and look at how and when we can&nbsp;use other&nbsp;functions of <code>$provide</code> service to create services.</p>
<p>The following are the four&nbsp;functions we are going to look at now</p>
<ol>
<li>factory</li>
<li>service</li>
<li>value</li>
<li>constant</li>
</ol>
<h2>Factory</h2>
<p>The factory is one of the functions exposed by $provide service to create services. Here is an example of service created using factory function of <code>$provide</code> service</p>

```js
// sample 1
$provide.factory('movieService', movieService);
function movieService() {
    return { // service
      getAllMovies: getAllMovies
    };

    function getAllMovies() {
	    return ['engMovie1', 'engMovie2', 'engMovie3'];
    }
}
```

<p>Here is the same service created using factory function&nbsp;available in module.</p>

```js
// sample 2
var app = angular.module('app');
app.factory('movieService', movieService);
function movieService() {
    return { // service
      getAllMovies: getAllMovies
    };

    function getAllMovies() {
	    return ['engMovie1', 'engMovie2', 'engMovie3'];
    }
}
```

<p>Note, module doesn't implement this function, it just allows us to invoke factory function of <code>$provide</code> in a convenient way.</p>
<p>You would have recognized by now that the factory function takes the service factory as second parameter, this is same as what we assign to $get member of service provider. Of course, the first parameter is name of the service we are creating.</p>
<p>When we create a service using factory function, <code>$provide</code>&nbsp;wraps it with service provider and registers it with <code>$injector</code>. We cannot create configurable services when factory function is used. So, if you don't want to create configurable service, you can use factory function. This is most used function to create services.</p>
<h2>Service&nbsp;</h2>
<p>The service function is used to create services if the service definition is defined as JavaScript class/type. The function name 'service' is kind of misleading in a way that it will make you think that this 'THE' function to create services.</p>
<p>When we use provider or factory function, the service factory typically uses module or revealing module pattern and returns an object with all the public functions. So, if we need to create an instance of the service, we just need to invoke service factory method. In the context of angular, <code>$injector</code> will invoke service factory method to get service instance.</p>
<p>When we use 'service' method of <code>$provide</code>, we will be defining our service as type/class and <code>$injector</code> will invoke it using new keyword, in other words, the function will be treated as constructor function.</p>
<p>Here is an example of how we use 'service' function to create services</p>

```js
    // sample 3
    app.service('movieService', movieService);

    function movieService() {
        this.getAllMovies = getAllMovies;

        function getAllMovies() {
            return ['engMovie1', 'engMovie2', 'engMovie3'];
        }
    }
```

<p>Note: this example uses the method available in module.</p>
<p>If you look at the service factory function, the public functions exposed by underlying service is attached to <code>this</code>. So, if we create new instance using new keyword, we can invoke the functions attached to <code>this</code>.</p>
<p>This way of creating services is recommended when we need to use class/type as a service.&nbsp;</p>
<h2>Value</h2>
<p>The value function is the simplest way to create a service if the service doesn't have any dependencies. This function takes service itself as second parameter(not the service provider or service factory) and simply returns&nbsp;it when requested. If we specify function as second parameter then the function is returned when the instance of the service is requested. Note, it will not invoke the function, it will just return it as if it is an object. We can use any value for the second parameter including string, number, object literal, function, etc...</p>
<p>The following are some&nbsp;examples of service created using value</p>

```js
    // sample 4 
    app.value('movieService', movieService()); // Note : function is invoked

    function movieService() {
        return {
            getAllMovies: getAllMovies
        }

        function getAllMovies() {
            return ['engMovie1', 'engMovie2', 'engMovie3'];
        }
    }

   // sample 5
   app.value('movieService', { getAllMovies: getAllMovies});

   // sample 6
   app.value('movieService', "sample service");
```

<p>Generally, this function is used to create services when we know that the service doesn't have any dependencies.</p>
<h2>Constant</h2>
<p>The constant is a special function to create constants. One of the specialty is that constants created this way can be injected into config block of a module but, we know only providers can be injected into config method of a module. How does it work? The works because the constant name is also the name of the provider. The second parameter we specify will be both service provider and service instance. Also, $provide won't suffix 'Provider' at the end of first parameter to create provider name. So, if we specify constant name as dependency in config function of a module, it will be seen as provider and <code>$injector</code> will inject it.</p>
<p>Here is an example of how constant is created</p>

```js
// sample 7
app.constant('PI', 3.14);
```
<p>We have seen all five ways to create services in angular. But, wait, did we not say there are six stars in angular? Yes, there are six and the sixth one is decorator function. We will have a look at decorator in the next post.</p>