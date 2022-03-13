# System design

### Table of content
* [Data persistent model](#data-persistent-model)
* [Network and distribution model](#network-and-distribution-model)

### Data persistent model

```mermaid
flowchart TD
  A(Application) -- "persist data" --> B(Data-Storage)
  B -- "delegate & manage" --> C(Browser storage)
  B -- "delegate & manage" --> D(Data storage)
```

```mermaid
sequenceDiagram
  participant A as Application
  participant D as Data-Storage
  participant B as Browser-Storage
  participant S as Server
  A->>D: App start with user signed-in
  D->>S: fetch user data
  S-->>D: User data
  D->>B: compare and merge
  B-->>D: Done!
  D-->>A: Done!
  A->>D: Data update
  par
    D->>B: update
    B-->>D: Done!
  and
    D->>S: update
    S-->>D: Done!
  end
  D-->>A: Done!
```

### Network and distribution model

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
