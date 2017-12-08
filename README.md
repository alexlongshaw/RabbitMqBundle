# RabbitMqBundle #

[![Join the chat at https://gitter.im/php-amqplib/RabbitMqBundle](https://badges.gitter.im/php-amqplib/RabbitMqBundle.svg)](https://gitter.im/php-amqplib/RabbitMqBundle?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) [![Build Status](https://secure.travis-ci.org/php-amqplib/RabbitMqBundle.png?branch=master)](http://travis-ci.org/php-amqplib/RabbitMqBundle)

## About ##

The RabbitMqBundle incorporates messaging in your application via [RabbitMQ](http://www.rabbitmq.com/) using the [php-amqplib](http://github.com/php-amqplib/php-amqplib) library.

The bundle implements several messaging patterns as seen on the [Thumper](https://github.com/php-amqplib/Thumper) library. Therefore publishing messages to RabbitMQ from a Symfony controller is as easy as:

```php
$msg = array('user_id' => 1235, 'image_path' => '/path/to/new/pic.png');
$this->get('old_sound_rabbit_mq.upload_picture_producer')->publish(serialize($msg));
```

Later when you want to consume 50 messages out of the `upload_pictures` queue, you just run on the CLI:

```bash
$ ./app/console rabbitmq:consumer -m 50 upload_picture
```

All the examples expect a running RabbitMQ server.

This bundle was presented at [Symfony Live Paris 2011](http://www.symfony-live.com/paris/schedule#session-av1) conference. See the slides [here](http://www.slideshare.net/old_sound/theres-a-rabbit-on-my-symfony).

## Documentation ##

- [Installation](Resources/docs/installation.md)
- [Usage](Resources/docs/usage.md)
- [Other Commands](Resources/docs/other-commands.md)

## How To Contribute ##

To contribute just open a Pull Request with your new code taking into account that if you add new features or modify existing ones you have to document in this README what they do. If you break BC then you have to document it as well. Also you have to update the CHANGELOG. So:

- Document New Features.
- Update CHANGELOG.
- Document BC breaking changes.

## License ##

[MIT License](Resources/meta/LICENSE.md)

## Credits ##

The bundle structure and the documentation is partially based on the [RedisBundle](http://github.com/Seldaek/RedisBundle)
