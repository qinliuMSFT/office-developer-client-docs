---
title: "Stat Method (ADO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: d3d3976b-14d4-dee0-412d-a37bc72fbfd3

---

# Stat Method (ADO)

Retrieves information about a **Stream** object. 
  
## Syntax

Long  *stream*  . **Stat**( *StatStg*  ,  *StatFlag*  ) 
  
## Return Value

A long value indicating the status of the operation.
  
## Parameters

-  *StatStg* 
    
- A STATSTG structure that will be filled in with information about the stream. The implementation of the Stat method used by the ADO Stream object does not fill in all of the fields of the structure.
    
-  *StatFlag* 
    
- Specifies that this method does not return some of the members in the STATSTG structure, thus saving a memory allocation operation. Values are taken from the STATFLAG enumeration.
  
 The STATFLAG enumeration has two values 
    
|**Constant**|**Value**|
|:-----|:-----|
|STATFLAG_DEFAULT  <br/> |0  <br/> |
|STATFLAG_NONAME  <br/> |1  <br/> |
   
## Remarks

The version of the Stat method implemented for the ADO Stream object fills in the following fields of the STATSTG structure:
  
-  *pwcsName* 
    
- A string containing the name of the stream, if one is available and the StatFlag value STATFLAG_NONAME was not specified.
    
-  *cbSize* 
    
- Specifies the size in bytes of the stream or byte array.
    
-  *mtime* 
    
- Indicates the last modification time for this storage, stream, or byte array.
    
-  *ctime* 
    
- Indicates the creation time for this storage, stream, or byte array.
    
-  *atime* 
    
- Indicates the last access time for this storage, stream or byte array.
    
If STATFLAG_NONAME is specified in the StatFlag parameter, the name of the stream is not returned.
  
If STATFLAG_NONAME was not specified in the StatFlag parameter, and there is no name available for the current stream, this value will be E_NOTIMPL.
  
