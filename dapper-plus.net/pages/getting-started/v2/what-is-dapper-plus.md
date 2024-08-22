---
Title: What is Dapper Plus? Join Thousands of Companies Boosting Performance Worldwide
MetaDescription: What is Dapper Plus? Join Thousands of Companies Boosting Performance Worldwide 
LastMod: 2024-06-27
---

# What is Dapper Plus? Join Thousands of Companies Boosting Performance Worldwide

When I discovered [Dapper](https://www.learndapper.com/), I fall in love with this library as it was making my life so much easier. I had only write my query and **BOOM!** Dapper was handling everything for me... From openning the connection, creating/executing the command, to mapping the result.

Like every library, I discovered eventually that Dapper have also its limitation.

One day, the job I had to do was to import more than 10,000 rows in my database. Since Dapper already support [inserting multiple rows in a database](https://www.learndapper.com/saving-data/insert#dapper-insert-multiple-rows), the job was already completed right? **WRONG!** This is at this moment I discovered that Dapper have a performance limitations by making one database round-trips for every entity I had to save instead of bulking them.

Obviously, I didn't want my end user to have to wait several seconds for this import operations, who would want to wait this time? I barely had the patience myself to wait that long when I was coding this import feature.

This is when and why I created Dapper Plus with the same goal as Dapper in my mind. So **What is Dapper Plus?** A library you can use with or without Dapper that make your life easier by providing a easy to use API that extend your connection. Dapper Plus handle everything for you... From openning the connection, creating/executing the most optimized saving command, to outputting values to your entities.


The most well knows methods are our bulk operations:
- [BulkInsert](/bulk-insert)
- [BulkUpdate](/bulk-update)
- [BulkDelete](/bulk-delete)
- [BulkMerge](/bulk-merge)
- [BulkSynchronize](/bulk-synchronize)
- And more


As we just said, Dapper Plus is very easy to get started with, here is an example how quickly it is:

```csharp
var connection = new SqlConnection(FiddleHelper.GetConnectionStringSqlServer());
		
// Easy to use
connection.BulkInsert(customers);

// Easy to customize
connection.UseBulkOptions(options => options.InsertIfNotExists = true)
          .BulkInsert(customers);
```

Yup, the code speak by itself!

- The first `BulkInsert` will insert all customers in your database 
- The second `BulkInsert` will insert only customers that doesn't already exists.

Click on this [Online Example](#) link and see this code in action.

You will see through our getting started, that we offer link so you can directly try the code live on [.NET Fiddle](https://dotnetfiddle.net/). You can also browse all our example and those created by the community in our [Online Examples](/online-examples) section.

## Who Uses This Library? Anyone and Everyone!

Me, you, governement, bank, school, etc! Over the years, all our bulk operations library including [Entity Framework Extensions](https://entityframework-extensions.net/) reached more than **5000 happy customers** in all type of industries including many in the fortune 100. I mean, we even have 2 well know spatial agency that use our library. So when our library is used  even for space program, we are everywhere!

Our offer is simple: **providing performance and flexibility**. That's what all developer and company want to reduce their developement/maintenance cost and getter a better client satisfaction (so more clients for **YOUR** entreprise!).

Why so many company trust us? Problably because we are proud to offer our **outstanding customer support**. We offer bulk extensions methods through our libraries since 2014 and we keep actively maintenaing them.

## Why You Need This Library to Save Your Data 95% Faster

We said earlier that Dapper Plus was faster then the tradinional way to insert in Dapper, but how much faster?

| Library | 2,000 rows | 5,000 rows | 10,000 rows |
| :------ | :--------: | :--------: | :---------: |
| Dapper ||||
| Dapper Plus ||||

**You don't believe our numbers?** Why you don't try it by yourself by running this [Live Benchmark](https://dotnetfiddle.net/nI4D4E). You simply have to open the link, click on the "Run" button. and let the numbers speaking by themself!

[TBD Here later...]
> Now that you trust our numbers, that mean 
> So, we can see in this example that Dapper insert **XYZ** rows per seconds while Dapper Plus insert **XYZ** rows per second.
> In other words, that mean Dapper Plus is **XYZ%** faster than the traditional way to insert!!!

Some developer will argue that you can use some alternatives techniques to insert faster than Dapper (obviously since we use those techniques!) but **remember:** One of the major advantage of our library is making your life easier.

If you ask to those same developer how to write a merge (insert or update) operations, that will take them several minutes and they will even need to search on Google how to make a MERGE statement (I know I still have to do it every time). While in other hands, you can simply call [BulkMerge](/bulk-merge). Even for explaining and writing code, we are still faster!

Saving your data as fast as possible is very important to make your application **responsive**, and that's exactly what our library offers.

## Who Else Wants to Develop Faster With More Flexibility? 

Unlike Dapper, a major difference with Dapper Plus is you don't have to write your own SQL, the library handle everything for you!

On my side, when I need to query my database, I **WANT** to write my own SQL (The complex one). I can make sure only the minimum columns is selected, and the `SELECT` statement is optimized especially if I need to `JOIN` multiple tables or need to do some `GROUP BY`. Then I let Dapper handle perfectly all the rest for me.

However, I find writing my `INSERT`, `UPDATE`, and `DELETE` statement boring as this is pretty much always the same pattern minus a few different options.

So letting Dapper Plus writing those saving SQL statement for you come with some major advantage:

- **Ease of Development:** The code is faster to write. Increasing your efficently
- **Ease of Maintenance:** The code is easier to read and to modify. Reducing the learning curve for new developers
- **Increased Accuracy:** The code is already well tested for you. Reduing making human mistake
- **Increased Scalability:** The code is already coded to be optimized. Increasing your application responsivity for your client.

There is multiples others avantages. But in short, your code is faster and **YOU** code faster allowing yourself to focus more on strategic tasks that require your expertise and less about writing those boring SQL.

While performance is always the main goal for Dapper Plus, providing you flexibility is another one. You will learn that Dapper Plus give you access to [hundred of options](#) enhancing even more those aedvantages that we just saw. Even when you looked at our first example, you understood with a blink of a eye what was the purpose of this option `InsertIfNotExists = true`.

We always like to say that our library is: **Easy to use, easy to customize!**

## Did You Know? We Are a Major Sponsor of Dapper

Our company [ZZZ Projects](https://zzzprojects.com/) was already a major contributor of Dapper since 2014 by creating and maintaining the best tutorial about it:

- [Learn Dapper](https://www.learndapper.com/)
- [Dapper Tutorial](https://dappertutorial.net/)

However we feel that was not enough. Let be honest, even if our tutorial have played maybe a small part in the growing popularity of Dapper, in exchange Dapper have contributed without any doubt for the success of Dapper Plus.

Since 2024, our company is proud to be a [major sponsor of Dapper](https://dapperlib.github.io/Dapper/dapperplus) ensuring that this library can keep to be **actively maintained** and being **100% free**.

So purchasing Dapper Plus directly benefits and help Dapper as well. You can learn more about our mission about [adding value to the .NET Community](#)

## Conclusion 

As the first article of our Getting Started section, we barely touched the full potential of Dapper Plus. We understand now more how Dapper Plus is related to Dapper and how both libraries help each others in different ways.

We have seen for basic scenario, our library is so simple to use that you can already [download it](/download) and start to use it.

It's now time to continue to get started by exploring our [Bulk Extensions Methods](#todo) and then our FREE [Single Extensions Methods](#) to better understand how to use this library.