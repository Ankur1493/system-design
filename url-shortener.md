# Url Shortener
In here, we'll be building a URL shortener platform like dub.sh and bit.ly

## Core Features 
We'll be covering these features in this article. You can go deeper and try out more things, but these I feel are enough to cover a platform like URL shortener
- Shortening a URL
- Redirection
- Custom Alias for URLs
- Analytics
- CDN caching for faster redirection


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


### Redirection Flow
In here, our main goal is that  when a user enters platform.com/alias or a URL we gave them, we'll have to redirect them to the original URL

Here, we'll use two layers of caching for faster redirectio,n as the main role of an application like this is to have a faster redirection. Let's discuss these one by one
<img width="1254" height="441" alt="Screenshot 2025-08-19 at 7 31 54 AM" src="https://github.com/user-attachments/assets/237ad015-890a-49d3-ac42-dac7fb691793" />
