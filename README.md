# Logi-link-backend

graph TD
    User[End User] -->|HTTPS/Text| Web[Frontend Interface]
    
    subgraph "Serverless Backend (Zapier)"
        Web -->|Async Request| Orchestrator[AI Orchestrator]
        Orchestrator -->|Context Window| LLM[OpenAI GPT-4o]
        
        LLM -->|SQL Lookup| DB[(Shipment Database)]
        LLM -->|Vector Search| RAG[Policy Documents]
    end
    
    DB -->|JSON Data| LLM
    RAG -->|Text Chunks| LLM
    LLM -->|Markdown Response| Web
