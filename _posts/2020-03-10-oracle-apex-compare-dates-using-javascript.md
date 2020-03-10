---
title: Oracle Apex: Compare dates using JavaScript
published: true
---

In this tutorial, you will learn how to compare dates in Oracle Apex using the JavaScript.

There was a requirement to highlight the date with red if the billing date value is less than the current date.

## Create an Item to Store Current Date

So first, I have created a hidden item P2_CURRDATE to store the current date as default on page initialization. Then added the following PL/SQL expression for the Default setting:

```plsql
trunc(sysdate)
```

## Create a Dynamic Action

Then I have created a dynamic action on the date field to which I need to highlight with red. 

The dynamic action event type is Change and add the following client side condition as JavaScript expression:

```js
new Date($v("P2_BILLDATE")).getTime() < new Date($v("P2_CURRDATE")).getTime()
```

### Then added a true action as following:

Action: **Set Style**
Style Name: **color**
Value: **red**

### Also created a false action:

Action: **Set Style**
Style Name: **color**
Value: **black**

Now save the changes and run the page to test.
