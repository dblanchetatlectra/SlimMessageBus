# Nats transport provider for SlimMessageBus <!-- omit in toc -->

Please read the [Introduction](intro.md) before reading this provider documentation.

- [Underlying Nats client](#underlying-nats-client)
- [Configuration](#configuration)
- [Message Serialization](#message-serialization)

## Underlying Nats client

This transport provider uses [Nats.Nets](https://www.nuget.org/packages/NATS.Net) client to connect to the Nats broker.

## Configuration

The configuration is arranged via the `.WithProviderNats(cfg => {})` method on the message bus builder.

@[:cs](../src/Samples/Sample.Nats.WebApi/Program.cs,ExampleConfiguringMessageBus)

The `NatsMessageBusSettings` property is used to configure the underlying [Nats.Net library client](https://github.com/nats-io/nats.net).
Please consult the Nats.Net library docs for more configuration options.

## Message Serialization

Nats offers native serialization functionality. This functionality conflicts with the serialization functionality provided by SlimMessageBus. We have chosen to leave the responsibility for serialization to SlimMessageBus and leave the default configuration of Nats serialization, which is raw serialization. This means that the message body is serialized as a byte array.