# Object Design

## Notes

From "Java Modeling in Color with UML" pg 41:

Where to put a method? Take a feature statement, `<action> the <result> <by|for|of|to> a <moment-interval|role|description|part, place, thing>`. Put the initiating method in the corresponding class.

Here we want to "calculate the anticipated total of an RFQ." So we put the initiating method in the RFQ class.

* [East-oriented](http://jamesladdcode.com/2011/08/10/east-example-code/)
* [Tell, Don't Ask](https://pragprog.com/articles/tell-dont-ask)
* Commands down the stack, notifications up the stack
* Event-based Programming
