+++
date  = 2026-01-01
draft  = false
title  = 'Python skills (part 2) - FastAPI'
tags = ["Code", "Python", "FastAPI"]
+++

## A Few Reminders

The first article was a refresher on Python basics. I created it to give myself a starting point. I won't detail it here, but I encourage you to read it if you haven't completed the first article yet. The second part aims to detail my journey toward deepening my Python learning. But for what purpose?

I am a proponent of DRY (Don't Repeat Yourself), which I borrow from Eric Johnson, and especially because I am lazy. My goal is to simplify my life by automating repetitive tasks and serve various objectives such as Security At Scale, Boto3, and Google Cloud Python.

However, I am going to present something more concrete, with zero bullshit or abstraction. We will work on a concrete project, and you will follow my evolution on the subject. However, I do not guarantee regularity in article publication, subject to children and other various activities giving me time. And clearly, they have priority.

We will explore concepts and their direct applications through the articles for real skill development. This will not necessarily be the right way to do it; it might even not be the best way to do it. In that case, I will ask you for feedback so I can improve and benefit everyone (I know this blog will be read by one or two people, so take advantage and let loose—we're among ourselves, hahaha).

## We Have the Basics, What Next

After reviewing the Python basics proposed in Python skills (part 1), you can supplement if you have the energy or for more variety with:
- Exercism (I personally use it and find it's a good way to practice and consolidate these bases. I like looking at others' solutions to confront my reasoning)
- LeetCode (I also use it, but I'm not a fan. I'm not a fan of this type of exercise; that said, I'll tackle it for intellectual gymnastics)
- Maybe I'll do other exercises like those from LeetCode for gymnastics

Let's get back on track. We are going to take a project and explore it together and develop it according to different criteria. I chose to go with **FastAPI** because it's the trendy framework of the moment (at least I believe so) and especially because I haven't really used this framework yet.

I learned FastAPI through the book "Hands-On APIs for AI and Data Science" (which I personally recommend only if you already have a good Python foundation) and here's the project repo based on the book.
I stopped at chapter 5 because I don't have much interest in pursuing the AI and Data Science aspect. Regarding AI, that will be the subject of another article.

Don't worry, we will discover and dissect the framework through the project; you won't be lost.

## Knowledge Agora

I didn't have an idea for an API as elaborate as Ryan Day's book. I prompted Perplexity to find ideas by giving it clues: "I want to make an anarchist knowledge-sharing web API; propose ideas to me." That's when **The Knowledge Agora** was born.

So, **The Knowledge Agora** is a collaborative micro-blogging platform where users can share thoughts, ideas, and knowledge on any topic.

### Key Stages of API Design

I wanted something freely accessible (not confined in a book that encourages spending). So I chose to go with the freely accessible Postman article (Postman is a reference in the API universe) source: https://www.postman.com/api-platform/api-design/

#### Step 1: Determine What the API is Intended to Do
"An API that is responsible for an authentication workflow will have different requirements than an API that allows a user to browse a product catalog, so it's important to align on the use case before making any other decisions. The use case may also have implications on the type of architecture you choose."

**The Potential Users**

This is fictional; I haven't done any in-depth research or user surveys who would be API users (for example: generative AI developers wanting to create a chatbot from the API to engage in philosophy; or curious people about human behavior wanting to analyze data; etc.).

The structure below defines the tasks that users would like to do and that justifies creating the API. But here, it doesn't make sense:

**User type:** Me and any curious person  
**Primary tasks:** Write something to leave a trace  
**Pain points:** Nothing, because this API is not created from a real need or existing site

I therefore don't have to justify to a product manager:

**User desirability:** Your users want the product; Fictional project  
**Technical feasibility:** Your technical environment and team can create it; Yes, it's possible.  
**Economic viability:** You expect it to be worth the investment; We'll try to do it with a cost approaching zero.

Or even to do User stories: "As a (user type), I want to (goal or intent), So that (motivation or benefits)." It's fictional; the project doesn't meet a real need.

The basic features are:

*   **Create & Share**: Write notes anonymously or with a nickname.
*   **Discover**: Browse notes, filter by topic or author, and search content.
*   **Engage**: Upvote the most interesting notes.
*   **Curate**: Pin important notes to highlight them.
*   **Manage**: Securely delete notes (Admin only).
*   **Documentation**: Interactive API documentation via Swagger UI.

#### Step 2: Define the API Contract with a Specification

First, the API architecture.

The most popular API architectures are:
- SOAP
- REST
- GraphQL
- gRPC
- WebSocket
- Webhook

I won't explore all of them here, but the following link makes a good comparison: https://openapi.com/blog/top-6-api-architectures

The 2025 State of the API Report shows that "REST still dominates at 93%" (https://www.postman.com/state-of-api/2025/#api-testing-and-tooling)

I chose REST because it is the industry standard, and it is appropriate for providing resource-based APIs for a simple CRUD application. It is also supported by a broad range of technologies, so future customers should have no problem using a RESTful API. Each action is explicitly an endpoint, which simplifies understanding and maintenance of the API.

GraphQL is also a good choice for users querying the data of the app, but I don't (yet) have the problem that GraphQL solves (for example: highly variable data requirements and many related objects).

Ok, the article is getting long, hahaha! The next article will continue defining the architecture and then dive into specifications. See you soon for the continuation!
