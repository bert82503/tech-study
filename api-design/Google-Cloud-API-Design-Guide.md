

Google Cloud API Design Guide
=============================
Current Version of the API Design Guide: **2017-02-21**


### Introduction


### Resource Oriented Design/面向资源的设计
The **goal** for this Design Guide is to help developers design **simple, consistent and easy-to-use** networked APIs.

The architectural style of [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)
was first introduced in 2000, primarily designed to work well with HTTP/1.1.
Its **core principle** is to **define named resources** that can be manipulated using a small number of **methods**.
The resources and methods are known as nouns and verbs of APIs.

On the Internet, HTTP REST APIs have been recently hugely successful.
In 2010, about 74% of public network APIs were HTTP REST APIs.

#### What is a REST API?
A REST API is modeled as _collections of individually-addressable resources_ (the nouns of the API).
**Resources** are referenced with their [resource names](https://cloud.google.com/apis/design/resource_names)
and manipulated via a small set of **methods** (also known as verbs or operations).

#### Design flow
The Design Guide suggests taking the following steps when designing resource-oriented APIs
(more details are covered in specific sections below):
* Determine what **types of resources** an API provides. 确定API提供的资源类型
* Determine the **relationships between resources**. 确定资源之间的关系
* Decide the **resource name schemes based on types and relationships**. 根据类型和关系确定资源名称方案
* Decide the **resource schemas**. 确定资源模式
* Attach minimum **set of methods** to resources. 将最少的方法集附加到资源

#### Resources
A resource-oriented API is generally modeled as a **resource hierarchy**,
where _each node is either a simple resource or a collection resource_.
For convenience, they are often called as a resource and a collection, respectively.
* **A collection** contains **a list of resources of the `same type`**. For example, a user has a collection of contacts.
* **A resource** has **some state and zero or more sub-resources**.
  Each sub-resource can be either a simple resource or a collection resource.

#### Methods
The `key characteristic of a resource-oriented API` is that it emphasizes **resources (data model)** over the methods performed on the resources (functionality).
A typical resource-oriented API exposes a large number of resources with a small number of methods.
The methods can be either the standard methods or custom methods.
For this guide, the standard methods are: `List`, `Get`, `Create`, `Update`, and `Delete`.


### Resource Names/资源名称


### Standard Methods


### Standard Fields


### Errors


### Naming Conventions


### Design Patterns


### Documentation


### Versioning/版本
Since one API service may provide multiple API interfaces, the API versioning strategy applies at the API interface level, not at the API service level.

Networked APIs **should** use [Semantic Versioning](https://semver.org/).
Given a version number `MAJOR.MINOR.PATCH`, increment the:
1. `MAJOR` version when you make `incompatible API changes`
2. `MINOR` version when you `add functionality` in a backwards-compatible manner
3. `PATCH` version when you make backwards-compatible `bug fixes`


### Compatibility


### Changelog


[原文](https://cloud.google.com/apis/design/)

