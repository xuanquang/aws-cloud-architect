# overview
This module includes the following sections:

1.  Architectural need
2.  Overview of caching
3.  Edge caching
4.  Caching web sessions
5.  Caching databases

The module also includes a guided lab in which you will learn how to stream dynamic content by using Amazon CloudFront.


# module objectives

At the end of this module, you should be able to:

-   Identify how caching content can improve application performance and reduce latency
-   Identify how to design architectures that use edge locations for distribution and distributed denial of service (DDoS) protection
-   Create architectures that use Amazon CloudFront to cache content
-   Recognize how session management relates to caching
-   Describe how to design architectures that use Amazon ElastiCache

#  1.  Architectural need

![](caching-architecture.png)
In this module, you will learn how to implement caching in your networking environment. The final components of the architecture diagram (that is, Amazon ElastiCache and Amazon CloudFront) are introduced in this module, and have been revealed. This module will also cover database caching with Amazon DynamoDB.

![](m11-cafe-require.png)
The capacity of the café’s infrastructure is constantly being overloaded with the same requests for static content, such as images of menu items. This situation is increasing both cost and latency. Sofía and Nikhil want to identify and cache frequently accessed static content to reduce latency and improve the customer experience. Every time a customer loads the menu, it is served from the cache. However, when menu items change, the request is routed to the database, and the cache is updated.

In addition, local celebrities are starting to endorse the café through video testimonials. Sofía and Nikhil must use edge caching for streaming data so they can serve appropriate, regionally- appealing content based on the geolocation of the user who is loading the site.


# 2.  Overview of caching

key takeaways:

-   A cache provides high throughput, low-latency access to commonly accessed application data by storing the data in memory
-   When you decide what data to cache, consider speed and expense, data and access patterns, and your application’s tolerance for stale data
-   Caches can be applied and used throughout various layers of technology, including operating systems, networking layers, web applications, and databases

![](caching-01.png)

![](caching-02.png)


![](caching-03.png)


![](caching-04.png)


![](caching-05.png)

![](caching-06.png)


# 3.  Edge caching

key takeaways:
-   Amazon CloudFront is a **global CDN service** that accelerates the delivery of content, including static and video, to users with no minimum usage commitments.
-   CloudFront uses a global network that comprises **edge locations and regional edge caches** to deliver content to your users.
-   To use CloudFront to deliver your content, you specify an **origin server** and configure a CloudFront **distribution**. CloudFront assigns a domain name and sends your distribution’s configuration to all of its edge locations.
-   You can use Amazon CloudFront to **improve the resilience** of your applications that run on AWS from DDoS attacks.

![](latency.png)

![](cdn.png)

![](cloudfront-01.png)

![](cloudfront-02.png)


![](cloudfront-03.png)


![](cloudfront-04.png)


![](cloudfront-05.png)

![](cloudfront-06.png)

![](cloudfront-07.png)

![](cloudfront-08.png)


# 4.  Caching web sessions

key takeaways:

-   **Sessions** are used to manage user authentication and store user data while the user interacts with the application.
-   You can manage sessions with **sticky sessions**, which is a feature of Elastic Load Balancing load balancers. Sticky sessions **route requests to the specific server** that is managing the user’s session.
-   You can also manage sessions by **persisting session data outside the web server instance** — for example, in a distributed cache or DynamoDB table.

![](session-01.png)

![](session-02.png)

![](session-03.png)

![](session-04.png)



# 5.  Caching databases

key takeaways:
-   A **database cache** supplements your primary database by removing unnecessary pressure on it, typically in the form of frequently accessed read data
-   **DAX** is a fully managed, highly available, in-memory cache for DynamoDB that delivers a performance improvement of up to 10 times—from milliseconds to microseconds
-   **Amazon ElastiCache** is a side cache that works as an in-memory data store to support the most demanding applications requiring submillisecond response times

![](cache.png)

![](dynamodb-state.png)


![](dynamodb-accelerator-dax.png)

![](ddb-with-dax.png)

![](remote-or-side-caches-01.png)

![](elasticache.png)

![](redis-memcached.png)

![](redis-vs-memcached.png)

![](elasticache-component.png)

![](caching-strategy-01.png)

![](caching-strategy-02.png)

![](cache-adding-ttl.png)

![](3-tier-web.png)


# quiz
Look at the answer choices and rule them out based on the keywords.
![](m11-quiz.png)

# links
N/A