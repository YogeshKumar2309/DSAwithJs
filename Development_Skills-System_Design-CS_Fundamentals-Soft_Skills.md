Complete Job-Ready Developer Syllabus (Deep Dive)
Total Time: 300-400 hours (3-4 months alongside DSA)

1. Development Skills (30% Weightage) - 120-150 hours

A. TypeScript (25-30 hours)
Basics (8-10 hours)

What is TypeScript

Superset of JavaScript
Static typing benefits
Compilation process


Type Annotations

Primitive types (string, number, boolean)
Array types
Object types
Any, unknown, never, void


Type Inference

How TS infers types
When to use explicit types


Functions

Parameter types
Return types
Optional parameters
Default parameters
Rest parameters



Intermediate (10-12 hours)

Interfaces

Defining interfaces
Optional properties
Readonly properties
Extending interfaces
Interface vs Type


Type Aliases

Union types
Intersection types
Literal types
Type narrowing


Enums

Numeric enums
String enums
Const enums


Classes

Class properties
Access modifiers (public, private, protected)
Readonly modifier
Inheritance
Abstract classes
Implements keyword



Advanced (7-8 hours)

Generics

Generic functions
Generic interfaces
Generic classes
Generic constraints
Utility types


Advanced Types

Mapped types
Conditional types
Template literal types
Index signatures


Type Guards

typeof guards
instanceof guards
Custom type guards


Decorators

Class decorators
Method decorators
Property decorators


Module System

Import/Export
Namespaces
Declaration files (.d.ts)



Practice Projects:

Todo App with TypeScript
Type-safe API client
E-commerce cart with strict types


B. Node.js & Express.js (40-50 hours)
Node.js Fundamentals (15-18 hours)
Core Concepts (6-7 hours)

What is Node.js

Event-driven architecture
Non-blocking I/O
Single-threaded event loop


Modules System

CommonJS (require/module.exports)
ES Modules (import/export)
Built-in modules
Third-party modules (npm)


File System (fs module)

Reading files (sync/async)
Writing files
Deleting files
Working with directories
Streams for large files


Path Module

Joining paths
Resolving paths
Getting file extensions


HTTP Module

Creating basic server
Handling requests
Sending responses
Routing basics



Asynchronous Programming (5-6 hours)

Callbacks

Callback pattern
Callback hell problem


Promises

Creating promises
.then() and .catch()
Promise chaining
Promise.all(), Promise.race()


Async/Await

Async functions
Await keyword
Error handling with try/catch
Sequential vs Parallel execution


Event Emitters

Creating custom events
Listening to events
Removing listeners



NPM & Package Management (4-5 hours)

Package.json

Dependencies vs devDependencies
Scripts
Versioning (semantic versioning)


Installing packages

Local vs global installation
Package-lock.json


Popular packages

dotenv (environment variables)
nodemon (auto-restart)
axios (HTTP requests)
joi (validation)



Express.js Framework (25-32 hours)
Basics (10-12 hours)

Express Setup

Installing Express
Creating first server
Port configuration


Routing

GET, POST, PUT, DELETE requests
Route parameters (/user/:id)
Query parameters (?name=value)
Route handlers
Router object
Chaining route handlers


Request & Response

req.body, req.params, req.query
req.headers
res.send(), res.json()
res.status()
res.redirect()


Middleware

What is middleware
app.use()
Order of middleware execution
Built-in middleware (express.json(), express.static())
Custom middleware
Error-handling middleware



Intermediate (8-10 hours)

RESTful API Design

REST principles
Resource naming
HTTP methods usage
Status codes (200, 201, 400, 404, 500)
API versioning


Database Integration

Connecting to MongoDB (Mongoose)
Connecting to PostgreSQL (pg/Sequelize)
CRUD operations
Schema design
Relationships (one-to-many, many-to-many)


Input Validation

Joi validation
Express-validator
Custom validators
Sanitization


File Uploads

Multer middleware
File size limits
File type validation
Storing in cloud (AWS S3, Cloudinary)



Advanced (7-10 hours)

Authentication & Authorization

JWT (JSON Web Tokens)

Creating tokens
Verifying tokens
Token expiration


Password hashing (bcrypt)
Protecting routes
Role-based access control (RBAC)
OAuth 2.0 basics


Security Best Practices

Helmet.js (security headers)
CORS (Cross-Origin Resource Sharing)
Rate limiting (express-rate-limit)
SQL injection prevention
XSS prevention
Input sanitization


Error Handling

Try-catch blocks
Global error handler
Custom error classes
Async error handling
Logging errors (Winston, Morgan)


Performance Optimization

Caching strategies
Compression middleware
Database indexing
Connection pooling
Load balancing basics



Must-Know Packages:

express
mongoose / sequelize
jsonwebtoken
bcrypt
dotenv
cors
helmet
express-validator / joi
multer
morgan
winston


C. Real Working Projects (40-50 hours)
Project 1: Task Management API (15-18 hours)
Features:

User Authentication (signup, login, logout)
JWT-based authorization
CRUD operations for tasks
Task categories/tags
Task priority and due dates
Search and filter tasks
User profile management

Tech Stack:

Node.js + Express
MongoDB + Mongoose
JWT authentication
bcrypt for passwords
Input validation (Joi)

Learning Goals:

RESTful API design
Authentication flow
Database relationships
Error handling
Input validation


Project 2: E-commerce Backend (15-20 hours)
Features:

User authentication (customer, admin)
Product management (CRUD)
Categories and subcategories
Shopping cart functionality
Order management
Payment integration basics
Product search and filters
Image uploads
Reviews and ratings

Tech Stack:

Node.js + Express + TypeScript
PostgreSQL + Sequelize (or MongoDB)
JWT + Role-based access
Multer for images
Stripe/Razorpay integration

Learning Goals:

Complex database schema
Role-based authorization
File uploads
Payment gateway integration
Advanced querying


Project 3: Real-time Chat Application (10-12 hours)
Features:

User authentication
One-on-one messaging
Group chats
Online/offline status
Typing indicators
Message read receipts
File sharing
Emoji support

Tech Stack:

Node.js + Express
Socket.io (WebSockets)
MongoDB
JWT authentication
React/Vue for frontend (optional)

Learning Goals:

WebSocket communication
Real-time features
Event-driven architecture
Scalability challenges


D. Git & GitHub (10-15 hours)
Git Basics (4-5 hours)

Version Control Concepts

What is version control
Distributed vs centralized


Git Installation & Setup

Installing Git
git config (username, email)


Basic Commands

git init
git clone
git status
git add
git commit
git log
git diff


Working with Remote

git remote add
git push
git pull
git fetch



Branching & Merging (3-4 hours)

Branches

git branch
git checkout / git switch
Creating feature branches
Branch naming conventions


Merging

git merge
Fast-forward merge
Three-way merge
Merge conflicts
Resolving conflicts


Rebasing

git rebase
Interactive rebase
When to use rebase vs merge



Advanced Git (3-4 hours)

Stashing

git stash
git stash pop
git stash apply


Undoing Changes

git reset (soft, mixed, hard)
git revert
git checkout -- file


Tagging

Lightweight tags
Annotated tags
Pushing tags


Git Best Practices

Commit message conventions
Atomic commits
When to commit
.gitignore file



GitHub (2-3 hours)

Repository Management

Creating repositories
README.md files
Licenses
.gitignore templates


Collaboration

Forking repositories
Pull requests
Code reviews
Issues and discussions


GitHub Actions (Basics)

CI/CD introduction
Simple workflows


Profile Optimization

Professional README
Pinned repositories
Contribution graph
GitHub stats




2. System Design (15% Weightage) - 60-80 hours

A. Scalability Concepts (20-25 hours)
Horizontal vs Vertical Scaling (3-4 hours)

Vertical Scaling

Adding more CPU/RAM
Limitations
When to use


Horizontal Scaling

Adding more servers
Load distribution
Challenges
Benefits


Comparison and trade-offs

Load Balancing (5-6 hours)

What is Load Balancing

Distribution of traffic
Benefits


Load Balancing Algorithms

Round Robin
Least Connections
IP Hash
Weighted Round Robin


Types of Load Balancers

Hardware vs Software
Layer 4 vs Layer 7
Nginx, HAProxy


Session Management

Sticky sessions
Session replication
Stateless applications



Caching Strategies (6-7 hours)

What is Caching

Benefits
Cache hit vs miss
Cache invalidation


Caching Levels

Client-side caching (Browser)
CDN caching
Application caching (Redis)
Database caching


Caching Patterns

Cache-aside (Lazy loading)
Write-through
Write-back
Refresh-ahead


Cache Eviction Policies

LRU (Least Recently Used)
LFU (Least Frequently Used)
FIFO
TTL (Time To Live)


Redis Basics

Key-value store
Data structures
Pub/Sub
Use cases



Database Scaling (6-8 hours)

Replication

Master-Slave
Master-Master
Read replicas
Replication lag


Sharding

Horizontal partitioning
Sharding strategies

Range-based
Hash-based
Directory-based


Challenges


Partitioning

Vertical partitioning
When to use


Denormalization

Trade-offs
When to denormalize




B. Database Design (20-25 hours)
SQL Databases (10-12 hours)
Relational Model

Tables, Rows, Columns
Primary Keys
Foreign Keys
Relationships

One-to-One
One-to-Many
Many-to-Many
Junction tables



Normalization

1NF (First Normal Form)
2NF (Second Normal Form)
3NF (Third Normal Form)
BCNF (Boyce-Codd Normal Form)
When to denormalize

Indexing

What are indexes
B-Tree indexes
Hash indexes
Composite indexes
When to use indexes
Index overhead

Transactions & ACID

Atomicity
Consistency
Isolation

Isolation levels
Read phenomena (dirty read, phantom read)


Durability
Transaction management

Query Optimization

EXPLAIN plan
Avoiding N+1 queries
Join optimization
Subquery vs Join
Query caching

NoSQL Databases (10-13 hours)
Types of NoSQL

Document Stores (MongoDB)
Key-Value Stores (Redis)
Column Family (Cassandra)
Graph Databases (Neo4j)

MongoDB Deep Dive

Documents and Collections
Schema Design

Embedding vs Referencing
When to embed
When to reference


Indexes in MongoDB

Single field index
Compound index
Text index
Geospatial index


Aggregation Pipeline

$match, $group, $project
$lookup (joins)
$unwind


Replication

Replica sets
Primary and Secondary


Sharding in MongoDB

CAP Theorem

Consistency
Availability
Partition Tolerance
Trade-offs

When to Use SQL vs NoSQL

Use cases comparison
Hybrid approaches


C. API Design (20-30 hours)
REST API Design (12-15 hours)
REST Principles

Statelessness
Client-Server architecture
Uniform interface
Cacheable
Layered system

Resource Naming

Nouns not verbs
Plural vs Singular
Nested resources
Examples:

/users
/users/:id
/users/:id/posts



HTTP Methods

GET (Read)
POST (Create)
PUT (Update/Replace)
PATCH (Partial Update)
DELETE (Remove)
Idempotency

Status Codes

2xx Success

200 OK
201 Created
204 No Content


3xx Redirection

301 Moved Permanently
304 Not Modified


4xx Client Errors

400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
422 Unprocessable Entity


5xx Server Errors

500 Internal Server Error
502 Bad Gateway
503 Service Unavailable



API Versioning

URL versioning (/v1/users)
Header versioning
Query parameter versioning

Pagination

Offset-based
Cursor-based
Page-based
Limit and offset

Filtering & Sorting

Query parameters
/users?role=admin&sort=-createdAt
Multiple filters

Error Handling

Consistent error format
Error codes
Meaningful messages

Rate Limiting

Why rate limit
Token bucket algorithm
Headers (X-RateLimit-*)

HATEOAS

Hypermedia links
API discoverability

GraphQL (Optional - 5-7 hours)

GraphQL vs REST
Schema definition
Queries
Mutations
Resolvers
N+1 problem and DataLoader
When to use GraphQL

API Documentation (3-4 hours)

Swagger/OpenAPI
Postman collections
API documentation best practices
Examples and use cases

API Security (4-5 hours)

Authentication

API Keys
OAuth 2.0
JWT


HTTPS/TLS
CORS configuration
Input validation
SQL injection prevention
Rate limiting
API Gateway pattern


3. CS Fundamentals (10% Weightage) - 60-80 hours

A. Database Management Systems (20-25 hours)
Database Basics (5-6 hours)

What is DBMS
File System vs DBMS
Types of DBMS
Database Architecture

Three-tier architecture
Client-Server model


Data Models

Hierarchical
Network
Relational
Object-oriented



SQL (8-10 hours)
DDL (Data Definition Language)

CREATE TABLE
ALTER TABLE
DROP TABLE
TRUNCATE
Constraints

PRIMARY KEY
FOREIGN KEY
UNIQUE
NOT NULL
CHECK
DEFAULT



DML (Data Manipulation Language)

SELECT

WHERE clause
AND, OR, NOT
IN, BETWEEN
LIKE (pattern matching)
ORDER BY
LIMIT/OFFSET


INSERT

Single row
Multiple rows


UPDATE

Conditional updates


DELETE

Conditional deletes



Joins

INNER JOIN
LEFT JOIN
RIGHT JOIN
FULL OUTER JOIN
CROSS JOIN
SELF JOIN

Aggregate Functions

COUNT()
SUM()
AVG()
MIN()
MAX()
GROUP BY
HAVING

Subqueries

Scalar subquery
Row subquery
Table subquery
Correlated subquery
EXISTS

Advanced Concepts

Views
Stored Procedures
Triggers
Cursors (basic understanding)

Transaction Management (4-5 hours)

BEGIN, COMMIT, ROLLBACK
ACID properties (detailed)
Concurrency Control

Lock-based protocols
Two-phase locking
Deadlocks


Recovery techniques

Interview Questions (3-4 hours)

Common SQL interview queries
Database design questions
Normalization examples
Index optimization scenarios


B. Operating Systems (20-25 hours)
Process Management (6-8 hours)

Process vs Thread
Process States

New
Ready
Running
Waiting
Terminated


Process Control Block (PCB)
Context Switching
Process Scheduling

FCFS (First Come First Serve)
SJF (Shortest Job First)
Round Robin
Priority Scheduling


Inter-Process Communication

Shared Memory
Message Passing
Pipes
Signals



Thread Management (4-5 hours)

Single vs Multi-threading
User-level vs Kernel-level threads
Thread synchronization
Race conditions
Critical Section Problem
Mutex
Semaphores
Deadlock

Conditions for deadlock
Prevention
Avoidance (Banker's Algorithm)
Detection and Recovery



Memory Management (6-7 hours)

Memory Hierarchy
Logical vs Physical Address
Memory Allocation

Contiguous allocation
Paging
Segmentation


Virtual Memory

Demand Paging
Page Replacement Algorithms

FIFO
LRU (Least Recently Used)
Optimal


Thrashing


Heap vs Stack memory

File Systems (4-5 hours)

File organization
Directory structure
File allocation methods

Contiguous
Linked
Indexed


Disk Scheduling

FCFS
SSTF
SCAN
C-SCAN




C. Computer Networks (15-20 hours)
OSI Model & TCP/IP (4-5 hours)

7 Layers of OSI Model

Physical
Data Link
Network
Transport
Session
Presentation
Application


TCP/IP Model (4 layers)
Comparison

Network Layer Protocols (4-5 hours)

IP Addressing

IPv4 vs IPv6
Public vs Private IP
Subnetting basics


ARP (Address Resolution Protocol)
ICMP (Ping, Traceroute)
Routing basics

Static vs Dynamic routing



Transport Layer (4-5 hours)

TCP (Transmission Control Protocol)

Connection-oriented
Three-way handshake
Flow control
Congestion control
Reliable delivery


UDP (User Datagram Protocol)

Connectionless
Faster but unreliable
Use cases


Port numbers
Socket programming basics

Application Layer Protocols (3-5 hours)

HTTP/HTTPS

Request methods
Status codes
Headers
Cookies
Sessions
HTTP/1.1 vs HTTP/2 vs HTTP/3


DNS (Domain Name System)

How DNS works
DNS lookup process
DNS records (A, CNAME, MX)


FTP, SMTP basics
WebSockets


D. Object-Oriented Programming (5-10 hours)
4 Pillars of OOP (3-4 hours)
Encapsulation

Bundling data and methods
Access modifiers (public, private, protected)
Getters and Setters

Abstraction

Hiding complexity
Abstract classes
Interfaces
Real-world examples

Inheritance

IS-A relationship
Parent-Child classes
Method overriding
super keyword
Single vs Multiple inheritance

Polymorphism

Compile-time (Method Overloading)
Runtime (Method Overriding)
Dynamic binding

SOLID Principles (2-3 hours)

Single Responsibility Principle
Open/Closed Principle
Liskov Substitution Principle
Interface Segregation Principle
Dependency Inversion Principle

Design Patterns (Optional - 3-4 hours)

Creational

Singleton
Factory


Structural

Adapter
Decorator


Behavioral

Observer
Strategy




4. Soft Skills (5% Weightage) - 20-30 hours

A. Communication Skills (8-10 hours)
Technical Communication (4-5 hours)

Explaining complex concepts simply
Code walkthroughs
Writing documentation
Technical writing
Email etiquette
Slack/Teams communication

Interview Communication (4-5 hours)

Thinking out loud
Asking clarifying questions
Explaining your approach
Handling "I don't know"
STAR method for behavioral questions

Situation
Task
Action
Result



Practice:

Mock interviews (10+ sessions)
Pair programming
Code reviews
Presenting solutions


B. Problem-Solving Approach (6-8 hours)
Structured Problem Solving

Understand the problem
Identify constraints
Think of examples
Break down the problem
Start with brute force
Optimize step by step
Test edge cases

Debugging Skills

Reading error messages
Using debugger
console.log strategies
Binary search debugging
Rubber duck debugging

Code Quality

Clean code principles
Meaningful variable names
Function decomposition
DRY (Don't Repeat Yourself)
KISS (Keep It Simple, Stupid)
Code comments (when and why)


C. Teamwork (6-8 hours)
Collaboration Skills

Code reviews

Giving feedback
Receiving feedback


Pair programming
Agile/Scrum basics

Sprints
Stand-ups
Retrospectives


Conflict resolution

Version Control Collaboration

Pull request etiquette
Commit message standards
Branching strategies

Git Flow
GitHub Flow


Code ownership

Remote Work Skills

Async communication
Documentation importance
Time management
Meeting etiquette


Complete Timeline Summary
CategoryHoursPriorityDevelopment Skills120-150HIGHSystem Design60-80MEDIUMCS Fundamentals60-80MEDIUMSoft Skills20-30MEDIUMTOTAL260-340-

4-Month Study Plan (Alongside DSA)
Month 1: TypeScript + Node.js Basics

Week 1-2: TypeScript (25-30 hours)
Week 3-4: Node.js fundamentals (15-18 hours)
Total: 40-48 hours

Month 2: Express.js + First Project

Week 1-2: Express.js (25-32 hours)
Week 3-4: Task Management API (15-18 hours)
Total: 40-50 hours

Month 3: Advanced Backend + Projects

Week 1-2: E-commerce Backend (15-20 hours)
Week 3: Chat Application (10-12 hours)
Week 4: Git/GitHub mastery (10-15 hours)
Total: 35-47 hours

Month 4: System Design + CS Fundamentals

Week 1: System Design basics (15-20 hours)
Week 2: DBMS + SQL (20-25 hours)
Week 3: OS + Networks (15-20 hours)
Week 4: OOP + Soft Skills (10-15 hours)
Total: 60-80 hours


Parallel with DSA (Recommended Schedule)
Daily:

Morning (2 hours): DSA practice
Afternoon (1.5 hours): Development/Projects
Evening (30 mins): CS Fundamentals/Soft Skills

Weekly:

DSA: 14-15 hours
Development: 10-12 hours
CS Fundamentals: 3-5 hours

In 4 months:

DSA: 240+ hours ✅
Development + Others: 180+ hours ✅
Total: 420+ hours of focused learning


Bro, yeh pura roadmap hai! Koi specific topic ka detailed guide chahiye? 🚀