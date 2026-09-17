---
theme:
  path: ./theme.yaml
---

MCP
===

> ​
> ​ El agente dispone de un repertorio limitado de herramientas que le permiten acceder al filesystem, shell etc.
> ​

<!-- new_lines: 4 -->

```mermaid +render +width:60%
flowchart TB
    LLM["LLM"]

    AGENT["Agente"]

    subgraph NATIVE["Herramientas"]
        FILESYSTEM["Filesystem"]
        TERMINAL["Shell"]
        OTHER["..."]
    end

    LLM --> AGENT

    AGENT --> NATIVE
```
<!-- end_slide -->

MCP
===

> ​
> ​ **MCP (Model Context Protocol)** es un protocolo que permite conectar un agente con herramientas y fuentes de información externas.
> ​

<!-- new_lines: 4 -->

```mermaid +render +width:95%
flowchart TB
    LLM["LLM"]

    AGENT["Agente"]

    subgraph NATIVE["Herramientas"]
        FILESYSTEM["Filesystem"]
        TERMINAL["Terminal"]
        OTHER["..."]
    end

    MCPCLIENT["MCP Client"]
    MCPSERVER["MCP Server"]

    subgraph MCP["Capacidades MCP"]
        TOOLS["Tools"]
        RESOURCES["Resources"]
    end

    LLM --> AGENT

    AGENT --> NATIVE
    AGENT --> MCPCLIENT

    MCPCLIENT <--> MCPSERVER

    MCPSERVER --> TOOLS
    MCPSERVER --> RESOURCES
```

<!-- end_slide -->

MCP
===

> ​
> ​ El agente descubre las capacidades del MCP y extiende su repertorio de herramientas disponibles.
> ​

<!-- new_lines: 4 -->

```mermaid +render +width:90%
sequenceDiagram
   actor U as Usuario
    participant A as Agente
    participant L as LLM
    participant C as MCP Client
    participant S as MCP Server

    Note over A,S: Descubrimiento inicial

    A->>C: Descubrir capacidades
    C->>S: tools/list
    S-->>C: Tools + descripciones + schemas
    C-->>A: Herramientas disponibles

    Note over U,L: Interacción

    U->>A: Solicitud
    A->>L: Prompt + contexto + tools
    L-->>A: Usar tool X

    A->>C: Invocar tool X
    C->>S: tools/call
    S-->>C: Resultado
    C-->>A: Resultado

    A->>L: Contexto + resultado
    L-->>A: Respuesta
    A-->>U: Respuesta
```
<!-- end_slide -->

MCP
===

> ​
> ​ El agente consulta al MCP las herramientas disponibles mediante **JSON-RPC**.
> ​

<!-- new_lines: 2 -->

Peticion:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "tools/list",
  "params": {}
}
```
Respuesta:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "tools": [
      {
        "name": "get_tasks",
        "description": "Obtiene las tareas dadas de alta.",
        "inputSchema": {
          "type": "object",
          "properties": {
            "project_id": {
              "type": "integer",
              "description": "Identificador de proyecto."
            }
          },
          "additionalProperties": false
        }
      },
...
}
```

<!-- end_slide -->

MCP
===

> ​
> ​ El agente invoca una herramienta del MCP usando también **JSON-RPC**.
> ​

<!-- new_lines: 2 -->

Peticion:

```json
{
 "jsonrpc": "2.0",
  "id": 2,
  "method": "tools/call",
  "params": {
    "name": "get_tasks",
    "arguments": {
      "project_id": 42
    }
  }
}
```
Respuesta:

```json
{
  "jsonrpc": "2.0",
  "id": 2,
  "result": {
    "content": [
      {
        "type": "text",
        "text": "[{\"id\":1,\"title\":\"Diseñar API\",\"completed\":true},{\"id\":2,\"title\":\"Implementar autenticación\",\"completed\":false}]"
      }
    ]
  }
}
```

<!-- end_slide -->

MCP
===

> ​
> ​ MCP usa **JSON-RPC** sobre diferentes transportes.
> ​

<!-- new_lines: 2 -->


```mermaid +render +width:70%
flowchart TB
    subgraph STDIO["MCP sobre stdio"]
        direction LR
        CLIENT1["MCP Client"]
        SERVER1["MCP Server"]

        CLIENT1 -->|fork| SERVER1
        SERVER1 <-->|stdio| CLIENT1
    end

    subgraph HTTP["MCP sobre HTTP"]
        direction LR
        CLIENT2["MCP Client"]
        SERVER2["MCP Server"]

        CLIENT2 <-->|HTTP| SERVER2
    end

    STDIO ~~~ HTTP
```
