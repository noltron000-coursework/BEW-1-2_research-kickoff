# Client & Server Persistence
A Reference Document for various forms of Persistance

HTTP itself is a stateless technology. That is to say that the user cannot make any personal changes to a website, only universal. A *State* is a sort of personalized version of a website. Without a *State*, everyone's shopping cart on Amazon would be the same at all times.

---

## LocalStorage
### Where this persistence lives:
Located on the user's hard drive, specifically behind the browser application.

### When the data would be deleted:
When removeItem(), clear(), or similar remove the data. If the user's hard drive is destroyed, this data is also lost. For the most part, it shouldn't be necessary to delete this data manually.

### Use Cases
Local Storage is a very simple sort of API. It is written all in JavaScript. It has been popularized in HTML5. It is easy to use and quite basic. It can be used for…
- Storing user settings, like whether dark mode is activated or not
- Storing info to be referenced by the application at an indefinitely later date

### Cons:
The fact that local storage is basic also leads to its downfall in places:
Totally not secure
- Synchronous
- ~5MB data cap
- Can only store strings

### Sources:
- https://dev.to/rdegges/please-stop-using-local-storage-1i04
- https://blog.logrocket.com/the-complete-guide-to-using-localstorage-in-javascript-apps-ba44edb53a36

---

## Persistent Cookies
### Where this persistence lives:
Located on the user's hard drive, specifically behind the browser application. However, cookies are created by the server itself.

### When the data would be deleted:
A persistent cookie is sometimes signed with an expiration date. When the date passes, the cookie is wiped from the user's hard drive unless it is updated. If the user's hard drive is destroyed, this data is also lost. For the most part, it shouldn't be necessary to delete this data manually.

### Use Cases:
Unlike Local Storage, Cookies can and will be accessed by the server. This means that using Cookies gives you more utility, where using Local Storage can save you valuable bandwidth.
- Storing user settings, like whether dark mode is activated or not.
- Storing data that will persist across computers when a user is logged in
- Storing low-security login information

### Cons:
Cookies are often used to communicate with the server. Despite their versatility, they can slow down web connections if there are too many.
- Indefinite file size…but browsers often limit it to a 4kb data cap
- Use network resources, a valuable asset

### Sources:
1. RFC 6265 https://tools.ietf.org/html/rfc6265#section-6.1
2. https://www.w3schools.com/js/js_cookies.asp
3. https://www.cisco.com/c/en/us/support/docs/security/web-security-appliance/117925-technote-csc-00.html

---

## Session Cookies
### Where this persistence lives:
Located on the user's Random Access Memory (RAM), specifically behind the current browser application processes. However, the cookies themselves are originally created from the server itself.

### When the data would be deleted:
Because the data is stored in RAM, the data is deleted as soon as the browser session is closed. This data can also be deleted from instructions in the code.

### Use Cases:
- Shopping Carts
- Online Game Sessions

### Cons:
Many of these pros and cons are double-edged swords when it comes to persistance and browser data storage. You might need to communicate with the server, and you might want the data to only last a session. On the other hand, there are many situation where you emphatically wouldn't want these things.
- Communicates with the server — uses network resources
- Data deletes when session is completed

### Sources:
1. https://www.sohamkamani.com/blog/2017/01/08/web-security-session-cookies/

---

## Sessions
### Where this persistence lives:
A *Session* is created in the server, sent over the network, and located on the user's machine. However, the server also takes note of the user's session so it can map a certain session token to a certain user, for example. In this way, it is stored on both the server and user machine. Because of this, the server can keep track of certain user trends to analyze on their end.

Often times, sessions utilize cookies to send the session key to the server, so it can understand who is requesting content.

### When the data would be deleted:
Sessions normally time out after a certain duration, because they use up valuable server resources. However, this downside seems to be mitigated with the help of cookies.

### Use Cases:
- Shopping Carts++
- Keeping pertinent user data handy

### Cons:
- Sessions time out after a set duration of time

### Sources:
1. http://www.lassosoft.com/Tutorial-Understanding-Cookies-and-Sessions
2. https://www.incapsula.com/load-balancing/sticky-session-persistence-and-cookies.html
3. https://www.f5.com/services/resources/white-papers/cookies-sessions-and-persistence

---

## Databases
### Where this persistence lives:
On a server, usually a server specifically dedicated to being a database. Databases are computers with huge amounts of hard drive storage space, and usually not that much else. Their other components' computing don't have to be explicitly amazing in comparison to other servers.

### When the data would be deleted:
When the data is requested to be deleted — often never for databases, since historical data trends can be as relevant as a subset of very recent data.

### Use Cases:
- Databases store large amounts of data.
- Databases are valuable for analyzing sets of information.
- Databases can track historical logs of data trailing back for years.

### Cons:
- Databases are slow because of the sheer amount of data that they must store.

### Sources:
1. http://www.agiledata.org/essays/relationalDatabases.html

---

## Client-Side Cache
### Where this persistence lives:
Client-side cache is stored in a folder on the user's machine hard-drive, and is accessed by RAM. If a request is repeated, client-side cache will speed up the process without even having to utilize the network.

### When the data would be deleted:
This data is deleted after a set duration of time, or when the user clears cache on their machine.

### Use Cases:
- Stores recently accessed data
- Often used to compliment databases
- Used in predictable access patterns

### Cons:
- Doesn't update data deltas frequently
- Client-side cache is not a solution for caching constantly updated assets, like stock prices.
- Doesn't account for randomness in data-access.

### Sources:
1. https://docs.gigaspaces.com/product_overview/client-side-caching.html
2. https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching

---

## Serve-Side Cache
### Where this persistence lives:
Server-side cache is generated and kept in the server. The server uses it to speed up redundent requests. It has many parellels to client-side cache.

### When the data would be deleted:

### Use Cases:
- Reducing repeat calculations and requests by having the result already prepared.
- Allowing for larger volumes of users to requests access a website.

### Cons:
- Needs to update data deltas if data changes.
- Only good for data that doesn't change much.
- Used in predictable access patterns.

### Sources:
1. https://medium.com/the-node-js-collection/simple-server-side-cache-for-express-js-with-node-js-45ff296ca0f0

---

## Remote Cache
### Where this persistence lives:

### When the data would be deleted:

### Use Cases:

### Cons:

### Sources:


---

## Remote Services
### Where this persistence lives:

### When the data would be deleted:

### Use Cases:

### Cons:

### Sources: