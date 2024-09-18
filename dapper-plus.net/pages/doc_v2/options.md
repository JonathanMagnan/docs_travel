---
Title: 100+ Options to Improve Flexibility in Your Data Saving Operations 
MetaDescription: 100+ Options to Improve Flexibility in Your Data Saving Operations 
LastMod: 2024-06-27
---

# 100+ Options to Improve Flexibility in Your Data Saving Operations

// TODO: We can also give option for a column... MapWithOptions

Being able to save entity very fast is always important but being able to save entity the **WAY YOU WANT** is often more important when using [Bulk Methods](#) and [Single Methods](#).

We just saw in the previous article how to [map your entity](#) for common scenario. However, this mapping only cover a subset of all option our library support.

Before learning more about all the [options](#), let learn first how to use the method `UseBulkOptions`:

- [From Mapping](#)
- [From Connection and Transaction](#)

## From Mapping

You can use the `UseBulkOptions` method by adding it to your mapping for a specific entity type. So every time your mapping is called, the bulk operations under the hood will use those options:

```csharp
todo
```

For options that are specific for an entity type or should always be used when saved this entity type, this is the recommanded way.

[Mapping Key]

## From Connection and Transaction

You can use the `UseBulkOptions` method by chaining it as the first method to a connection or transaction. When performing this way, all bulk operations chained after will use those options.

```csharp
```

This is the recommand way for option that are more generic such as auditing and logging. Options that are generic for a type should not be used this way.

As their will be used for maybe more than 1 type, you should only specify global option here like a `BatchSize` or if you want to use the `Audit`.

You can specify options that are more generate during the connection such as `Audit`, `BatchSize`, and `Logging`.
```csharp
todo
```

## Options

In this section, we will only show the most common options. You can learn them all in our [Documention - Options & UseBulkOptions](#) article as there is too many to list them all for a getting started.

### InsertIfNotExists

We already seen this option a few times through some of our Getting Started article. The `InsertIfNotExists` option will only insert data that doesn't already exists in the database.

In this [Online Example](#), we insert some customers that already exists and some that are new and as we will see, only new customers will be inserted.

```csharp
// code
```

### InsertKeepIdentity

The `InsertKeepIdentity` will allow you to insert data but inserting at the same time the identity you provided to your entity. By default, an identity is always ignored as it's expected the database generate the value for you but sometime you might want to insert it, especially if the value is coming from an external system. It's possible to use a similar options with [Bulk Merge](#) and [Bulk Synchronizes](#) method by using their respective option `MergeKeepIdentity` and `SynchronizeKeepIdentity`.

In this [Online Example](#), we will insert some customers but by providing the `CustomerID` that should be inserted in the database

```csharp
```

### IgnoreOnMergeInsertExpression and IgnoreOnMergeUpdateExpression

Having audit columns (`CreatedDate`, `CreatedBy`, `UpdatedDate`, `UpdatedBy`) are very common for a database table. However, `Created` columns value should never be modified while `Updated` columns are ignored for the insert (not always as inserting them make also sense, but let ignore them for our scenario). So how to we handle this situation during a merge?

The option `IgnoreOnMergeInsertExpression` and `IgnoreOnMergeUpdateExpression` will let you to handle this scenario perfectly:

```csharp
```

You have similar option for the [Bulk Synchronize](#) with the `IgnoreOnSynchronizeInsertExpression` and `IgnoreOnSynchornizeUpdateExpression` options.

Usually all options having a `Expression` suffix also have their `Names` equivalent suffix. Instead of providing a lambda expression, you can now provide a list of string:

```csharp

```

## Conclusion

In this article, we only have seen an introduction to all options we provide. Fortunately (because this is a good thing), our library provide too many options to cover them all in a getting started.

We highly encourage you to read from time to time our [Documention - Options & UseBulkOptions](#), to better understand everything you can do through our library.

One major problem when providing options through the mapping is you might need different options for different scenario, so how can you handle this? Obviously that is not a problem as the next article about [Mapping Key](#) will solve this.