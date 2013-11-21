---
layout: post
title: "Apache Solr ScriptTransformer and the int Type"
description: ""
category: "solr"
tags: [solr, javascript, rhino]
---
{% include JB/setup %}

#### The Problem

We have a field with int as its type in one of our solr cores. It looks like this:

{% highlight xml %}
<field name="property_type" type="int" indexed="true" stored="true" />
{% endhighlight %}

Solr DIH is used to import data from mysql into the solr index. In the db-data-config.xml, we use a script transformer to make the indexed data more readable for the client. Eventually the property_type will be set with a calculated value. The code was originally like this:

{% highlight javascript %}
var property_type = 1; //In the real code, property_type was calculated. This is just to show that it is an integer. 
row.put("property_type", property_type);
{% endhighlight %}

When I tried to run a full-import command on the core. Solr kept complaining about wrong field values of property_type.

{% highlight text %}
org.apache.solr.common.SolrException: ERROR: [doc=house:2446] Error adding field 'property_type'='2.0'
{% endhighlight %}

Apparently the solr script transformer transforms the integer into a floating point number. But the question was why. 

#### The Cause

After a bit of [digging](http://stackoverflow.com/a/15528721), I found out that this is because JavaScript has only one numerical type - [Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number) which is analogous to Java's [Double](http://docs.oracle.com/javase/7/docs/api/java/lang/Double.html) type. Since <code>row.put()</code> expects the second parameter to be an object, the rhino script engine must have converted the Number object to a Double. I downloaded and ran [rhino](https://github.com/mozilla/rhino) to confirm the theory.

{% highlight javascript %}
Rhino 1.7 release 4 2012 06 18
js> var i = 2;
js> print(i);
2
js> var row = new java.util.HashMap();
js> row.put("prop", i);
null
js> row.get("prop");
2.0
> row.put("prop", i.toString());
2.0
js> row.get("prop");
2
{% endhighlight %}


#### The Solution

Just like many other problems, the solution is easy once the cause is found. In this case, converting the integer to a string before setting the field value fixes the problem. Luckily solr doesn't have problem using a string value for an int-typed field.

{% highlight js %}
row.put("property_type", property_type.toString();
{% endhighlight %}


