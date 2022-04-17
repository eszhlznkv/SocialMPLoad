# Problem 1
Aim: https://jsonplaceholder.typicode.com/.simple social media platform.

Based on data,
**Here I have to say that these kind of statistics is not enough to do smart performance tests. We should know more from access logs/databases if your platform performs in production. First of all out proportion should be clear. But lets make it simple and imagine that we have only business predictions without numbers.**

Posts between [1-100] we know that almost all of our user activity is based on reading lists of comments on posts. 
**80%  GET  https://jsonplaceholder.typicode.com/posts/[1-100]/comments.**
Occasionally, users create their own comments. 
**10% POST https://jsonplaceholder.typicode.com/posts/[1-100]/comments**

Rarely does a user create a post. **5% POST https://jsonplaceholder.typicode.com/posts/**
While it is also rare for a user to look at a specific post, they first have to access all the posts
before they go to the specific one. 
**5% GET posts —> https://jsonplaceholder.typicode.com/posts/[1-100]**

## Types of tests
Then we need to do some scenarios. In my opinion in this "foggy" task we have to use 3 basic types of tests to verify out platform:
### Max performance
### Reliability
### Spike test

### Ideal test process schema
![alt text](https://github.com/eszhlznkv/SocialMPLoad/blob/master/Schema.png "Schema")

# Problem 2

