# Agent Types

## Core Agent Architecture
```mermaid
classDiagram
    class BaseAgent {
        <<abstract>>
        +agent_id: string
        +resources: ResourceSpec
        +start() bool
        +stop() bool
        +report_status() StatusUpdate
    }
    
    class TrainerAgent {
        +model_architecture: string
        +training_data: string
        +train() ModelWeights
        +evaluate() Metrics
    }
    
    class InferencerAgent {
        +model: ModelWeights
        +inference(input) Output
        +batch_inference(inputs) [Output]
    }
    
    class CrawlerAgent {
        +seed_urls: [string]
        +crawl_depth: int
        +crawl() [DataItem]
    }
    
    class LabellerAgent {
        +labeling_rules: string
        +label_data(data) LabeledData
    }
    
    class RaterAgent {
        +rating_criteria: string
        +rate_output(output) Score
    }
    
    BaseAgent <|-- TrainerAgent
    BaseAgent <|-- InferencerAgent
    BaseAgent <|-- CrawlerAgent
    BaseAgent <|-- LabellerAgent
    BaseAgent <|-- RaterAgent
```


## Workflow Examples
### ML Training Pipeline
```mermaid
sequenceDiagram
    participant Scheduler
    participant Crawler
    participant Labeller
    participant Trainer
    participant Rater
    Scheduler->>Crawler: Collect training data
    Crawler->>Labeller: Raw data
    Labeller->>Trainer: Labeled dataset
    Trainer->>Rater: Trained model
    Rater->>Scheduler: Model evaluation
```

### Inference Service
```mermaid
flowchart TD
    A[User Request] --> B[Load Balancer]
    B --> C{Request Type}
    C -->|Simple| D[Inferencer Agent]
    C -->|Complex| E[Inferencer Cluster]
    D & E --> F[Response]
```

## Security Considerations
1. **Isolation**: Each agent runs in dedicated VM
2. **Input Validation**: Sanitize all external inputs
3. **Resource Limits**: Prevent resource exhaustion attacks
4. **Access Control**: Agent-specific credentials
5. **Audit Logging**: Record all agent operations
