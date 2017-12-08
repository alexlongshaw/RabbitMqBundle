## Other Commands ##

### Setting up the RabbitMQ fabric ###

The purpose of this bundle is to let your application produce messages and publish them to some exchanges you configured.

In some cases and even if your configuration is right, the messages you are producing will not be routed to any queue because none exist. The consumer responsible for the queue consumption has to be run for the queue to be created.

Launching a command for each consumer can be a nightmare when the number of consumers is high.

In order to create exchanges, queues and bindings at once and be sure you will not lose any message, you can run the following command:

```bash
$ ./app/console rabbitmq:setup-fabric
```

When desired, you can configure your consumers and producers to assume the RabbitMQ fabric is already defined. To do this, add the following to your configuration:

```yaml
producers:
    upload_picture:
      auto_setup_fabric: false
consumers:
    upload_picture:
      auto_setup_fabric: false
```

By default a consumer or producer will declare everything it needs with RabbitMQ when it starts.
Be careful using this, when exchanges or queues are not defined, there will be errors. When you've changed any configuration you need to run the above setup-fabric command to declare your configuration.
