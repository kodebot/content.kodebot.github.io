---
title: "TypeScript - Accessing object with null key"
date: 2015-06-03T00:00:00+00:00
publishdate: 2015-06-03T00:00:00+00:00
lastmod: 2015-06-03T00:00:00+00:00
tags: ["TypeScript"]
comments: true
draft: false
disableBreadcrumb: true
---

<p>Objects in JavaScript is just a key value pair and key is usually string and value can be anything. The following is an example of JavaScript object literal</p>

```js
var car = {
    wheels : 3,
    colour: 'red',
    drive: function(){
    ...
    }
}
```    

<p>The key in the object can be null. The default route in AngularJS is associated with null key, for example.</p>
<p>We can access the value associated with the null key in JavaScript quite easily like this:</p>

```js
routes[null].redirectTo
```

<p>If you do the same in TypeScript, you will get the following error</p>

An index expression argument must be of type `string`, `number`, `symbol`, or `any`.

<p>So, how do we make it work? It turns out that rather than using null key word, you can use a variable which is null. The following code is valid in TypeScript.</p>

```ts
var nullRef: any = null;
routes[nullRef].redirectTo
```

<p>I spent long time to get it working so posting this here for future reference.</p>