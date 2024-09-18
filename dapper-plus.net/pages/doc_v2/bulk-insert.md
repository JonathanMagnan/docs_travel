---
Title: Dapper Bulk Insert | The Fastest Way to Insert a List in Dapper
MetaDescription: Optimize Dapper insert performance with Dapper Plus Bulk Insert Extensions. Easily insert multiple rows in a database from a list with customizable options. Improve your database operations - try it now.
LastMod: 2024-09-11
---

# Dapper Bulk Insert: Fastest Way in Dapper to Insert Multiple Rows

The Dapper Plus `BulkInsert` extension method lets you insert rows around **75x faster** than the traditional way to insert with Dapper.

```csharp
// Easy to use
connection.BulkInsert(orders);

// Easy to customize
connection.UseBulkOptions(options => options.InsertIfNotExists = true)
          .BulkInsert(orders);
```
[Online Example](https://dotnetfiddle.net/ltIqrC)

It is really that fast? Yes, Dapper Plus ensure to use the most effecient know techniques depending on your [providers](/supported-providers) to ensure your data is inserted as fast as possible.

| Operations      | 50 Entities | 2,000 Entities | 5,000 Entities |
| :-------------- | -------------: | -------------: | -------------: |
| Dapper Insert  | 1,200 ms       | 2,400 ms       | 6,000 ms       |
| BulkInsert      | 50 ms          | 55 ms          | 75 ms          |

Don't trust those internet numbers, use our [online example](https://dotnetfiddle.net/CqTwfr) on .NET Fiddle and see the performance difference by yourself.

The BulkInsert method allow you to reduce saving times by up to 99% when saving a large number of entities but even for 50 rows, it reduce saving times by 88% which can dramatically change in a positive ways the user experience you provide to your client.

## Getting Started with Bulk Insert

Bla bla bla... big example and refers to the bulk extensions article???

This section is a very quick summary of what we saw in our article [Getting Started - Bulk Extensions](/bulk-extensions-methods). For more details, please refer at this article.

### Async

```csharp
```

### Chaining

```csharp
```

### Connection / Context

```csharp
```

### DataSource

```csharp
```

### Providers

```csharp
```

## Options

// TBD: What to do with "specialized" options... we can show them here and for Single Insert refer to this article

## Scenario

In this section, we include only basic scenario. Click on the example title to expend it to see the description and online example.

See the following article: [Bulk Insert - Advanced Scenario](#) for additional examples

<!--- details
#####  Bulk Insert Standard

details -->

## Conclusion
