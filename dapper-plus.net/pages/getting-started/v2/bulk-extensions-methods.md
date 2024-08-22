---
Title: The Quickest Way to Save Data: Mastering Bulk Extension Methods 
MetaDescription: The Quickest Way to Save Data: Mastering Bulk Extension Methods 
LastMod: 2024-06-27
---

TBD: Add also a context part???

# The Quickest Way to Save Data: Mastering Bulk Extension Methods

We have seen in our [Benchmark](#) of our getting started article that Dapper Plus was way faster then the traditional way to [insert multiple rows with Dapper](https://www.learndapper.com/saving-data/insert#dapper-insert-multiple-rows).

Our library do more then only inserting, in fact, it cover all your saving scenarios:

- [BulkInsert](/bulk-insert): This method allow you to **INSERT** miltiple rows in Bulk.
- [BulkUpdate](/bulk-update): This method allow your to **UPDATE** multiple rows in Bulk.
- [BulkDelete](/bulk-delete): This method allow your to **DELETE** multiple rows in Bulk
- [BulkMerge](/bulk-merge): This method is an **UPSERT** operation. It will **UPDATE** existing rows, and **INSERT** not existing one in bulk.
- [BulkSynchronize](/bulk-synchronize): This method is like a **MIRROR** operation, your table become exactly like your datasource. In other words, it will **UPDATE** existing rows, **INSERT** not existing one, and **DELETE** rows that are not in your datasource.

Let now see how simple is to use those bulk extension methods. Let assume we receive data from an external system that provide a list of customers with their new order and order items.

- Since customer might already exists, we will use the [BulkMerge](/bulk-merge) method
- Since Order and order item are always news, so we will use the [BulkInsert](/bulk-insert) method

```csharp
Merge Customer
Insert Order
Insert OrderItem
```

You can try yourself in this [Online Example](#)

It was easy no? Well, it will get even easier in the next section when we will learn about chaining methods.

## The Secret of Chaining Methods to write quicker and fluently

Chaining method is a way to write code and get a "flow" in it. Over the time, it become easier to write, to read, and also to maintain.

We offer 3 types of chaining methods:

- [AlsoBulk[Action]](#): Performs additional bulk actions at the last hierarchy level without changing hierarchy.
- [ThenBulk[Action]](#): Performs additional bulk actions at the last hierarchy level and moves deeper into the hierarchy.
- [Include](#): Performs included bulk actions at the last hierarchy level without changing hierarchy.

**Uhhh What?** Yeah I guess since those description was hard to write, they are probably hard to understand on first sight but be assured, you will easily understood and know how to use them once you finish with this section.

Let go step by step by starting to use only the [AlsoBulkInsert](#) method with the same example at our first one:

```
connection.BulkMerge(customers)
   .AlsoBulkInsert(customer => customer.Orders) // customers.Orders
   .AlsoBulkInsert(customer => customer.Orders.SelectMany(order => order.Items)); // customers.Orders.SelectMany(x => x.Items)
```

As you have seen, we only have to use the connection once and all other methods was chained from it. The `AlsoBulk[Action]` method (in this case `AlsoBulkInsert`) doesn't change the hierarchy level so we always had to start from the customer.

However, the `OrderItem` is more related to the `Order` (the next hierarchy level), so starting from the customer for this one doesn't really make sense and make the code hard to read.

This is now the time to introduce the [ThenBulkInsert](#) method to understand how to move the hierarchy level:

```
connection.BulkMerge(customers)
   .ThenBulkInsert(customer => customer.Orders) // customers.Orders
   .AlsoBulkInsert(order => order.Items)); // order.Items
```

We now saw that the syntax for inserting `OrderItem` is way more simple, so more readable.

Let complexify a little bit our scenario and assume we also need to insert a list of `Invoice` and `InvoiceItem` from the customer level. The problem of the previous example is using the `ThenBulkInsert` moved the hierarchy to the `Order` level so how do we go back? Well, you cannot! Those two methods alone cannot cover all scenarios as sometime you need to go back to the previous hierarchy level (the customer in this case).

So it's time to introduce the `Include` method to fix this problem:

```
connection.BulkMerge(customers)
   .Include(x => x.ThenBulkInsert(customer => customer.Orders)
      .AlsoBulkInsert(order => order.Items)))
   .Include(x => x.ThenBulkInsert(customer => customer.Invoices)
      .AlsoBulkInsert(invoice => invoice.Items)))
```

The include method allow everything which is inside the method to move the hierarchy level but it only affect what is inside the method. The Include method itself is not impacted and always stay at the same level (the customer).

Now that you have seen some explanation about how to implement them, read again the description we provided at the beginning of this section to see if they make more sense.

Once you know how to use them, you simply know how to use them. Weither you chose to use chaining method or not will not impact the performance. However, chaining bulk extension methods can surely help you to **write code faster**, make it **more readable**,  and **easier to maintain**.

## Async Method

All our bulk extension methods offer their async equivalence:

- [BulkInsertAsync](#)
- [BulkUpdateAsync](#)
- [BulkDeleteAsync](#)
- [BulkMergeAsync](#)
- [BulkSynchronizeAsync](#)

You can also chain methods as we previously such saw by always awaiting the last bulk operations to be completed:

```
await(await(await connection.BulkMergeAsync(customers)
   .ThenBulkInsertAsync(customer => customer.Orders))
   .AlsoBulkInsertAsync(order => order.Items)));
```

What about the cancellation token? To make it simpler (for you and for us), we choose to don't support it inside the method itself but by allowing you to pass it by using the `UseBulkOptions` method:

```
await(await(await connection.UseBulkOptions(x => {x.CancellationToken = cancellationToken}).BulkMergeAsync(customers)
   .ThenBulkInsertAsync(customer => customer.Orders))
   .AlsoBulkInsertAsync(order => order.Items)));
```

We will learn later in our getting started about the [UseBulkOptions](#) method.

## Conclusion

In this article, we have seen a high level of how to use our bulk extension methods, how to chain them, and finally how to use them asynchronously.

One of the major reason why people like to use [Dapper](https://www.learndapper.com/) is for his simplicity. So we did the same when we created our Bulk Extensions method in Dapper Plus. We make them very easy to use and very easy to customize through hundred of options we provide.

But before digging in the customization subject, let first see our [Single Extensions Method](#) that are **100% free**.