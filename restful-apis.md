---
description: Building RESTful  Services with Python and Flask
---

# RESTful APIs

## HyperText Transfer Protocol (HTTP)

The HyperText Transport Protocol (HTTP) is how web browsers talk to servers.

An HTTP request consists of:

- URL
- Header
- Body

## What is an API?

- **A**pplication **P**rogramming **I**nterface
- A documented way to interact with a program or service
- Defines the **requests** that you can make of the service
- Defines the **data** that you can interchange with the service
- Defines the **results** that will be returned by the service

## What is REST?

- **RE**presentational **S**tate **T**ransfer
  - A REST API describes a set of resources
  - A simple way to transfer and manipulate the state of a resource
- A service based on REST is called a RESTful service
- A RESTful service is exposed through a Uniform Resource Locator (URL)
- A client would issue a Hypertext Transfer Protocol (HTTP) request to
  manipulate it

REST is not a Remote Procedure Call (RPC) or just a bunch of verbs as URI's.

## REST Architecture

- REST is a **client-server** architecture: The client and the server provide a
  separation of concerns which allows both the client and the server to evolve
  independently as it only requires that the interface stays the same
- REST is **stateless**: The communication between the client and the server
  always contains all the information needed to perform the request. There is no
  session state in the server.
- REST is **cacheable**: The client, the server can cache resources in order to
  improve performance
- REST provides a **uniform interface** between components: All components
  follow the same rules to speak to one another
- REST is a **layered system**: Individual components cannot see beyond the
  immediate layer with which they are interacting

## What Does It Mean to Be RESTful?

- Everything is represented as a Resource
- Resource identification through URI (Uniform Resource Identifier), e.g., GET
  http://myservice.com/users/123
- Uniform interface (I should be able to guess the interface given a resource
  name)
- Self-descriptive messages are used to represent Resources (usually XML or
  JSON)
- Stateful interactions through hyperlinks
- A service based on REST is called a RESTful service

## What is a Resource?

- The fundamental concept in any RESTful API is the resource
- A resource is an object with a type, associated data, relationships to other
  resources, and a set of methods that operate on it
- Only a few standard methods are defined for the resource corresponding to the
  standard HTTP GET, POST, PUT and DELETE methods

## What Does Resource-Based Mean?

- Things vs Actions
- Nouns vs Verbs
- Not a Remote Procedure Call mechanism
- Everything is Identified by URI’s: Multiple URI’s can manipulate the same
  Resource using different HTTP Verbs

## REST Provides a Uniform Interface

- Simplifies and decouples the architecture
- Fundamental to RESTful design is an interface that almost be guessed: Perform
  CRUD on Resources
- Uses HTTP verbs (POST, GET, PUT, DELETE)
- Uses URL’s to address resources
- Uses HTTP Response (status, body)

## Stateless Applications

- Server maintains no client state
- Each request contains enough context to process the message
- Any application state must be held on the client side
- Allows easy horizontal scaling of application services

## REST API Conventions

- Use REST API conventions to provide a consistent and easy to use interface for
- REST API conventions define specific behavior for each type of HTTP method.
  Use the following guidelines as a starting point for designing your API.
  - **GET** (read) operations only query data. A GET request should never modify
    data.
  - **POST** (create) operations create new resource but do not modify existing
    resources.
  - **PUT** and **PATCH** (update) operations modify existing resources. (PUT is
    more common)
  - **DELETE** (delete) operations destroy resources

**PUT** and **DELETE** operations are idempotent, which means they have no
further effect when performed multiple times after the first time.
