## Table of contents

- [What is Abstraction](#what-is-abstraction)
- [View of Data (Three Schema Architecture)](#view-of-data-three-schema-architecture)
  - [Internal level / Physical level](#internal-level--physical-level)
  - [Logical level / Conceptual level](#logical-level--conceptual-level)
  - [View level / External level](#view-level--external-level)
- [Instances and Schemas](#instances-and-schemas)
- [Data Models](#data-models)
- [Database Languages](#database-languages)
- [What is ORM (Object Relational Mapping)](#what-is-orm-object-relational-mapping)
- [How is Database accessed from Application programs?](#how-is-database-accessed-from-application-programs)
- [DBMS Application Architectures](#dbms-application-architectures)
  - [T1 Architecture](#t1-architecture)
  - [T2 Architecture](#t2-architecture)
  - [T3 Architecture](#t3-architecture)

Before moving into DBMS architecture let's understand some basic terminologies.

## What is Abstraction?

- Abstraction is the process of hiding the internal details of an application from the outer world.
- Think of an ATM the internal workings of an ATM like how the circuit is connected, how money is stored, etc are not required to know by the end user to withdraw money.

Let's start with DBMS architecture

## View of Data (Three Schema Architecture)

- The major purpose of DBMS is to provide users with an abstract view of the data. That is, the
  system hides certain details of how the data is stored and maintained.
- The main objective of three level architecture is to enable multiple users to access the same data
  with a personalized view while storing the underlying data only once

### Internal level / Physical level

- Physical level of a database describes how the data is being stored in secondary storage devices like disks and tapes and also gives insights on additional storage details.
- It is the lowest level of abstraction describes how the data are stored.
- Low-level data structures used.
- It has Physical schema which describes physical storage structure of DB.
- Talks about: Storage allocation (N-ary tree etc), Data compression & encryption etc.
- Goal: We must define algorithms that allow efficient access to data.

### Logical level / Conceptual level

- At conceptual level, data is represented in the form of various database tables. For Example, STUDENT database may contain STUDENT and COURSE tables which will be visible to users but users are unaware of their storage. Also referred as logical schema,
- The conceptual schema describes the design of a database at the conceptual level, describes what data are stored in DB, and what relationships exist among those data.
- User at logical level does not need to be aware about physical-level structures.
- DBA, who must decide what information to keep in the DB use the logical level of abstraction.
- Goal: ease to use.

![how-data-stored-in-physical-and-logical-level](https://github.com/subrat611/Core-Subject-Notes/assets/77252075/3ee9ea12-f391-4e1b-a3a6-4002cf118bde)

### View level / External level

- Highest level of abstraction aims to simplify users’ interaction with the system by providing different view to different end-user.
- Each view schema describes the database part that a particular user group is interested and hides the remaining database from that user group.
- At the external level, a database contains several schemas that sometimes called as subschema.
- The subschema is used to describe the different view of the database.
- At views also provide a security mechanism to prevent users from accessing certain parts of DB.
- For Example, FACULTY of a university is interested in looking course details of students, STUDENTS are interested in looking at all details related to academics, accounts, courses and hostel details as well

## Instances and Schemas

- The collection of information stored in the DB at a particular moment is called an instance of DB.
- A schema refers to the logical structure that defines how data is organized and how relationships between data elements are handled (The overall design of the DB is called the DB schema).
- Schema is structural description of data. Schema doesn’t change frequently. Data may change frequently.
- DB schema corresponds to the variable declarations (along with type) in a program.
- We have 3 types of Schemas: Physical, Logical, several view schemas called subschemas.
- Logical schema is most important in terms of its effect on application programs, as programmers construct apps by using logical schema.
- Physical data independence, physical schema change should not affect logical schema/application programs.

## Data Models

- Provides a way to describe the design of a DB at logical level.
- A database model is a high-level, abstract representation of how data is organized and structured within a database system. It defines the logical design and the relationships between data elements.
- A database schema, on the other hand, is a specific implementation of a database model. It is a blueprint that defines the structure of a database within a particular database management system (DBMS).
- Underlying the structure of the DB is the Data Model; a collection of conceptual tools for describing data, data relationships, data semantics & consistency constraints.
- Data models define how data is connected to each other and how they are processed and stored inside the system.
- E.g., ER model, Relational Model, object-oriented model, object-relational data model etc.

## Database Languages

- Data definition language (DDL) to specify the database schema.
- Data manipulation language (DML) to express database queries and updates.
- Practically, both language features are present in a single DB language, e.g., SQL language.
- DDL
  - We specify consistency constraints, which must be checked, every time DB is updated.
- DML

  - Data manipulation involves

    - Retrieval of information stored in DB.
    - Insertion of new information into DB.
    - Deletion of information from the DB.
    - Updating existing information stored in DB.

  - Query language, a part of DML to specify statement requesting the retrieval of information.

## What is ORM (Object Relational Mapping)

- ODM is a software design pattern and a set of tools and libraries that allow developers to map data between object-oriented programming languages and relational databases.
- It bridges the gap between the object-oriented model used in application code and the relational model used in databases.

## How is Database accessed from Application programs?

- Apps (written in host languages, C/C++, Java) interacts with DB.
- E.g., Banking system’s module generating payrolls access DB by executing DML statements from the host language.
- API is provided to send DML/DDL statements to DB and retrieve the results.
  - Open Database Connectivity (ODBC), Microsoft “C”.
  - Java Database Connectivity (JDBC), Java.

## DBMS Application Architectures

- Client machine - on which remote DB users work
- Server machines - on which DB system runs.

### T1 Architecture

- The client, server & DB all present on the same machine.

### T2 Architecture

- App is partitioned into 2-components.
- Client machine, which invokes DB system functionality at server end through query language statements.
- API standards like ODBC & JDBC are used to interact between client and server.

### T3 Architecture

- App is partitioned into 3 logical components.
- Client machine is just a frontend and doesn’t contain any direct DB calls.
- Client machine communicates with App server, and App server communicated with DB system to access data.
- Business logic, what action to take at that condition is in App server itself.
- T3 architecture are best for WWW Applications.

Advantages:

- Scalability due to distributed application servers.
- Data integrity, App server acts as a middle layer between client and DB, which minimize the chances of data corruption.
- Security, client can’t directly access DB, hence it is more secure.
