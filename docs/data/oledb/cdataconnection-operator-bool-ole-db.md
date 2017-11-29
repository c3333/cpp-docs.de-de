---
title: "CDataConnection::operator bool (OLE DB) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDataConnection::operatorBOOL"
  - "ATL::CDataConnection::operatorBOOL"
  - "CDataConnection.operatorBOOL"
  - "ATL.CDataConnection.operatorBOOL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BOOL-Operator"
  - "operator bool"
ms.assetid: e0791faf-2ed2-4dbb-9e68-3b9b5da2b7a7
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDataConnection::operator bool (OLE DB)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Bestimmt, ob die aktuelle Sitzung oder nicht geöffnet ist.  
  
## Syntax  
  
```  
  
operator bool( ) throw( );  
  
```  
  
## Hinweise  
 Gibt einen Wert `bool` \(C\+\+\-Datentyp\) zurück.  **true** gibt an, dass die aktuelle Sitzung geöffnet ist; **false** gibt an, dass die aktuelle Sitzung geschlossen wird.  
  
## Anforderungen  
 **Header:** atldbcli.h  
  
## Siehe auch  
 [CDataConnection\-Klasse](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator BOOL](../../data/oledb/cdataconnection-operator-bool.md)