# Problem 1
Aim: https://jsonplaceholder.typicode.com/
simple social media platform.
To be honest it will be my first experience with Artillery tool, but lets try:

Based on data,
**Here I have to say that these kind of statistics is not enough to do smart performance tests. We should know more from access logs/databases if your platform performs in production. First of all out proportion should be clear. But lets make it simple and imagine that we have only business predictions without numbers.**⋅⋅

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
![alt text](https://github.com/eszhlznkv/SocialMPLoad/blob/master/png/maxperf.png "maxperf")
The most frequent type of tests. We startet from scratch and increase load by stairs and trying to find critical performance level
### Reliability
![alt text](https://github.com/eszhlznkv/SocialMPLoad/blob/master/png/reliability.png "reliability")
We startet from scratch and increase load to high rate, but less then in maxperf level and leave system under that load for long time. In this way we can find a lot of diffrent leaks.
### Spike test
![alt text](https://github.com/eszhlznkv/SocialMPLoad/blob/master/png/spike.png "spike")
This test shows us how we can use our service during high spike of rates. Frequent pattern especially when product has agressive marketing via pushes or sms'es.
### Ideal test process schema
My viewpoint of schema about organizing stable, repeated tests execution
![alt text](https://github.com/eszhlznkv/SocialMPLoad/blob/master/png/Schema.png "Schema")

# Problem 2
Without access to logs, server metrics and source code it's only possible to rely on artillery's metrics.
Most important in my oppinion:
**Error count** - our API should work correct and expect blocks have to provide that checks
**Response time per diffrent percentiles(http.response_time)** - The most important, response time's affect on quality of service. It should be fast.
**Request rate (http.request_rate)** - Shows to us how our workload is going, correct as expected or not.
Unfortunatelly I didn't find in Artillery **APDEX** metric, which could be useful when we try to compare diffrent releases and make conclusion about quality of service on long time interval.
