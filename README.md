# vue-application-insights


## Installation


```console
$ npm install vue-application-insights --save
```

## Get started


```js
import Vue from 'vue'
import VueAppInsights from 'vue-application-insights'

Vue.use(VueAppInsights, {
  id: 'XXXXXXXX--XXXX-XXXX-XXXXXXXXXXXX'
})
```

With vue router


```js
import Vue from 'vue'
import router from './router'

import VueAppInsights from 'vue-application-insights'

Vue.use(VueAppInsights, {
  id: 'XXXXXXXX--XXXX-XXXX-XXXXXXXXXXXX',
  router
})
```

Example with custom track event

```js
Vue.extend({

  methods: {
    custom_action() {
      this.$appInsights.trackEvent("custom_action", { value: 'ok' });
    }   
  }
  
});
```

## Options

**id** The instrumentation key of your AppInsights resource on Azure.
**router** The router instance, which events should be tracked as page view _(optional)_.
**basePath** Prefix of the tracked page view _(optional, default is '(Application Root)')_
**appInsights** Can be used if you don't want this module to initialize the AppInsights instance _(optional)_.
**trackInitialPageView** Boolean that determines whether or not the initial page view should be tracked. _(optional, defaults to true)_

## Initializing AppInsights from outside the Vue application

Maybe you use server side code to include the javascript snippet that initializes AppInsights. In that case you want to provide the AppInsights instance to this Vue plugin and prevent the plugin from tracking the initial page view.

```js
import Vue from 'vue'
import router from './router'

import VueAppInsights from 'vue-application-insights'

Vue.use(VueAppInsights, {
  appInsights: window.appInsights,
  trackInitialPageView: false,
  router
})
```