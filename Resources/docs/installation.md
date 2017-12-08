## Installation ##

### For Symfony Framework >= 2.3 ###

Require the bundle and its dependencies with composer:

```bash
$ composer require php-amqplib/rabbitmq-bundle
```

Register the bundle:

```php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        new OldSound\RabbitMqBundle\OldSoundRabbitMqBundle(),
    );
}
```

Enjoy !

### For a console application that uses Symfony Console, Dependency Injection and Config components ###

If you have a console application used to run RabbitMQ consumers, you do not need Symfony HttpKernel and FrameworkBundle.
From version 1.6, you can use the Dependency Injection component to load this bundle configuration and services, and then use the consumer command.

Require the bundle in your composer.json file:

```
{
    "require": {
        "php-amqplib/rabbitmq-bundle": "~1.6",
    }
}
```

Register the extension and the compiler pass:

```php
use OldSound\RabbitMqBundle\DependencyInjection\OldSoundRabbitMqExtension;
use OldSound\RabbitMqBundle\DependencyInjection\Compiler\RegisterPartsPass;

// ...

$containerBuilder->registerExtension(new OldSoundRabbitMqExtension());
$containerBuilder->addCompilerPass(new RegisterPartsPass());
```

### Warning - BC Breaking Changes ###

* Since 2012-06-04 Some default options for exchanges declared in the "producers" config section
  have changed to match the defaults of exchanges declared in the "consumers" section.
  The affected settings are:

  * `durable` was changed from `false` to `true`,
  * `auto_delete` was changed from `true` to `false`.

  Your configuration must be updated if you were relying on the previous default values.
* Since 2012-04-24 The ConsumerInterface::execute method signature has changed
* Since 2012-01-03 the consumers execute method gets the whole AMQP message object and not just the body. See the CHANGELOG file for more details.
