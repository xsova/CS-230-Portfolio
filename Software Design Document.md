# Software Design Document

## Draw It or Lose It
### CS 230 Project Software Design Template
#### Version 3.0

## Table of Contents
1. Document Revision History
2. Executive Summary
3. Requirements
4. Design Constraints
5. System Architecture View
6. Domain Model
7. Evaluation
8. Recommendations

## Document Revision History
| Version | Date       | Author       | Comments                                                                                                      |
|---------|------------|--------------|---------------------------------------------------------------------------------------------------------------|
| 1.0     | 06/02/2024 | Bryce Schultz | Added information and details.                                                                                |
| 2.0     | 06/16/2024 | Bryce Schultz | Verified that document meets Project 2 requirements. I didn’t realize when I originally turned this in that I wasn’t supposed to do the comparisons. |
| 3.0     | 6/22/2024  | Bryce Schultz | Verified that document meets Project 3 requirements made some refinements to the final section.               |

## Executive Summary
The Gaming Room, a game development company, wants to expand their game “Draw It or Lose It” to a web-based distributed environment allowing for multiple teams to play at the same time. The game involves guessing what is being drawn based on images rendered from a library of stock drawings. The client requires a software design document and a functional prototype of the game application.

To address these requirements, I will be developing a web-based version of the game using Java. The application will follow object-oriented programming principles and utilize design patterns such as ‘singleton’ and ‘iterator’ to ensure that the games, teams, and players are unique. The application will be designed to support multiple platforms and allow for future expansion.

## Requirements
The Gaming Room has outlined the following business and technical requirements for the "Draw It or Lose It" game application:

### Business Requirements
1. **Cross-Platform Support**: The application must be accessible on multiple platforms, including Windows, Mac, Linux, iOS, and Android.
2. **Scalability**: The application should support multiple teams and players simultaneously.
3. **User Engagement**: The application should be engaging and provide a smooth user experience across all platforms.
4. **Monetization**: The application should include features that allow for monetization, such as in-app purchases or advertisements.

### Technical Requirements
1. **Web-Based Distributed Environment**: The application must be web-based and support a distributed environment.
2. **Unique Game and Team Names**: Each game and team must have a unique name.
3. **Single Instance**: Only one instance of the game can exist in memory at any given time.
4. **Responsive Design**: The application must be responsive and adapt to various screen sizes and orientations.
5. **Security**: The application must ensure secure communication and data protection for users.
6. **Future-Proof**: The application should be designed to allow for future expansions and feature additions.
## Design Constraints
- The application must be developed for a web-based distributed environment.
- The game must support multiple teams and players simultaneously.
- Game and team names must be unique.
- Only one instance of the game can exist in the memory at any given time.
- The application should be scalable and extensible to accommodate future requirements.

## System Architecture View
The system architecture for the "Draw It or Lose It" game application is designed to support a web-based distributed environment, ensuring scalability, security, and seamless user interaction across multiple platforms. The architecture includes the following components:

### Overview
1. **Client-Side**: The front-end application running on users' devices (browsers, iOS, Android).
2. **Server-Side**: The back-end infrastructure responsible for game logic, data management, and communication with clients.
3. **Database**: The storage system for game data, user information, and other persistent data.

### Components
1. **Web Server**: Hosts the web application and serves static content (HTML, CSS, JavaScript). Examples include Apache, NGINX.
2. **Application Server**: Manages the core game logic, handles client requests, and communicates with the database. Typically implemented using a framework like Spring Boot (Java).
3. **Database Server**: Stores and manages data using a relational database management system (RDBMS) like MySQL or PostgreSQL.
4. **Load Balancer**: Distributes incoming traffic across multiple application server instances to ensure high availability and reliability.
5. **Caching Layer**: Improves performance by storing frequently accessed data in a cache (e.g., Redis).
6. **Authentication Server**: Manages user authentication and authorization using protocols like OAuth 2.0.
7. **API Gateway**: Acts as an entry point for client requests, routing them to appropriate services and handling tasks like rate limiting and logging.

### Logical Topology
1. **Client-Side**:
   - **Web Browser**: For desktop users on Windows, Mac, and Linux.
   - **Mobile Apps**: Native apps for iOS and Android, developed using frameworks like React Native or Flutter.

2. **Server-Side**:
   - **Web Server**: Handles HTTP requests, serves static files.
   - **Application Server**: Executes game logic, handles WebSocket connections for real-time gameplay updates.
   - **Database Server**: Manages game state, user information, and other persistent data.
   - **Load Balancer**: Ensures even distribution of traffic across application servers.
   - **Caching Layer**: Stores frequently accessed data to reduce database load.
   - **Authentication Server**: Verifies user identities and manages session data.

### Communication Flow
1. **Client Requests**: Users interact with the application via web browsers or mobile apps, sending requests to the web server.
2. **Web Server Processing**: The web server routes requests to the application server for processing.
3. **Application Server Logic**: The application server executes the game logic, updates game state, and communicates with the database.
4. **Database Operations**: The database server handles read/write operations, ensuring data consistency and persistence.
5. **Real-Time Updates**: For real-time gameplay, WebSocket connections between clients and the application server enable instant updates.
6. **Load Balancing**: The load balancer distributes incoming requests across multiple application server instances to maintain performance and availability.
7. **Caching**: Frequently accessed data is served from the cache to improve response times and reduce database load.
8. **Authentication**: The authentication server validates user credentials and manages secure sessions.

## Domain Model
- **Entity**: An abstract base class that holds common attributes (id and name) and behaviors for all entities in the application.
- **Game**: Represents a game instance and contains a list of teams. It inherits from the Entity class.
- **Team**: Represents a team participating in a game and contains a list of players. It also inherits from the Entity class.
- **Player**: Represents an individual player belonging to a team. It also inherits from the Entity class.
- **GameService**: A singleton class responsible for managing game instances, generating unique identifiers, and providing utility methods for adding and retrieving games.

### Relationships
- A game has a composition relationship with Team, so a game consists of one or more teams.
- A team has a composition relationship with Player, so a team consists of one or more players.
- The GameService class acts as a centralized manager for game instances and provides methods for adding and retrieving games.

## Evaluation
Using your experience to evaluate the characteristics, advantages, and weaknesses of each operating platform (Linux, Mac, and Windows), as well as mobile devices, consider the requirements outlined below and articulate your findings for each. As you complete the table, keep in mind your client’s requirements and look at the situation holistically, as it all has to work together.

### Server Side

| Development Requirements | Mac | Linux | Windows | Mobile Devices |
|--------------------------|-----|-------|---------|----------------|
| Server Side              | Stable and secure Unix-based OS. Easy to set up and maintain. Limited support for servers. Higher costs for hardware across the board. | Highly stable and secure. Free and Open Source and highly customizable. Dominant in the server world. | Wide adoption for enterprise systems. Extensive support and tooling. Integration with Microsoft’s stack. Higher licensing costs. | Limited server-side capabilities. Rely on cloud-based services. Scalability and performance challenges that need addressing. |

### Client Side

| Development Requirements | Mac | Linux | Windows | Mobile Devices |
|--------------------------|-----|-------|---------|----------------|
| Client Side              | Consistent user experience. Proprietary hardware and OS. Limited level of buy-in from developers. Higher Development costs (fee to be Apple Developer). | Varied user experience across distributions. Requires technical proficiency (depending on the distro). Fragmented in terms of popularity. | Dominant desktop OS. Wide range of supported hardware. Extensive application ecosystem. Easier for end-users to adopt. | Diverse range of devices and OSes. Touchscreen and mobile-optimized. Platform-specific development. Varying screen sizes and device capabilities. |

### Development Tools

| Development Requirements | Mac | Linux | Windows | Mobile Devices |
|--------------------------|-----|-------|---------|----------------|
| Development Tools        | Xcode IDE for native apps. Swift and Objective-C languages. Cocoa frameworks. Well-documented APIs. | Wide range of open-source tools. GCC, Clang compilers. Java, Python, C/C++ support. Extensive command-line tools / TUI apps. | Visual Studio IDE. .NET framework. C#, C++, Visual Basic languages. Extensive documentation and resources. | Android Studio for Android apps. Xcode for iOS apps. Java and Kotlin for Android. Swift and Objective-C for iOS. Cross-platform tools like React Native and Flutter. |

## Recommendations

### Operating Platform
For expanding to other computing environments, I recommend using Linux as the primary operating system for server-side deployment. Specifically, we suggest using Ubuntu Server, a popular and well-supported Linux distribution. This choice is based on the following factors:
- Open-source and cost-effective
- Highly stable and secure
- Excellent performance for web-based applications
- Wide range of supported hardware architectures
- Strong community support and regular updates

### Operating Systems Architectures
- **Linux**: Uses a modular and layered architecture. The key components of the Linux architecture include:
  - **Kernel**: The core of the OS managing system resources, process and memory management, and device drivers.
  - **Shell**: The user interface for interacting with the OS through commands.
  - **Filesystem**: A hierarchical structure for organizing and storing files and directories.
  - **Networking**: Support for various networking protocols and tools for network configuration and management.
  - **Libraries and Utilities**: Extensive collection of reusable code and tools for system and application development.

### Storage Management
For storage management, we recommend using the ext4 (fourth extended filesystem) for the following reasons:
- Journaling support ensuring data integrity and faster recovery after system crashes
- Backwards compatibility with ext2 and ext3
- Support for large file systems and large files
- Improved performance and reliability compared to its predecessors

### Memory Management
Linux employs several memory management techniques that will benefit the "Draw It or Lose It" game:
- **Virtual Memory**: Provides each process with its own virtual address space allowing multiple processes to run concurrently without interference.
- **Paging**: Divides memory into fixed-size pages enabling efficient swapping between main memory and secondary storage.
- **Dynamic Memory Allocation**: Efficient management of heap memory through functions like malloc() and free().
- **Memory Mapping**: Allows processes to map files or devices into their address space for efficient access to large data sets.

### Distributed Systems and Networks
To enable "Draw It or Lose It" to communicate between various platforms:
- Implement a client-server architecture where the game server hosts core logic and manages game state.
- Use RESTful APIs over HTTPS for client-server communication ensuring platform independence.
- Implement WebSocket connections for real-time updates during gameplay.
- Use a load balancer to distribute traffic across multiple server instances for improved performance and fault tolerance.
- Implement a distributed caching system (e.g., Redis) to reduce database load and improve response times.
- Use a message queue system (e.g., RabbitMQ) for asynchronous communication between different components of the system.

To handle connectivity issues and outages:
- Implement retry mechanisms with exponential backoff for failed requests.
- Use circuit breakers to prevent cascading failures in the distributed system.
- Implement a robust logging and monitoring system to quickly identify and resolve issues.
- Use database replication and regular backups to ensure data persistence and quick recovery in case of failures.

### Security
To protect user information and ensure secure communication between platforms:
- Use HTTPS (SSL/TLS) for all client-server communications to encrypt data in transit.
- Implement strong user authentication using industry-standard protocols (e.g., OAuth 2.0, OpenID Connect).
- Use bcrypt or Argon2 for securely hashing and storing user passwords.
- Implement role-based access control (RBAC) to manage user permissions effectively.
- Use prepared statements and parameterized queries to prevent SQL injection attacks.
- Implement input validation and sanitization to prevent cross-site scripting (XSS) attacks.
- Use security headers (e.g., Content Security Policy, X-XSS-Protection) to enhance browser security.
- Regularly update all software components, including the OS, web server, and application dependencies.
- Implement a Web Application Firewall (WAF) to protect against common web exploits.
- Use intrusion detection and prevention systems (IDS/IPS) to monitor and block suspicious network activity.
- Conduct regular security audits and penetration testing to identify and address potential vulnerabilities.

By implementing these recommendations, The Gaming Room can ensure a secure, scalable, and efficient deployment of "Draw It or Lose It" across multiple platforms while meeting the specific requirements of the game and its users.
