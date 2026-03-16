# Build solutions

**Introduction**

We will continue to talk about Problem Solving. Today we will move on to Chapter 4, which is about building solutions. In other words, it is about actual development of portable code or designing solutions. The content discussed in this chapter is relatively fragmented, going down point by point, unlike before when it was more structured. The main focus is on some details that are often encountered in development. If you see areas where everyone is prone to mistakes or pitfalls, you can sort them out and briefly discuss them.

- The theme of this chapter is "Building Solutions", focusing on common problems in development practice.
- The content is developed in dots, covering multiple error-prone details in development.

## 4.1 Do one thing at a time

The first one, one at a time, means to do one thing at a time, or to take small steps and run fast. According to the Lean Startup, it means to take small steps and run fast. This can also be said to be a common principle in building solutions. It means to do one thing at a time, not too much at a time, and not to become fat all at once.

- Emphasize the development principle of "small steps and fast running" to avoid being greedy and seeking speed.
- Focus on solving one problem at a time to reduce complexity.

### 4.1.1 Trap: Trying to Kill Two with One Stone

Common counterexamples include, for example, in the process of developing a certain function, if I accidentally find a bug there, I will fix it together. This is a kind of counterexample. However, the specific ratio is hard to say, maybe it's 50%. In the case of 50%, you can easily fix it. In the other 50% of cases, you will accidentally fix it and a new bug will appear. Then you originally planned to implement that function, but the whole thing went off track. When you went to fix that bug, a new bug was fixed.Then I went to fix the newly fixed bug, and then the whole thing went off track.

So this is a common pitfall. Of course, it doesn't mean that fixing bugs is bad. It's just that fixing some bugs at the right time is also a good and necessary thing to do. It's just that when you become fat in one breath, sometimes things become complicated, simple things become complicated. In fact, most of the time, you can solve each problem one by one. If you really encounter a bug and want to fix it, just remember it.As for me, during the actual coding process, I will open a document next to me to take notes. That is, I will focus on the problem I want to solve. Of course, if I find any other problems, I will write them down in that note. After I solve the problem, I will look back at my notes and set the route. If I see some other problems just now, I will make some changes.

This is one example, and the rest can basically fit into this general principle. So let's expand on it bit by bit.

- Fixing bugs while implementing functions may lead to deviation from the original task.
- There is a high risk of "easy modification" with a 50% success rate.
- It is recommended to record non-current key issues and deal with them later.

### 4.1.2 reduce the possibility of multiple things going wrong at the same time

The main problem behind this principle is that there are many uncertainties in the actual development process. That is to say, there are many assumptions. We think we are right, but we may actually make mistakes.

For example, in the code you write, the problem that may cause errors is whether the original code, which can be inherited from the code itself, has problems. It is possible that there are problems with the code logic or your understanding of the business logic. Although your understanding of the business logic may be correct, the code you write may have problems. It is possible that the code you write does not fully implement the business logic you understand. There may also be syntax errors or inaccurate understanding of the business.So even if you write the code correctly, if the understanding of the business itself is wrong, then it is still wrong.

Actually, when you write a set of code, although it seems like you are just writing code, there are many aspects involved behind it. This includes, for example, if you need to call a third-party library or API interface, it may be that you are using it incorrectly. For example, if the interface is like this, and you understand it as this, but it should actually be used that way. There may also be mistakes in this.And there may even be problems, such as the SenderGrid API that was previously shared with Ames, which may have problems with its API interface or package itself. It may not be your problem, but a third-party problem.

It seems that only a part of the code has been written, but in fact, there are many possible errors behind it. Therefore, the main purpose of only working on one thing at a time is to reduce the possibility of such errors. Try to avoid situations where two or three errors occur at the same time, or problems occur in two or three places at the same time. Try to only have one problem at a time, then fix that problem, and correct that problem.

Because another very common situation, or a very common possibility, is that there are two bugs in a piece of code at the same time, which is the most difficult to fix. Because there are two bugs at the same time, if you fix one, you will find that your program is still broken. Then if you fix that, you will find that this program is still broken. You need to fix both at the same time for this program to run.So once there are two bugs or two problems in a piece of code, or another possibility, as mentioned earlier, it may be that on one hand, you have a deviation in understanding the business itself and the business logic itself. At the same time, you may not be familiar with the syntax of that code. When there are two possible errors at the same time, it is difficult to correct that thing, because it may be that you correct it slightly, but because of that mistake, it still does not run smoothly. Then, it may be that this aspect is correct, the syntax is correct, but the logic is still wrong.So it still didn't work out.

Fixing two or more things at the same time will greatly increase the difficulty of development and error correction. OK, this can be said to be a big principle. Then there are some more common ones that I have sorted out and summarized myself. The most important and best practices can be considered.

- The development process is full of uncertainty and assumptions, and mistakes are prone to occur.
- Error sources include business understanding, code logic, syntax, third-party dependencies, etc.
- Only changing one point at a time can more clearly locate and fix the problem.
- When there are multiple bugs at the same time, it is difficult to determine the root cause, which greatly increases the difficulty of fixing.

**Common Error Source Table**

| Source of error                  | Description                                                  |
| -------------------------------- | ------------------------------------------------------------ |
| Business misunderstandings       | Developers have a biased understanding of business logic, leading to incorrect goal implementation |
| Logic implementation error       | Although understood correctly, the code logic did not correctly reflect business requirements |
| Syntax error                     | Syntax issues at the programming language level cause the code to not run properly |
| Misuse of third-party interfaces | Usage error when calling third-party APIs, such as parameter format or calling method that does not comply with the documentation |
| Third party interface defect     | There is a problem with the third-party library itself, not the developer's own problem |

## 4.2 Simplification and Prototyping (Iteration)

One is to simplify a problem first and then create a prototype. This is actually in line with what was just said, don't become fat all at once, don't think about getting everything done in one step.

- Simplifying problems and prototyping can help avoid over-designing or getting stuck in complex implementations.
- Complementary to the principle of "doing one thing at a time".

### 4.2.1 Example: How to Implement Binary Search in Python

For example, let's say we need to solve a problem and implement a binary search algorithm. I don't know if we are familiar with this algorithm or if we have heard of binary search. This algorithm is not just an algorithm, but also an algorithm and data structure. Then, for example, we need to use this binary search to sort a list or array. Then we need to use the language Python. And some other details, such as this task, especially if you are not familiar with it, it is actually quite difficult to do all these things at once.Because on the one hand, you need to understand what binary search is, and on the other hand, if you are not familiar with Python, you may need to understand its syntax. Then, you may also need to be familiar with the sorted list or the variable type sorted list. If you need to do additional tasks such as outputting logs, you may also need to familiarize yourself with how to use this logging library, how to write its logs, and so on.

So when it comes to this kind of problem, the first step may be to solve it one problem at a time, as we just mentioned. Of course, if you are familiar with all of these, you are familiar with binary search, you know Python, and you are familiar with these related logging libraries, then of course you can solve it all at once. But if you are not familiar with it, stripping it out, prototyping and simplifying the problem can help you to some extent, so as not to fall into many problems at once and be at a loss.

- When unfamiliar, tasks should be decomposed and processed according to skill modules (such as algorithms, syntax, data structures, logs).
- Prototyping is an effective way to reduce difficulty and quickly validate ideas.

### 4.2.2 example: Writing test code for transaction notifications

Another example is that there was a programmer on our side who encountered a problem. He was assigned a task, which is actually our CP Ad Manager system. He was assigned a task to write a piece of code for each transaction. When a customer recharges, a prompt will be sent on Telegram, indicating that a customer has recharged in that system. At the same time, corresponding test code needs to be written. Therefore, the problem he encountered at that time was that it was stuck for a long time.However, if we look at it separately, there are actually many problems encountered. Firstly, he may not be familiar with that framework. Secondly, he may not be familiar with the business logic. The CPI side is just a business logic of the advertising system, and he is not particularly familiar with it. Thirdly, he is not familiar with how to call the Telegram interface. Fourthly, he is not familiar with the testing code framework, which is Ruby. The testing code framework is actually RSpec and Cucumber.When he wanted to make it all at once, he actually encountered many bottlenecks and obstacles. Especially when it came to the testing part, he was stuck for several weeks.

This situation is actually about how to simplify the problem, especially when there are many uncertainties and unfamiliar things. How to simplify the problem step by step and solve it part by part. For example, here is a simple splitting method, or the first step is to learn binary search.As for the first example, the first step may be to simplify, and the core may be the binary search algorithm. We should first familiarize ourselves with the binary search algorithm, and it is not necessary to use Python at the beginning. For example, if you are not familiar with Python, then if you are familiar with other programming languages, you can first use the programming language you are familiar with to implement the binary search algorithm and see if it can be implemented. Alternatively, if you may not be particularly familiar with it, you can find a tutorial on binary search.Then you follow the tutorial, simplify the problem step by step, and then apply it back to the big problem.

The same goes for writing the test code for Telegram. The first step may be to simplify the problem. For example, if I am not familiar with this testing framework, I may not necessarily test Telegram's interface for sending messages. Instead, I may test a relatively simple API call to see if it works.After testing, run the basic prototype test code smoothly, and then replace it with something like Telegram. Actually, call the Telegram interface to see if it can be tested properly and so on.

OK, this set is actually time-limited, so I can't prepare a more specific example. If I have the opportunity to talk about this chapter again next time, I may or I may go back to make up for it. I may add some things in words and find some more suitable examples, but the general idea is like this. For a particularly complex or unfamiliar problem, after it comes out, first consider how to simplify it, and then consider taking a prototype to make it.

- When facing complex tasks, gradually break them down into multiple modules such as framework familiarity, business understanding, interface invocation, and testing framework.
- Each module can be studied independently, experimented with, and then combined into a complete plan.
- Prototyping helps to explore step by step and reduces lag time.

### Prototyping 4.2.3 using third-party libraries

Another common prototype is to say that if you want to use a third-party library, the method of becoming fat in one breath is to go through the documentation and then directly start thinking of ways to apply this library to the current use case and application scenario. If you take it step by step, for example, if I am not familiar with this library at this time, I will use this library first and follow its tutorial. Then follow the examples in its tutorial, implement all those examples first, and ensure that the example can run.Because there is another possibility that the example given by the library itself may be incorrect. Of course, for popular and widely used libraries, this situation is unlikely to occur, but the more niche the library, the more likely it is to occur. Even for some commonly used libraries, there may be bugs in the documentation, such as the lack of timely updates. Therefore, if the usage in the documentation is appropriate, the actual usage may also differ.

So if we want to extract the prototype and simplify it for him, sometimes the first step of simplification is to use the library and see if it works according to his example.Another place where it's easy to get stuck is in his example. Your example itself has problems, or your understanding of that example is problematic. Or, the example he gave may be from this version, but his library may have already reached another version, or the version of the library you installed may be different from the version of the library you saw in that example. If you take it for granted that you can refer to his example and directly apply it to your code to run it in one step, it may run smoothly in 80% of cases, but the remaining 20% is very tricky.You think there is no problem, but after using it for a while, you find that it doesn't work no matter how you adjust it. You will encounter this situation.

So while it may seem like you can save time by doing it all at once, the other 20% of the cases where you get trapped and stuck are also very annoying. So conversely, if you first use that example to ensure that the example itself works, and then the version of the example I installed that day also works, and then transform it into the actual code in our application scenario, although it looks good, it is done in two steps, but the probability of two errors occurring at the same time is reduced. This is an idea.

- Prototype-first helps verify the availability and version compatibility of third-party libraries.
- The sample code may have version differences, semantic misunderstandings, or documentation errors, and needs to be verified step by step.
- Step-by-step implementation reduces the probability of problem stacking and improves integration stability.

**Common reasons for failure with third-party libraries**

| Reasons for failure                       | Description                                                  |
| ----------------------------------------- | ------------------------------------------------------------ |
| The sample code itself is wrong           | There is an error in the sample code that comes with the third-party library, causing the operation to fail |
| Document not timely updated               | The usage described in the official documentation is inconsistent with the current library version, causing deviations in usage |
| Library version is not compatible         | The sample code does not match the currently installed library version, resulting in different interfaces or behaviors |
| Example Logic Understanding Bias          | Developers misunderstand the intent or logic in the sample code, resulting in incorrect usage |
| Dependencies or environmental differences | The example runtime environment is different from the local Development Environment (such as dependencies, system settings, etc.), causing execution to fail |

## 4.3 Practice with specific examples

Then another idea is to use specific examples to incorporate it into actual development and code writing. The example here is different from the previous one. The example mentioned earlier is the example code of a third-party library, while the example mentioned here feels more like a test case.

- This section focuses on practicing complex logic through specific examples (test case style).
- Unlike the example code in the third-party library documentation, it focuses more on business logic deduction and verification.

### 4.3.1 example: Manual writing of test case inputs and outputs

Let's take the CP Ad Manager system as an example. At the beginning of our development, we encountered a long-discussed problem, which was to deal with the calculation of the account book in the CP Ad Manager recharge system. Because there are several transactions in an account, one is the entire amount of money it has deposited, and the second is the coupon we give it, such as the credit we give it and the additional credit limit we give it. It can be used for free, such as trial.For example, if you use Facebook, they will give you, for example, 500 yuan at the beginning. If I remember correctly, you can invest in the free advertising quota of 500 yuan.The same idea applies. In our system, there is a newly registered user who is given a free credit limit, a second user who recharges their own money, and a third user who considers that some customers may be able to pay in advance, but not in advance. They can advertise first and pay later, similar to a credit card system. We can give it a credit limit, and then it can be used up first and paid after 30 days.Therefore, in this scenario, it is necessary to sort out the logic at that time. When going to deduct money, if a person has both the free credit limit and the recharged money, as well as the credit line that can be paid later, then when he goes to purchase an advertising campaign, such as a 1000 yuan campaign, where will the 1000 yuan be deducted? This situation needs to be sorted out at that time.

So this involves sorting out the business logic during the development process. Some say that the business logic is relatively complex. When encountering complex business logic, a good way to break it down is to take small steps quickly. The first step is not to become fat all at once. Don't sort out the complex business logic all at once, but to break it down step by step.First, let's take a specific example. At that time, what we did was to get a list and a Google Sheet list, and then list out all the specific situations we could think of. For example, the simplest case is that if a person has deposited 1000 yuan and has no other credit, then this logic is relatively simple. If it is about how much money has been deposited and used, then if he wants to deduct 500 yuan from a campaign, he will deduct 500 yuan from the 1000 yuan.If you want to deduct 1000 yuan from a campaign, then deduct all 1000 yuan. If you want to deduct 1500 yuan from a campaign, and the balance of 1000 yuan is insufficient, then an error message will be prompted saying that the balance is insufficient. Sort it out one by one. However, starting from the simplest case, and then moving on to more complex cases, for example, the most complex case to consider is the situation where there is both a free credit limit and a credit line with all three limits. Of course, the logic here is complicated.I won't go into details here, just using this example to illustrate that when it comes to sorting out business logic, especially complex business logic, a step-by-step approach is to use a specific example to walk through.

- Sample exercises help break down complex business logic (such as deduction order) step by step.
- Starting from the simplest recharge situation, gradually add conditions such as discount limit and credit line.
- It is recommended to use a table or list to list different scenarios one by one for analysis.

**Table** : Below is the "CP Ad Manager Deduction Priority Example Table"

| Situation number | Free credit | Recharge amount | Credit Line | Purchase amount | Order of deduction            | Whether successful | Explanation                                                  |
| ---------------- | ----------- | --------------- | ----------- | --------------- | ----------------------------- | ------------------ | ------------------------------------------------------------ |
| 1                | 0           | 1000            | 0           | 500             | Recharge amount → 500         | Success            | Sufficient balance                                           |
| 2                | 0           | 1000            | 0           | 1500            | Recharge amount (1000)        | Failure            | Insufficient balance                                         |
| 3                | 200         | 800             | 0           | 900             | Free amount → Recharge amount | Success            | The total amount is sufficient, and priority is given to using the free credit. |
| 4                | 100         | 500             | 600         | 1000            | Free → Recharge → Credit Line | Success            | It involves three types of quotas, and the logic is more complicated. |
| 5                | 100         | 200             | 0           | 400             | Free → Recharge               | Failure            | The total amount is insufficient                             |

### 4.3.2 example: Solving recursion function in middle school mathematics

In fact, in our middle and high school math, we often have similar ideas when solving math problems, such as recursion function, which is like solving this kind of problem, simplifying it, and then summing or calculating something.The standard is something like a geometric sequence or an arithmetic sequence. Later on, in high school math, whether it was high school or junior high school math, we would discuss more complex situations, such as non-geometric or non-geometric but represented by recursion, such as Fn-1 where F1 equals 10 and Fn equals 2 minutes G, which is actually a geometric sequence. There will be more complex forms at some point, just like the approach to solving math problems. Generally speaking, teachers will teach that the first step is not to overcomplicate the problem. Take a few numbers in and calculate them first, then take F1 in and calculate it, then take F2 in and calculate it, take F3 in and calculate it. You first calculate the first five numbers to see if there is any pattern or feeling.Then go and abstract it, and then calculate it. What is the situation with Fn? I don't know if you still remember the math from high school, junior high school, and high school, but the idea is the same. In fact, factorial is the same here. Yes, when encountering complex problems like this, first bring in a few numbers, take a look first, use that example as a stepping stone, and try it out first to get a feel for it.Then, through these specific examples, a general business logic can be sorted out, and then abstracted. It's not about abstracting at the beginning. Of course, if you encounter some familiar or experienced problems, you can do it all at once. But in more cases, when you are not very familiar or not very confident, you can first bring in specific examples, then use them to calculate in your head, simplify them, and then abstract the algorithm or code logic. This can also reduce the risk of simultaneous errors.

Speaking of this, let me mention that the counterexample here is that after completing everything step by step, it is possible to think that the business logic has been sorted out, and then write code. However, in the end, the business logic may not have been sorted out yet. Perhaps 90% of the situations have been considered, and perhaps 10% have not. Then, while writing code, there may be some syntax errors or problems with the code or implementation logic. At this time, as mentioned earlier, two problems may occur at the same time, which is very troublesome when it comes to debugging.So try to break it down and take it step by step.

- The idea of "substituting examples to find patterns" in mathematical problem-solving is also applicable to programming logic sorting.
- When facing unfamiliar problems, run a few examples first, then abstract to reduce the risk of simultaneous errors.
- Beware of the illusion of getting everything done in one step: when there are blind spots in both business logic and implementation, the debugging cost increases dramatically.

## 4.4 Abstraction

OK, then the third point, this is abstraction, or rather, there are actually two directions involved here. One direction is abstraction, that is, we just talked about this. First, give it some specific examples and sort out the business logic. Then, when writing the code after sorting, of course, you can't write it with specific situations. You can't say that A is equal to 1 and B is equal to 2, and then write it like this. Finally, the variable has to be abstracted into a variable, so there is an abstraction process, and there is a generalization process, which turns the concrete into an abstract algorithm.Of course, on the other hand, when encountering problems, it is also necessary to have this mindset, which is to abstract specific problems into a more general problem. Therefore, there are two directions here. One direction is to sometimes give complex problems a concrete example. But conversely, sometimes it is necessary to abstract that specific problem into a more general scenario.

- Abstract thinking includes two directions:
- Generate variables or general structures from specific examples.
- Refine specific problems into broader and more general problem forms.
- Common abstraction processes in programming include: variable extraction, function extraction, and general component encapsulation.

### 4.4.1 abstract search keywords from concrete use cases

The purpose of abstracting it is to search better. Of course, it is not necessary now because there is a large language model. Basically, if you ask specific questions, it can give you answers. But before the large language model, you often need to search by yourself. When searching on Google, if you search for specific questions, there are too specific situations.

- The purpose of abstract problems is to achieve better information retrieval results.
- When interacting with search engines, too many specific details may affect search matching.
- Even with the use of AI for question answering now, a clear question structure still helps to obtain more accurate answers.

Like here, here is a simple example. For example, how to convert a five-by-three table into CSV format using Python. For example, five and three are very specific. If you search for five and three on Google, you may not find very suitable results.When you really need to search, you may simply search for how to format a Table into CSV format, or how to format a Table into CSV format. If you want to abstract it, it should be asked like this. Of course, there should be better examples, but I can't think of any at once. When many pages need to use it, we abstract it and just give it a parameter, yes, yes, yes.This is also a form of abstraction, a concrete manifestation. Therefore, this abstract ability is actually used in all aspects.

- Example explanation:
- ❌ inefficient keywords: "Convert 5x3 tables to CSV with Python"
- ✅ efficient keywords: "Python table to CSV" or "Python write CSV from 2D list"
- Abstract keywords help to cover more general information and avoid being limited by specific values or scenarios.

**Chart** : "Search Expression Hierarchy Diagram", sorted from high to low by concreteness:

| Expression hierarchy | Example keywords                                  |
| -------------------- | ------------------------------------------------- |
| Very specific        | Convert a 5x3 table to CSV format (Python)        |
| Medium specific      | "Python writes tables to CSV"                     |
| Abstract generic     | Python export table to CSV "or" Python CSV writer |

The other thing is that what I mainly mentioned here is that when searching for solutions, because we don't have to write all the code ourselves, in most cases, if we can think of it, we should go back to this example, for example, this is a specific example, a specific case. Then when you want to search for solutions, if I don't know what the solution is, you need to abstract it when searching. Then I just simply search for how to convert the table into CSV format in Python.Then for the same other things, there is a need to have that feeling, but it's hard to say what this feeling is. I don't know if I have the opportunity to sort it out again. What exactly is the so-called feeling? However, it's about searching, refining the search keywords, or in other words, for ChatGPT, refining the Prompt, refining the ability to ask good questions. Anyway, in our daily development, we often encounter problems that we need to solve, and it's very likely that others have already solved them.It's just that we are more specific. We may have a specific scenario and then bring in a specific number or a specific variable, but how can we separate that specific variable from it? Then we just use that universal one to find a solution and search for that keyword. Yes.

- The essence of search ability is the practical application of abstract ability in knowledge retrieval.
- ChatGPT and Google both rely on the quality of input information, and the quality of results is higher when the level of abstraction is appropriate.
- Clear questioning "" Abstract and reasonable "→ is the starting point for problem-solving.

### Paradigm Shift 4.4.2 Large Language Models

Of course, another opportunity I want to try now is to see if ChatGPT or current large language models can extract search keywords. Specifically, we may ask a specific question and see if ChatGPT can abstract it and extract search keywords from Google. Then we use these keywords to search for this question in Google. I think this is a reference idea.

- LLM (Large Language Model) can be used to extract the general structure and keywords behind the problem, assisting in subsequent searches.
- It is recommended to use it as a "semantic organizer before search".

Sometimes, you may not ask questions that are particularly accurate, especially with Google. Nowadays, ChatGPT and other large language models are much better. Even if you ask a question that is not particularly good, it can still answer it accurately. Of course, sometimes it's another matter if its answer is outrageous or if it hallucinates. But compared to when there was only Google, if you ask a bad question or don't select the right search keywords, you may not be able to find the results you want at all.

- Even though ChatGPT may occasionally "hallucinate", its fault tolerance is still better than traditional search engines.
- The clearer the structure of the question, the more stable and reliable the response will be.

#### The combination of abstraction and search

So, how can we abstract the common part, which is the part that others have also implemented? For example, in this example, the most common common function is Authentication. Previously, I discussed with Amos that basically any website with users will have permission management functions. If I take specific requirements, such as A-class users having these permissions and B-class users only being able to do these things, and then search on Google, it is highly likely that good results will not be found.

But if we can abstract a layer, because permission management is an abstract concept that most websites will use. Then I can use Google to search for the permission management solution of this framework. Then, I can reapply the abstracted general results to our specific usage scenarios. I feel that the ability to extract search keywords or problems is more difficult to abstract.

- Example explanation: Abstracting "A/B user permission details in a certain framework" as "permission management mechanism" makes it easier to obtain ready-made information.
- Avoid bringing in business specificity when searching, first extract domain-specific keywords.

#### The challenge of abstraction ability

I think, logically speaking, it should be possible to break down this thing into more specific parts like a class, and then expand on it. But I can't think clearly about this issue for now. If there is a chance, I will also learn it. Maybe I will think about it again and hold a separate workshop to talk about this abstract ability. I think sometimes abstraction is something more common, such as the verification function you just talked about. You can just search for it directly. If you don't want to search, you can also ask artificial intelligence directly. Its generated results are similar several times.

- The ability to abstract itself can be taught and practiced, but it is rarely systematically trained.
- It is recommended to use "Abstraction Power" as an independent workshop or special topic for explanation.

#### Complexity of specific cases

For example, if you want to add this artificial intelligence, how to manage the existing user permissions in the database? If you search, the models in your example, such as the relationship between this model and that model, are different from what I want to consider. For example, the problem I want is a one-to-many model, but the example given online is a one-to-one model. Also, in my own experience, it is either a one-to-many model or a one-to-many sub-model that does not have a complex model.This situation is quite special. It may not be good to simply copy it. At least you need to ask, but sometimes the thinking is a bit confusing, so you need to ask this question clearly.

- The higher the case specificity, the harder it is to reuse online solutions directly.
- Abstraction helps to clarify the "essential structure" and "implementation differences", and then combine existing solutions.

#### The complexity of induction and deduction

This abstraction ability is actually quite complex, or the ability to induce and deduce. It means finding differences and similarities, which parts are the same and can be applied, and which parts are different. It cannot be directly applied and needs to be changed. There are actually many things that need to be felt, or I think some systematic things can also be sorted out. Maybe I happened to encounter a relatively special situation or a difficult point in this category, but it could also be a relatively simple one in another category.

- Abstract ability can be seen as a dual process of "finding commonalities" and "identifying variables".
- Technology migration and code to reuse depends on the sensitivity and judgment of similar structures.

#### Distinguish between special and general cases

It is necessary to distinguish whether the current situation belongs to a special case or a more general case. There are many things that can be investigated here, OK, let's briefly introduce them here. I think this is also a big part. If you really want to consider it, there are many things that can be expanded, and I haven't figured it out yet. Anyway, having this awareness can at least abstract a problem and then search for it on Google or find a challenge more appropriately.

- A good abstract judgment framework should include:
- Does the current problem belong to the common problem paradigm?
- Is there a widely used solution model?
- Which elements can be separated into parameters?
- Which parts need to be customized for implementation?

### ✅, Abstract Thinking Flow Teaching Diagram (Text Version Flowchart)

[Realistic/operational issues]

​        ↓

[Step 1] Identify key information

- Clear input, output, data structure, context
  - ​       ↓

[Step 2] Peel off context details

- Remove irrelevant numbers and specific names (such as "5 rows and 3 lists" → "Any two-dimensional table").
  - ​       ↓

[Step 3] Extract general keywords

- Summarize the essence of tasks, such as "format conversion", "permission management", "recursion algorithm".
  - ​       ↓

[Step 4] Organize search expressions

- Combine keywords into concise search statements or LLM questions, for example:

→ “Python write 2D list to CSV”

→ “Django role-based access control”

→ “recursive function sum example”

​       ↓

[Step 5] Perform a search or ask a question

- Choose search engines or large language models as tools
  - ​       ↓

[Step 6] Match & Adjust

- Judge whether the result matches expectations
- If it is invalid, go back to step 3 and optimize the keywords.

### 🧩 II. "Problem → Keywords → Search Hit Rate" Comparison Table

This table shows the impact of problem expressions at different levels of abstraction on search performance, used to train "keyword extraction ability".

| Original problem expression (input)                          | Abstract keyword expression             | Expected search hit rate | Remarks note                                                 |
| ------------------------------------------------------------ | --------------------------------------- | ------------------------ | ------------------------------------------------------------ |
| How to convert a 5x3 table to CSV using Python?              | Python write table to CSV               | ⭐⭐⭐⭐☆                    | Removing the specific number of rows and columns is beneficial for matching all common solutions |
| How to write a list as CSV in Python?                        | Python write list to CSV                | ⭐⭐⭐⭐⭐                    | The most concise and common expression, with the highest hit rate |
| How to make A-type users upload while B-type users can only view in Django? | Django role-based access control (RBAC) | ⭐⭐⭐⭐☆                    | Using the generic term RBAC to improve matching              |
| How to handle nested permission verification logic in a one-to-many model? | Django nested permissions model         | ⭐⭐⭐☆                     | Specific term combinations suitable for moderately complex scenarios |
| How to write Fn = 2 * Fn-1 + 1?                              | Python recursive function example       | ⭐⭐⭐⭐☆                    | Using "recursive function" as the keyword is the most universal |
| F1 = 1, F2 = 2, F3 =?, F4 =?, how to find?                   | recursive sequence problem example      | ⭐⭐⭐⭐                     | Sequence-based abstract keywords are more suitable for searching educational and problem-solving content |

## 4.5 Logical and grammatical errors

OK, off-topic. Let's come back to this and break down the logical errors and grammatical errors. Here, grammatical errors are given as a simple example. For example, these are not strict grammatical errors, but more semantic errors.

> [Example] `if (a = 1)`

For example, writing `a = 1 `, in fact, most people can know how to write the normal syntax normally. Normally, it should be `a == 1 `, so compare whether `a `is equal to 1. If there is only one equal sign, it becomes an assignment. This is especially true for those who are just starting to learn programming, and it is easy to encounter such a situation where typing an equal sign incorrectly can cause a long time of lag.

But this is not just for beginners. Sometimes experienced people also make this mistake and get stuck for a long time. You may think the code is correct, but it turns out to be wrong. Sometimes it may just be a joke from Northeast China, but this can be considered a grammatical or semantic error. At this time, you need to make a distinction, that is, you may think that this thing reports an error, or sometimes it does not report an error, but it runs out and the result is wrong. After thinking for a long time, you may think that my logic is quite correct, and I don't think there is anything wrong with my code logic.Then I repeatedly adjusted my logic, feeling like there was a problem with the logic, but in fact, it was a grammatical error, or just a typo, or a semantic error.

- Common misconception: "Grammar errors ≈ beginner's problems" is not true, experienced developers can also make basic mistakes.
- Example `if (a = 1) `is actually an assignment, unconditional judgment, which belongs to a typical semantic level error.
- Error symptoms are often mistakenly diagnosed as "logical errors", resulting in wasted debugging time.

### Separation of logic and grammar

So there is a consciousness to separate logic and grammar. Sometimes, especially after being stuck for a long time, it is necessary to step out and think first, whether it is possible that the direction I am thinking is completely wrong. Especially in this example, you may spend an hour and a whole day thinking, whether there is a problem with the logic of my code, and it takes a long time to adjust it incorrectly. In fact, at this time, you need to step out and think, whether it is possible that there is a problem with the grammar and semantics, and a wrong equal sign is typed.Actually, this logic is not a problem because the equal sign was mistyped. Originally, it was for comparison, but it became assignment, and then it was wrong.

Of course, the actual problem behind it is that the debugger is actually used to call it. Generally speaking, it will jump out immediately and it will be found that there is a syntax error here. However, let's abstract it first. There is a deliberate separation of this logic, code logic, business logic, and the code itself. So it is possible that the opposite is true. It is possible that this logic is wrong, but if you always think that this syntax is wrong and cannot be called for a long time, it is also possible to reverse the situation.

- When encountering debugging difficulties, it is recommended to establish a "separation hypothesis": Is it a logical error or a syntax error?
- Debugger can speed up positioning, but the premise is that it has been realized that both can independently fail.
- It is recommended to form a "troubleshooting path": first check the syntax structure → then verify the business logic.

**Chart** : "Error type troubleshooting decision tree":

[Program running result is abnormal]

​      ↓

Clear error message → Is it a syntax error? (such as missing parentheses, equal sign error)

​      ↓

No error but output exception → Is it a logical error? (such as conditional judgment, boundary omission)

### Grammar and Usage Errors

Once you are familiar with it to a certain extent, generally speaking, there are not many syntax errors, but more semantic errors. Another common situation is usage errors, which means that even if you use a third-party package or library, your business logic is completely fine when calling a third-party API. However, when you call a third-party package or API, if the calling method is wrong, the result may not be what you want. This situation occurs in the category of semantic errors.

At this time, you may have been adjusting your syntax and usage for a long time. It is possible that the logic is wrong, or vice versa, the logic may be correct, but the usage of your package is wrong. Therefore, the result of executing this method is incorrect. At this time, you need to check and extract whether the usage and syntax are wrong.

- Besides syntax and logic errors, there are also "usage errors": API/library usage does not meet expectations.
- Usage errors are often highly similar to logical errors in the early stages and can be easily confused.
- Recommended strategy: **Separate usage tests from the business logic for validation** .

### Simplify and split

Of course, a good way to eliminate this thing is to simplify it first. Especially when using unfamiliar syntax, libraries, and APIs, it may be better to implement all the usage and logic in one breath than to try it all at once. Instead of doing it this way, a better way is to break it down and take small steps. First, adjust the usage of these libraries, third-party libraries, and third-party APIs with the simplest method to see if the result is what you want.Then apply it back to the actual business logic, break down these two parts to prevent them from being mixed together and unable to distinguish where the problem lies when problems arise.

- "Small steps and fast running" is suitable for low-coupling operations such as syntax verification and API call testing.
- Recommended process: 1. Test syntax/API call success with minimal code 2. Verify business logic conditions and data structures individually 3. Finally, merge the two to build a complete function

**Table** : Error types and troubleshooting methods comparison table

| Error type    | Feature performance                                      | Common scenarios                                        | Recommended troubleshooting method                           |
| ------------- | -------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| Syntax error  | Compile or interpreter error                             | Spelling errors, missing parentheses, mixed equal signs | Static inspection tool, IDE, debugger                        |
| Logical error | The program is running but the result is not as expected | Conditional judgment, loop boundary, order error        | Unit test, breakpoint debugging, Console output              |
| Usage error   | The grammar is correct but the result is strange         | Third-party libraries, APIs, document misreading        | Official documentation, simplified prototype testing, StackOverflow |

## 4.6 Make good use of debuggers

OK, the next one is to make good use of this debugger in the development process, or what is this called? It should be called a debugger in Chinese. I don't know if you have the habit of using a debugger. I know that there are quite a few programmers who are not used to using a debugger. Yes, they are used to `console.log `, or the `print `in PHP, just print that variable directly. Of course, it doesn't mean that this is absolutely bad. In 80-90% of cases, this is enough.However, when encountering complex logic that needs to be debugged, it is often not enough to simply type out the variable.

- Beginners often use `console.log `/ `print `debugging, but the information is incomplete or difficult to locate in complex logic.
- The debugger provides more systematic tools such as breakpoint control, variable monitoring, and call stack viewing.
- Applicable to: variable state tracking, process control verification, cross-function jump and other scenarios.

#### Advantages of Debugger

It's hard for me to give an example of this thing all at once, but when there's a chance, especially if you're not used to using a debugger or a debugger, you can try using a debugger. Yes, whether it's in the IDE, it depends on everyone's habits. Some people are used to using the debugger in the IDE, and some people are used to using the debugger in the command line, which is possible. Because the debugger will print out all the current states and everything in the memory stack for you.At once, it is very clear to see what the current state of your global variables is. When you stop at the breakpoint after hitting the breakpoint, you can clearly see what the global variables are and what the local variables are. Then its call stack, or what is called the method call stack, can be clearly seen at once. Then you can also use that `step `and that distribution to debug.

- The core functions of the debugger include:
- Breakpoint pauses execution (breakpoint)
- Step into/step over
- Real-time viewing of local and global variables
- Call stack traceback
- Graphical IDE and command line debugger each have their own advantages, while visual debugging is more suitable for beginners.

**Table** : Comparison table of debugging tools and common functions

| Tools/Commands | Function Description                      | Common uses                                                  |
| -------------- | ----------------------------------------- | ------------------------------------------------------------ |
| breakpoint     | Set pause point                           | The program automatically stops executing when it reaches this line |
| step over      | Step through current line (skip function) | View variable changes before and after function calls        |
| step into      | Execute inside the function               | Debug function internal logic                                |
| watch / locals | View the current scope variable status    | Tracking variable value changes                              |
| call stack     | Display function call sequence            | Understanding program execution path and error location      |

### 4.6.1 verify if the intermediate execution result is logical

Actually, the logic behind debugger is to facilitate you to verify whether the business logic you understand, or the code logic you understand, is the same as the code logic that actually runs. This also involves the specific example of `walkthrough `mentioned earlier. In the actual development process, the first thing is to have an understanding of this algorithm logic and business logic in your mind.Then you will know what process it will go through in this code if I substitute these input values, how it will be converted, and what the final output will be.

Of course, with this specific example in mind, when you can follow this logic step by step and then use debugging, it is actually equivalent to verifying your hypothesis about this business logic. You will see that each variable has an input value, and how it undergoes and changes step by step, and finally becomes an output value. Then, at each step, you can see that there is a problem with this step, which deviates from your understanding of the business logic.

- The core use of the Debugger is to **verify whether the "thinking model" is consistent with the "actual operation of the program"** .
- If the program behavior deviates from expectations, the debugger can clearly show which step is different.

#### The practical application of the debugger

Of course, sometimes it is very simple to verify this, that is, use the `console.log `, or use `print `to type it out, and sometimes it is enough to verify. But sometimes it is not enough to verify, it is possible that the variable you think is problematic is not actually a problematic variable, it may be a problem with other variables. In particular, the most prone situation is the global variable. But this is another place that may be mentioned, that is, you can use less global variables and less global variables.Global variables are the most prone to problems, that is, code that may have nothing to do with you, or your code may malfunction.

When using debug here, you will see that you can see how it runs step by step. Then, you can teach it to verify, and then say where the code logic you understand and the code logic that actually runs out went wrong. Then use this to debug that problem more effectively.

- `Console.log works `in simple cases, but is limited in complex processes or variable crossovers.
- The debugger can detect deeper state errors, such as scope obfuscation, global variable contamination, and so on.
- It is recommended to think of the debugger as a "procedural endoscope" rather than just a "magnifying glass".

## 4.7 Fake it before making it.

The next one is "fake it before make it". This is not just a technical issue, many Product Managers like to use it, or many AI professionals like to use it now. That is, before the robot is made, it is first disguised as a robot by humans. Of course, in the actual development process, the more common usage is, for example, when you develop something, it needs to be divided into several modules, methods, or classes.The same goes for this. When you need to split this piece of code, try to avoid getting fat all at once. That is to first "fake it" a part of the methods, classes, or something else, and make a simple version or a fake version for it to interact with reluctantly.

- "Fake it before make it" is an effective phased development strategy that emphasizes building the skeleton first and then filling in the content.
- Commonly used in scenarios that require Modularization splitting or task division, it is convenient to advance the overall process first.
- Widely used in software development, product design, and even AI prototype construction.

#### Applications at the micro level

Then focus on filling up the big part of the logic and solving it. Ignore the small modules that are broken down into specific details. Let it respond as long as it can, and then respond according to some special cases. Of course, this is the specific level of writing code at the micro level. But from a macro perspective, there are also things in the development work, such as doing mockups, making wireframes, making wireframes, and so on. This is also the same, the same idea.It means that before we actually solve the problem perfectly, we can first see the effect, that is, pretend that the effect is what the effect is.

- Microscopic level: "stub/mocked function" helps run the main process first.
- Macro level: Mockup and Wireframe allow project stakeholders to see the "result outline" earlier.

**Table** : Fake-it methods and typical application levels

| Application level      | Fake-it method                              | Examples of practical uses                                   |
| ---------------------- | ------------------------------------------- | ------------------------------------------------------------ |
| Micro (code)           | Stub/Mock function                          | Return a fixed value so that the main process can be tested and run first. |
| Macro (product)        | Wireframe/Prototype/Mock UI                 | Present the interface form of future products to the team or customers |
| Interaction (AI, etc.) | Manual operation simulation system response | Make users mistakenly think it has been automated and improve the perceptual experience |

#### Macro-level applications

At the level of this project, it is possible to let the relevant parties of that project see the effect of that. Sometimes, it is a higher priority than directly solving the problem, and there may be more steps that need to be done in advance. Conversely, it is the same at the microscopic level of writing code. Sometimes you know that you need to split out a method, and then you need to call that method, but if you write all the methods before you can develop specific code logic, sometimes the pace will be too slow, and then it will be too slow, and then the problem will be complicated.

- In project management, "prioritizing results" helps to gain consensus and evaluate direction.
- In micro-development, getting stuck in details too early can easily lead to delayed development pace or chaotic debugging.
- It is recommended to use "fake implementation" as a transition during the uncertain period, so that the main process can be fully implemented first.

#### Strategies to Avoid Complexity

Because it's the same, as mentioned earlier, this may cause errors in multiple places, such as in your main method, in the sub-method you split out, or in the sub-module. That is to say, how you call after reporting an error will actually make the problem more difficult to tune. So one idea is to "fake it" first, make a fake method, or make a fake class, or make a fake module, as long as it can return the correct result in that special case, just leave it there.At this point, you can proceed to the next step without hindering the implementation of your main method.

- "Fake implementation" is a practical technique for **separating complexity** : errors in the main logic and submodules do not cross-interfere.
- It can effectively control the debugging focus and shorten the error chain caused by Path Dependence.

#### Example: Stub/Mock

> [Example] Stub/Mock. So that you can move on to next part first.

I also don't have enough time to come up with an example, but similar situations often occur in algorithm courses. I don't know if you have ever taken a data structure algorithm course or actually encountered similar situations. For example, I need to implement an algorithm, which needs to be divided into several steps or modules. Then, one way is to first implement a module, if there is a ready-made one, of course, before taking the algorithm course, I need to write the implementation code myself.But sometimes some algorithms may have open-source solutions that you can directly use.

- Stub and Mock are common techniques for "fake it" in code.
- Stub: empty shell function that returns default value
- Mock: A disguised implementation that records call behavior
- Especially useful in algorithm step-by-step implementation and multi-person collaborative development.

#### Temporary use of open source solutions

Actually, you can take the existing solution and use it first, then replace it. After you finish developing the entire logic, you can go back and overwrite the thing that was temporarily replaced with the open source solution. As for these examples here, if there is a chance later, we will add some specific examples.

- Using existing open source implementations as a transitional alternative is an efficient strategy of "go through the process first, optimize performance later".
- Finally, we can proceed with "backfill" development and replace temporary code with custom implementation.

**Schematic** : Development Flowchart

## 4.8 Start from the normal state (especially when troubleshooting)

In this text, the next one is the most common situation encountered when troubleshooting or fixing bugs. I am also often asked this question, which means that when fixing bugs, I don't know where to fix them. Then, I don't know where the mistake is. Therefore, the ideal situation at this time is to start from the bug-free state. Because it is basically impossible for something to have a bug from the beginning.That bug must have been introduced during the process of adding some feature, or introduced during the process of modifying something.

- The primary strategy for troubleshooting bugs is **to return to a known "normal state" as a starting point** .
- Bugs usually come from new features or changes, not the initial state, so reverse tracing helps locate problems.
- Avoid debugging like finding a needle in a haystack in a "chaotic state".

#### The importance of starting from a normal state

So in this debugging process, it's not very funny to start from the problematic state and adjust from your crisis point. Generally speaking, because there is a problem, you don't know that, just like in our sermons, we talk about physiology and pathology. I said that when a doctor sees a patient, if they don't teach you physiology at the beginning and teach you pathology directly, they will tell you where the person is sick and how the normal human body should operate under their non-sick state.If I don't learn that first, I'll just tell you that there's a problem with this thing and you can start doing it yourself. This kind of phone is not easy to repair, not very easy to repair.

Similarly, if, for example, a car is being repaired and you don't know how the car should work, and then everyone tells you that the car can't be driven and you don't know why, you can check it yourself. Actually, it's not easy to troubleshoot the problem when I suggest checking.

- Analogy explanation: Doctors need to understand the normal physiological state first, and mechanics also need to know how the engine works normally.
- Similarly, debugging programs should first understand how they "should work properly".

#### Example: Start with sample code or normal commit

> [Example] start with example code / start with good commit

So the same goes for a set of code. If the starting state is that there is a problem, it is generally difficult to troubleshoot. So try to find the node before the problem, because we have given it to them. Of course, some projects that are more painful are those that are not given to them, and those projects are the most painful. If there are projects given to them, at least you can go back and trace them back to a normal state.

Generally speaking, if you have been working on this project by yourself for a period of time and have a general understanding of the cause and effect, you don't need to go through this step. However, if you are accepting someone else's project or continuing someone else's development work, sometimes you need to compare and trace back to a normal state to know how the code runs normally. Then use this as the basis point to adjust the error, which is generally easier to adjust.

- Recommended strategy: Use version control (such as Git) to trace back to the "last known good" commit record.
- When taking over someone else's project, it is essential to first find a "reference state" that can run successfully.

**Chart** : Debugging Path Selection Flowchart

[Code is currently unable to run]

​     ↓

Is there sample code? - Yes → Validate from example → Modify to minimize differences

↓ No

Is there a Git version history? - Yes → Roll back to a known good commit → Stepwise diff

↓ No

Try to restore the recent operation record → Manually troubleshoot recent changes

#### Analogy: Starting with sample code

The same train of thought, in fact, there is a similar analogy just now. That is to say, if we want to call the usage of an unfamiliar library, we start with its sample code. Because we assume that its sample code is correct. So if we eat a lot in one breath, and then ignore the sample code, we directly start to apply it to our own code. Sometimes you may not be sure whether the usage of its sample code itself is correct.

So break it down, first ensure that this part is working, it is correct, follow at least the example code, and it can run normally. Then distinguish and see if there is a problem with its usage in my scenario.

- Sample code = Known input of "running normally" → Beneficial for isolating bugs caused by environmental and parameter differences.
- It is recommended to prioritize running official examples of third-party libraries → Ensure that the libraries themselves are problem-free.

#### Back to normal commit

Then, as mentioned earlier, we need to trace back to the previous commit. If there is a problem with the code at this commit time point, can I trace back to a node of the code that is not problematic? Then, we can first see its normal operation status. Once we know the normal operation status, we can do the diff. Generally, git tools come with diff.

Or, to put it another way, manually diff and compare the difference between the normally running code and the currently buggy code. Generally speaking, in a hundred lines of code, the difference after modification may only be about ten lines. The key point is to adjust the ten lines that have been modified. However, if you don't do this step, you only know that there are errors in those hundred lines. The difference in difficulty between finding the error in one hundred lines and finding it in ten lines is geometric.

- Using `git diff `to focus on changing areas is a powerful tool for quickly locating bugs.
- The core idea is to compress the "debugging scope" from the entire code segment to "specific modification lines".

#### Debugging starts from the running state

So especially when there is an error in debugging, the idea is to start debugging from the runnable state, instead of immediately saying that there is a problem with this thing, which is very difficult. This is also related to the previous example. As I mentioned earlier, the CP Ad Manager assigned a programmer who had been working on this for a long time.

Part of the reason is that he is not familiar with the framework of the test code, so he is not familiar with Rspec or Cucumber. Therefore, he directly applied it to the testing environment to try to develop the test code. If he applies this situation, it means that he has not yet figured out how to use the testing framework, or he has not even finished all the examples given by the testing framework itself.

- Case study: Using it recklessly without understanding the framework can lead to difficulty locating the source of confusion.
- First let the testing framework itself "run smoothly", and then write the test scenario code, which is a good way to reduce confusion.

#### Split the problem and debug step by step

Then he directly tried to use that framework to apply the test code and write the new test code. So he got stuck there. He didn't know if there was a problem with the test code he wrote, the test framework, the usage of the test framework, the test case itself, or the code being tested. Once there are problems in multiple places, it is particularly easy to get stuck.

But break down these things, and then part by part, and make sure that this thing is in the working state, so that I can at least have a certain degree of understanding of how to use this testing framework. I ran the code of that instance for him. At least I know that this state is in the working state. Then step by step, I called it and added a line of code to it, and added another line of code to make it look like the actual scene.

- Splitting principle: first verify that the framework itself can run → then add logical verification → finally combine with real business data.
- Only change one variable or logic segment at a time, gradually building a stable path.

#### Quote: Happy families and unhappy families

> “All happy families are alike; each unhappy family is unhappy in its own way.”

So this reminds me of another commonly used saying, which is that happy families are all similar, while unhappy families have their own misfortunes. I think it's the same when applied to code. The code for work is all similar, and the code that cannot be run out has its own problems.

- Golden phrase tip: All code structures that work are similar, while those that don't work are vastly different.
- This sentence emphasizes: **first build a runnable foundation, and then pursue personalized logic implementation.**

#### Approach to solving complex problems

So how can we solve this problem? Because there may be problems in the code, and there are really all kinds of problems. To repeat it again, for example, there may be syntax problems, semantic problems, incorrect library usage, problems with the library itself, incorrect business logic, testing, problems with the code itself, problems with the tested code, problems with the tested code, problems with the tested framework usage, and so on and so forth. When they are all mixed together, it is a pot of porridge, and it is very difficult to find any problems.

But once the code is the same, once it runs, you know it works. Once it doesn't work, you can only say that some part of it didn't work. But which part didn't work specifically needs to be checked. Then how to simplify it, peel it off and check it bit by bit, this is generally the most difficult part in the development process.

- Key points for investigation: "Slice" mixed problems and debug them separately.
- Recommended methods include:
- Control variable method
- Stub/Mock Substitution
- Version comparison method (such as git bisect)

**Schematic diagram** : Problem location strategy diagram

## 4.9 When and how to borrow code?

OK, let's talk about some other details next. This part discusses how to borrow code. Personally, I strongly encourage borrowing code. Although some programmers may prefer to write all the code themselves, relying too much on writing code can also lead to low efficiency. The key is how to find a balance between the two. Below, I will share my experience.

- Borrowing code ≠ lazy, but a practical strategy to improve development efficiency and avoid reinventing the wheel.
- The core is: **knowing which code can be borrowed, when to understand its principles, and when to just know its purpose.**

### 4.9.1 Google vs ChatGPT vs Package

First of all, the most common situation of borrowing code is that I can use Google to search for relevant information myself. Now ChatGPT has also appeared. I tried it a while ago, especially in front-end code, and the effect was good. Although its sorting of back-end logic may not be clear enough, it performs well in front-end modification. As for code generation, I personally recommend using Claude and Perplexity. They each have their own limitations, so you still need to judge according to the actual situation.My current experience is that in some scenarios, Claude and Perplexity perform better than ChatGPT, although they also have usage limitations and cannot be fully relied upon.

As for the use of these two tools, my general approach is: if I need to call third-party APIs or rely on third-party libraries, I tend to use Perplexity because it has a network search function, can read relevant document links, and then develop code based on documents; while if I don't need to rely on documents, I am more accustomed to using Claude. Since my daily development time is limited and I don't have much time to write code per week, even if they have daily usage restrictions, it won't have a big impact on me. I just need to wait for a while to continue using them.

Overall, there are no strict standards for these tools, it's just my personal usage preference and preference, and there may be new models in the future. Recently, DeepSeek was introduced and I had the opportunity to try it out, which may have better results. However, it often crashes at present. As far as I know, DeepSeek has lower hardware requirements, but it is still not suitable for daily use. In addition, DeepSeek also supports deployment in local environments for trial.

- Tool Recommendation Summary:

| Scene                                      | Recommendation tool  | Reason                                                       |
| ------------------------------------------ | -------------------- | ------------------------------------------------------------ |
| Third-party API lookup and usage           | Perplexity           | Equipped with network search function, can reference official documents |
| Front-end code generation/style adjustment | ChatGPT、Claude      | Fast response, neat format, suitable for HTML/CSS level      |
| Non-networked, model behavior control      | Claude               | The model has a clear idea and stable answers                |
| Explore new models                         | DeepSeek (to mature) | Possibility of local deployment, but current stability is poor |

#### The principle of borrowing code

In actual development, use what you need, whether it's Google, ChatGPT, or other tools. For third-party packages, I personally prefer to use ready-made solutions, which is often referred to as "don't reinvent the wheel". Programmers generally agree that since someone else has already invented the wheel, there is no need to spend ten hours reinventing it. Therefore, borrow the code that can be borrowed, and there is no need to rewrite it.

- Principle summary:
- ✅ borrow existing packages/libraries → improve efficiency
- ❌ don't have to start from scratch
- 🎯 goal is "functional achievement", not "code originality"

#### Example: Practical application of borrowing code

I once encountered an interesting situation: when checking someone else's code, I found that a package had a monthly download volume of tens of millions, and many people were using it. I also used this package when developing with J Leheng. Out of curiosity, I clicked to take a look and found that there were actually only a few lines of code inside, containing only one Regular Expression. In fact, after I directly copied this Regular Expression, it could be used normally. This shows that in specific scenarios, sometimes the code can be directly copied, and sometimes it needs to be encapsulated. Specific situations require specific analysis.

- High download volume ≠ necessarily complex, and sometimes the core logic is just an expression.
- The granularity of borrowed code needs to be flexibly adjusted according to the situation: **whole package/function/one line of logic** .

#### Google Search and Stack Overflow

By searching on Google, you can usually find relevant code on Stack Overflow, which is completely OK to use directly. However, it should be noted that code generated by ChatGPT or other AI often has errors. Although the code appears to be in the correct format, it may not run properly after careful inspection.

- Suggestions for using AI-generated code:
- ✅ can be borrowed when the structure is clear
- Test ⚠️ before running
- ❌ do not blindly trust automatically generated results, especially involving asynchronous, permission, and state change logic

#### Two cases of borrowing code

Overall, borrowing code can mainly be divided into two situations. The first is to use a ready-made code library or package: when you encounter a problem and there is a high probability that someone has already developed a solution, try to use a ready-made package; if the content of the package is relatively simple, you can also directly copy its code.

- Classification of borrowing methods:

| Type                         | Feature description                              | Recommended practice                           |
| ---------------------------- | ------------------------------------------------ | ---------------------------------------------- |
| Third party libraries        | Active maintenance, documented, multi-user       | Directly install and read documentation        |
| Lightweight function section | Less than 30 lines, no dependencies, clear logic | Adjust according to actual needs after copying |

#### Knowing the result and knowing the reason

When using a package, it is usually not necessary to understand its specific implementation. During the development process, you only need to master how to use it. Of course, if interested, you can use your spare time to delve into the underlying logic of the package. But in practical applications, it is enough to know how to call it and have confidence in its basic functions. For example, you can judge its reliability by checking the number of stars, followers, and monthly downloads of the package on GitHub.

- When using a package:
- Actual development → Know it (how to use it)
- Technical improvement → Know why (how to achieve it)

#### Long-term investment: read the source code

Writing business code for a long time may lead to a stagnation in programming skills. Therefore, I suggest that everyone use their spare time to read the source code of some high-quality packages and try to understand their business logic, coding style, and design pattern. Although this is not a direct solution to the current problem, it is a long-term investment in improving personal coding skills.

- Recommended reading objects:
- Web frameworks (such as Flask, Express)
- Tools library (e.g. Lodash, Requests)
- Popular SDKs or database drivers (such as Prisma, SQLAlchemy)

#### The risk of borrowing code

Using third-party packages means borrowing code without fully understanding its internal implementation. As long as you can confirm its reliability through indicators such as GitHub's stars, followers, and download data, you can use it with confidence. However, two well-known packages were recently injected with Trojans, and there have been cases of contributors submitting malicious code in supply chain attacks, all of which remind us that borrowing code is inevitably risky. Ultimately, this is a trade-off between input and output: writing your own code consumes more energy, while borrowing someone else's code may improve efficiency, but may bring security risks or bugs, so you must choose carefully.

- Safety advice:
- Check maintenance active level (last commit time)
- Follow GitHub issues and CVE risk notifications
- Enterprise projects avoid using packages with "0 stars/0 maintainers"

#### Borrowing of small pieces of code

Another situation is to use small pieces of code. For example, the code found through Google search usually has only a dozen or twenty lines, which is not suitable for large-scale copying and pasting, and usually needs to be adjusted according to the actual situation; only in some cases, the code can be used directly.

- ✅ small piece of code that can be borrowed:
- Array deduplicate
- File path concatenation
- Small general logic such as time format conversion

### 4.9.2 make sure you understand the code vs make sure you understand how to use the code

For borrowing small pieces of code, I suggest that everyone try to understand its logic as much as possible, even if it doesn't have to be completely thorough, but at least know the function of the code, because in most cases you need to adjust it. This can avoid relying solely on copy and paste. Some novice programmers may now prefer to directly copy and paste code, but in the long run, if they don't understand the operation of the code, they may be replaced by AI. Therefore, at least have a clear understanding of the basic idea of the code.

- Understand the code ≠ memorize all the implementation details
- At the very least, you should be able to answer: 'What does this code do? What happens after changing a parameter?'

#### Review of AI generated code

For the code generated by AI, I suggest that you weigh it according to the specific situation. Especially when using it for the first time, you should try to figure out which parts AI has modified. For example, I asked AI to modify the front-end code of a Bible quiz game some time ago. I roughly understand its changes because the front-end mainly involves HTML syntax, so there is no need to review it line by line. However, when encountering unfamiliar code logic, it is best to spend some time carefully reviewing it to avoid blind copying and pasting, otherwise it may fall behind the pace of AI in the long run.

- Suggestion: **"Code that can be replaced by AI can also be replaced by humans with low threshold."**
- Using AI to improve efficiency → ✅
- Blind trust in AI, loss of judgment → ⚠️

#### Environment variables and sensitive data

There is a certain risk in exposing environment variables and sensitive data to AI. Therefore, when dealing with sensitive projects, free AI tools should be avoided and products with commercial security guarantees and Non Disclosure Agreements should be chosen. For less sensitive projects, the risk is relatively low.

- Suggestions for handling sensitive data:
- Local deployment model first (such as Ollama/DeepSeek)
- Avoid pasting `.env `, API Key, and database password directly into the AI window
- Commercial projects prioritize the use of enterprise products with paid agreements

**Schematic diagram** : flowchart of borrowing code judgment

## 4.10 Don't be afraid to break things

What I'm going to talk about next is actually the other side of "small steps and fast running". I seem to have missed a paragraph, so I'll add it here. It's a comparison of the methods of "small steps and fast running" or "eating fat in one breath". Occasionally, I see some programmers, especially beginners who have just started programming, easily write a large piece of code at once, and then run the test again, such as writing more than ten or twenty lines of code and then verifying the effect. This approach is actually quite dangerous or inefficient.Although it seems efficient on the surface, thinking "write a long paragraph in one breath and continue writing once it works", in reality, it often doesn't work. As mentioned before, in most cases, there will definitely be problems.

- "Destruction" in development is inevitable, the key is: **whether problems can be quickly discovered and repaired in time** .
- Writing more than ten lines of code before testing often leads to an increase in the difficulty of error location.
- Compared to "unified debugging after accumulating errors", **writing while verifying is safer and more efficient** .

### 4.10.1 frequent testing to find problems quickly

So if you write ten lines of code, you have to debug ten lines of code. If you write line by line and debug line by line, the debugging efficiency will be much higher. As mentioned earlier, if you find an error in one hundred lines of code, it's like finding a needle in a haystack. Similarly, debugging a problem in ten lines of code may also be difficult. For example, if you write ten lines of code and think the problem may be in the first five lines, but in fact the problem is in the sixth to tenth lines. You may spend half a day troubleshooting the error.

Therefore, we should follow the principle of "test often and break fast", which is a commonly mentioned phrase in the programmer community. That is to say, we should frequently test and quickly expose problems. Do not wait until the tenth line to go back and solve the problem in the first line. Try to run every line and discover problems in a timely manner. In order to achieve this, we need a convenient debugging Development Environment.

- 🌟 principle: **Test Often, Break Fast**
- The earlier the error is triggered, the faster the problem is located
- The longer errors accumulate, the harder it is to restore the context
- ✅ recommended practices:
- Write 2-3 lines of logic → Run verification immediately
- When an error occurs, prioritize locating and repairing before continuing to write

### 4.10.2 Create a Comfortable Development Environment

I have also encountered this situation myself: sometimes I don't want to debug after writing a line of code, because the debugging process is too troublesome. If it takes ten minutes to test each time, or if I have to click on the browser to test a certain function, it takes a minute to click on several pages to reach the target page, then I will feel annoyed and tend to write more code to debug at once to avoid frequent testing. However, the risk of doing so is that once there is a problem, debugging will be very troublesome. As mentioned earlier, finding a problem in ten lines of code is completely different from finding a problem in two lines of code.

Therefore, if conditions permit, I suggest that everyone try to set up the Development Environment as handy as possible. Because people are lazy, once debugging is troublesome, they will subconsciously avoid debugging. If the Development Environment is uncomfortable, I myself will not want to debug, and I will tend to write a long section first and then call it together, so that it will be more difficult to troubleshoot if there is a problem. Therefore, it is recommended to optimize the Development Environment as comfortable as possible under conditions. For example, if you can run the code every five seconds and verify it immediately after changing a line, this rhythm is actually the most ideal.

- The biggest obstacle to development rhythm is the **high debugging cost** .
- ⚙️ recommended tools/methods:
- Auto-save & compile (Auto-reload, Hot Reload)
- Run test scripts or pages with one click
- Quick input of test data (mock data, toolbar injection)

#### Personalization of Development Environment

Some frameworks do not support Hot Module Replacement or Live Reload. Of course, how to set up a comfortable Development Environment may vary depending on your mileage and personal preferences. However, the principle is to configure the environment to be comfortable enough that you are willing to write a line of code to test the effect, which is the most ideal state. Although not all projects can achieve this.

For some PHP projects, especially the old ones we are still maintaining (although most of them have been updated), those old projects have nothing: no Development Environment, no documentation, no test data, everything is missing. If you want to debug a certain function, you can only directly go to the server to call PHP code. Such extreme situations do exist. This does not mean that it is completely impossible to set up a Development Environment, but that the original project was not well-equipped, and rebuilding it requires a lot of effort, time, configuration, and understanding of the principle, etc.

So it's not a "hard standard" to test every line of code you write. Instead, if **conditions permit** , especially if you already have a basic Development Environment, or at least know how to set up a Development Environment, it is recommended to make the environment as comfortable as possible. This is more conducive to taking small steps and debugging quickly, which is an ideal best practice.

- Development Environment Comfort directly affects "testing frequency" → indirectly affects "debugging efficiency".
- Even in old projects that are not ideal, you should consider whether there is an opportunity to **build a minimal test entrance first** .

**Flow diagram** (can generate flowcharts):

[Start development]

​    ↓

Is the fast testing environment configured?

↓ Yes ↓ No

[Test every 2-3 lines] [Prioritize building a simple debugging entrance]

​    ↓                            ↓

[Quickly identify problems] [Reduce future debugging time costs]

​    ↓

Smaller-grained debugging → Fewer errors → Higher development efficiency

## 4.11 Temporary Solutions vs. Best Practices

The last point is about the trade-off between temporary solutions and best practices. These two often conflict in actual development. Here is a quote, "Perfection is not attainable, but if we chase perfection, we can catch excellence." In Chinese, it can be roughly translated as: "Perfection is never attainable, but in the process of pursuing perfection, we can approach excellence."In fact, in development work, there is always room for optimization in many codes - whether it's code style, logical structure, Design pattern, reusability, abstraction ability, or even the entire architecture level, there will always be a more ideal solution, which is the so-called best practice.

- 🎯 Best Practice is a "long-term sense of direction" rather than a "short-term mandatory standard".
- ✅ allow the function to be written first → but **keep the awareness and list of "can be optimized"** .
- 🛠️ software development is never "finished writing", but the process of approaching the ideal.

#### Realistic limitations

However, many times, we do not have the conditions to achieve the ideal solution in actual work. For example, due to tight deadlines, time constraints, or already feeling overwhelmed, especially when we first encounter a new project, framework, or language, just implementing the function may have already exhausted a lot of energy. At this time, it is difficult to spend time polishing the code and finding the optimal solution. Whether due to limited energy or project progress constraints, we often have to settle for temporary or non-optimal solutions.

- Common limiting factors in reality:
- ⏱️ tight project cycle/fast launch requirements
- 🧠 novice stage/technology stack is not yet proficient
- 🤝 team collaboration complexity/code style inconsistency
- Temporary solutions ≠ mistakes, but **pragmatic choices under constraints** .

#### Pursue excellence rather than perfection

But what I want to say is that although reality often limits us from making the optimal solution, it does not prevent us from **maintaining the awareness of pursuing the optimal solution** . In other words, don't "slack off". I have seen some programmers who belong to the completely slack off type - they have no requirements for code quality, as long as the function can run smoothly, it is completed, and they clap their hands and turn to the next task. Although the task is completed in the short term, if you have a little pursuit of yourself, you should not be satisfied with just completing the task. Even if time does not allow you to write the ideal elegant code, at least you should have that sense of direction.

- Don't give up the pursuit, just **put it aside for now** .
- ✨ having "improvement awareness" is more important than the code itself.
- Direction determines growth rate more than current state.

#### Establish code aesthetics

In other words, using the "deliberate practice" concept of "Yi Tang" to explain, it is to establish **aesthetic standards for code** . Knowing what good code is and what clear structure is. Even if the code you currently write does not meet that "beautiful" standard, at least you should know what the ideal state is like and move towards that direction when you have spare energy. This is actually a kind of training in itself. As you become more accustomed to thinking about "how to write better code", the quality of your code will naturally improve.At the beginning, you may think that writing high-quality code is an extra effort, but once you develop the habit, this kind of thinking will become a subconscious behavior. You don't need to spend time on "optimization". The code you write is already of higher quality.

- 💡 way to build "code beauty":
- Read high-quality open source projects (such as Rails/Vue/Next.js).
- After writing the code, **go back and refactor** it once
- Pay attention to the "naming/layering/commenting habits" in other people's code.

#### Quote: Pursuit of Excellence

> [Quote] “Perfection is not attainable, but if we chase perfection, we can catch excellence.” - Vince Lombardi

As this sentence says, although we may never achieve perfection, in the process of pursuing perfection, we will constantly approach excellence. Even if we cannot achieve perfection in some projects, we can keep trying and thinking to make our code closer and closer to high-quality standards.

- ✨ "pursuit of perfection" is never to achieve perfection, but to **raise the lower limit and raise the upper limit** .
- If you can't write to the extreme, don't give up on "writing better".

#### Balanced art

But it is also necessary to avoid the other extreme: **excessive pursuit of perfection** . In many practical situations, project progress, team collaboration, resource constraints, etc. do not allow you to spend a lot of time picking every detail and polishing the code to perfection alone. Therefore, a balance point must be found in between. On the one hand, accept the imperfection of reality, and on the other hand, do not completely give up the pursuit because of imperfection. In other words, do not write casually just because you don't have time or energy, regardless of the code quality. This "lying flat programming" is also not advisable.

- Extreme one: ❌ "perfectionism obsessive-compulsive disorder" → procrastination on the line, wasting time
- Extreme two: ❌ "can run on the line to slack off" → technical growth stagnation, quality is difficult to maintain
- ✅ Recommended status: **"Written + retained + changed"** = stable + maintainable + room for improvement

**Chart** : Code Balance Chart of Ideal and Reality

| State of mind                          | Typical behavior                                  | Risk                                                         | Adjust direction                                           |
| -------------------------------------- | ------------------------------------------------- | ------------------------------------------------------------ | ---------------------------------------------------------- |
| Extreme perfectionism                  | Refuse to launch, excessive refactoring           | Delay/Delivery failure                                       | Clear iteration rhythm, deliver first and optimize later   |
| Function Oriented/No Quality Standards | As long as you can run, never look back           | Technical debt accumulation/follow-up maintenance difficulties | Establish aesthetic consciousness and stage reconstruction |
| Balanced thinking                      | Have a sense of purpose, tolerate flaws in stages | Consciously compromise, but pursue a long-term optimization path | Leave TODO/code review post-processing backlog             |

### Questions and Summary

Is there any problem? Yes, in the end, it's actually a matter of "balance", yes. Some people may say that we should treat code like our own children, haha. Yes, we can't always have the mentality of "just make do with running", nor can we write a few lines of code in a year. That's right. I think the same goes for being a person. Many things are actually about finding that balance point. We may all want to do our best, but reality doesn't always allow us to do so. Being aware of the gap between our ideals and reality, and continuously moving towards our ideals, is actually growth.