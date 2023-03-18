# Scheduling using GPT-4

Exploring if GPT-4 can generate a conference schedule using constraints.  For the moment without success 🥹

I've taken the public available [VoxxedDays Zurich](https://voxxeddays.com/zurich/schedule/) conference schedule details including the accepted talks.

## The constraints

HIGH CONSTRAINTS:

1. Use the talk summary to decide which talks should follow each other 
3. Don't use talks with the same tracks at the same time 
4. A speaker can't speak at different rooms during the same time
5. Only use the listed talks
6. List the talk id, from/to time, room name, title, speaker names, level and track name 

MEDIUM CONSTRAINTS:
1. Use markdown to list the generated schedule 

## The schedule info in CSV format

```
"from hour";"to hour";"session type";"room name"
"10:35";"11:20";Conference;Room 2 
"10:35";"11:20";Conference;Room 8
"10:35";"11:20";Conference;Room 7 
"10:35";"11:20";Conference;Room 3
"11:30";"12:15";Conference;Room 3
"11:30";"12:15";Conference;Room 8
"11:30";"12:15";Conference;Room 7
"11:30";"12:15";Conference;Room 2
"13:25";"14:10";Conference;Room 8
"13:25";"14:10";Conference;Room 7
"13:25";"14:10";Conference;Room 3
"13:25";"14:10";Conference;Room 2
"14:20";"15:05";Conference;Room 7
"14:20";"15:05";Conference;Room 8
"14:20";"15:05";Conference;Room 2
"14:20";"15:05";Conference;Room 3
"15:25";"16:10";Conference;Room 3
"15:25";"16:10";Conference;Room 2
"15:25";"16:10";Conference;Room 8
"15:25";"16:10";Conference;Room 7
"16:20";"17:05";Conference;Room 3
"16:20";"17:05";Conference;Room 2
"16:20";"17:05";Conference;Room 8
"16:20";"17:05";Conference;Room 7
```

## The talks to schedule in CSV format

```
"Talk ID";"Talk Title";"Audience Level";"Talk Sumamry";"Track Name";"Speaker Availability days";"Available from";"Available to";"Speaker names"
1411;Unit Test Your Java Architecture With ArchUnit;BEGINNER;ArchUnit is a library in the Java ecosystem that can be used to test architecture within unit tests to help structure code and prevent an unmaintainable code base. jMolecules can also be used to model architectural concepts within the code.;Development Practices;;;;Roland Weisleder
3872;Full-stack development is dead, long live full-stack development!;INTERMEDIATE;Java developers can develop web applications quickly by using frameworks such as Thymeleaf, Vaadin, and Hilla.;UI & UX;;;;Simon Martinelli
4367;Let's talk about software behaviour (BDD);BEGINNER;This session teaches you about Behaviour Driven Development and how it can be useful in software development.;Development Practices;;;;Katrin Rabow
4372;Wasmer Things: An Upside-Down Guide to WebAssembly;INTERMEDIATE;This talk is for all developers interested in learning more about WebAssembly from a low-level perspective. We will explore the WebAssembly specification, how it plugs into your own development ecosystem, and how it is similar to other compilation targets. We will also discuss why many projects are making Wasm their preferred runtime environment.;Mind the Geek;;;;Edoardo Vacchi
4505;Awesome Java applications with GraalVM and Java microservices frameworks;INTERMEDIATE;This session will explore microservices frameworks for Java applications and how to configure them for use with GraalVM Native Image for fast startup and low resource usage.;Server Side Java;;;;Alina Yurenko
4506;Resumability in the next generation frontend framework With O(1) loading time;BEGINNER;"Qwik is a JavaScript framework that uses a new render paradigm called resumability to serialize JavaScript apps into HTML without the need for the hydration technique used in meta-frameworks like Next.js. It enables us to build ""resumable apps"" with near-zero JavaScript and fine-grained lazy loading. It is not the world's first O(1) JavaScript framework. This article covers what Qwik is, how it compares to React and Angular, how to make";UI & UX;;;;Ruby Jane Cabagnot
4515;Developer Joy – How great teams get s%*t done;INTERMEDIATE;In this talk, Sven will discuss how great software teams measure and improve their developer productivity, coordinate work across teams, run microservice teams, and create a healthy and joyful engineering culture. He will share practical advice based on his experience with Atlassian and other tech companies on how to build and run a distributed architecture in the cloud, ensure observability, and keep a healthy balance between dev speed and code quality.;People & Culture;;;;Sven Peters
4521;The monolith must die! - How to convince managers;ADVANCED;We can use the DORA metrics by Google to help us evaluate when it is worth investing in a move from a monolith to microservices. We can also discuss the business view and use it as a basis for the next round of management discussions.;Architecture;;;;Anja Kunkel
4913;Keep your dependencies in check;BEGINNER;We need to stay on top of updating our applications, but doing so can take a lot of time. Luckily, there are plenty of tools that can help, from package managers to bots that can create changes on our repositories. We should evaluate these options to find the best solution for our particular situation.;Build & Deploy;;;;Marit van Dijk
4914;Monorepos - The Benefits, Challenges and Importance of Tooling Support;BEGINNER;This talk will provide clarity about monorepos, why you might want to use one, and how to set them up for success in the long run. We'll discuss what monorepos are, how they differ from other code organization approaches, and the benefits and challenges that come with using them. We'll also explore the tooling available to help create and maintain healthy monorepos.;Development Practices;;;;Juri Strumpflohner
4918;Unleash the power of your applications with Micronaut and GraalVM;BEGINNER;In this talk, Micronaut committer Álvaro Sánchez-Mariscal will demonstrate how to quickly build optimised microservices with Micronaut and GraalVM Native Image. Attendees will learn how the combination of GraalVM Native Image and Micronaut can lead to efficient and highly performant applications that can be deployed to environments like Kubernetes or serverless platforms. The talk will include a live coding demo of an application using Micronaut Data;Server Side Java;;;;Álvaro Sánchez-Mariscal
4921;From User Action to Framework Reaction: A comparison of the Reactivity Concepts in Angular, React, Vue and Svelte;INTERMEDIATE;This talk compares the different approaches Angular, React, Vue and Svelte use to implement reactivity and how this affects application programming and architecture. Live coding demos will be used to demonstrate the differences between the frameworks.;UI & UX;;;;Jonas Bandi
4929;Revisiting Design Patterns after 20;INTERMEDIATE;In this talk, attendees will learn how to use the latest improvements in Java 20 to refactor code using legacy implementations of design patterns such as Strategy, Template Method, Visitor, Command, Decorator, Builder, and more. Live demonstrations will showcase how lambdas, records, switch expressions, and other modern features can improve code design.;Java;;;;Edson Yanaga
4931;Sailing Modern Java;INTERMEDIATE;This talk will cover new features in recent Java versions, such as Pattern Matching for switch, Record Patterns, Virtual Threads, Calling native stuff, Simple Web server, what's gone and what will be gone.;Java;;;;Piotr Przybyl
4945;A Glance At The Java Performance Toolbox;BEGINNER;This talk covers the use of JDK tools to analyze and improve the performance of Java applications. It explains the different functional areas of visibility needed in Java and how the JDK tools can provide that information.;Java;;;;Ana-Maria Mihalceanu
4947;Architecture aspects - evolutionary architecture development;INTERMEDIATE;When designing new software, it is important to consider 23 architectural aspects such as persistence, communication, translations, archiving, scaling, security, exception handling, etc. An evolutionary approach can be taken to tackle these aspects incrementally and learn more about the problem to be solved, allowing us to make an optimal decision as late as possible.;Architecture;;;;Urs Enzler
5251;Enterprise Serverless Adoption. An Experience Report;BEGINNER;This talk will discuss the unique serverless adoption story at the LEGO Group, including an overview of the evolution of serverless adoption, tips on growing serverless teams, best practices, and strategies to achieve sustainability with serverless.;Architecture;;;;Sheen Brisals
5259;Respect estimates;BEGINNER;"In this talk, Donald Knuth's statement, ""Software is hard,"" will be discussed and examples of practices that are often followed, even though they are no longer needed, will be presented. These waste and cults include estimates, tests, agile meetings, and architecture of systems.";Development Practices;;;;Jarek Ratajski
5261;Game of Loom: implementation patterns and performance implications playing with virtual threads;ADVANCED;Virtual threads are a potentially great game changer in the Java ecosystem, but their benefits and costs need to be carefully weighed before being implemented in a production system.;Java;;;;Mario Fusco
5268;What We've Learned from Scanning 10K+ Kubernetes Clusters;BEGINNER;We analyzed Kubescape data to find the most common misconfigurations and vulnerabilities in Kubernetes deployments. We will explain the implications of these findings and provide simple tips on how to reduce your risk.;Security;;;;Rotem Refael
5298;Why Building Your Ship (Application) with Raw Materials is a Bad Idea!;BEGINNER;This session will discuss how to create a secure and compliant software bill of materials (SBOM) that complies with regulations and best practices, even when the source of certain code cannot be verified. It will also cover what applications are not able to use open source code, and what companies are doing to circumnavigate these tricky waters.;Security;;;;Jamie Coleman
5456;Java Next - From Amber to Loom, from Panama to Valhalla;ADVANCED;This talk is about the four big Java projects: Amber, Panama, Loom, and Valhalla. It will discuss how each project will improve the language and how they will shape Java in the years to come.;Java;;;;Nicolai Parlog
5464;Spring Modulith – Spring for the Architecturally Curious Developer;ADVANCED;This talk discusses how Spring architects can use libraries such as jMolecules and Moduliths to improve the structuring of their code and make it more maintainable.;Server Side Java;;;;Oliver Drotbohm
5487;Spring Security: The Good Parts;INTERMEDIATE;This talk will teach you how to use Spring Security to secure your applications. You will learn about the library's architecture and how to use common abstraction patterns to make your code easier to read and maintain. You will also learn about the latest features in Spring Security 6.0.;Server Side Java;;;;Daniel Garnier-Moiroux
```

## The prompt

```
The conference schedule in CSV format:

"from hour";"to hour";"session type";"room name"
"10:35";"11:20";Conference;Room 2
"10:35";"11:20";Conference;Room 8
"10:35";"11:20";Conference;Room 7
"10:35";"11:20";Conference;Room 3
"11:30";"12:15";Conference;Room 3
"11:30";"12:15";Conference;Room 8
"11:30";"12:15";Conference;Room 7
"11:30";"12:15";Conference;Room 2
"13:25";"14:10";Conference;Room 8
"13:25";"14:10";Conference;Room 7
"13:25";"14:10";Conference;Room 3
"13:25";"14:10";Conference;Room 2
"14:20";"15:05";Conference;Room 7
"14:20";"15:05";Conference;Room 8
"14:20";"15:05";Conference;Room 2
"14:20";"15:05";Conference;Room 3
"15:25";"16:10";Conference;Room 3
"15:25";"16:10";Conference;Room 2
"15:25";"16:10";Conference;Room 8
"15:25";"16:10";Conference;Room 7
"16:20";"17:05";Conference;Room 3
"16:20";"17:05";Conference;Room 2
"16:20";"17:05";Conference;Room 8
"16:20";"17:05";Conference;Room 7

The talks in CSV format: 

"Talk ID";"Talk Title";"Audience Level";"Talk Sumamry";"Track Name";"Speaker Availability days";"Available from";"Available to";"Speaker names"
1411;Unit Test Your Java Architecture With ArchUnit;BEGINNER;ArchUnit is a library in the Java ecosystem that can be used to test architecture within unit tests to help structure code and prevent an unmaintainable code base. jMolecules can also be used to model architectural concepts within the code.;Development Practices;;;;Roland Weisleder
3872;Full-stack development is dead, long live full-stack development!;INTERMEDIATE;Java developers can develop web applications quickly by using frameworks such as Thymeleaf, Vaadin, and Hilla.;UI & UX;;;;Simon Martinelli
4367;Let's talk about software behaviour (BDD);BEGINNER;This session teaches you about Behaviour Driven Development and how it can be useful in software development.;Development Practices;;;;Katrin Rabow
4372;Wasmer Things: An Upside-Down Guide to WebAssembly;INTERMEDIATE;This talk is for all developers interested in learning more about WebAssembly from a low-level perspective. We will explore the WebAssembly specification, how it plugs into your own development ecosystem, and how it is similar to other compilation targets. We will also discuss why many projects are making Wasm their preferred runtime environment.;Mind the Geek;;;;Edoardo Vacchi
4505;Awesome Java applications with GraalVM and Java microservices frameworks;INTERMEDIATE;This session will explore microservices frameworks for Java applications and how to configure them for use with GraalVM Native Image for fast startup and low resource usage.;Server Side Java;;;;Alina Yurenko
4506;Resumability in the next generation frontend framework With O(1) loading time;BEGINNER;"Qwik is a JavaScript framework that uses a new render paradigm called resumability to serialize JavaScript apps into HTML without the need for the hydration technique used in meta-frameworks like Next.js. It enables us to build ""resumable apps"" with near-zero JavaScript and fine-grained lazy loading. It is not the world's first O(1) JavaScript framework. This article covers what Qwik is, how it compares to React and Angular, how to make";UI & UX;;;;Ruby Jane Cabagnot
4515;Developer Joy – How great teams get s%*t done;INTERMEDIATE;In this talk, Sven will discuss how great software teams measure and improve their developer productivity, coordinate work across teams, run microservice teams, and create a healthy and joyful engineering culture. He will share practical advice based on his experience with Atlassian and other tech companies on how to build and run a distributed architecture in the cloud, ensure observability, and keep a healthy balance between dev speed and code quality.;People & Culture;;;;Sven Peters
4521;The monolith must die! - How to convince managers;ADVANCED;We can use the DORA metrics by Google to help us evaluate when it is worth investing in a move from a monolith to microservices. We can also discuss the business view and use it as a basis for the next round of management discussions.;Architecture;;;;Anja Kunkel
4913;Keep your dependencies in check;BEGINNER;We need to stay on top of updating our applications, but doing so can take a lot of time. Luckily, there are plenty of tools that can help, from package managers to bots that can create changes on our repositories. We should evaluate these options to find the best solution for our particular situation.;Build & Deploy;;;;Marit van Dijk
4914;Monorepos - The Benefits, Challenges and Importance of Tooling Support;BEGINNER;This talk will provide clarity about monorepos, why you might want to use one, and how to set them up for success in the long run. We'll discuss what monorepos are, how they differ from other code organization approaches, and the benefits and challenges that come with using them. We'll also explore the tooling available to help create and maintain healthy monorepos.;Development Practices;;;;Juri Strumpflohner
4918;Unleash the power of your applications with Micronaut and GraalVM;BEGINNER;In this talk, Micronaut committer Álvaro Sánchez-Mariscal will demonstrate how to quickly build optimised microservices with Micronaut and GraalVM Native Image. Attendees will learn how the combination of GraalVM Native Image and Micronaut can lead to efficient and highly performant applications that can be deployed to environments like Kubernetes or serverless platforms. The talk will include a live coding demo of an application using Micronaut Data;Server Side Java;;;;Álvaro Sánchez-Mariscal
4921;From User Action to Framework Reaction: A comparison of the Reactivity Concepts in Angular, React, Vue and Svelte;INTERMEDIATE;This talk compares the different approaches Angular, React, Vue and Svelte use to implement reactivity and how this affects application programming and architecture. Live coding demos will be used to demonstrate the differences between the frameworks.;UI & UX;;;;Jonas Bandi
4929;Revisiting Design Patterns after 20;INTERMEDIATE;In this talk, attendees will learn how to use the latest improvements in Java 20 to refactor code using legacy implementations of design patterns such as Strategy, Template Method, Visitor, Command, Decorator, Builder, and more. Live demonstrations will showcase how lambdas, records, switch expressions, and other modern features can improve code design.;Java;;;;Edson Yanaga
4931;Sailing Modern Java;INTERMEDIATE;This talk will cover new features in recent Java versions, such as Pattern Matching for switch, Record Patterns, Virtual Threads, Calling native stuff, Simple Web server, what's gone and what will be gone.;Java;;;;Piotr Przybyl
4945;A Glance At The Java Performance Toolbox;BEGINNER;This talk covers the use of JDK tools to analyze and improve the performance of Java applications. It explains the different functional areas of visibility needed in Java and how the JDK tools can provide that information.;Java;;;;Ana-Maria Mihalceanu
4947;Architecture aspects - evolutionary architecture development;INTERMEDIATE;When designing new software, it is important to consider 23 architectural aspects such as persistence, communication, translations, archiving, scaling, security, exception handling, etc. An evolutionary approach can be taken to tackle these aspects incrementally and learn more about the problem to be solved, allowing us to make an optimal decision as late as possible.;Architecture;;;;Urs Enzler
5251;Enterprise Serverless Adoption. An Experience Report;BEGINNER;This talk will discuss the unique serverless adoption story at the LEGO Group, including an overview of the evolution of serverless adoption, tips on growing serverless teams, best practices, and strategies to achieve sustainability with serverless.;Architecture;;;;Sheen Brisals
5259;Respect estimates;BEGINNER;"In this talk, Donald Knuth's statement, ""Software is hard,"" will be discussed and examples of practices that are often followed, even though they are no longer needed, will be presented. These waste and cults include estimates, tests, agile meetings, and architecture of systems.";Development Practices;;;;Jarek Ratajski
5261;Game of Loom: implementation patterns and performance implications playing with virtual threads;ADVANCED;Virtual threads are a potentially great game changer in the Java ecosystem, but their benefits and costs need to be carefully weighed before being implemented in a production system.;Java;;;;Mario Fusco
5268;What We've Learned from Scanning 10K+ Kubernetes Clusters;BEGINNER;We analyzed Kubescape data to find the most common misconfigurations and vulnerabilities in Kubernetes deployments. We will explain the implications of these findings and provide simple tips on how to reduce your risk.;Security;;;;Rotem Refael
5298;Why Building Your Ship (Application) with Raw Materials is a Bad Idea!;BEGINNER;This session will discuss how to create a secure and compliant software bill of materials (SBOM) that complies with regulations and best practices, even when the source of certain code cannot be verified. It will also cover what applications are not able to use open source code, and what companies are doing to circumnavigate these tricky waters.;Security;;;;Jamie Coleman
5456;Java Next - From Amber to Loom, from Panama to Valhalla;ADVANCED;This talk is about the four big Java projects: Amber, Panama, Loom, and Valhalla. It will discuss how each project will improve the language and how they will shape Java in the years to come.;Java;;;;Nicolai Parlog
5464;Spring Modulith – Spring for the Architecturally Curious Developer;ADVANCED;This talk discusses how Spring architects can use libraries such as jMolecules and Moduliths to improve the structuring of their code and make it more maintainable.;Server Side Java;;;;Oliver Drotbohm
5487;Spring Security: The Good Parts;INTERMEDIATE;This talk will teach you how to use Spring Security to secure your applications. You will learn about the library's architecture and how to use common abstraction patterns to make your code easier to read and maintain. You will also learn about the latest features in Spring Security 6.0.;Server Side Java;;;;Daniel Garnier-Moiroux

Create me a conference schedule with following constraints: 
1. HIGH CONSTRAINT: Talks have great educational flow 
2. HIGH CONSTRAINT: Use the talk summary to decide which talks should follow each other 
3. HIGH CONSTRAINT: Don't have the same tracks at the same time. 
4. HIGH CONSTRAINT: A speaker can't speak at different rooms during the same time. 
5. List the talk id, from/to schedule time, room name, title, speaker names, level and track name 
6. Only use the listed talks! 
7. Use markdown to list the generated schedule
```

## The results

### Generation error

![Generation error](https://github.com/stephanj/Scheduling-using-GPT4/raw/master/assets/error-output-1.png)

### Generation stop prematurely

![Generation error](https://github.com/stephanj/Scheduling-using-GPT4/raw/master/assets/error-output-3.png)

### Doesn't follow constraints

![Constraints violation](https://github.com/stephanj/Scheduling-using-GPT4/raw/master/assets/error-output-2.png)

### Hallucinations

Creates new schedule slots which were not defined

![Generation error](https://github.com/stephanj/Scheduling-using-GPT4/raw/master/assets/error-output-4.png)



