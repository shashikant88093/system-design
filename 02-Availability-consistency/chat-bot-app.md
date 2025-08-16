# Chat App

## Functional Requirements
- one one chat
- group chat
- typing indicators
- seen status
- message delivery confirmation
- online/offline status
- Notifications
- Shared media (images, videos)



## system requirements
- low latency
- High availability
- High reliability
- Mobile and Desktop support
- Chat history
- High blob storage
- End-to-end encryption
- websocket support
- Scalability
- Real-time updates

## Non-Functional Requirements
- Performance: Low latency for real-time communication.
- Scalability: Support for millions of concurrent users.
- Availability: 99.99% uptime to ensure continuous service.
- Security: End-to-end encryption for user privacy.
- Usability: Intuitive user interface for seamless interaction. 
- Maintainability: Modular architecture for easy updates and feature additions.
- Extensibility: Support for third-party integrations and plugins.

## capacity planning
- Estimate user base growth and peak concurrent users.
- Plan for horizontal scaling to handle increased load.
- Allocate resources for data storage and processing.
- total active users: 100,000
- messages per user per day: 100
- total messages per day: 10,000,000


## stoage estimation
- Average message size: 1 KB
- Total storage for messages per day: 10 GB
- each media file size: 5 MB


# API Endpoints
- sendMessage (POST /api/messages)
    - Parameters: senderId, receiverId, content, type (text/image/video)
- getMessages (GET /api/messages)
    - Parameters: userId, chatId, limit, timestamp
  
## services
- User Service: Manages user profiles, authentication, and online status.
- Chat Service: Handles message sending, receiving, and storage.
- Group Service: Manages group chats, including creation, membership, and permissions.
- sesssion Service: Manages user sessions and real-time updates.
- Relay Service: Facilitates message delivery across distributed nodes.
- Last seen Service: Tracks and updates the last seen status of users.
- Asset Service: Manages shared media files, including upload, retrieval, and storage.


# Frontend
- React Native for mobile apps
- React for web app
- Redux for state management
- WebSockets for real-time communication
- GraphQL for API interactions
- Tailwind CSS for styling
- Testing with Jest and React Testing Library
- Accessibility compliance (WCAG 2.1)
- Progressive Web App (PWA) support for offline access
- Internationalization (i18n) for multi-language support
- Responsive design for various screen sizes
- Performance optimization (code splitting, lazy loading)
- Analytics integration (Google Analytics, Mixpanel)
- User authentication (OAuth, JWT)
- Push notifications for updates
- Dark mode support
  
# Backend
- Node.js with Express for REST API 
- GraphQL for flexible data querying
- WebSocket for real-time communication
- Redis for caching and session management
- MongoDB for NoSQL database
- PostgreSQL for relational data
- Elasticsearch for search functionality
- RabbitMQ for message queuing
- Docker for containerization
- Docker Compose for multi-container applications
- Kubernetes for orchestration and scaling
- NGINX for reverse proxy and load balancing
- JWT for user authentication
- OAuth 2.0 for third-party integrations
- End-to-end encryption using TLS
- API rate limiting for security
- Logging with Winston or Morgan
- Monitoring with Prometheus and Grafana
- Unit testing with Mocha and Chai
- Integration testing with Supertest

# ChatterMesh: A Distributed Chat Application
## Overview
ChatterMesh is a distributed chat application designed to handle real-time communication with high availability and low latency. It supports one-on-one and group chats, ensuring message delivery confirmation and typing indicators. The application is built to scale horizontally across multiple regions, providing a seamless user experience.

## Explain Latency and it's types
- Latency refers to the delay between a user's action and the system's response. In the context of ChatterMesh, low latency is crucial for real-time communication. There are several types of latency to consider:
  
- **Network Latency**: The time taken for data to travel across the network. This can be minimized by using Content Delivery Networks (CDNs) and optimizing routing paths.
- **Processing Latency**: The time taken by the server to process a request. This can be reduced by optimizing algorithms and using efficient data structures.
- **Database Latency**: The time taken to read from or write to the database. This can be minimized by using in-memory databases like Redis for caching frequently accessed data and optimizing database queries.
- **Application Latency**: The time taken by the application to render a response to the user. This can be improved by optimizing frontend code and using techniques like lazy loading and code splitting.