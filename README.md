# llm-filtering-microservice

https://github.com/satishsinghpbh/llm-filtering-microservice.git

```mermaid
flowchart TD
    subgraph UI[User Interface]
        A1("User enters smart query (e.g. Failed trades in March above $5M)")
        A2(Smart Search Bar)
        A3(AG Grid Table)
    end

    subgraph LLM[LLM Filter Microservice]
        B1(Receive Query Input)
        B2(LLM Prompt Engine)
        B3(LLM e.g. GPT-4, Mistral)
        B4(Convert to AG Grid JSON Filters)
        B5(Return JSON Filter Model)
    end

    subgraph Backend[Spring Boot Service]
        C1(Receive Filter JSON)
        C2(Convert to JPA Specification)
        C3(Execute DB2 Query)
        C4(Return Filtered Results)
    end

    subgraph DB[DB2 Database]
        D1(Trades Table)
    end

    %% Flow
    A1 --> A2 --> B1
    B1 --> B2 --> B3 --> B4 --> B5
    B5 --> A3
    A3 --> C1
    C1 --> C2 --> C3 --> D1
    D1 --> C4 --> A3

    %% Optional Enhancements
    subgraph OPT[Optional Components]
        E1(Vector DB or Redis Cache)
        E2(Logging & Monitoring)
        E3(User Feedback Loop)
    end

    B3 --> E1
    B3 --> E2
    A3 --> E3


```
