#  Eureka Server (Service Discovery)

The **Eureka Server** acts as the **central service registry** for the Ecommerce Microservices system.

All microservices (API Gateway, User Service, Product Service, Cart Service, Order Service, Payment Service, OTP Service) register themselves with Eureka, allowing **dynamic service discovery and load-balanced communication**.

---

#  Tech Stack

* **Spring Boot**
* **Spring Cloud Netflix Eureka Server**
* **Microservices Architecture**
* **REST-based Service Discovery**

---

# 📌 Responsibilities

###  **Service Registration**

* Registers all running microservices
* Maintains service instance metadata

###  **Service Discovery**

* Enables services to discover each other dynamically
* Eliminates hard-coded service URLs

###  **Health Monitoring**

* Tracks service availability using heartbeats
* Removes unavailable instances automatically

###  **Load Balancing Support**

* Works with Spring Cloud LoadBalancer
* Enables client-side load balancing

---

#  Eureka Dashboard

Once the Eureka Server is running, the dashboard can be accessed at:

```
http://localhost:8761
```

The dashboard displays:

* Registered services
* Active instances
* Instance status (UP / DOWN)

---

#  Registered Services (Examples)

* **API-GATEWAY**
* **USER-SERVICE**
* **PRODUCT-SERVICE**
* **CART-SERVICE**
* **ORDER-SERVICE**
* **PAYMENT-SERVICE**
* **OTP-SERVICE**

---

#  Architecture Flow

```
Microservices
      ↓
 Eureka Server
      ↑
 API Gateway
```

* All services register with Eureka
* API Gateway uses Eureka for dynamic routing
* Services communicate without knowing physical addresses

---


##  Author

**Pranav Sharma**
Spring Boot | Microservices | Service Discovery

---
