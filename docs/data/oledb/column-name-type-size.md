---
title: "COLUMN_NAME_TYPE_SIZE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLUMN_NAME_TYPE_SIZE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_NAME_TYPE_SIZE-Makro"
ms.assetid: b10f8ef9-78ce-4ec9-b4cc-4278271a46dd
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# COLUMN_NAME_TYPE_SIZE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Stellt eine Bindung im Rowset zur jeweiligen Spalte im Rowset dar.  Wie auch [COLUMN\_NAME](../../data/oledb/column-name.md), außer dass zu diesem Makro nimmt außerdem Datentyp und Größe.  
  
## Syntax  
  
```  
  
COLUMN_NAME_TYPE_SIZE(  
pszName  
,   
wType  
,   
nLength  
,   
data  
 )  
  
```  
  
#### Parameter  
 `pszName`  
 \[in\] Ein Zeiger auf den Spaltennamen.  Der Name muss eine Unicode\-Zeichenfolge sein.  Sie können dies bewerkstelligen, indem Sie "L" vor dem Namen, zum Beispiel einfügen: `L"MyColumn"`.  
  
 `wType`  
 \[in\] Der Datentyp.  
  
 `nLength`  
 \[in\] die Datengröße in Bytes.  
  
 `data`  
 \[in\] der entsprechenden Datenmember im Benutzerdatensatz.  
  
## Hinweise  
 Siehe [COLUMN\_NAME](../../data/oledb/column-name.md) Informationen zu, der die **COLUMN\_NAME\_\***\-Makros verwendet werden.  
  
## Anforderungen  
 **Header:** atldbcli.h  
  
## Siehe auch  
 [Makros und globale Funktionen für OLE\-Consumervorlagen](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN\_NAME](../../data/oledb/column-name.md)   
 [COLUMN\_NAME\_EX](../../data/oledb/column-name-ex.md)   
 [COLUMN\_NAME\_LENGTH](../../data/oledb/column-name-length.md)   
 [COLUMN\_NAME\_LENGTH\_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN\_NAME\_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN\_NAME\_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN\_NAME\_PS\_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN\_NAME\_PS\_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN\_NAME\_PS\_LENGTH\_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN\_NAME\_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN\_NAME\_TYPE\_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN\_NAME\_TYPE\_STATUS](../../data/oledb/column-name-type-status.md)