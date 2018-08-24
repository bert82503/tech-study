

Best Practices in API Design API设计的最佳实践
============================
> Keshav Vasudevan, 2016.10.10

Good API design is a topic that comes up a lot for teams that are trying to perfect their API strategy.
**The benefits of a well-designed API** include: **improved developer experience**, **faster documentation**,
and **higher adoption for your API**. But **what exactly goes into good API design?**
In this blog post, I will detail **a few best practices for designing RESTful APIs**.
精心设计的API的好处包括：改善的开发者体验，更快的文档记录，更高的API采用率。


### Characteristics of a well-designed API 精心设计的API的特征
In general, an effective API design will have the following characteristics:
* **Easy to read and work with 易于阅读和使用**: A well designed API will be easy to work with,
  and its resources and associated operations can quickly be memorized by developers who work with it constantly.
* **Hard to misuse 难以滥用**: Implementing and integrating with an API with good design will be a straightforward process,
  and writing incorrect code will be a less likely outcome. It has informative feedback, and does not enforce strict guidelines on the API’s end consumer.
* **Complete and concise 完整而简洁**: Finally, a complete API will make it possible for developers to make full-fledged applications against the data you expose.
  Completeness happens over time usually, and most API designers and developers incrementally build on top of existing APIs.
  It is an ideal which every engineer or company with an API must strive towards.


### Collections, Resources, and their URLs

#### Understanding resources and collections 理解资源和集合
**Resources are fundamental to the concept of REST.**
**A resource is an object** that’s important enough to be referenced in itself.
A resource has **data, relationships to other resources, and methods** that operate against it to allow for accessing and manipulating the associated information.
**A group of resources is called a collection.**
The contents of collections and resources depend on your organizational and consumer requirements.
**A Uniform Resource Locator (URL) identifies the online location of a resource.**
This URL points to the location where your API’s resources exist. The base URL is the consistent part of this location.

#### Nouns describe URLs better 名词描述URL更好
The base URL should be **neat, elegant and simple** so that developers using your product can easily use them in their web applications.
A long and difficult-to-read base URL is not just bad to look at, but can also be prone to mistakes when trying to recode it.
Nouns should always be trusted. There’s no rule on keeping the resource nouns singular or plural, though it is advisable to keep collections plural.
**Having the same plurality across all resources and collections respectively for consistency** is **good practice**.


### Describe resource functionality with HTTP methods 使用HTTP方法描述资源的功能
All resources have a set of methods that can be operated against them to work with the data being exposed by the API.
RESTful APIs comprise majorly of HTTP methods which have well defined and unique actions against any resource.


### Responses

#### Give feedback to help developers succeed 提供反馈以帮助开发人员成功
Providing good feedback to developers on how well they are using your product goes a long way in improving adoption and retention.
Every client request and server side response is a message and, in an ideal RESTful ecosystem, these messages must be self descriptive.
Good feedback involves positive validation on correct implementation,
and an informative error on incorrect implementation that can help users debug and correct the way they use the product.
For an API, **errors are a great way to provide context to using an API.**
**Align your errors around the standard HTTP codes.**
Incorrect, client side calls should have 400-type errors associated with them.
If there are any server side errors, then a suitable 500 response must be associated with them.
A successful method used against your resource should return a 200-type response.
For additional information, [check out this REST API tutorial](http://www.restapitutorial.com/httpstatuscodes.html).
In general, there are three possible outcomes when using your API:

1. The client application behaved erroneously (client error - 4xx response code)
2. The API behaved erroneously (server error - 5xx response code)
3. The client and API worked (success - 2xx response code)


### Requests

#### Handle complexity elegantly 优雅地处理复杂问题
The data you’re trying to expose can be characterized by a lot of properties which could be beneficial for the end consumer working with your API.
These properties describe the base resource and isolate specific assets of information that can be manipulated with the appropriate method.


[原文](https://swagger.io/blog/api-design/api-design-best-practices/)

