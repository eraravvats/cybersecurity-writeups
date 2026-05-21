# How The Web Works

Comprehensive notes and understanding from the “How The Web Works” module.

---

# DNS (Domain Name System)

## What is DNS?

* Converts domain names → IP addresses
* Humans understand names
* Computers communicate using IP addresses

Example:

```text
google.com → 142.x.x.x
```

## Why DNS Exists

Without DNS:

* users would need to memorize IP addresses of websites

DNS acts like:

* internet phonebook
* internet translator

## Main Function

* Helps browser locate correct server
* Converts human-readable names → machine-readable IP addresses

---

# DNS Resolution Cycle

User enters domain
↓
Local Cache
↓
Recursive DNS Server
↓
Root DNS Server
↓
TLD Server
↓
Authoritative DNS Server
↓
IP Address Returned
↓
Browser connects to server
↓
Website loads

---

# DNS Components

## Local Cache

* Browser/computer first checks locally cached DNS entries
* Prevents unnecessary DNS requests
* Improves speed

## Recursive DNS Server

* Searches for IP address on behalf of client
* Usually provided by:

  * ISP
  * Google DNS
  * Cloudflare DNS

Examples:

```text
8.8.8.8
1.1.1.1
```

* Maintains own cache of previously resolved domains

## Root DNS Server

* Backbone of DNS hierarchy
* Redirects request to correct TLD server
* Does NOT know final IP address

## TLD (Top Level Domain) Server

* Handles domains like:

  * .com
  * .org
  * .in
* Points toward authoritative DNS server

## Authoritative DNS Server

* Stores actual DNS records for domain
* Returns final IP address

---

# DNS Records

## A Record

* Domain → IPv4 address

## AAAA Record

* Domain → IPv6 address

## CNAME Record

* Domain alias → another domain

Example:

```text
www.google.com → google.com
```

## MX Record

* Handles email routing

## TXT Record

* Stores verification/security information

Examples:

* SPF
* DKIM
* ownership verification

---

# TTL (Time To Live)

* Defines how long DNS response remains cached

Example:

```text
TTL = 3600
```

Meaning:

* cache response for 1 hour

---

# Domain Hierarchy

Example:

```text
www.google.com
```

Breakdown:

* .com → Top Level Domain (TLD)
* google → Second Level Domain
* www → Subdomain

Domains are read:
RIGHT → LEFT

---

# Important DNS Understanding

DNS uses distributed hierarchical architecture because:

* internet is too large for one server
* improves scalability
* improves reliability
* improves fault tolerance
* reduces workload
* caching improves speed

---

# HTTP (HyperText Transfer Protocol)

## What is HTTP?

* Protocol used for communication between client and server
* Defines rules for requests and responses
* Transfers webpages/resources over internet

## Main Purpose

* Allows browser and server to communicate
* Works on request-response model

---

# Basic Web Flow

User enters domain
↓
DNS resolves IP address
↓
TCP connection established
↓
Browser sends HTTP request
↓
Server sends HTTP response
↓
Browser renders webpage

---

# Client and Server

## Client

* Requests data/resources

Examples:

* Browser
* Mobile app

## Server

* Stores/processes website data
* Responds to requests

---

# HTTP Request

* Message sent from client → server

Example:

```http
GET / HTTP/1.1
```

## Breakdown

* GET → HTTP method
* / → requested resource/homepage
* HTTP/1.1 → protocol version

---

# HTTP Response

* Message sent from server → client

Example:

```http
HTTP/1.1 200 OK
```

## Breakdown

* HTTP/1.1 → protocol version
* 200 → status code
* OK → request successful

---

# HTTP Methods

## GET

* Requests/receives data from server

Example:

```http
GET /login
```

## POST

* Sends data to server

Example:

```http
POST /login
```

## PUT

* Updates existing data/resource

## DELETE

* Deletes resource/data

---

# HTTP Status Codes

## 200 OK

* Request successful

## 403 Forbidden

* Access denied

## 404 Not Found

* Requested page/resource not found

## 500 Internal Server Error

* Server-side issue/error

---

# URL (Uniform Resource Locator)

## What is URL?

* Address/instructions for accessing internet resource

Example:

```text
http://user:password@tryhackme.com:80/view-room?id=1#task3
```

---

# URL Components

## Scheme

* Protocol used for communication

Examples:

* HTTP
* HTTPS
* FTP

## User:Password

* Authentication credentials

## Host

* Domain name/IP of target server

Example:

```text
tryhackme.com
```

## Port

* Service port to connect to

Common Ports:

* 80 → HTTP
* 443 → HTTPS

## Path

* Specific resource/page location

Example:

```text
/view-room
```

## Query String

* Extra information/data sent to server

Example:

```text
?id=1
```

Meaning:

* request resource with id = 1

## Fragment

* Reference to section within webpage

Example:

```text
#task3
```

---

# HTTP Headers

* Extra metadata/information sent with requests/responses

---

# Request Headers

## Host

* Specifies target website/domain

Example:

```http
Host: tryhackme.com
```

## User-Agent

* Tells server browser/software being used

Example:

```http
User-Agent: Firefox
```

## Referer

* Shows which webpage redirected user

Example:

```http
Referer: https://tryhackme.com
```

## Cookies

* Stores session/user information

---

# Response Headers

## Content-Type

* Type of data being returned

Examples:

* text/html
* image/png
* application/json

## Content-Length

* Size of response data

## Server

* Server software/version information

---

# Example HTTP Request

```http
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Firefox
Referer: https://tryhackme.com
```

---

# Example HTTP Response

```http
HTTP/1.1 200 OK
Server: nginx
Content-Type: text/html
Content-Length: 98
```

---

# Response Body

* Actual data/resource returned by server

Examples:

* HTML
* CSS
* images
* JSON
* videos

Example:

```html
<html>
<body>
Welcome
</body>
</html>
```

---

# Stateless Protocol

* HTTP does NOT remember previous requests automatically
* Every request treated independently

This is why:

* cookies
* sessions
  exist

---

# Cookies

## What are Cookies?

* Small pieces of data stored in browser
* Used to maintain session/state information

## Why Cookies Exist

HTTP is stateless:

* server does NOT automatically remember previous requests

Cookies help websites remember users/sessions.

---

# Cookie Flow

User logs in
↓
Server creates session
↓
Server sends cookie
↓
Browser stores cookie
↓
Browser sends cookie in future requests
↓
Server identifies user/session

---

# Example Cookie

## Server Response

```http
Set-Cookie: session=abc123
```

## Future Browser Request

```http
Cookie: session=abc123
```

---

# Main Uses of Cookies

* authentication
* session management
* user preferences
* tracking

---

# Session vs Cookie

## Session

* Stored on server
* Contains user/session data

## Cookie

* Stored in browser
* Usually stores session ID/token

---

# Cookie Security Attributes

## HttpOnly

* Prevents JavaScript access to cookie

## Secure

* Cookie only sent over HTTPS

## Expires / Max-Age

* Defines cookie lifetime

## SameSite

* Helps prevent CSRF attacks

---

# HTTP vs HTTPS

## HTTP

* Unencrypted communication
* Insecure

## HTTPS

* Encrypted HTTP using SSL/TLS
* Secure communication

---

# HTML Injection

## What is HTML Injection?

* Injecting HTML code into webpage through user input
* Occurs when website does NOT properly sanitize user input

Example:

```html
<h1>HACKED</h1>
```

If website renders input directly:

* browser interprets it as HTML

---

# Sanitization

* Process of filtering/cleaning dangerous input

Example:

```html
<h1>HACKED</h1>
```

Converted to:

```text
&lt;h1&gt;HACKED&lt;/h1&gt;
```

Now browser displays it as plain text.

---

# HTML Injection vs XSS

## HTML Injection

* Injects HTML tags
* Usually affects webpage appearance/layout

## XSS (Cross-Site Scripting)

* Injects JavaScript
* More dangerous
* Can steal cookies/sessions

Example:

```html
<script>alert(1)</script>
```

---

# Risks of HTML Injection

* page defacement
* fake forms
* phishing
* UI manipulation

---

# Important Security Principle

Never trust user input.

---

# How Websites Work

# Complete Website Architecture

Browser (Client)
↓
Web Server
↓
Backend/Application Logic
↓
Database

---

# Complete Web Flow

User enters domain
↓
DNS resolves domain → IP
↓
Browser establishes TCP connection
↓
Browser sends HTTP request
↓
Web server receives request
↓
Backend processes request
↓
Backend communicates with database
↓
Database returns data
↓
Backend creates response
↓
Server sends HTTP response
↓
Browser renders webpage
↓
Cookies/sessions maintain login state

---

# Frontend

* User-facing/client-side part of website
* Runs in browser

Technologies:

* HTML
* CSS
* JavaScript

Handles:

* forms
* buttons
* layouts
* user interaction

---

# Backend

* Server-side application logic

Handles:

* authentication
* sessions
* APIs
* database communication
* business logic

Languages:

* Python
* JavaScript (Node.js)
* PHP
* Java
* Go

---

# Web Server

* Handles HTTP traffic
* Receives requests and sends responses

Examples:

* Apache
* Nginx

---

# Database

* Organized persistent storage system

Stores:

* users
* passwords
* posts
* comments
* transactions

Examples:

* PostgreSQL
* MySQL
* MongoDB

---

# Static vs Dynamic Websites

## Static Website

* Same content for every user
* Usually HTML/CSS only

## Dynamic Website

* Content changes based on:

  * user
  * database
  * interaction

Requires:

* backend
* database

Examples:

* Instagram
* YouTube
* Amazon

---

# Login Flow

User enters credentials
↓
Browser sends POST /login
↓
Backend checks database
↓
Session created
↓
Server sends Set-Cookie header
↓
Browser stores cookie
↓
Future requests include cookie
↓
Server recognizes authenticated user

---

# APIs (Application Programming Interface)

* Allows applications/systems to communicate

Usually uses:

* HTTP
* JSON

Example JSON:

```json
{
  "username": "arav",
  "followers": 120
}
```

---

# Web Infrastructure Components

# Load Balancer

## What is Load Balancer?

* Distributes traffic across multiple servers
* Prevents server overload
* Improves reliability and scalability

## Flow

Users
↓
Load Balancer
↓
Server 1
Server 2
Server 3

## Main Functions

* traffic distribution
* failover handling
* performance improvement

Examples:

* Nginx
* HAProxy
* AWS ELB

---

# CDN (Content Delivery Network)

## What is CDN?

* Network of globally distributed servers
* Stores cached copies of website content

## Purpose

* reduce latency
* improve loading speed
* reduce server load
* provide DDoS protection

## Usually Stores

* images
* videos
* CSS
* JavaScript
* static files

Examples:

* Cloudflare
* Akamai
* AWS CloudFront

---

# Database Types

# Relational Database (SQL)

* Uses tables, rows, columns

Examples:

* PostgreSQL
* MySQL

Example Table:

| id | username |
| -- | -------- |
| 1  | arav     |

---

# NoSQL Database

* Flexible structure
* Often used for scalability/caching

Examples:

* MongoDB
* Redis

---

# WAF (Web Application Firewall)

## What is WAF?

* Security layer between user and website
* Filters malicious web traffic

## Flow

User
↓
WAF
↓
Website

## Detects/Blocks

* SQL Injection
* XSS
* malicious requests
* suspicious payloads

## Purpose

* protection
* filtering
* monitoring
* attack mitigation

---

# Real-World Website Architecture

User
↓
CDN
↓
WAF
↓
Load Balancer
↓
Backend Servers
↓
Database

---

# How Web Servers Work

# Web Server

## What is Web Server?

* Software that listens for incoming HTTP requests
* Delivers web content/resources to clients

## Examples

* Apache
* Nginx
* IIS
* NodeJS

---

# Basic Web Server Flow

Browser sends HTTP request
↓
Web server receives request
↓
Requested files/resources processed
↓
HTTP response returned

---

# Root Directory

* Default directory from which web server serves files

## Linux

/var/www/html

## Windows

C:\inetpub\wwwroot

---

# Virtual Hosts

## What are Virtual Hosts?

* Allow one web server to host multiple websites/domains

## How it Works

* Web server checks Host header from HTTP request
* Matches requested hostname to correct website configuration

Example:

```http
Host: google.com
```

## Example Mapping

google.com → /var/www/google

youtube.com → /var/www/youtube

---

# Static Content

## What is Static Content?

* Content that does NOT change

Examples:

* images
* CSS
* JavaScript
* fixed HTML

## Important

* Served directly from web server

---

# Dynamic Content

## What is Dynamic Content?

* Content changes based on:

  * user
  * database
  * interaction
  * request

Examples:

* Instagram feed
* dashboards
* search results

---

# Dynamic Website Flow

Browser request
↓
Backend code executes
↓
Database queried
↓
Dynamic content generated
↓
HTTP response returned

---

# Backend Languages

## Purpose

* Create dynamic/interactive websites

## Examples

* PHP
* Python
* NodeJS
* Ruby
* Java

---

# PHP Example

Request:

index.php?name=adam

Backend Code:

```php
<?php echo $_GET["name"]; ?>
```

Output:

```html
Hello adam
```

---

# Frontend vs Backend

## Frontend

* User-facing/client-side part
* Runs in browser

Technologies:

* HTML
* CSS
* JavaScript

## Backend

* Server-side processing logic

Handles:

* authentication
* APIs
* databases
* sessions
* dynamic content

---

# Final Important Cybersecurity Understanding

Most web attacks target:

* requests
* responses
* headers
* cookies
* sessions
* parameters
* frontend inputs
* backend logic
* APIs
* databases

Common Vulnerabilities:

* HTML Injection
* XSS
* SQL Injection
* CSRF
* authentication flaws
* session hijacking
* logic vulnerabilities

---

# Core Cybersecurity Principle

Never trust user input.

---

# Final Understanding

Modern websites are interconnected systems built using:

Frontend
↓
HTTP Requests/Responses
↓
Web Servers
↓
Backend Logic
↓
Databases
↓
Sessions/Cookies
↓
Rendered Response

Understanding this architecture is foundational for:

* web security
* APIs
* bug bounty
* pentesting
* application security
* backend security
* web exploitation
