
# Overview
This page describes the FIWARE vision and roadmap on Digital Twins, from fundamental concepts to advanced orchestration. It starts with the [digital twin concpet](#digital-twin-concept), followed by the 
[NGSI-LD Information model](#ngsi-ld-information-model-for-modelling-digital-twins) for formally modeling Digital Twins and the [NGSI-LD API](#ngsi-ld-api-for-accessing-digital-twin-information) for standardized
access to their data and context. Next, it covers [Digital Twin Capabilities](#digital-twin-capabilities), including descriptive, predictive, prospective, prescriptive, and diagnostic functions. 
The page then presents [Digital Twin Orchestration using FogFlow](#digital-twin-orchestration-using-fogflow) and outlines a [roadmap](#roadmap) for future developments, including 
[service execution for actuation](#service-execution-for-supporting-actuation-and-instantiation-of-digital-twin-capabilities), 
[snapshots for advanced analytics](#snapshots-for-supporting-predictive-prospective-and-prescriptive-digital-twin-capabilities), and 
[integration with geospatial and building information management systems](#integration-with-geospatial-systems-and-building-information-management). 
It concludes with a [summary of resources](#summary-of-resources) for further reference.

---

# Digital Twin concept

In FIWARE, a Digital Twin is an entity that digitally represents a real‑world physical asset (e.g., a bus in a city, a milling machine in a factory), a concept (e.g., a weather forecast, a product order), or a structured collection of entities (e.g., a building composed of floors, which in turn contain rooms). Each Digital Twin:

- is uniquely identified by a URI (Universal Resource Identifier),
- belongs to a well‑defined type (e.g., _Bus_, _Room_), also identified by a URI, and
- is described through a set of attributes, classified as either:
  - **properties**, which hold data (e.g., the _current speed_ of a bus or the _maximum temperature_ of a room), or
  - **relationships**, which link the entity to other Digital Twins via their URIs (e.g., the _Building_ a specific _Room_ belongs to).

The attributes of a Digital Twin can range from highly static (e.g., the _license plate_ of a bus), to very dynamic (e.g., _speed_ or _number of passengers_), to moderately variable (e.g., the _driver_ of a bus, which may change a few times a day). Crucially, Digital Twins are not limited to observable data — they may also include **inferred or computed information**. For example, the Digital Twin of a street may include a _current traffic_ attribute derived from sensors or cameras, as well as a _traffic forecast for the next 30 minutes_, computed using AI models that take into account current conditions, weather data, events, and historical patterns.

As a result, the Digital Twin–based representation of the world within a “Powered by FIWARE” architecture is expected to contain not only raw, measurable data but also enriched insights and knowledge accumulated over time, providing smart applications with all the contextual information they need.

Digital Twins enable key capabilities: **Descriptive** (current and past states), **Predictive** (future behavior), **Prospective** (“what‑if” analysis), **Prescriptive** (recommended actions), and **Diagnosis** (evaluation of past events, including malfunctions), making them central to interoperable and replicable smart solutions.

The Digital Twin concept is a key abstraction for building systems at multiple levels: from local smart solutions that integrate sensors and third‑party information systems, to organization‑wide system‑of‑systems architectures, and even to cross‑organization data sharing within Data Spaces.

![Digital Twins: System Perspective](images/DigitalTwins_System_Perspective.png)
*Figure: Digital Twins – System Perspective*

---

# NGSI-LD information model for modelling Digital Twins

The NGSI-LD information model is built around a property‑graph approach, where the core element is the **Entity**, representing a physical or virtual object. Each Entity is assigned one or more **Entity Types** and is uniquely identified by an **Entity Id**, expressed as a URI. An Entity can have zero or more **attributes**, each identified by a name, and these attributes fall into two main categories: **Properties** and **Relationships**.

**Properties** describe the static or dynamic characteristics of an Entity, including **GeoProperties** that provide its geospatial context. Each Property holds a value, which may be a simple type such as a number, string, or boolean, or a more complex structure such as an array or an object (structured value).

**Relationships** capture associations between Entities and are always unidirectional. A Relationship has an **object**, represented by a URI that identifies the target Entity it points to.

A key aspect of the NGSI‑LD model is its recursive structure: **both Properties and Relationships can themselves have additional Properties and Relationships**. This allows for rich, extensible descriptions and fine‑grained contextualization, enabling NGSI‑LD to represent complex, interconnected digital twins and their evolving states within a property graph.

![NGSI-LD Information Model Instantiation](images/NGSI-LD_Information_Model_Instantiation.png)

# Digital Twins: Digital Twin Modeling

The complexity of a Digital Twin depends on what it represents. An **Atomic Twin** can be modeled as a single Entity, a **System Twin** as a graph of interconnected Entities, and a **System‑of‑Systems Twin** as an aggregation of multiple System Twins.

![Digital Twins: Digital Twin Modeling](Digital_Twins_Digital_Twin_Modelling.png)

# NGSI-LD compatible Smart Data Models

The NGSI‑LD information model is a meta‑model that represents the world in terms of **Entities**, each identified by an **Entity Id** and associated with one or more **Entity Types**, and enriched through **Properties** and **Relationships**. However, NGSI‑LD itself does not define which specific Entity Types exist or which Properties and Relationships are valid for a given type. These details are defined separately by a **Data Model**, which specifies the structure and semantics of each Entity Type.

The **Smart Data Models initiative**, launched by the FIWARE Foundation, provides a comprehensive library of Data Models designed to be fully compatible with the NGSI‑LD information model and API. These Data Models align with schema.org and adhere to existing sector‑specific standards whenever such standards are available.

Since its inception, the initiative has published more than 900 Data Models, with a steadily increasing number of organizations contributing new specifications. Major contributors such as TM Forum and IUDX have supported the adoption of an open governance model, ensuring the initiative follows established open‑source best practices.

---



