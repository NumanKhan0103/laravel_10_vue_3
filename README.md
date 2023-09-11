
# Laravel 10 With Vue 3

complate step by step process how to install vue 3 with laravel 10


## Laravel Installation And Vue configration 

Step 1 :: Laravel comand 

```bash
  laravel new laravel_10_with_vue_3
```
Step 2 :: Go to project folder 
```bash
  cd laravel_10_with_vue_3
```

Step 3 :: Install Node js
```bash
  npm install 
```
Step 4 :: Install vue js
```bash
  npm install vue@next
```

Step 5 :: install vitejs plugin for vue js
```bash
  npm install @vitejs/plugin-vue
```

Step 6 :: Go to vite.config.js normal look like this

```bash
  import { defineConfig } from 'vite';
  import laravel from 'laravel-vite-plugin';

  export default defineConfig({
      plugins: [
          laravel({
              input: ['resources/css/app.css',    'resources/js/app.js'],
              refresh: true,
          }),
      ],
  });
```

add these both  line 

```bash
import vue from "@vitejs/plugin-vue";
```

```bash
vue(),
```

Now your vite.config.js look like this
```bash
  import { defineConfig } from 'vite';
  import laravel from 'laravel-vite-plugin';
  import vue from "@vitejs/plugin-vue";

  export default defineConfig({
      plugins: [
          laravel({
              input: ['resources/css/app.css',    'resources/js/app.js'],
              refresh: true,
          }),
          vue(),
      ],
  });
```

Step 7 :: Now Go To public/js/app.js file 

```bash
  import './bootstrap';
 
```
 update with this code 

```bash
  import './bootstrap';

  import {createApp } from 'vue';
  import Example from './components/Example.vue';

  const app = createApp({
    components:{
        Example,
    }
  });

app.mount("#app");
```

Step 8 :: Go To resources/view/ main.blade.php or add in the head of website 

```bash 

  @vite('resources/js/app.js')

```
Step 9 ::  And add this in the body 
```bash 

  <div id="app"></div>

```

## Create a Basic Compnent
Step 10 :: Create a components folder in the resources/js/
```bash 

  resources/js/components
```
Step 11 :: Create a Example.vue file in the components folder 

```bash 
   resources/js/components/Example.vue
```
Example.vue
```bash 
  <template>
    <div>
       <h1> Example Component form Vue</h1>
    </div>
  </template>
```

Step 12 :: Go To resources/js/app.js  add line of code 

```bash 
import Example from './components/Example.vue';
```
and update this code 
```bash 
import Example from './components/Example.vue';

const app = createApp({
    components:{
        Example,
    }
});
```

Now your code look like this .
```bash 
import './bootstrap';

import {createApp } from 'vue/dist/vue.esm-bundler.js';
import Example from './components/Example.vue';

const app = createApp({
    components:{
        Example,
    }
});

app.mount("#app");
```

Step 13 :: run migration command  

```bash 
php artisan migrate 
```

Step 14 :: start live server   
```bash 
php artisan serve
```

Step 15 :: run node server.  
```bash 
npm run dev
```

Step 16 ::    Add this line of code in the AppServiceProvider.php file 
```bash 
use Illuminate\Support\Facades\Schema;

class AppServiceProvider extends ServiceProvider
{
    /**
     * Bootstrap any application services.
     */
    public function boot(): void
    {
        Schema::defaultStringLength(191);
    }
}

```

