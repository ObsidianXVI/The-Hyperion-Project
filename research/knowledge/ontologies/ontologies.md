# Ontologies

In Autonomic Computing (AC), there needs to be a way for the program to access certain "knowledge" to aid its decision-making. Let us consider a simple Autonomic System (AS). There are two ways the decision-making engine can improve the AS — machine learning for blackbox optimisation, or through knowledge about each Autonomic Element (AE) to perform whitebox optimisation.

```
Design a system for ontological knowledge to be represented and manipulated by computer programs
```

# Defining Key Terms

## Ontologies
*What is an ontology?*

From [Wikipedia](https://en.wikipedia.org/wiki/Ontology_(computer_science)):

> In computer science and information science, an ontology encompasses a representation, formal naming, and definition of the categories, properties, and relations between the concepts, data, and entities that substantiate one, many, or all domains of discourse. More simply, an ontology is a way of showing the properties of a subject area and how they are related, by defining a set of concepts and categories that represent the subject.

A more AC-related definition (AC Springer TB, pg2):

> The ontology used by an autonomic manager includes objects like components, data structures, events, files, libraries, operating systems and functions relating these different objects in some points in time. But it also contains concepts like requirements, traceability links and deployment strategies, pertaining to the initial phases of software development.

### Our Definition
> An ontology is a collection of information about a particular field, including object properties, actions and their corresponding results, relations between ontological elements, as well as implementation details for the AS to use the knowledge.


## Knowledge
*What are the different types of knowledge?*

Knowledge is an extremely broad topic in philosophy, but in AC, we can scope out the applications for each type of knowledge:
- Explicit Knowledge
    - systemetically documented info about algorithms, patterns
- Implicit Knowledge
    - skills, problem-solving for particular problems, by applying explicit knowledge to a specific problem (can expand the ontology)
- Tacit Knowledge
    - NA
- Declarative Knowledge
    - information, facts about a topic, such as the suitability of various algorithms, patterns
- Procedural Knowledge
    - ability to do certain tasks
- A Posteriori Knowledge
    - Probably NA, since an AS is deployed for one use case only
- A Priori Knowledge
    - inferring, logical deudctions to gain more knowledge from given info

## Representation
*What information do we want to represent?*

Let's take the field of Networks as an example and say we want to make API calls to HTTP endpoints. When even talking about HTTP requests and all that, what do we even mean when we say "I know how to implement networking features in the system"? Perhaps any of the following:
- Knowing how to create and send HTTP requests (procedural knowledge)
    - using language libraries (explicit knowledge)
- Knowing how to parse the response (procedural knowledge)
- Knowing how to handle HTTP errors (implicit knowledge)
- Knowing how the different parameters affect the resource's features (declarative knowledge)

*How will this information be stored?*

The first thing that comes to mind when "data storage" is mentioned is obviously databases. But using only databases, in my opinion, might not be efficient for the task, since the AS will have to perform large queries every other second. Instead some knowledge should be stored in a database, which the AS can reference to aid its decision-making, while the rest is stored within the AS, as native code.

Let us put aside the "native knowledge" (so to speak) for now, and focus on the knowledge stored on the "imported knowledge" (stored in the database). We need to come up with the schema for four different types of knowledge (this will be done further down in the section titled [Knowledge Schemas](#knowledge-schemas)):
- implicit
- explicit
- procedural
- declarative

*How will the information integrate with the AS?*

Stored as a separate repository, the ontological information can be looked up by Intelligence by filtering through meta information. An AS would then be able to handle reification of the knowledge through Mutability.

## Manipulation
*How will the information be updated by different sources?*

The ontologies can be updated by the AS, but changes will remain local, and will be overwritten next time the ontology is fetched from the Autonomic Knowledge Registry (AKR). Local changes can help finetune the ontology for the current use case.


# Developments In The Field

- [Web Ontology Language](https://en.wikipedia.org/wiki/Web_Ontology_Language) (OWL), [Resource Description Framework](https://en.wikipedia.org/wiki/Resource_Description_Framework) (RDF)
- [Protégé](https://protege.stanford.edu)
- [Common Logic](https://www.w3.org/2004/12/rules-ws/slides/pathayes.pdf)
- [Description Logic](https://www.cs.toronto.edu/~jm/2507S/Notes04/DL.pdf)
- [Cyc](https://en.wikipedia.org/wiki/Cyc)

Other projects that are related ontologies, such as [RIF](https://en.wikipedia.org/wiki/Rule_Interchange_Format) lean more into reasoning and inference than knowledge representation, and are therefore omitted from the list above.

# Knowledge Schemas