# Internet Ontology Framework (IOF)

## A Multi-Perspective Ontology for Internet Reachability, Resilience, and Strategic Functionality

---

## Status of This Document

This document specifies the Internet Ontology Framework (IOF). Distribution of this document is unlimited.

This document is intended to provide a conceptual and technical foundation for modeling Internet reachability and functionality across multiple perspectives. It does not define a wire protocol and does not require IANA actions.

---

## Abstract

This document defines a formal ontology for the structured observation and evaluation of Internet reachability, resilience, and functional availability. Conventional monitoring approaches reduce Internet state to binary reachability or service uptime, which is insufficient for modern distributed systems and socio-technical dependencies.

The Internet Ontology Framework (IOF) introduces a multi-dimensional model that distinguishes between local observability, global systemic behavior, and strategic functional availability. It further defines a domain classification system and associated meta-dimensions to enable semantically meaningful interpretation of measurement results.

The IOF separates semantic classification from measurement endpoints, enabling extensibility, neutrality, and applicability across domains such as industrial systems, public infrastructure, digital platforms, and federated data ecosystems.

---

## Table of Contents

1. Introduction
2. Terminology
3. Architectural Overview
4. Perspective Dimension
5. Domain Dimension
6. Meta-Dimensions
7. Data Model
8. Semantic Interpretation
9. Design Considerations
10. Security Considerations
11. IANA Considerations
12. References

---

## 1. Introduction

The Internet has evolved into a critical infrastructure supporting industrial production, financial systems, governance, and information exchange. Traditional monitoring approaches focus on technical metrics such as reachability, latency, and uptime, but lack the ability to represent:

* Functional dependencies
* Geographic variability
* Policy-induced fragmentation
* Sector-specific availability

This document defines an ontology that enables structured modeling of Internet observability across multiple dimensions. The framework is designed to support:

* Multi-perspective analysis
* Domain-specific evaluation
* Resilience and fragmentation assessment

---

## 2. Terminology

The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”,
“SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “NOT RECOMMENDED”,
“MAY”, and “OPTIONAL” in this document are to be interpreted as described in RFC 2119.

### 2.1 Definitions

| Term        | Definition                                                     |
| ----------- | -------------------------------------------------------------- |
| Node        | An abstract representation of a measurable Internet entity     |
| View        | A projection representing a specific observational perspective |
| Domain      | Functional classification of a node                            |
| Measurement | A method for evaluating a node                                 |
| Region      | Geographic or geopolitical classification                      |

---

## 3. Architectural Overview

The IOF defines three orthogonal dimensions:

| Dimension       | Description                                  |
| --------------- | -------------------------------------------- |
| Perspective     | Observational viewpoint                      |
| Domain          | Functional classification                    |
| Meta-Dimensions | Attributes for evaluation and interpretation |

These dimensions are independent and composable.

---

## 4. Perspective Dimension

### 4.1 Overview

The framework defines three primary views:

| View      | Description                                     |
| --------- | ----------------------------------------------- |
| Local     | Observability from a specific execution context |
| Global    | System-wide behavior of the Internet            |
| Strategic | Availability of functionally critical domains   |

---

### 4.2 Local View

The Local View describes reachability from the perspective of a specific node or network environment.

#### 4.2.1 Scope Classification

| Scope    | Description                      |
| -------- | -------------------------------- |
| Loopback | Local host communication         |
| LAN      | Local network                    |
| Intranet | Organizational internal services |
| Edge     | Gateway and boundary devices     |
| Internet | External connectivity            |

Implementations SHOULD use the Local View to diagnose segmentation, routing, and policy enforcement effects.

---

### 4.3 Global View

The Global View models the Internet as a distributed system.

#### 4.3.1 Aspects

| Aspect        | Description                          |
| ------------- | ------------------------------------ |
| Connectivity  | Reachability across regions          |
| Fragmentation | Regional accessibility differences   |
| Latency       | Temporal performance characteristics |
| Resilience    | Behavior under failure conditions    |
| Censorship    | Presence of filtering or blocking    |

Implementations SHOULD consider regional diversity when evaluating Global View results.

---

### 4.4 Strategic View

The Strategic View evaluates the availability of systems that are critical to societal and economic functions.

This view abstracts from pure connectivity and focuses on functional operability.

---

## 5. Domain Dimension

### 5.1 Overview

Domains classify nodes based on functional role.

| Domain         | Description                         |
| -------------- | ----------------------------------- |
| Infrastructure | Core Internet services              |
| Industrial     | Production and supply chain systems |
| Science        | Research and knowledge systems      |
| Media          | Information dissemination systems   |
| Government     | Public administration               |
| Finance        | Financial systems                   |
| Platform       | Digital ecosystems                  |
| X-Initiatives  | Cross-industry federations          |

---

### 5.2 Domain Requirements

Implementations SHOULD assign nodes to at least one domain.
Nodes MAY belong to multiple domains if functionally justified.

---

## 6. Meta-Dimensions

### 6.1 Geography

| Attribute | Description               |
| --------- | ------------------------- |
| Region    | Geographic classification |

Regions SHOULD be defined consistently across implementations.

---

### 6.2 Access Type

| Type       | Description                          |
| ---------- | ------------------------------------ |
| Open       | Publicly accessible                  |
| Restricted | Limited by policy or region          |
| Internal   | Private network                      |
| Federated  | Requires identity or trust framework |

---

### 6.3 Protocol

| Protocol | Description               |
| -------- | ------------------------- |
| HTTPS    | Web access                |
| DNS      | Name resolution           |
| API      | Programmatic access       |
| Custom   | Domain-specific protocols |

---

### 6.4 Measurement Type

| Type         | Description         |
| ------------ | ------------------- |
| Reachability | Accessibility       |
| Latency      | Response time       |
| Availability | Stability over time |
| Consistency  | Result uniformity   |

---

### 6.5 Criticality

| Level | Description        |
| ----- | ------------------ |
| 1     | Low relevance      |
| 2     | Moderate relevance |
| 3     | Important          |
| 4     | High importance    |
| 5     | System-critical    |

Criticality SHOULD be used for weighting and prioritization.

---

## 7. Data Model

The following abstract data model is RECOMMENDED:

```ts
type OntologyNode = {
  id: string;

  view: "local" | "global" | "strategic";

  domain:
    | "infrastructure"
    | "industrial"
    | "media"
    | "government"
    | "finance"
    | "science"
    | "platform"
    | "x-initiatives";

  region?: string;

  access: "open" | "restricted" | "internal" | "federated";

  protocol: "https" | "dns" | "api" | "custom";

  measurement:
    | "reachability"
    | "latency"
    | "availability"
    | "consistency";

  criticality: 1 | 2 | 3 | 4 | 5;
};
```

Implementations MAY extend this model.

---

## 8. Semantic Interpretation

The IOF enables interpretation across three layers:

| Layer      | Description                       |
| ---------- | --------------------------------- |
| Physical   | Network reachability              |
| Functional | Service operability               |
| Systemic   | Preservation of societal function |

Implementations SHOULD distinguish between these layers to avoid misinterpretation.

---

## 9. Design Considerations

### 9.1 Separation of Concerns

Semantic classification MUST be independent of measurement endpoints.

### 9.2 Extensibility

The ontology MUST allow addition of new domains and attributes.

### 9.3 Neutrality

The framework MUST NOT assume geographic or political bias.

### 9.4 Partial Failure

The model MUST support partial connectivity scenarios.

---

## 10. Security Considerations

The IOF itself does not introduce new network protocols. However:

* Measurement endpoints MAY expose sensitive metadata
* Active probing MAY be interpreted as scanning
* Access-restricted systems MUST NOT be probed without authorization

Implementations SHOULD respect legal and policy constraints.

---

## 11. IANA Considerations

This document has no IANA actions.

---

## 12. References

* RFC 2119

---

## 13. Conclusion

The Internet Ontology Framework (IOF) provides a structured approach to modeling Internet observability beyond binary connectivity. By integrating multiple perspectives, domains, and meta-dimensions, it enables a comprehensive understanding of Internet state in technical, functional, and systemic terms.

Future work includes mapping ontology nodes to concrete measurement endpoints and defining standardized evaluation procedures.

---

