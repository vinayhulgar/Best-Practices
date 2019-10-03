# Best-Practices
Repo on some of the best practices

# Continuous Learning:
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


# Encapsulate Behaviour, Not Just State:
In systems theory , containment is one of the most useful constructs when dealing with large and complex system structures. In the software industry, the value of containment or encapsulation is well understood. Containment is supported by programming language constructs such as subroutines and functions, modules and packages, classes, and so on. Modules and packages address the larger-scale needs for encapsulation, while classes, subroutines, and functions address the more fine-grained aspects of the matter. Over the years, I have discovered that classes seem to be one of the hardest encapsulation constructs for developers to get right. It’s not uncommon to find a class with a single 3,000-line main method, or a class with only set and get methods for its primitive attributes. These examples demonstrate that the developers involved have not fully understood object-oriented thinking, having failed to take advantage of the power of objects as modeling constructs.
 
For developers familiar with the terms POJO (Plain Old Java Object) and POCO (Plain Old C# Object or Plain Old CLR Object), this was the intent in going back to the basics of OO as a modeling paradigm—the objects are plain and simple, but not dumb.

An object encapsulates both state and behavior, where the behavior is defined by the actual state. Consider a door object. It has four states: closed, open, closing, opening. It provides two operations: open and close. Depending on the state, the open and close operations will behave differently. This inherent property of an object makes the design process conceptually simple. It boils down to two simple tasks: allocation and delegation of responsibility to the different objects including the interobject interaction protocols.
 
How this works in practice is best illustrated with an example.Let’s say we have three classes: Customer, Order, and Item. A Customer object is the natural placeholder for the credit limit and credit validation rules. An Order object knows about its associated Customer, and its addItem operation delegates the actual credit check by calling customer.validateCredit(item.price()). If the postcondition for the method fails, an exception can be thrown and the purchase aborted.

Less experienced object-oriented developers might decide to wrap all the business rules into an object very often referred to as OrderManager or OrderService. In these designs, Order, Customer, and Item are treated as little more than record types. All logic is factored out of the classes and tied together in one large, procedural method with a lot of internal if-then-else constructs. These methods are easily broken and are almost impossible to maintain. The reason? The encapsulation is broken. So, in the end, don’t break the encapsulation, and use the power of your programming language to maintain it.

# Do Lots Of Deliberate Practice

 1. Deliberate practice is not simply performing a task . If you ask yourself, “Why am I performing this task?” and your answer is, “To complete the task,” then you’re not doing deliberate practice.

 2. You do deliberate practice to improve your ability to perform a task. It’s about skill and technique. Deliberate practice means repetition. It means performing the task with the aim of increasing your mastery of one or more aspects of the task. It means repeating the repetition. Slowly, over and over again, until you achieve your desired level of mastery. You do deliberate practice to master the task, not to complete the task.

 3. The key [to developing expertise] is deliberative practice: not just doing it again and again, but challenging yourself with a task that is just beyond your current ability, trying it, analyzing your performance while and after doing it, and correcting any mistakes.
 
 4. Deliberate practice does not mean doing what you are good at; it means challenging yourself, doing what you are not good at. So it’s not necessarily fun. Deliberate practice is about learning—learning that changes you, learning that changes your behavior.


# Don't Repeat Yourself
Of all the principles of programming , Don’t Repeat Yourself (DRY) is perhaps one of the most fundamental. The principle was formulated by Andy Hunt and Dave Thomas in The Pragmatic Programmer, and underlies many other well known software development best practices and design patterns. The developer who learns to recognize duplication, and understands how to eliminate it through appropriate practice and proper abstraction, can produce much cleaner code than one who continuously infects the application with unnecessary repetition.

1. Duplication Is Waste: Every line of code that goes into an application must be maintained, and is a potential source of future bugs. Duplication needlessly bloats the code base, resulting in more opportunities for bugs and adding accidental complexity to the system. The bloat that duplication adds to the system also makes it more difficult for developers working with the system to fully understand the entire system, or to be certain that changes made in one location do not also need to be made in other places that duplicate the logic they are working on. DRY requires that “every piece of knowledge must have a single, unambiguous, authoritative representation within a system.”
 
2. Repetition in Process Calls for Automation: Many processes in software development are repetitive and easily automated. The DRY principle applies in these contexts, as well as in the source code of the application. Manual testing is slow, error-prone, and difficult to repeat, so automated test suites should be used where possible. Integrating software can be time consuming and error-prone if done manually, so a build process should be run as frequently as possible, ideally with every check-in. Wherever painful manual processes exist that can be automated, they should be automated and standardized. The goal is to ensure that there is only one way of accomplishing the task, and it is as painless as possible.

3. Repetition in Logic Calls for Abstraction: Repetition in logic can take many forms. Copy-and-paste if-then or switch case logic is among the easiest to detect and correct. Many design patterns have the explicit goal of reducing or eliminating duplication in logic within an application. If an object typically requires several things to happen before it can be used, this can be accomplished with an Abstract Factory or a Factory Method pattern. If an object has many possible variations in its behavior, these behaviors can be injected using the Strategy pattern rather than large if-then structures. In fact, the formulation of design patterns themselves is an attempt to reduce the duplication of effort required to solve common problems and discuss such solutions. In addition, DRY can be applied to structures, such as database schema, resulting in normalization.
 
4. A Matter of Principle: Other software principles are also related to DRY. The Once and Only Once principle, which applies only to the functional behavior of code, can be thought of as a subset of DRY. The Open/Closed Principle, which states that “software entities should be open for extension, but closed for modification,” only works in practice when DRY is followed. Likewise, the well-known Single Responsibility Principle, which requires that a class have “only one reason to change,” relies on DRY. When followed with regard to structure, logic, process, and function, the DRY principle provides fundamental guidance to software developers and aids the creation of simpler, more maintainable, higher-quality applications. While there are scenarios where repetition can be necessary to meet performance or other requirements (e.g., data denormalization in a database), it should be used only where it directly addresses an actual rather than an imagined problem.


# Don't Rely On Magic Happens Here
On any project, there are likely many things that an individual programmer doesn’t get actively involved in: eliciting requirements from users, getting budgets approved, setting up the build server, deploying the application to QA and production environments, migrating the business from the old processes or programs, etc.
When you aren’t actively involved in things, there is an unconscious tendency to assume that they are simple and happen “by magic.” While the magic continues to happen, all is well. But when—it is usually “when” and not “if”—the magic stops, the project is in trouble


# Don't Ignore That Error
No matter how unlikely you think an error is in your code, you should always check for it, and always handle it. Every time. You’re not saving time if you don’t; you’re storing up potential problems for the future.
We report errors in our code in a number of ways, including:

• Return codes can be used as the resulting value of a function to mean “it didn’t work.” Error return codes are far too easy to ignore. You won’t see anything in the code to highlight the problem. Indeed, it’s become normal practice to ignore some standard C functions’ return values. How often do you check the return value from printf?

• errno is a curious C aberration, a separate global variable set to signal error. It’s easy to ignore, hard to use, and leads to all sorts of nasty problems— for example, what happens when you have multiple threads calling the same function? Some platforms insulate you from pain here; others do not.

• Exceptions are a more structured language-supported way of signaling and handling errors. And you can’t possibly ignore them. Or can you? I’ve seen lots of code like this:
try {
// ...do something...
}
catch (...) {} // ignore errors
The saving grace of this awful construct is that it highlights the fact that you’re doing something morally dubious.
Not handling errors leads to:
• Brittle code. Code that’s filled with exciting, hard-to-find bugs.
• Insecure code. Crackers often exploit poor error handling to break into
software systems.
• Poor structure. If there are errors from your code that are tedious to deal with continually, you probably have a poor interface. Express it so that the errors are less intrusive and their handling is less onerous.


# Don't Be Cute With Your Test Data
When writing any text in your code—whether comments, logging, dialogs, or test data—always ask yourself how it will look if it becomes public. It will save some red faces all around


# Don't Be Afraid To Break The Things
Redefine internal interfaces
Restructure modules
Refactor copy–pasted code
Simplify your design by reducing dependencies.
 
You can significantly reduce code complexity by eliminating corner cases, which often result from
improperly coupled features. Slowly transition the old structure into the new one, testing along the way. Trying to accomplish a large refactor in “one big shebang” will cause enough problems to make you consider abandoning the whole effort midway through.
 
Be the surgeon who isn’t afraid to cut out the sick parts to make room for healing. The attitude is contagious and will inspire others to start working on those cleanup projects they've been putting off.
 
Keep a “hygiene” list of tasks that the team feels are worthwhile for the general good of the project. Convince management that even though these tasks may not produce visible results, they
will reduce expenses and expedite future releases. Never stop caring about the general “health” of the code.


# Distinguish Business Exceptions From technical
Mixing technical exceptions and business exceptions in the same hierarchy blurs the distinction and confuses the caller about what the method contract is, what conditions it is required to ensure before calling, and what situations it is supposed to handle.
 
Separating the cases gives clarity and increases the chances that technical exceptions will be handled by some application framework, while the business domain exceptions actually are considered and handled by the client code.


# Deploy Early And Often.
The installation/deployment process is essential to the productivity of your customers or your professional services team, so you should be testing and refactoring this process as you go. We test and refactor the source code throughout a project. The deployment deserves no less.


# Convenience Is Not An Ility
An API should provide an expressive language, which gives the next layer above sufficient vocabulary to ask and answer useful questions.

This does not imply that it should provide exactly one method, or verb, for each question that may be worth asking. A diverse vocabulary allows us to express subtleties in meaning.
For example, we prefer to say run instead of walk(true), even though it could be viewed as essentially the same operation, just executed at different speeds.
A consistent and well-thought-out API vocabulary makes for expressive and easy-to-understand code in the next layer up. More importantly, a compo-sable vocabulary allows other programmers to use the API in ways you may not have anticipated—a great convenience indeed for the users of the API!


# Code Is Design
Software designs need to be validated with simulations equates to automated testing.
Brutal Battery of tests


# Comment Only What The Code Cannot Say
What of comments that are not technically wrong, but add no value to the code? Such comments are noise.
Comments that parrot the code offer nothing extra to the reader—stating something once in code and again in natural language does not make it any truer or more real.
Commented-out code is not executable code, so it has no useful effect for either reader or runtime.
It also becomes stale very quickly.
Version-related comments and commented-out code try to address questions of versioning and history. 
A prevalence of noisy comments and incorrect comments in a codebase encourages programmers to ignore all comments, either by skipping past them or by taking active measures to hide them.
Programmers are resourceful and will route around anything perceived to be damage: folding comments
up; switching coloring scheme so that comments and the background are the
same color; scripting to filter out comments.
To save a codebase from such misapplications of programmer ingenuity, and to reduce the risk of overlooking
any comments of genuine value, comments should be treated as though they were code. Each comment should add some value for the reader, otherwise it is waste that should be removed or rewritten.
What then qualifies as value? Comments should say something code does not and cannot say.
A comment explaining what a piece of code should already say is an invitation to change code structure or coding conventions so the code speaks for itself.
Instead of compensating for poor method or class names, rename them.
Instead of commenting sections in long functions, extract smaller functions whose names capture the former sections’ intent.
Try to express as much as possible through code. Any shortfall between what you can express in code and what you would like to express in total becomes a plausible candidate for a useful comment. Comment what the code cannot say, not simply what it does not say.


# A Comment On Comments
Make sure that your comments clarify your code but do not obscure it.
Sprinkle your code with relevant comments explaining what the code is supposed to accomplish.
Your header comments should give any programmer enough information to use your code without having to read it, while your inline comments should assist the next developer in fixing or extending it.


# Coding With Reason
Avoid using goto statements, as they make remote sections highly interdependent.
Avoid using modifiable global variables, as they make all sections that use them dependent.
Each variable should have the smallest possible scope. For example, a local object can be declared right before its first usage.
Make objects immutable whenever relevant.
Make the code readable by using spacing, both horizontal and vertical—e.g.,aligning related structures and using an empty line to separate two sections.
Make the code self-documenting by choosing descriptive (but relatively short) names for objects, types, functions, etc.
If you need a nested section, make it a function.
Make your functions short and focused on a single task. The old 24-line limit still applies. Although screen size and resolution have changed, nothing has changed in human cognition since the 1960s.
Functions should have few parameters (four is a good upper bound). This does not restrict the data communicated to functions: grouping related parameters into a single object localizes object invariants, which simplifies reasoning with respect to their coherence and consistency.
More generally, each unit of code, from a block to a library, should have a narrow interface. Less communication reduces the reasoning required. This means that getters that return internal state are a liability—don’t ask an object for information to work with. Instead, ask the object to do the work with the information it already has. In other words, encapsulation is all—and only—about narrow interfaces.
In order to preserve class invariants, usage of setters should be discouraged. Setters tend to allow invariants that govern an object’s state to be broken.


# Feynman Technique of learning
Choose a Concept
Teach it to a toddler
Identify the gaps and go back to the source material
Review and simplify


# 6 Tips to Become Senior Developer
Develop quickly - Write Correct Code
Tip 1: Code Katas
Tip 2: Keyboard
Find the ideal Solution
Tip 3: have an algorithm and practice it
Tip 4: Approach Code Problem with a method
Teach Others and Help Others
Tip 5: Inspire people by expressing ideas clearly
Tip 6: Share what you already know.

# To Learn any code base
Best Way to Learn  New Things is get involve in Code Reviews.

# Code Improve
Be Declarative.
Promote Immutability.
Avoid Side Effects.
Prefer expressions over  Statements.
Design with Higher order functions.


# 12 Ways To Make Code Suck Less
Reduce State & State Mutation
Do Tactical Code Reviews
Give Good MeaningFul Names
Avoid Long Methods - Apply SLAP
Comment Why, not What
Apply Zinsser's Principle on Writing.
Prefer Clear Code Over Clever Code.
Avoid Primitive Obsession.
Program with Intention.
Favor Loose Coupling
Favor High Cohesion
Schedule Time to Lower Technical Debt.


# Technical Debt
Track technical debt and pay it back quickly.
Write a task card or log it in issue tracking system.


# Functional Progamming
Astute test driven design
Mock roles not objects


# Watch Users
Ask what would the user do? (You are not the user)
Don't Assume


# Automate Your Coding Standards
Make sure code formatting is part of build process.
Use static code analysis tools to find specific anti patterns.
Do not only measure test coverage, but automatically check the results.


# Beauty is in Simplicity
Readability
Maintainability
Speed of Development
The elusive quality Of Beauty.
No matter How complex the total application or system is, the individual parts have to be kept simple.
Simple objects with a single responsibility containing similarly simple, focused methods with descriptive names


# Before You Refactor
Start by taking stock of existing code base.
Avoid the temptation of rewriting everything
Many incremental changes are better than one massive change.
After each development iteration, ensure the existing tests pass.
Personal preferences & ego should't get in way.
New Technology is insufficient reason to refactor.


# Beware the Share
Check your Context Only then proceed.

# Boy Scout Rule
Always check a module in cleaner than when you checked it out.
Any code you add to the module must be clean.
Improve name of the variable
Split One long function into smaller functions.
Break Circular dependency
Add an interface to decouple policy from detail.


# Check Your Code First Before Looking to blame others
Isolate the problem
Stub out calls
Surround it with tests
check calling conventions, shared libraries & version numbers
Explain it to someone else
look out for stack corruption & variable type mismatch
try code on different machines, different build configurations
Question your own assumptions & assumptions of others.


# Choose Your Tools With Care
Start small by using only the tools which are absolutely necessary.

# Code In the launguage of the domain
Add domian concepts explicit in the code.


# Code Layout Matters
Optimizing to where to make change
Easy to scan - observe conventions about how to lay out the parts of a class within a compilation unit: constants, fields, public methods, private methods
Expressive layout - Find the right names so that your code express as clearly as possible 
Compact Format
