UPI Offline Mesh

UPI Offline Mesh is a simulated offline payment architecture built using Java and Spring Boot. It demonstrates how an encrypted payment request can be transferred through virtual mesh devices when the originating device does not have direct internet connectivity.

An internet-connected bridge device can forward the encrypted transaction to the backend, where the payment packet is validated and processed.

Note: This project uses simulated mesh devices for demonstration. It does not implement real Bluetooth/BLE communication or connect to actual UPI banking infrastructure.

Features
Simulated offline payment flow
Virtual mesh devices
Bridge-node transaction forwarding
RSA + AES-GCM hybrid encryption
SHA-256 ciphertext hashing
TTL-based packet freshness validation
Idempotency to prevent duplicate processing
Tampered-packet detection
Transaction settlement
H2 in-memory database
Web-based dashboard
Concurrent duplicate-delivery testing
Technologies Used
Backend
Java 17
Spring Boot
Spring Web / REST APIs
Spring Data JPA
Database
H2 In-Memory Database
Security
RSA
AES-GCM
SHA-256
Frontend
Thymeleaf
HTML
CSS
JavaScript
Tools
Maven
IntelliJ IDEA
Git
GitHub
How to Run
Prerequisites

Install:

Java 17
Git

The project includes Maven Wrapper, so Maven does not need to be installed separately.

1. Clone the repository
   git clone https://github.com/sakshisawant2203-stack/UPI-Offline-Mesh.git
   cd UPI-Offline-
2. 2. Run the application

On Windows:

.\mvnw.cmd spring-boot:run

Or run the Spring Boot application from IntelliJ IDEA.

3. Open the dashboard
   http://localhost:8080/

The project also provides an H2 database console at:

http://localhost:8080/h2-console
How It Works

The basic payment flow is:

User Device

 Encrypted Payment Packet

Virtual Mesh Device

Forward Packet

Bridge Device

 Internet Connection

Spring Boot Backend


Validation & Processing


Transaction Settlement

The mesh devices are simulated in software to demonstrate the concept of offline transaction forwarding.

Security

The project uses multiple security mechanisms.

Hybrid Encryption

Payment data is protected using:

RSA + AES-GCM

RSA is used for secure key handling, while AES-GCM is used for encrypting the payment payload.

SHA-256 Hashing

A SHA-256 hash is used to detect changes to encrypted payment data.

TTL Validation

Each payment packet contains freshness information. Expired packets are rejected to help prevent replay of old transactions.

Idempotency

The backend uses idempotency checks to prevent the same transaction from being processed multiple times when duplicate packets are received.

Project Structure
UPI-Offline-Mesh/
│
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── demo/
│   │   │           └── upimesh/
│   │   │
│   │   └── resources/
│   │       └── templates/
│   │           └── dashboard.html
│   │
│   └── test/
│
├── pom.xml
├── mvnw
├── mvnw.cmd
├── .gitignore
└── README.md

The main application contains components for encryption, packet validation, mesh simulation, bridge processing, transaction handling and the dashboard.

Testing

The project includes tests for important payment-security scenarios:

Encryption and decryption
Duplicate transaction delivery
Tampered ciphertext detection
Packet freshness / TTL validation
Concurrent duplicate requests

The project also includes a concurrent idempotency test using multiple simultaneous bridge deliveries.

Current Scope

This project demonstrates the engineering concepts behind an offline payment architecture, including:

Offline transaction propagation
Secure packet transmission
Replay protection
Duplicate prevention
Bridge-based synchronization
Backend transaction processing

It is intended as a software simulation and learning project, not as a production banking or UPI implementation.

Limitations

The current implementation does not include:

Real Bluetooth/BLE communication
Real banking integration
Real NPCI/UPI infrastructure
Production payment settlement
Distributed cloud deployment
Hardware-based mesh networking

Real Bluetooth/BLE communication and production banking integration would require additional infrastructure and hardware.

License

This project is intended for educational and portfolio purposes.

