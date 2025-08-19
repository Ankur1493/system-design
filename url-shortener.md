# Url Shortener
In here, we'll be building a URL shortener platform like dub.sh and bit.ly

## Core Features 
We'll be covering these features in this article. You can go deeper and try out more things, but these I feel are enough to cover a platform like URL shortener
- Shortening a URL
- Redirection
- Analytics


### Shortening a URL
User sends a request to our server for shortening a URL, let's say user uploads this URL https://github.com/Ankur1493/system-design with an alias ankur, so the URL will be platform.com/ankur

After the server receives the request, it checks if the user provides an Alias or not
If they send an alias, we have to check our DB to see if that alias is assignable or not, and just process based on this.
In case of not sending an alias, we'll look later

We can prefer PostgreSQL over here instead of a db like MongoDB, for some of these reasons
- We know the schema will be simple for this, maybe go through the schema of dub.sh on github
- It has a faster lookup if the indexes are integrated properly
- It is preferred over databases like MongoDB for analytics
<img width="1003" height="383" alt="Screenshot 2025-08-19 at 7 34 52 AM" src="https://github.com/user-attachments/assets/04fd3a8f-8d87-4257-8b5a-56662b6db024" />

In here, if the user doesn't send an alias, we'll need to generate a customised URL on our own! For this, we'll need to use something that keeps each URL unique.
We can use a counter that increments by 1 for every URL created, but this is very basic and works for a personal project. But in a scalable fashion, we need to use Snowflake and use some kind of encoding over here. Also, Snowflake allows us to have no DB lookup as the ID generated will be unique, so we can use Snowflake ID generation (it is a 64-bit number, it includes timestamp, worker, counter, etc)
**Note** Read a bit about Snowflake, it's a good thing you will use it in many projects

### Redirection Flow
In here, our main goal is that  when a user enters platform.com/alias or a URL we gave them, we'll have to redirect them to the original URL

Here, we'll use two layers of caching for faster redirection, as the main role of an application like this is to have a faster redirection. Let's discuss these one by one

1. CDN
Our request first hits the CDN (CloudFront, Cloudflare), and it checks if it's cached over there or not. If it is! It redirects the user to the original URL with a 302 status code
**Why even use a CDN?** CDNs are hosted globally and are the fastest way of redirecting users to the original page

If the CDN doesn't have this cached, meaning a cache miss, we move to the server (next step)

2. Redis
When CDN fails to redirect the user, the request reaches to our server, and we first check in our Redis if it's cached over there or not.
If it is, we use that and redirect the user; otherwise, we go to PostgreSQL for data


**Note** we'll have to take care of cache invalidation, we can use TTL and also if a user updates the registered URL
<img width="1254" height="441" alt="Screenshot 2025-08-19 at 7 31 54 AM" src="https://github.com/user-attachments/assets/237ad015-890a-49d3-ac42-dac7fb691793" />


### Analytics

First of all, we can use a queue kinda thing for async processing because if we just keep updating our DB each time a url is redirected it will cause a lot of writes and that's not good thing to have on our main DBs like PostgreSQL because of low throughput, so we'll use Kafka over here as it has high throughput but the thing with kafka is it's not good for keeping data longer so we'll update our main DB in batches!

**Note** Every redirection that happens via CDN won't show in the analytics as no event will be generated from there!

What we'll do is that we can create some partitions(based on shortID) in Kafka, and all the events of let's say shortID 1 will be in a single partition, there can be several IDs in a single partition!
After this, we can have a service that goes through the Kafka partitions one by one, and writes everything in batches, so we decrease our writes by a lot in this case
