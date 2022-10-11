# What happens when you type…

The internet is probably the most successful invention ever. It has woven itself into the fabric of society and entire cultures have been built around it.
> At the highest level of abstraction, the internet is just a public network of connected devices.

Thinking of it this way would naturally make you see the logic behind another powerful invention; The **World Wide Web** (which shall hereafter be called *The Web*).

In this article, I will explain some important concepts around the workings of the internet and the web. The approach would be from a user’s perspective; what happens when you type `https://www.google.com` in your browser and hit `Enter`. What I hope to capture here is not just the complexity of events that happen almost in the blink of an eye, but the ingenuity of the human mind and how the convenience we enjoy today came from years of work. Alright, time for a deep dive…

# The Web
The web was invented by *Sir Timothy Berners-Lee*. By definition, the web is a subset of the internet. Think of it this way, if the internet is essentially a network, the web would be a particular functionality of this network. There are definitely other “functionalities”, but the web is arguably the most important and definitely the one I’ll be explaining.

It is best to think of the web in terms of what it was designed to do. This will help us understand how this underlying idea has evolved over time. 
> At its core, the web is an information system enabling documents and other resources to be accessed over the internet.

While this underlying idea has not changed, the implementation of it has evolved over time primarily in response to human activity. More and more resources can now be shared, the rendering of these resources is constantly improving, sharing important data can now be done securely, the infrastructure enabling the web is moving towards decentralization, and the list goes on and on. The evolution of the web has been grouped into stages and the version of the web I’ll be discussing here is tagged *Web 2.0*.

## The Web Browser
The implementation of the web is simply just crafting a set of rules that leverages the internet to provide a functionality. You need a tool, however, to help you assess and use this new functionality. **The web browser** is what this tool is called. Having given you a proper introduction, we will begin our journey from here.

# DNS Request
We shall begin with a simple idea; since the web is a way to share and access resources, we need to be able identify and locate what we need. The solution to this is called a **Uniform Resource Identifier** (*URI*). A URI is a unique sequence of characters that can be used to identify anything, including real-world objects, such as people and places, concepts, or information resources such as web pages. There are two classes of URIs:
- Uniform Resource Locator (URL): provides a means of locating and retrieving information resources on a network, either on the Internet or on another private network.
- Uniform Resource Name (URN): provides only a unique name, without a means of locating or retrieving the resource or information about it.

A classic example of a URL is `https://www.google.com`, which is exactly what you type in your browser. You're telling your browser to go find the resources located at `https://www.google.com`. But what computers really understand are numbers and while URLs are useful, they are really just a convenience, a string of characters in human language so you understand the request you are making.

A couple of definitions before I continue:
> A network protocol is a set of established rules that dictate how to format, transmit and receive data so that computer network devices can communicate, regardless of the differences in their underlying infrastructures, designs or standards. A set of cooperating network protocols is called a *protocol suite*.

> The Transmission Control Protocol/Internet Protocol (TCP/IP) is a protocol suite that specifies how data is exchanged over a network by providing end-to-end communications that identify how it should be broken into packets, addressed, transmitted, routed and received at the destination.

> An Internet Protocol Address (IP Address) is the method used by the TCP/IP to identify a device on a network.

The internet works using the TCP/IP and so your browser has to first find the IP address for that URL. To do this, your browser makes a request to the DNS (**Domain Name System**) resolver. The DNS works in the background to match URLs with the corresponding IP address. It's still possible for you to type an IP address into a browser to reach a website, but most people want an internet address to consist of easy-to-remember words.

DNS is organized in a hierarchy. An initial DNS request for an IP address is made to a resolver, which is typically operated by an Internet Service Providers (ISP). This search first leads to a root server, which has information on top-level domains (.com, .net, .org), as well as country domains. Root servers are located all around the world, so the DNS system routes the request to the closest one.

Once the request reaches the correct root server, it goes to a top-level domain server (TLD nameserver), which stores information for the second-level domain, which in our example would be the `google` in `www.google.com`. The request then goes to a domain nameserver, which looks up the IP address and sends it back to the web browser so it can visit the appropriate website. All of this takes mere milliseconds.

# Servers
Now your browser has the required IP address, which means your browser knows which device on the network (internet) has the resource you are looking for. Another important concept
> Client-Server Architecture is a computer network architecture in which devices called *clients* request and receive service/data from a centralized device called a *server*.

Following this architecture, your computer is the client and it has to make a request to another computer on the network which is the server. To help you make the request and view the received resource, you run a software called a **web browser** (for example, Mozilla Firefox). To help the other computer receive your request and send the requested resource, it needs to run a different software called a **web server** (for example, Nginx).

## Ports and Firewalls
Ports are logical constructs which act as connection endpoints within an operating system where network connections start and end. They help computers sort the network traffic they receive and easily differentiate between different kinds of traffic: emails go to a different port than webpages, for instance, even though both reach a computer over the same Internet connection.

Ports are standardized across all network-connected devices, with each port assigned a number. There are 65,535 possible port numbers, although not all are in common use. While IP addresses enable messages to go to and from specific devices, port numbers allow targeting of specific services or applications within those devices. Only a transport protocol such as the Transmission Control Protocol (TCP) can indicate which port a packet should go to.

A firewall is a security system that monitors and blocks or allows network traffic based on a set of security rules. A firewall typically establishes a barrier between a trusted network and an untrusted network, such as the Internet. Firewalls achieve this by allowing or disallowing specific ports from receiving or sending data over a network.

## Web Servers and Load Balancers
A web server is a software that uses HTTP, HTTPS and other protocols to respond to client requests made over the web. The main job of a web server is to display static website content through storing, processing and delivering webpages to users. Web servers could also support SMTP (Simple Mail Transfer Protocol) and FTP (File Transfer Protocol), used for email, file transfer and storage.
> The Hypertext Transfer Protocol (HTTP) is an application layer protocol in the TCP/suite designed to transfer information between networked devices and runs on top of TCP and other layers of the network protocol stack. HTTP runs on port 80.

HTTPS is an extension of HTTP with the `S` standing for *secure*. The principal motivations for HTTPS are authentication of the accessed website, and protection of the privacy and integrity of the exchanged data while in transit. HTTPS uses port 443. The need for security were the mandates for the creation of network security protocols. SSL (Secure Sockets Layer) and its successor, TLS (Transport Layer Security), are protocols for establishing authenticated and encrypted links between networked computers.

In order to provide a high degree of privacy, SSL/TLS encrypts data that is transmitted across the web. This means that anyone who tries to intercept this data will only see a garbled mix of characters that is nearly impossible to decrypt. To do this, SSL/TLS initiates an authentication process called a handshake between two communicating devices to ensure that both devices are really who they claim to be. SSL/TLS also digitally signs data in order to provide data integrity, verifying that the data is not tampered with before reaching its intended recipient.

An SSL/TLS Certificate is used to perform this handshake. An SSL/TLS certificate is a digital document that binds the identity of a website to a cryptographic key pair consisting of a public key and a private key. The public key, included in the certificate, allows a web browser to initiate an encrypted communication session with a web server. The private key is kept secure on the server, and is used to digitally sign web pages and other documents (such as images and JavaScript files). An SSL certificate also includes identifying information about a website, including its domain name and, optionally, identifying information about the site’s owner.

There is a limit to how responsive web servers can be. These limits are imposed by a myriad of factors including the design of the web server itself and the capacity of the computers they run on. As strain increases on a website or business application, eventually, a single server cannot support the full workload. To meet demand, organizations spread the workload over multiple servers.
> A Load Balancer is a critical component of any distributed system. It acts as a reverse proxy and distributes network traffic across a cluster of servers to improve the responsiveness and availability of applications, websites and compute resources.

In a typical setup, the IP address the DNS returns is actually that of the load balancer. The load balancer keeps track of the status of all the resources in its purview and when it receives a HTTP/HTTPS request, by some predetermined algorithm, it forwards the request to the right/available server.

## Application Servers and Databases.
Application servers are a critical aspect of Web 2.0. The motivation was the need to be able to deliver not only resources via the web but services too.
> An application server is a server that hosts applications or software that delivers a business application through a communication protocol.

This is the part of the stack that implements the business logic. It receives request from the web server, processes it, and sends the request back to the web server. In order to do this processing, many times it needs data. This is where databases come in.
> A database is an organized collection of structured information, or data, typically stored electronically in a computer system. A database is usually controlled by a database management system (DBMS).

A database management system is really just another server that listens for queries, usually from an application server, and returns the requested data. All the data the application server needs to provide its functionality is stored and retrieved from the database. Database servers also face the same limitation that web servers do and so you could have a couple of them and put a load balancer in front of them to distribute the traffic from the application server(s).

# Conclusion
Infrastructure security is a critical topic. Another reason to have distributed systems is to avoid having a "single point of failure". An important approach to consider is called the "method of least privilege"
> The Method of Least Privilege states that a subject should be given only those privileges needed for it to complete its task. If a subject does not need an access right, the subject should not have that right. Further, the function of the subject (as opposed to its identity) should control the assignment of rights.

An example would be that your database server should only be able to communicate with your application server.

It is also important to note that the distinctions between these technologies are rapidly blurring. For example, Nginx can function both as a load balancer and as a web server, NodeJS with ExpressJS on top of it can function as an application server and a web server in one.

All the processes explained here occur in milliseconds and your browser gets a bunch of HTML, CSS and Javascript files and uses those to render you a clean user interface.This article is in no way exhaustive, so you should read up some more on the concepts explained. But you now have a pretty clear understanding of all the work that happens when you type `https://www.google.com` in your browser and hit `Enter`.