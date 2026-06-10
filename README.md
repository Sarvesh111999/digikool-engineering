# digikool-engineering
Engineering overview of the Digikool platform, including system architecture, frontend applications, backend microservices, integrations, and technical documentation.

## Product Overview
DigiKool is a multi-tenant School Management Platform designed for educational institutions to manage authentication, user administration, attendance tracking, fee payments, and school operations through a scalable microservices architecture.
The platform serves multiple user roles, including System Administrators, School Administrators, Teachers, Students, and Parents, while maintaining secure tenant isolation and centralized identity management.

Repositories -
Frontend Application - https://github.com/Sarvesh111999/digikool-frontend-ui
Auth Service - https://github.com/ashishthalia/digikool-auth
Gateway Service - https://github.com/ashishthalia/digikool-gateway
Payment Gateway Service - https://github.com/Sarvesh111999/digikool-payment-gateway
Attendance Service - https://github.com/ashishthalia/digikool-attendance

## Engineering Highlights

- Microservices Architecture
- OAuth2 / OpenID Connect Authentication
- JWT-based Authorization
- Multi-Tenant SaaS Platform
- API Gateway Pattern
- Role-Based Access Control (RBAC)
- Stripe Payment Integration
- PostgreSQL Persistence Layer
- Reactive Gateway using Spring WebFlux
- Frontend built with Nuxt 3 and Vue 3

Authentication & Authorization Service
Overview - 
The Authentication & Authorization Service is the core identity and access management component of the DigiKool platform. It serves as the centralized authority for authentication, authorization, user management, school management, role administration, and permission enforcement across all microservices.
This service manages the complete lifecycle of schools, users, classes, roles, permissions, and user relationships while providing secure OAuth2/OIDC-based authentication for the entire platform. All user access, security policies, and authorization decisions originate from this service.
The service is built using Spring Boot, Spring Security, and Spring Authorization Server, implementing industry-standard OAuth2 and OpenID Connect protocols for secure authentication and token management.

Responsibilities & Features - 
- Centralized identity and access management for the entire platform.
- Manages schools, users, classes, roles, permissions, user-role mappings, and parent-student relationships.
- Implements OAuth2/OIDC authentication, Authorization Code Flow, JWT token issuance, refresh token handling, and secure service-to-service authorization.
- Provides RBAC and custom permission-based access control across all platform modules.
- Maintains multi-tenant data isolation and acts as the single source of truth for user identity, access governance, and authorization policies.

Tech Stack - Spring Boot, Spring Security, Spring Authorization Server, OAuth2, OpenID Connect (OIDC), JWT, Spring Data JPA, Hibernate, PostgreSQL, Flyway, HikariCP, BCrypt, Spring Mail, Maven, Java 21

API Gateway Service
Overview - 
The API Gateway acts as the centralized entry point for all client requests within the DigiKool platform. Every request from frontend applications passes through the gateway before reaching downstream microservices.
The gateway is responsible for request routing, authentication enforcement, token propagation, user-context forwarding, security policies, and cross-service communication management.
Built using Spring Cloud Gateway and WebFlux, the service provides a reactive and scalable architecture capable of handling authentication-aware routing across multiple backend services.

Responsibilities & Features - 
- Central entry point for all platform traffic across Authentication, Attendance, Payment, and future services.
- Handles request routing, OAuth2 authentication flow coordination, Token Relay, JWT propagation, and gateway-level access enforcement.
- Forwards authenticated user context including user identity, school context, roles, and permissions to downstream microservices.
- Implements tenant-aware request processing, CORS management, Redis-backed sessions, and resilient service communication.
- Provides centralized security, traffic management, and observability for the platform.

Tech Stack - Spring Boot, Spring Cloud Gateway, Spring WebFlux, Spring Security, OAuth2 Client, JWT, Redis, Resilience4j, Spring Actuator, Reactor Netty, Maven, Java 21

Payment Gateway Service
Overview - 
The Payment Gateway Service manages online fee collection and payment processing for the DigiKool platform. It enables students and parents to securely pay school fees while providing schools with real-time payment tracking and transaction management capabilities.
The service integrates with Stripe Payment Gateway and maintains complete payment lifecycle visibility from checkout creation to final payment confirmation.

Responsibilities & Features - 
- Manages fee collection workflows, payment processing, transaction tracking, and payment status management.
- Integrates Stripe Checkout, Payment Intents, and webhook events for secure payment verification and reconciliation.
- Synchronizes payment events with platform records and automatically updates transaction states in the database.
- Supports student fee tracking, pending dues, payment history, and school-level payment reporting.
- Consumes authenticated user context from the API Gateway to enforce secure and tenant-aware payment operations.

Tech Stack - Spring Boot, Spring Security, Spring Data JPA, Hibernate, PostgreSQL, Stripe API, Stripe Webhooks, Maven, Java 17

Attendance Service
Overview - 
The Attendance Service manages attendance operations across the DigiKool platform and provides schools with attendance tracking, reporting, and analytics capabilities.
The service enables teachers and administrators to manage attendance records while maintaining secure school-level data isolation and permission-based access control.

Responsibilities & Features - 
- Manages attendance sessions, attendance records, and student attendance tracking workflows.
- Supports attendance marking, updates, reporting, and school-level attendance management.
- Enforces permission-based attendance operations using the user context received from the API Gateway.
- Maintains tenant-aware attendance data isolation across multiple schools.
- Provides attendance insights and reporting capabilities for teachers and administrators.

Tech Stack - Spring Boot, Spring Security, Spring Data JPA, Hibernate, PostgreSQL, REST APIs, Maven, Java

Frontend Application
Overview - 
The DigiKool Frontend is the primary user-facing application for the platform, providing a unified experience for System Administrators, School Administrators, Teachers, Students, and Parents.
The application integrates with the Authentication Service, API Gateway, Attendance Service, and Payment Service to deliver a complete school management experience.

Responsibilities & Features - 
- Provides role-based dashboards and workflows for administrators, teachers, students, and parents.
- Supports school management, user management, role-permission administration, attendance operations, and fee management.
- Integrates with OAuth2 authentication flows and maintains secure user sessions across platform modules.
- Implements responsive UI, reusable components, centralized state management, and API-driven data workflows.
- Delivers attendance tracking, fee payment, reporting, and administration capabilities through a unified interface.
- Tech Stack - Nuxt 3, Vue 3, Pinia, Tailwind CSS, Axios, OAuth2, Docker, HTML5, CSS3, JavaScript
