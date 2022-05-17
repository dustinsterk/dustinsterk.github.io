---
title: "Google Sheets - How to return multiple values in a single call with ImportXML"
date: "2015-06-23"
categories: [Google]
published: true
---

![](../images/sheets.jpg)

I have been tinkering with Google Sheets and building a document that can automatically pull data from other websites.

I stumbled across the importXML() function.  After some time I realized to optimize the number of calls to a specific URL, you can return multiple values in a single call using the XPath concat() function.

For example, to retrieve food information (protein, carbs, fat, and calories) you can do the following which will return all of the values seperated by a '|' :

**Cell A1 Formula:**
```

=importXML("http://www.calorieking.com/foods/calories-in-pizzas-14-pizza-cheese-topping-original-crust\_f-ZmlkPTU0ODQ2.html","concat(//tr\[@class='protein'\]/td\[2\], '| ', //tr\[@class='total-carbs'\]/td\[2\], '| ', //tr\[@class='total-fat'\]/td\[2\], '| ', //tr\[@class='alcohol'\]/td\[2\], '| ', //option\[@value='0'\], '| ', //span\[@id='mCal'\]\[@class='calorie-display'\])")

```

From here you can then split the values into seperate columns by doing the following:

**Cell B1 Formula:**

```

=split(A1,"|")

```

Hope this helps.
