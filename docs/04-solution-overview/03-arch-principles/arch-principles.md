The following architecture principles are reflected in the architecture and consist of a set of rules and guidelines that set the basis for the use and deployment of IT resources and assets.
These principles are foundational considerations for all of the decisions applied to the architecture.
Each principle is accompagnied by its own rationale and implications to make sure there is a common understanding of its nature and justified reason for its use in making architectural decisions.

### 4.3.1 Principle – Asynchronous communication

| Principle Name | Asynchronous Interfaces |
| :------------- | :----------------------------------- |
| Statement      | I/O Communication should be asynchronous and non-blocking wherever possible |
| Rationale      | Provides highest performance. Handle higher number of events |
| Implications   | Microservices must be able to take advantage of this paradigm, and will use publish and subscribe type of API |

### 4.3.2 Principle - Loose Coupling

| Principle Name | Loosely Coupled Modules |
| :------------- | :----------------------------------- |
| Statement      | Each module has its own responsibility & operates on its own |
| Rationale      | Any module changes should not impact the other services and each module can have its own technology stack |
| Implications   | Improve the development & shortens the testing lifecycle |

### 4.3.3 Principle – Cacheable
| Principle Name | Cacheable |
| :------------- | :----------------------------------- |
| Statement	     | Caching should be supported where it makes sense |
| Rationale      | Caching of resources helps in faster access & improve the overall performance |
| Implications   | Improve the performance |

### 4.3.4 Principle – Stateless
|Principle Name  | Stateless
| :------------- | :----------------------------------- |
| Statement	     | Service acts on the request it receives |
| Rationale	     | Services should be stateless and should act only on the data it receives |
| Implications	 | Helps with flexibility of architecture |

### 4.3.5 Principle – Resiliency
|Principle Name  | Resiliency
| :------------- | :----------------------------------- |
| Statement	     | Highly available and responsive in spite of system interruptions |
| Rationale	     | Designing a system to maintain a pre-designated level of capability in the face of disturbance or adversity |
| Implications	 | System able to respond to external impacts in a controlled manner and remain responsive |

### 4.3.6 Principle – Scalability
|Principle Name  | Scalability
| :------------- | :----------------------------------- |
| Statement	     | Highly efficient and reliable |
| Rationale	     | Designing a system to handle sudden changes in workload without compromising performance under stress |
| Implications	 | System able to respond to all requests with the same quality/performance level as demand increases |

### 4.3.7 Principle – Compliance with Law
|Principle Name  | Compliance with Law
| :------------- | :----------------------------------- |
| Statement	     | Information and data management processes comply with all relevant laws, policies and regulations |
| Rationale	     | Abide by laws and policies and work on improvements towards them |
| Implications	 | Business that is compliance aware and educated by facilitating access and implementing needed measures |

### 4.3.8 Principle – Data is an Asset
|Principle Name  | Data is an Asset
| :------------- | :----------------------------------- |
| Statement	     | Data is valuable and should be managed accordingly |
| Rationale	     | Data is a corporate resource that should be at the foundation of decision-making, for which we should know how, where and when to keep it |
| Implications	 | Data management procedures are put into place, continuously revised/improved and used to prevent and correct information errors |

### 4.3.9 Principle – Data Security
|Principle Name  | Data Security
| :------------- | :----------------------------------- |
| Statement	     | Data is protected from unauthorized use and disclosure |
| Rationale	     | The idea of open sharing of data and information should be balanced against the importance of protecting classified, proprietary and sensitive information |
| Implications	 | Proper policies, procedures and security designs define and restrict adequate access for data and information as requested by data owners |

### 4.3.10 Principle – Common Vocabulary and Data Definitions
|Principle Name  | Common Vocabulary and Data Definitions
| :------------- | :----------------------------------- |
| Statement	     | Data definitions are available and accessible to all its users |
| Rationale	     | Having a common understanding of general terms and vocabulary helps in enabling communication and dialogs. It is especially required for system interfaces and data exchange. |
| Implications	 | A common vocabulary and set of definitions - also referred to as "corporate glossary" - is agreed upon  in order for it to be used uniformly across all units |

### 4.3.11 Principle – Ease-of-Use
|Principle Name  | Ease-of-Use Application
| :------------- | :----------------------------------- |
| Statement	     | Applications are easy to use so users can concentrate on their tasks |
| Rationale	     | An easy-to-use application is a positive incentive for its use; the less users have to understand the technology and technicality behind the application, the more productive they become |
| Implications	 | Applications are intuitive with a common "look and feel" without the need to make certain assumptions about their use |

### 4.3.12 Principle – Interoperability
|Principle Name  | Interoperability
| :------------- | :----------------------------------- |
| Statement	     | Ability of different systems to exchange and use information between each other |
| Rationale	     | Systems should be able to interpret the information exchanged in a meaningful and correct way |
| Implications	 | Systems provide services to and accept services from other systems which enables them to operate effectively together |
