# Progressive Webapps - Service Worker Test
[Progressive Webapps](https://developers.google.com/web/progressive-web-apps/) are Webapps that give you a richer offline experience and facilitate background fetching and push notifications
[Here](https://developers.google.com/web/progressive-web-apps/checklist) you see a checklist of what it means to have a webapp that is considered "progressive".

## Description
This is a LabDay Test Project for a first implementation of a [Service Worker](https://developers.google.com/web/fundamentals/getting-started/primers/service-workers). The Project/Implementation is looseley based upon this [Tutorial](https://developers.google.com/web/fundamentals/getting-started/codelabs/your-first-pwapp/)

* There are 2 important prerequisites for service workers:
  1. The file of the worker must be in the root of the application
  2. You must use HTTPS
Especially because of the necessity for https i have chosen to deploy the demo site on github pages (see Demo)

## _Attention_ be aware that this Code is not to be used for production purposes for the following Reasons:
1. __Cache depends on updating the cache key for every change__ For example this caching method requires you to update the cache key every time content is changed, otherwise, the cache will not be updated, and the old content will be served. So be sure to change the cache key with every change as you're working on your project!

2. __Requires everything to be redownloaded for every change__ Another downside is that the entire cache is invalidated and needs to be re-downloaded every time a file changes. That means fixing a simple single character spelling mistake will invalidate the cache and require everything to be downloaded again. Not exactly efficient.

3. __Browser cache may prevent the service worker cache from updating__ There's another important caveat here. It's crucial that the HTTPS request made during the install handler goes directly to the network and doesn't return a response from the browser's cache. Otherwise the browser may return the old, cached version, resulting in the service worker cache never actually updating!

4. __Beware of cache-first strategies in production__ Our app uses a cache-first strategy, which results in a copy of any cached content being returned without consulting the network. While a cache-first strategy is easy to implement, it can cause challenges in the future. Once the copy of the host page and service worker registration is cached, it can be extremely difficult to change the configuration of the service worker (since the configuration depends on where it was defined), and you could find yourself deploying sites that are extremely difficult to update!

* __How do I avoid these edge cases?__ So how do we avoid these edge cases? Use a library like [sw-precache](https://github.com/GoogleChrome/sw-precache), which provides fine control over what gets expired, ensures requests go directly to the network and handles all of the hard work for you.

## Demo
The Source is exposed in a GitHub-Pages Site for a short demo
https://quasarchimaere.github.io/progressivewebapp_serviceworker_test/

Supported Browsers 
 * Chrome
 * Firefox
 * Opera
 * [Edge(shows public support for future implementation)](https://developer.microsoft.com/en-us/microsoft-edge/platform/status/serviceworker/)
 * NO SUPPORT for Safari
