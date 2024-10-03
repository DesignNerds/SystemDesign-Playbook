# [DesignNerds](https://designnerds.medium.com/) | SystemDesign-Playbook


Repository of system design, low level design concepts, design pattern and deep dive on low/medium/high complexity problems. 


## System Design 
### Prerequisites: 
i. [Structured approach for system design interviews](https://medium.com/dev-nectar/structured-approach-for-system-design-interviews-ef616b2af1c7)
ii. [Most useful concepts for system design interviews](https://designnerds.medium.com/most-useful-concepts-for-system-design-interviews-part-1-da3b35e2c1b6)
 ### Concepts
   #### i. [Load balancer, API Gateway, Forward Proxy, Reverse Proxy](https://medium.com/dev-nectar/load-balancers-api-gateways-forward-proxies-and-reverse-proxies-cdd03e629553)
   ```mermaid
graph TD;

    %% Forward Proxy Flow (External Request to Load Balancer)
    A[Client] -->|Request| B[Forward Proxy]
    B -->|Forwarded Request| C[Load Balancer]
    
    %% Load Balancer distributes the request to API Gateway
    C -->|Distribute Request| D[API Gateway]
    
    %% API Gateway routes to microservices through Reverse Proxy
    D -->|Route to Microservice| E[Reverse Proxy]
    E -->|Forward Request to Backend| F1[Microservice 1]
    E -->|Forward Request to Backend| F2[Microservice 2]

    %% Backend Services Response
    F1 -->|Response| E
    F2 -->|Response| E
    E -->|Send Response| D
    D -->|Send Final Response| C
    C -->|Send Response| B
    B -->|Send Response to Client| A

    %% Grouping for Clarity
    subgraph External Network
        A --> B
    end

    subgraph Proxy & Balancer
        B --> C --> D
    end

    subgraph Backend Architecture
        D --> E --> F1
        E --> F2
    end

    %% Styles
    style B fill:#ffcc00,stroke:#333,stroke-width:2px
    style C fill:#ff6699,stroke:#333,stroke-width:2px
    style D fill:#00ccff,stroke:#333,stroke-width:2px
    style E fill:#66ff66,stroke:#333,stroke-width:2px

```
#### ii. [API Essentials : Versioning and HATEOAS](https://medium.com/dev-nectar/api-essentials-versioning-and-hateoas-ddd0b69685f7)
#### iii. [How to design Enterprise-Ready APIs](https://medium.com/dev-nectar/how-to-design-enterprise-ready-apis-5a19c141b09e)
#### iv. [Designing Smart APIs for Serverless Architectures](https://medium.com/dev-nectar/designing-smart-apis-for-serverless-architectures-17f9a45608b8)
#### v. [Top Microservices Anti-Patterns: How to Identify and Fix Them with Java Implementation](https://medium.com/dev-nectar/top-microservices-anti-patterns-how-to-identify-and-fix-them-with-java-implementation-440918569d36)
#### vi. [The Secret Weapon for System Design Interviews: API Essentials](https://medium.com/dev-nectar/the-secret-weapon-for-system-design-interviews-api-essentials-8665c6585d9a)
#### vii. [API Gateway vs Load Balancer - Data driven approach](https://medium.com/dev-nectar/system-design-concepts-api-gateway-vs-load-balancer-71d7f2fd048e)
#### viii. [Bursty traffic handling](https://designnerds.medium.com/system-design-concepts-bursty-traffic-handling-7738127f5a0d)
#### ix. 
 
 ### Problem deep dives

## Low Level Design

**MUST HAVE PRACTICE PROBLEMS FOR LOW LEVEL DESIGN INTERVIEW** - 

**1. [Designing a Scalable In-Memory File System Using SOLID Principles.](https://blog.devgenius.io/low-level-design-designing-a-scalable-in-memory-file-system-using-solid-principles-df792aa21f6d)** 

**2. [Rate Limiting System](https://levelup.gitconnected.com/low-level-design-rate-limiting-system-a815eac97fea?source=user_profile_page---------0-------------9e7bd989dd82---------------)** 

**3. [Load Balancer Design with Health Checks, Metrics, and Fallbacks](https://blog.devgenius.io/low-level-design-load-balancer-design-with-health-checks-metrics-and-fallbacks-e7ef23a8620a)** 

**4. [Online Food Delivery System design](https://levelup.gitconnected.com/low-level-design-online-food-delivery-system-a-solid-and-scalable-architecture-ae2ab287d9a8)** 

**5. [Payment gateway system design](https://blog.devgenius.io/low-level-design-payment-gateway-system-aead85996fd9)** 
