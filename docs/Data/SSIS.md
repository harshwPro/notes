---
# title:  
# description: 
tags:
  - Data
---

# SQL Server Integration Services

## Introduction

SSIS is the glue that holds it all together. More than that, SSIS is the circulatory system of your data warehousing and BI solutions.

### ETL
ETL is an acronym for extract, transform, and load, which is a very literal description of modern data manipulation and movement processes. When we talk about ETL, we are specifically talking about:  
1. Extracting data from a source, such as a database or flat files; 
1. Transforming data, or manipulating and enriching it en route to its destination;
1. Loading data into its destination, often a database.

### What Can SSIS Do for You? (Functional)
SSIS provides a wide array of out-of-the-box functionality to accomplish common ETL-related tasks. The major tasks you’ll encounter during most ETL processing include the following:

- **Extracting data** from a wide variety of sources including flat files, XML, the Internet, Microsoft Excel spreadsheets, and relational and nonrelational databases. If the stock source adapters don’t cover your needs, SSIS’s support for .NET gives you the ability to extract data from literally any data source that you have access to.
- **Validating data** according to predefined rules you specify as it moves through your ETL process. You can validate data by using a variety of methods such as ensuring that strings match patterns and that numeric values are within a given range.
- Performing Data cleansing, or the process of identifying invalid data values and removing them or modifying them to conform to your predefined constraints. Examples include changing negative numbers to zero or removing extra whitespace characters from strings.
- **Deduplicating data**, which is the elimination of data records that you consider to be duplicates. For a given process, you may consider entire records that are value-for-value matches to be duplicates; for other processes, you may determine that a value match on a single field (or set of fields), such as Telephone Number, identifies a duplicate record.
- **Loading data** into files, databases such as SQL Server, or other destinations. SSIS provides a wide range of stock destination adapters that allow you to output data to several well-defined destinations. As with data extraction, if you have a special destination in mind that’s not supported by the SSIS stock adapters, the built-in .NET support lets you output to nearly any destination you can access.

### What Can SSIS Do for You? (Nonfunctional)

- **Robustness** is provided in SSIS primarily through built-in error-handling to capture and deal with bad data and execution exceptions as they occur, transactions that ensure consistency of your data should a process enter an unrecoverable processing exception, and checkpoints that allow some ability to restart packages.  
- **Performance and efficiency** are closely related, but not entirely synonymous, concepts. You can think of performance as the raw speed with which your ETL processes accomplish their tasks. Efficiency digs a bit deeper and includes minimizing resource (memory, CPU, and persistent storage) contention and usage. SSIS has many optimizations baked directly into its data flow components and data flow engine—for instance, to tweak the raw performance and resource efficiency of the data flow.   
- **Maintainability** can be boiled down to the ongoing cost of managing and administering your ETL solution after it’s in production. Maintainability is also one of the easiest items to measure, because you can ask questions such as, “How many hours each month do I have to spend fixing issues in ETL processes?” or “How many hours of manual intervention are required each week to deal with, or to avoid, errors in my ETL process?” SSIS provides a new project deployment model to make it easier to move ETL projects from one environment to the next; and BIDS provides built-in support for source control systems such as Team Foundation Server (TFS) to help minimize the maintenance costs of your solutions.  
- **Security** is provided in SSIS through a variety of methods and interactions with other systems, including Windows NT File System (NTFS) and SQL Server 11. Package and project deployment to SQL Server is a powerful method of securing your packages. In this case, SQL Server uses its robust security model to control access to, and encryption of, SSIS package contents.  
- **Scalability** can be defined as how well your ETL solution can handle increasing quantities of data. SSIS provides the ability to scale predictably with your increased demands, providing of course that you create your packages to maximize SSIS’s throughput.   
- **Reliability**, put simply, can be defined as how resistant your ETL solution is to failure—and if failure does occur, how well your solution handles the situation. SSIS provides extensive logging capabilities that, when combined with BIDS’s built-in debugging capabilities, can help you quickly track down and fix the root cause of failure. SSIS can also notify you in the event of a failure situation.

### SSIS Architecture

One of the major improvements that SSIS introduced over DTS was the separation of the concepts of control flow and data flow. The control flow manages the order of execution for packages and manages communication with support elements such as event handlers. The data flow engine is exposed as a component within the control flow and it provides high-performance data extraction, transformation, and loading services.

Simply speaking, a package contains the control flow. The control flow contains control flow tasks and containers. The Data Flow task is a special type of task that contains the data flow. The data flow contains data flow components, which move and manipulate your data. There are three types of data flow components:
- **Sources** can pull data from any of a variety of data stores, and feed that data into the data flow.
- **Transformations** allow you to manipulate and modify data within the data flow one row at a time.
- **Destinations** provide a means for the data flow to output and persist data after it moves through the final stage of the data flow.

