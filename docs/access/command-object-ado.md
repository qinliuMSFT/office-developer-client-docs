---
title: "Command Object (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- ado210.chm1231106
  
localization_priority: Normal
ms.assetid: 64f4ef03-f858-c004-b891-0c96d13a5e6e
---

# Command Object (ADO)

Defines a specific command that you intend to execute against a data source.
  
## Remarks

Use a **Command** object to query a database and return records in a [Recordset](recordset-object-ado.md) object, to execute a bulk operation, or to manipulate the structure of a database. Depending on the functionality of the provider, some **Command** collections, methods, or properties may generate an error when referenced. 
  
With the collections, methods, and properties of a **Command** object, you can do the following: 
  
- Define the executable text of the command (for example, an SQL statement) with the [CommandText](commandtext-property-ado.md) property. 
    
- Define parameterized queries or stored-procedure arguments with [Parameter](parameter-object-ado.md) objects and the [Parameters](parameters-collection-ado.md) collection. 
    
- Execute a command and return a **Recordset** object if appropriate with the [Execute](http://msdn.microsoft.com/library/01812c8c-403e-4428-23f6-86bda747bd0e%28Office.15%29.aspx) method. 
    
- Specify the type of command with the [CommandType](commandtype-property-ado.md) property prior to execution to optimize performance. 
    
- Control whether the provider saves a prepared (or compiled) version of the command prior to execution with the [Prepared](prepared-property-ado.md) property. 
    
- Set the number of seconds that a provider will wait for a command to execute with the [CommandTimeout](commandtimeout-property-ado.md) property. 
    
- Associate an open connection with a **Command** object by setting its [ActiveConnection](activeconnection-property-ado.md) property. 
    
- Set the [Name](name-property-ado.md) property to identify the **Command** object as a method on the associated [Connection](connection-object-ado.md) object. 
    
- Pass a **Command** object to the [Source](source-property-ado-recordset.md) property of a **Recordset** in order to obtain data. 
    
- Access provider-specific attributes with the [Properties](properties-collection-ado.md) collection. 
    
> [!NOTE]
> To execute a query without using a **Command** object, pass a query string to the [Execute](http://msdn.microsoft.com/library/af190bd9-7167-df59-29ca-a9a86c4957fd%28Office.15%29.aspx) method of a **Connection** object or to the [Open](open-method-ado-recordset.md) method of a **Recordset** object. However, a **Command** object is required when you want to persist the command text and re-execute it, or use query parameters. 
  
To create a **Command** object independently of a previously defined **Connection** object, set its **ActiveConnection** property to a valid connection string. ADO still creates a **Connection** object, but it doesn't assign that object to an object variable. However, if you are associating multiple **Command** objects with the same connection, you should explicitly create and open a **Connection** object; this assigns the **Connection** object to an object variable. If you do not set the **Command** object's **ActiveConnection** property to this object variable, ADO creates a new **Connection** object for each **Command** object, even if you use the same connection string. 
  
To execute a **Command**, simply call it by its [Name](name-property-ado.md) property on the associated **Connection** object. The **Command** must have its **ActiveConnection** property set to the **Connection** object. If the **Command** has parameters, pass their values as arguments to the method. 
  
If two or more **Command** objects are executed on the same connection and either **Command** object is a stored procedure with output parameters, an error occurs. To execute each **Command** object, use separate connections or disconnect all other **Command** objects from the connection. 
  
The **Parameters** collection is the default member of the **Command** object. As a result, the following two code statements are equivalent. 
  
