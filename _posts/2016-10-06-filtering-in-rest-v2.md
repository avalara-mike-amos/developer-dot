---
layout: post
title: Filtering in AvaTax REST v2
date: 2016-10-06 10:00
author: Ted Spence
comments: true
categories: [Sales Tax APIs]
product: blog
doctype: blog
disqus: 1
---

# I'm sure I left this somewhere...

The REST API pattern is designed to make it easy to store and retrieve data.  Every piece of data in REST is assigned a single unique URL - and you can always fetch that item back by retrieving its URL.  It works a bit like this:

<table class="styled-table">
    <tr>
        <th>Note</th>
        <th>HTTP Action</th>
        <th>Request</th>
        <th>Result</th>
    </tr>
    <tr>
        <td>Store data by **POST**ing to a URL.</td>
        <td><pre>POST /api/v2/companies</pre></td>
        <td>In the request body: <pre>{ "name": "Bob's Artisan Pottery" }</pre></td>
        <td>In the HTTP headers: <pre>Location: /api/v2/companies/123</pre></td>
    </tr>
    <tr>
        <td>Fetch data by **GET**ting from that URL.</td>
        <td><pre>GET /api/v2/companies/123</pre></td>
        <td></td>
        <td>In the response body: <pre>{ "name": "Bob's Artisan Pottery" }</pre></td>
    </tr>
</table>

This works great as long as you know the URL of the thing.  How do you find something if you don't know what it is?

# Listing All Objects

Let's say you have three companies, and these are their URLs:
<ul class="normal">
<li><pre>/api/v2/companies/123</pre></li>
<li><pre>/api/v2/companies/456</pre></li>
<li><pre>/api/v2/companies/789</pre></li>
</ul>

You can fetch all of them back as follows:
### Request
```
GET /api/v2/companies
```
### Result
```javascript
[ 
    { "id": 123, ... }, 
    { "id": 456, ... }, 
    { "id": 789, ... }
]
```

Voila! In AvaTax, your credentials will automatically allow you to access all companies within your account with no extra hassle.  The query to <pre>GET /api/v2/companies</pre> will return all three objects.  If you only have three objects this is the easiest way to find what you want.

# What if I have more than three objects?

Sooner or later it will be a nuisance to fetch everything.  To reduce the number of records you get, you'll have to start filtering.

In the <a href="https://github.com/Microsoft/api-guidelines/blob/master/Guidelines.md#97-filtering">Microsoft REST API Guidelines</a>, Microsoft established a nice and friendly standard for finding objects.  You can use a simplified search syntax to find something you want.  Let's say you want to search for the company whose names start with 'A':

### Request
```
GET /api/v2/companies?$filter=name ge A and name lt B
```
### Result
```javascript
[ 
    { "name": "Aardvark" ... }, 
    { "name": "Aaron's Antiques" }, 
    { "name": "Andes Climbing Supply" }
]
```

You can use these same types of filters in lots of different ways - here are a few samples:

<ul class="normal">
<li><pre>GET /api/v2/companies?$filter=name eq 'Bob''s Artisan Pottery'</pre></li>
<li><pre>GET /api/v2/companies?$filter=id gt 100000</pre></li>
<li><pre>GET /api/v2/companies?$filter=isTest eq true and isActive eq true</pre></li>
</ul>

# What filtering options are available?

Avalara supports all filtering language options specified by Microsoft in its standard, plus a few extra items.  We support some useful features like the ability to nest filter statements - you can use AND and OR clauses to construct more complex searches.  You can retrieve a large number of items in a list.

The full list of <a href="/avatax/filtering-in-rest">available filtering options is here</a>.  Please let us know what you think!

Happy Filtering!

--Ted Spence, Director, AvaTax Core Engine