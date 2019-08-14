---
layout: post_layout
title: What is JAMstack
date: 2019-06-23 00:00:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

JAMstack refers to the technology stack built using JavaScript, API and Markup. JAM is short for JavaScript, API and Markup. The first letter is abbreviated. JAMstack is a modern web development based on client-side JavaScript, reusable API and pre-built Markup. The architecture needs to meet the following three criteria:

1. JavaScript: Any dynamic programming in the request/response cycle is handled by JavaScript and runs entirely on the client. This can be any front-end framework, library, or even lightweight JavaScript.

2. API: All server-side processes or database operations are abstracted into reusable APIs that are accessed via HTTPS using JavaScript. These can be customized or utilize third party services.

3. &nbsp;

   Markup: Templated tags should be pre-built at deployment time, usually using the site builder of the content site or the build tool for the web application.

When we talk about "stacks," we don't talk about operating systems, specific web servers, backend programming languages, or databases. JAMstack has nothing to do with specific technologies. This is a new way to build websites and applications that deliver better performance, greater security, lower expansion costs, and a better developer experience.

&nbsp;

### What is not JAMstack?

&nbsp;

Any project that relies on tight coupling between the client and the server is not built using JAMstack. include:

* Sites built using server-side CMS, such as WordPress, Drupal, Joomla, or Squarespace.

* A web application running on a single server, it relies on Ruby, Node or other backend languages.

* &nbsp;

  A one-page application that uses isomorphic rendering to build views on the server at runtime.

### **Why do we choose JAMstack?**

1. Better performance: Why wait for the page to be dynamically built when the page is generated at deployment time? When it comes to minimizing the time of the first byte, nothing is better than the pre-built files provided by the CDN.

2. More security: abstracting server-side processes into microservice APIs can reduce the surface area of ​​the attack. You can also take advantage of the expertise of professional third-party services.

3. &nbsp;

   Cheaper, easier to extend: When your deployment is equivalent to a bunch of files that can be served anywhere, the extension is the problem of providing these files in more places. CDNs are perfect and usually include all the plans to expand them.

4. A better developer experience: loose coupling and control separation allow for more targeted development and debugging, and the choice of CMS options for site builder extensions eliminates the need to maintain separate stacks for content and marketing.

### Best Practices

&nbsp;

1. The entire project is placed on the CDN.

2. Everything is in Git

3. Modern build tool

4. Automatic build

5. &nbsp;

   Atomic deployment

6. &nbsp;

   Instant cache invalidation