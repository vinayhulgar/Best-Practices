# Best-Practices
Repo on some of the best practices

Continuous Learning
Here’s a list of ways to keep you learning. Many of these can be found on the Internet for free:

• Read books, magazines, blogs, Twitter feeds, and websites. If you want to go deeper into a subject, consider joining a mailing list or newsgroup.

• If you really want to get immersed in a technology, get hands on—write some code.

• Always try to work with a mentor, as being the top guy can hinder your education. Although you can learn something from anybody, you can learn a whole lot more from someone smarter or more experienced than you. If you can’t find a mentor, consider moving on.

• Use virtual mentors. Find authors and developers on the Web who you really like and read everything they write. Subscribe to their blogs.

• Get to know the frameworks and libraries you use. Knowing how something works makes you know how to use it better. If they’re open source, you’re really in luck. Use the debugger to step through the code to see what’s going on under the hood. You’ll get to see code written and reviewed by some really smart people.
Whenever you make a mistake, fix a bug, or run into a problem, try to really understand what happened. It’s likely that someone else ran into the same problem and posted it on the Web. Google is really useful here.

• A good way to learn something is to teach or speak about it. When people are going to listen to you and ask you questions, you’ll be highly motivated to learn. Try a lunch-’n’-learn at work, a user group, or a local conference.

• Join or start a study group (à la patterns community) or a local user group for a language, technology, or discipline you are interested in.

• Go to conferences. And if you can’t go, many conferences put their talks online for free.

• Long commute? Listen to podcasts.

• Ever run a static analysis tool over the codebase or look at the warnings in your IDE? Understand what they’re reporting and why.

• Follow the advice of the Pragmatic Programmers* and learn a new language every year. At least learn a new technology or tool. Branching out gives you new ideas you can use in your current technology stack.

• Not everything you learn has to be about technology. Learn the domain you’re working in so you can better understand the requirements and help solve the business problem. Learning how to be more productive — how to work better — is another good option.

• Go back to school.


Encapsulate Behaviour, Not Just State
In systems theory , containment is one of the most useful constructs when dealing with large and complex system structures. In the software industry, the value of containment or encapsulation is well understood. Containment is supported by programming language constructs such as subroutines and functions, modules and packages, classes, and so on. Modules and packages address the larger-scale needs for encapsulation, while classes, subroutines, and functions address the more fine-grained aspects of the matter. Over the years, I have discovered that classes seem to be one of the hardest encapsulation constructs for developers to get right. It’s not uncommon to find a class with a single 3,000-line main method, or a class with only set and get methods for its primitive attributes. These examples demonstrate that the developers involved have not fully understood object-oriented thinking, having failed to take advantage of the power of objects as modeling constructs.
 
For developers familiar with the terms POJO (Plain Old Java Object) and POCO (Plain Old C# Object or Plain Old CLR Object), this was the intent in going back to the basics of OO as a modeling paradigm—the objects are plain and simple, but not dumb.

An object encapsulates both state and behavior, where the behavior is defined by the actual state. Consider a door object. It has four states: closed, open, closing, opening. It provides two operations: open and close. Depending on the state, the open and close operations will behave differently. This inherent property of an object makes the design process conceptually simple. It boils down to two simple tasks: allocation and delegation of responsibility to the different objects including the interobject interaction protocols.
 
How this works in practice is best illustrated with an example.
Let’s say we have three classes: Customer, Order, and Item. A Customer object is the natural placeholder for the credit limit and credit validation rules. An Order object knows about its associated Customer, and its addItem operation delegates the actual credit check by calling customer.validateCredit(item.price()). If the postcondition for the method fails, an exception can be thrown and the purchase aborted.

Less experienced object-oriented developers might decide to wrap all the business rules into an object very often referred to as OrderManager or OrderService. In these designs, Order, Customer, and Item are treated as little more than record types. All logic is factored out of the classes and tied together in one large, procedural method with a lot of internal if-then-else constructs. These methods are easily broken and are almost impossible to maintain. The reason? The encapsulation is broken. So, in the end, don’t break the encapsulation, and use the power of your programming language to maintain it.


