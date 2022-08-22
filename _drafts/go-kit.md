---
layout: post
title:  "Introduce to Go Kit"
author: kean
image: assets/images/golang-banner.png
categories:
  - "golang"
---

Introduce to Go Kit

There are 3 major components in the Go kit based application architecture.
- Transport layer: the transport domain
- Endpoint layer: an RPC method
- Service layer: business logic layer

There is many kind of transports: HTTP, gRPC, NATS, Thrift, AMQP...
One single microservice can support multiple transports.
Transport domain is bound to concrete transports

Each endpoint exposes the service method to the outside world using Transport layer, RPC is the primary message pattern.

Business logic modelled as interfaces, based on Clean Architecture or Hexagon Architecture, have no knowledge about endpoint, concrete transports and encoding/decoding.

There are 2 types of middleware in Go Kit: Endpoint Middleware and Service Middleware.
Use Endpoint Middleware for transport-domain concern: circuit breaker, rate limiter
Use Service Middleware for business-domain concern: logging, instrumentation

