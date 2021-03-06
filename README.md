# Service Layer for laravel framework

Extra simple, lightweight service manager module for laravel app

## Installation

- Require repository
 ```code
 composer require takeoo/laravel-service-layer
 ```

 - Add **\Takeoo\Service\TakeooServiceServiceProvider::class** to *config/app.php* "providers" array

 - Run:
 ```bash
   php artisan vendor:publish      
 ```


## Usage

 - Create new service class (Example.php) anywhere in your project:
```php

//Example.php


namespace  My\Service\Namespace;


use Takeoo\Service;

class MyService extends Service
{
// your code 
}

```
or if you do not want to extend Service.php just use Service trait;

```php

//Example.php


namespace  My\Service\Namespace;


use Takeoo\Service\Traits;

class MyService 
{
 use Service;
// your code 
}

```

- when you created new service class, you have to register it:
 - go to config/service.php
 - add your service to "services" array:
 
```php

'services' => [
  'Example' => \My\Service\Namespace\Example::class,
]
```


- Add Service trait to your Controller.php class (if you extend it  with all your controllers) or to every controller
 class in which you want to use Service layer
 
 
**By default all services are created as singletons, if you want to create non singleton class, provided its alias 
in "service.non-singleton" array**

## Code

In code you can call your service as:

```php

$service = $this->getService("Example");
             
```

if you want to use autocomplete (tested in JetBrains IDE) add PHPDoc above variable 

```php

/**
 * @var \My\Service\Namespace\Example $serivce
 */
$service = $this->getService("Example");
             
```

or you can always create helper functions for your commonly used services e.g: 



```php

/**
 * return \My\Service\Namespace\Example
 */
 public function getExampleService()
 {
  return $this->getService("Example");
 }             

```



