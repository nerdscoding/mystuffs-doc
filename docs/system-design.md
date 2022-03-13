# System design

### Data persistent model

```mermaid
erDiagram
  Application ||--|| Data-Storage : "persist data"
  Data-Storage ||--|| Browser-Storage : "delegate & manage"
  Data-Storage ||--o| Server-Storage: "delegate & manage"
```

### Network and distribution module

```mermaid
flowchart LR
  A(Browser):::internal --> B(Gateway)
  subgraph internal
  B --> C(App shell):::external
  B --> D(Stuff list):::external
  B --> E(User & Auth):::external
  end
  classDef external fill:#99f,stroke:#333;
  classDef internal fill:#9f9,stroke:#333,color:#333;
  style B fill:#ff9,stroke:#333,color:#333;
```
