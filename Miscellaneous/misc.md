## HTTP

<details>
<summary>What is HTTP?</summary><br><b>

[Avinetworks](https://avinetworks.com/glossary/layer-7/): HTTP stands for Hypertext Transfer Protocol. HTTP uses TCP port 80 to enable internet communication. It is part of the Application Layer (L7) in OSI Model. 
</b></details>

<details>
<summary>Describe HTTP request lifecycle</summary><br><b>

* Resolve host by request to DNS resolver
* Client SYN
* Server SYN+ACK
* Client SYN
* HTTP request
* HTTP response
</b></details>

<details>
<summary>True or False? HTTP is stateful</summary><br><b>

False. It doesn't maintain state for incoming request.
</b></details>

<details>
<summary>How HTTP request looks like?</summary><br><b>

It consists of:

 * Request line - request type
 * Headers - content info like length, encoding, etc.
 * Body (not always included)
</b></details>

<details>
<summary>What HTTP method types are there?</summary><br><b>

* GET
* POST
* HEAD
* PUT
* DELETE
* CONNECT
* OPTIONS
* TRACE
</b></details>

<details>
<summary>What HTTP response codes are there?</summary><br><b>

* 1xx - informational
* 2xx - Success
* 3xx - Redirect
* 4xx - Error, client fault
* 5xx - Error, server fault
</b></details>

<details>
<summary>What is HTTPS?</summary><br><b>


HTTPS is a secure version of the HTTP protocol used to transfer data between a web browser and a web server. It encrypts the communication using SSL/TLS encryption to ensure that the data is private and secure.

Learn more: https://www.cloudflare.com/learning/ssl/why-is-http-not-secure/
</b></details>

<details>
<summary>Explain HTTP Cookies</summary><br><b>

HTTP is stateless. To share state, we can use Cookies.

TODO: explain what is actually a Cookie
</b></details>

<details>
<summary>What is HTTP Pipelining?</summary><br><b>
</b></details>

<details>
<summary>You get "504 Gateway Timeout" error from an HTTP server. What does it mean?</summary><br><b>

The server didn't receive a response from another server it communicates with in a timely manner.
</b></details>

<details>
<summary>What is a proxy?</summary><br><b>

A proxy is a server that acts as a middleman between a client device and a destination server. It can help improve privacy, security, and performance by hiding the client's IP address, filtering content, and caching frequently accessed data. 
  - Proxies can be used for load balancing, distributing traffic across multiple servers to help prevent server overload and improve website or application performance. They can also be used for data analysis, as they can log requests and traffic, providing useful insights into user behavior and preferences.
</b></details>

<details>
<summary>What is a reverse proxy?</summary><br><b>

A reverse proxy is a type of proxy server that sits between a client and a server, but it is used to manage traffic going in the opposite direction of a traditional forward proxy. In a forward proxy, the client sends requests to the proxy server, which then forwards them to the destination server. However, in a reverse proxy, the client sends requests to the destination server, but the requests are intercepted by the reverse proxy before they reach the server. 
  - They're commonly used to improve web server performance, provide high availability and fault tolerance, and enhance security by preventing direct access to the back-end server. They are often used in large-scale web applications and high-traffic websites to manage and distribute requests to multiple servers, resulting in improved scalability and reliability.
</b></details>

<details>
<summary>When you publish a project, you usually publish it with a license. What types of licenses are you familiar with and which one do you prefer to use?</summary><br><b>
</b></details>

<details>
<summary>Explain what is "X-Forwarded-For"</summary><br><b>

[Wikipedia](https://en.wikipedia.org/wiki/X-Forwarded-For): "The X-Forwarded-For (XFF) HTTP header field is a common method for identifying the originating IP address of a client connecting to a web server through an HTTP proxy or load balancer."
</b></details>

#### Load Balancers

<details>
<summary>What is a load balancer?</summary><br><b>

A load balancer accepts (or denies) incoming network traffic from a client, and based on some criteria (application related, network, etc.) it distributes those communications out to servers (at least one).
</b></details>

<details>
<summary>Why to used a load balancer?</summary><br><b>

* Scalability - using a load balancer, you can possibly add more servers in the backend to handle more requests/traffic from the clients, as opposed to using one server.
* Redundancy - if one server in the backend dies, the load balancer will keep forwarding the traffic/requests to the second server so users won't even notice one of the servers in the backend is down.
</b></details>

<details>
<summary>What load balancer techniques/algorithms are you familiar with?</summary><br><b>

  * Round Robin
  * Weighted Round Robin
  * Least Connection
  * Weighted Least Connection
  * Resource Based
  * Fixed Weighting
  * Weighted Response Time
  * Source IP Hash
  * URL Hash
</b></details>

<details>
<summary>What are the drawbacks of round robin algorithm in load balancing?</summary><br><b>

  * A simple round robin algorithm knows nothing about the load and the spec of each server it forwards the requests to. It is possible, that multiple heavy workloads requests will get to the same server while other servers will got only lightweight requests which will result in one server doing most of the work, maybe even crashing at some point because it unable to handle all the heavy workloads requests by its own.
  * Each request from the client creates a whole new session. This might be a problem for certain scenarios where you would like to perform multiple operations where the server has to know about the result of operation so basically, being sort of aware of the history it has with the client. In round robin, first request might hit server X, while second request might hit server Y and ask to continue processing the data that was processed on server X already.
</b></details>

<details>
<summary>What is an Application Load Balancer?</summary><br><b>
</b></details>

<details>
<summary>In which scenarios would you use ALB?</summary><br><b>
</b></details>

<details>
<summary>At what layers a load balancer can operate?</summary><br><b>

L4 and L7
</b></details>

<details>
<summary>Can you perform load balancing without using a dedicated load balancer instance?</summary><br><b>

Yes, you can use DNS for performing load balancing.
</b></details>

<details>
<summary>What is DNS load balancing? What its advantages? When would you use it?</summary><br><b>
</b></details>

#### Load Balancers - Sticky Sessions

<details>
<summary>What are sticky sessions? What are their pros and cons?</summary><br><b>

Recommended read:
  * [Red Hat Article](https://access.redhat.com/solutions/900933)

Cons:
  * Can cause uneven load on instance (since requests routed to the same instances)
Pros:
  * Ensures in-proc sessions are not lost when a new request is created
</b></details>

<details>
<summary>Name one use case for using sticky sessions</summary><br><b>

You would like to make sure the user doesn't lose the current session data.
</b></details>

<details>
<summary>What sticky sessions use for enabling the "stickiness"?</summary><br><b>

Cookies. There are application based cookies and duration based cookies.
</b></details>

<details>
<summary>Explain application-based cookies</summary><br><b>

* Generated by the application and/or the load balancer
* Usually allows to include custom data
</b></details>

<details>
<summary>Explain duration-based cookies</summary><br><b>

* Generated by the load balancer
* Session is not sticky anymore once the duration elapsed
</b></details>

#### Load Balancers - Load Balancing Algorithms

<details>
<summary>Explain each of the following load balancing techniques

  * Round Robin
  * Weighted Round Robin
  * Least Connection
  * Weighted Least Connection
  * Resource Based
  * Fixed Weighting
  * Weighted Response Time
  * Source IP Hash
  * URL Hash
</summary><br><b>
</b></details>

<details>
<summary>Explain use case for connection draining?</summary><br><b>
To ensure that a Classic Load Balancer stops sending requests to instances that are de-registering or unhealthy, while keeping the existing connections open, use connection draining. This enables the load balancer to complete in-flight requests made to instances that are de-registering or unhealthy.

The maximum timeout value can be set between 1 and 3,600 seconds on both GCP and AWS.

</b></details>

#### Licenses

<details>
<summary>Are you familiar with "Creative Commons"? What do you know about it?</summary><br><b>

The Creative Commons license is a set of copyright licenses that allow creators to share their work with the public while retaining some control over how it can be used. The license was developed as a response to the restrictive standards of traditional copyright laws, which limited access of creative works. Its creators to choose the terms under which their works can be shared, distributed, and used by others. They're six main types of Creative Commons licenses, each with different levels of restrictions and permissions, the six licenses are:

  * Attribution (CC BY): Allows others to distribute, remix, and build upon the work, even commercially, as long as they credit the original creator.
  * Attribution-ShareAlike (CC BY-SA): Allows others to remix and build upon the work, even commercially, as long as they credit the original creator and release any new creations under the same license.
  * Attribution-NoDerivs (CC BY-ND): Allows others to distribute the work, even commercially, but they cannot remix or change it in any way and must credit the original creator.
  * Attribution-NonCommercial (CC BY-NC): Allows others to remix and build upon the work, but they cannot use it commercially and must credit the original creator.
  * Attribution-NonCommercial-ShareAlike (CC BY-NC-SA): Allows others to remix and build upon the work, but they cannot use it commercially, must credit the original creator, and must release any new creations under the same license.
  * Attribution-NonCommercial-NoDerivs (CC BY-NC-ND): Allows others to download and share the work, but they cannot use it commercially, remix or change it in any way, and must credit the original creator.

Simply stated, the Creative Commons licenses are a way for creators to share their work with the public while retaining some control over how it can be used. The licenses promote creativity, innovation, and collaboration, while also respecting the rights of creators while still encouraging the responsible use of creative works.

More information: https://creativecommons.org/licenses/
</b></details>

<details>
<summary>Explain the differences between copyleft and permissive licenses</summary><br><b>

In Copyleft, any derivative work must use the same licensing while in permissive licensing there are no such condition. GPL-3 is an example of copyleft license while BSD is an example of permissive license.
</b></details>

#### Random

<details>
<summary>How a search engine works?</summary><br><b>
</b></details>

<details>
<summary>How auto completion works?</summary><br><b>
</b></details>

<details>
<summary>What is faster than RAM?</summary><br><b>

CPU cache.
[Source](https://www.enterprisestorageforum.com/hardware/cache-memory/)
</b></details>

<details>
<summary>What is a memory leak?</summary><br><b>

A memory leak is a programming error that occurs when a program fails to release memory that is no longer needed, causing the program to consume increasing amounts of memory over time.

The leaks can lead to a variety of problems, including system crashes, performance degradation, and instability. Usually occurring after failed maintenance on older systems and compatibility with new components over time.
</b></details>

<details>
<summary>What is your favorite protocol?</summary><br><b>

SSH
HTTP
DHCP
DNS
...
</b></details>

<details>
<summary>What is Cache API?</summary><br><b>
</b></details>

<details>
<summary>What is the C10K problem? Is it relevant today?</summary><br><b>

https://idiallo.com/blog/c10k-2016
</b></details>

## Storage

<details>
<summary>What types of storage are there?</summary><br><b>

  * File
  * Block
  * Object
</b></details>

<details>
<summary>Explain Object Storage</summary><br><b>

- Data is divided to self-contained objects
- Objects can contain metadata
</b></details>

<details>
<summary>What are the pros and cons of object storage?</summary><br><b>

Pros:
  - Usually with object storage, you pay for what you use as opposed to other storage types where you pay for the storage space you allocate
  - Scalable storage: Object storage mostly based on a model where what you use, is what you get and you can add storage as need
Cons:
  - Usually performs slower than other types of storage
  - No granular modification: to change an object, you have re-create it
</b></details>

<details>
<summary>What are some use cases for using object storage?</summary><br><b>
</b></details>

<details>
<summary>Explain File Storage</summary><br><b>

- File Storage used for storing data in files, in a hierarchical structure
- Some of the devices for file storage: hard drive, flash drive, cloud-based file storage
- Files usually organized in directories
</b></details>

<details>
<summary>What are the pros and cons of File Storage?</summary><br><b>

Pros:
- Users have full control of their own files and can run variety of operations on the files: delete, read, write and move.
- Security mechanism allows for users to have a better control at things such as file locking
</b></details>

<details>
<summary>What are some examples of file storage?</summary><br><b>

Local filesystem
Dropbox
Google Drive
</b></details>

<details>
<summary>What types of storage devices are there?</summary><br><b>
</b></details>

<details>
<summary>Explain IOPS</summary><br><b>
</b></details>

<details>
<summary>Explain storage throughput</summary><br><b>
</b></details>

<details>
<summary>What is a filesystem?</summary><br><b>

A file system is a way for computers and other electronic devices to organize and store data files. It provides a structure that helps to organize data into files and directories, making it easier to find and manage information. A file system is crucial for providing a way to store and manage data in an organized manner.

Commonly used filed systems:
  Windows:
  * NTFS
  * exFAT

  Mac OS:
  * HFS+
  *APFS

</b></details>

<details>
<summary>Explain Dark Data</summary><br><b>
</b></details>

<details>
<summary>Explain MBR</summary><br><b>
</b></details>
