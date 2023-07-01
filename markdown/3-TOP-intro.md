# TOP Intro

## Asking Questions in TOP

<u>How To Ask Questions:</u> 
in Discord, Stack Overflow, etc

 - provide your code and surrounding context
 - point to the function/line number
 - see link: [how to ask programming questions](https://medium.com/@gordon_zhu/how-to-be-great-at-asking-questions-e37be04d0603)

If you can’t pinpoint the problem, you can share a screenshot.
In Discord, drag and drop your screenshot image file into the chat box - or simply use the PrtScn and paste keyboard shortcuts.

Always include the corresponding files containing the error. Even if it is a short amount of code, providing it in the discord server in the proper format along with a screenshot of the output is helpful to those debugging it. Make sure to also push your project to GitHub or put your corresponding code in a replit so that others can comb through and debug the code. 

----

In the Discord chat rooms, code can be displayed by using backticks ``

ex: \`Your Code`

For multiple lines of code:

\```
Your Multiple Lines of Code

\```

or

\```javascript
Your Multiple Lines of Colorful Code
\```

<u>Taking a Screenshot</u>:
\- use Snipping Tool to take a full screen snip
OR
\- use the shortcut..
PrtScr (button) = copies the entire screen to clipboard
Alt+PrtScr          = copies the active window or dialog box



## Basics of Computers

There are many types of computers now.. Personal, smartphone, tablet, watches, refrigerators, etc

There are two main styles of Personal Computer.. PC and Mac
PC - stemming from the original IBM PC from 1981 - usually run the Microsoft Windows operating system
Mac - the Macintosh computer came in 1984 and was the first widely used personal comp with a GUI - All Macs are made by Apple and almost always run Mac OS X

<u>Hardware</u>:
Computer Case (desktop computer box) contains..
Motherboard - the main circuit board - includes the CPU, memory, connections to the hard drive and optical drives, expansion card slots, and connections to the computer's ports
Central Processing Unit (CPU) aka processor - the brain - carries out commands - a processor's speed is measured in megahertz (MHz)
RAM (random access memory) - short term memory - temporary data storage - empty when computer is shut down - measured in megabytes (MB) or gigabytes (GB)
Hard Drive (HD) - long term storage - when you open a word file, info is copied from hard drive to RAM, then when you save, it is copied back to hard drive
Expansion Cards - expansion slots on the motherboard allow you to add PCI (peripheral compenent interconnect) cards for enhanced video, sound, network, etc
Graphics Processing Unit (GPU) - or video card is responsible for what you see on the monitor

<u>Software</u>:
Operating System: is the most important software that runs on a computer - it manages everything - operating systems use a GUI to bridge between computer and human - pressing buttons on the GUI is really running commands through the OS - it used to (1980s) all be just commands no GUI
\- Microsoft Windows - created in mid-1980s - about 80% of global operating systems
\- macOS - created right after Windows - macOS is <10% of global operating systems
\- Linux - a family of open-source operating systems (so linux is free) and there are many different distributions/versions to choose from
Linux accounts for <2% of global operating systems, however most servers run Linux

<u>Applications</u>:
an app is a type of software that allows you to perform tasks - there are desktop applications, mobile, etc

<u>Protection</u>:
Malware - any type of software that is designed to damage your computer or access personal information
malware includes.. viruses, worms, Trojan horses, and spyware
*most malware is distributed over the internet and is often bundled with other software

Bitdefender is an antivirus software which helps prevent malware from being installed and can also remove malware from your computer

<u>Software</u>:
source code = a technical blueprint that tells a program how to function
open source code = when the source code for a program/app/software is made open to the public
closed source code = when the source code for a program/app/software is kept closed (aka proprietary) to the public

closed source is way more common - but the open source options out there enable programmers to view and change the source code

closed source: Microsoft Office - Windows OS - Chrome Browser
open source: LibreOffice - Linux OS - Firefox Browser - WordPress

open source advantages.. usually free, and code availability invites public collaboration which can fix bugs, add features, and improve features quickly



## The Internet

the internet is **the hardware** \- the technical infrastructure that makes the web possible - it is a large network of computers which communicate

the world wide web is **the software**

information is broken up into packets before being sent through a literal network of wires to arrive on your screen

a server is a special computer connected directly to the **internet**, and **web pages** are files stored directly on that server's **hard drive**
every server has a unique Internet Protocol Address (IP Adress)

personal computers (my laptop) is not a server bc it is not connected **directly** to the internet - it is connected **indirectly** (through an Internet Service Provider)
and is therefore a client

every device connected directly or indirectly to the internet has an IP Address = a unique identification number (computer, server, smartphone, alexa, router, etc)

a **router** directs packets of info around the internet - insuring they arrive at the correct IP Address

note each website (domain) has a specific IP address (youtube.com = 208.42.428.284) and a server can host (physically store) multiple websites (domains) and therefore
'host headers' are sometimes added to server IP Addresses to create the website IP Address?

when you request the domain 'youtube.com' you are really requesting the IP Address 208.42.428.284

the DNS server is like a huge phonebook which keeps track of which domain name corresponds to which IP Address

DNS servers are managed by your Internet Service Provider or other entity (there is not only one?) but the assignment of IP Addresses and registration of domain names is all managed by an institution called ICANN (Internet Corporation for Assigned Names and Numbers)

Enter domain name (youtube.com) > browser sends a request to the DNS server > DNS server responds with the correct IP Address > your browser now forwards the IP Address as a request which is directed through the internet, helped along the way by routers, to reach the server hosting that IP Address > that server now starts sending the data back to you, again being guided by routers at each junction

again a youtube video (or any info) isn't sent all at once but rather as packets - the server breaks the video up into packets before sending them out - each packet contains the servers IP Address, your IP Address, and the sequence number of that specific packet (so it can be ordered correctly upon arrival)

the labeling of packets can vary depending on the Protocol used.. different internet protocols are used for different types of information..
TCP/IP - transports data
http/https - for web access
RTP - for live video, streaming, and video calls

among the billions of computers connected by the internet - web servers are a special kind that can send messages to web browsers
note: the *internet* is the infrastructure
the *web* is a service built on top of the infrastructure
*email* is another service built on top of the internet
*IRC* (internet relay chat) is another service

Internet - the big one - the public network
Intranets - a private network for example of a company or office building - an organization's intranet might host web pages
Extranets - are similar to intranets except they open all or part of the private network to allow sharing with other organizations



## The Web

Web Page: has a unique URL - is a simple document displayed by a browser - the base document is written in HTML -
the term **web page** specifically refers to HTML documents

Website: has a unique domain name and IP Address - a collection of linked web pages under one domain name -

Web Server: a computer hosting one or more websites - meaning all the web pages and supporting files are stored on that computer

Search Engine: a special kind of website which provides a service; searches for web pages from other websites

Browser: software application used to retrieve and display web pages

*note: the terms web page and website are especially easy to confuse for a website that contains only one web page. Such a website is sometimes called a single-page website or SPA

TCP/IP: Transmission Control Protocol and Internet Protocol are communication protocols that define how data should travel across the internet.

DNS: Domain Name System is like an address book for websites. Your browser asks the DNS server to convert the requested web address aka domain name to an associated IP Address (the IP Address of the web server where the website is stored) so that the browser can send HTTP messages to the right place

HTTP: Hypertext Transfer Protocol is an application protocol that defines a language for clients and servers to speak to each other.

Component files: A website is made up of many different files. These files come in two main types:
Code files: Websites are built primarily from HTML, CSS, and JavaScript, though sometimes other technologies.
Assets: all the other stuff, such as images, music, video, Word documents, and PDFs.

What's going on..?
you type web address in your browser > browser asks DNS server for the IP Address associated with that website (server IP Address) > the browser now sends an HTTP request message to the right server, asking it to send a copy of the website to you (this message is sent across the internet using TCP/IP protocol) > if the server approves the client request, it sends the client a 200 Ok message and sends the website's files to the browser as a series of packets > the browser assembles the packets



## Parsing Order

Order in which component files are parsed:

When browsers send requests to servers for HTML files, those HTML files often contain &lt;link&gt; elements referencing external CSS stylesheets and &lt;script&gt; elements referencing external JavaScript scripts. It's important to know the order in which those files are parsed by the browser as the browser loads the page:

\- The browser parses the HTML file first, and that leads to the browser recognizing any &lt;link&gt; element references to external CSS stylesheets and any &lt;script&gt; element references to JS scripts.

\- As the browser parses the HTML, it sends requests back to the server for any CSS files it has found from &lt;link&gt; elements, and any JavaScript files it has found from &lt;script&gt; elements, and from those, then parses the CSS and JavaScript.

\- The browser generates an in-memory DOM tree from the parsed HTML, generates an in-memory CSSOM structure from the parsed CSS, and compiles and executes the parsed JavaScript.

\- As the browser builds the DOM tree and applies the styles from the CSSOM tree and executes the JavaScript, a visual representation of the page is painted to the screen, and the user sees the page content and can begin to interact with it.



## Domain Names

Domain Names provide a human-readable address for any web server on the internet

a domain name may be made of several parts seperated by dots: developer.mozilla.org

the TLD or top-level-domain is that end bit (for example .org, .com, or .net)
(some TLDs require websites to meet strict policies as it shows what service the website provides to the user)

 .org, .com, and .net = don't require websites to meet any particular criteria
​ .us, .fr, and .se = can require the website be in a specific language or hosted in a certain country
​ .gov = is only allowed for government departments
​ .edu = is only used for educational or academic institutions

 note: TLDs can contain special as well as latin characters. A TLD's maximum length is 63 characters, although most are around 2–3

the Label (aka the SLD or secondary level domain) is the part just before the TLD and is case-insensitive sequence, up to 63 characters involving A to Z, 0 to 9, and the '-' character

a domain can have up to 3 labels, seperated by periods, if desired - often used to create 'subdomains' for a specific domain name
ex: mozilla.org developer.mozilla.org iot.mozilla.org bugzilla.mozilla.org (mozilla is the SLD in each case)

Domain Names connot be bought - else the web would fill up with unused domain names

you rent the Domain Name per year

there are Registrar companies who keep domain name registries which detail who is renting what