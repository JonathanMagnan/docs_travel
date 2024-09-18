---
Title: What is Dapper Plus? Join Thousands of Companies Boosting Performance Worldwide
MetaDescription: Learn what Dapper Plus is, who uses this library, why you need this library, how it helps you to develop faster, and how Dapper Plus helps Dapper.
LastMod: 2024-09-17
---

# Getting Started with Dapper Plus

Ready to try Dapper Plus for the first time?

After taking around 10 minutes of your time to read and try this getting started tutorial, you will already be confortable using our library in your day to day basis.

You will learn how in one line you can reduce your saving times by up **99%**, how to have access to [hundred of options](/options), and how to map your entities to save it the way **you want**.

Enough talk, let get started!

## Download Dapper Plus

The first step is obviously adding Dapper Plus to your project.

Go to our [download](/download) page and add the NuGet library to your project.

As you now know, Dapper Plus contains some free but also some paid features but don't worry, you can fully try all features of our library for free. Every month, a new [trial](/trial) is available, that expires at the end of the month. So using the latest version allow you to test our library without having to purchase it.

Don't forget also to leave us a feedback to enter in our [contest to win a free license](https://dapper-plus.net/contest)

## Using Directive

Now that the library has been added to your project, the second step is adding the `using Z.Dapper.Plus;` header directive to have access to all our extension methods. Exactly the same way you normally do with Dapper and the `using Dapper;` header directive:

```csharp
using Dapper
using Z.Dapper.Plus
```

So far, so good we did really nothing special but your project should look like this [online example](#).


## My First SingleInsert / BulkInsert

Now that we are done with the basic, let use a common scenario about inserting an order and all related order items.

To insert the order, we will use the  [SingleInsert](/single-extensions-methods#single-insert) extension method and to insert the order items, we will use the [BulkInsert](/bulk-insert) extension method.

```csharp

```

To make it even simpler, you can copy & paste the whole code directly to your project from our [online example](#)

Note that it can be done even easier using [chaining methods](/#todo), but let stick to the basic in this getting started article.

## Mapping and Mapping Key

So far so good, but what if I want to insert only a few properties and not all entity properties?

You can easily specify the [Mapping](/mapping) of your entity type to save it the way you want such as:

```csharp
TODO
```

Dapper Plus doesn't limit you to only one mapping, you can map your entity time an unlimited amount of time by using a [Mapping Key](/mapping-key) and specify it when you want to save your entity

```csharp
TODO
```
 
## Propagating the Identity Value

We have seen in our last example that we manually had to propagate the `OrderID` identity value to the order items.

This logic can be done automatically by using the [Identity Propagation](/identity-key-propagation) mapping.

```csharp

```

[options](/options)


## My First Options



## Data Source

It's now time to complicate a little bit the thing, let assume that our order and order items was imported from a CSV and loaded in a DataTable.

How to exactly handle this?

- [Data Source](/data-source)

## Conclusion

Did you success to go through all this getting started?


And this conclude our little getting started article.

It's now time to continue getting started by exploring all our [Bulk Extensions Methods](#bulk-extensions-methods) and then all our **FREE** [Single Extensions Methods](/single-extensions-methods) to better understand how to utilize Dapper Plus effectively.