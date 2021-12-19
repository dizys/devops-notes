---
description: Introduction to Swagger & OpenAPI
---

# Swagger and OpenAPI

## Why is Documentation Important?

- Without documentation, no one will know how to call your API
- If no one calls your API, it has no reason to exist
- If your API has no reason to exist, you will be unemployed
- When you are unemployed, you will wish you had written documentation for your
  API ;-)

## What is Swagger?

An open-source framework for designing and describing REST APIs. Equally
suitable for both designing new APIs and documenting your existing APIs.

A Swagger specification describes the API endpoint, available resources and
operations that can be called against these resources.

### Why Swagger?

- The simple YAML format is human-readable, machine-readable and self-
  explanatory
- There is a variety of tools built around it that facilitate API development
  - Swagger `Codegen` can generate server code and client SDKs based on a
    Swagger specification
  - `Swagger UI` can render Swagger specifications to interactive API
    documentation, like the one at http://petstore.swagger.io
  - These are just a few examples of how Swagger can help API developers

### API First Approach

- Design the API First and generate a Mock
- Use Python Library like `Connexion` to Implement
- `Connexion` allows the code to comply with the API !

### Problems with using External Documentation

- A separate thing for developers to update
- Too easy for developers to change the code and forget to change the
  documentation
- Requires developers to look in a separate place for documentation instead of
  being in-line with the code

## What is SwaggerHub?

SwaggerHub is an online platform where you can design your APIs and collaborate
on them using Swagger – be it public APIs, internal private APIs or
microservices

The core principle behind Swagger and SwaggerHub is Design First, Code Later.
That is, you start by laying out your API, its resources, operations and data
models, and once the design is complete you implement the business logic

Your API definitions are saved in the SwaggerHub cloud and can be synchronized
with external systems like GitHub or Amazon API Gateway
