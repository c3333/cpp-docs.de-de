---
title: CAssertions, CAssertionInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CAssertions
- m_szCatalog
- m_bInitiallyDeferred
- CONSTRAINT_NAME
- m_szSchema
- INITIALLY_DEFERRED
- m_bIsDeferrable
- m_szName
- CAssertionInfo
- CONSTRAINT_CATALOG
- CONSTRAINT_SCHEMA
- IS_DEFERRABLE
dev_langs: C++
helpviewer_keywords:
- CAssertionInfo parameter class
- DESCRIPTION class data member
- CAssertions typedef class
- IS_DEFERRABLE
- m_szSchema
- m_bInitiallyDeferred
- CONSTRAINT_CATALOG
- m_szCatalog
- CONSTRAINT_NAME
- CONSTRAINT_SCHEMA
- m_szName
- m_szDescription
- INITIALLY_DEFERRED
- m_bIsDeferrable
ms.assetid: 2a79c2da-5c9b-4fa6-98e8-90b7f5d6f021
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e13ef57486a948b8cb702c004ca144d4ec6d2e59
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="cassertions-cassertioninfo"></a>CAssertions, CAssertionInfo
Rufen Sie die-typedefklasse **CAssertions** zum Implementieren der Parameterklasse **CAssertionInfo**.  
  
## <a name="remarks"></a>Hinweise  
 Finden Sie unter [Schemarowset-Klassen und TypeDef-Klassen](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) für Weitere Informationen zur Verwendung von typedef-Klassen.  
  
 Diese Klasse gibt die im Katalog definierten Assertionen, die von einem angegebenen Benutzer gehören.  
  
 Die folgende Tabelle enthält die Klassendatenmember für **CAssertionInfo** und ihre entsprechenden OLE DB-Spalten. Finden Sie unter [ASSERTIONEN Rowset](https://msdn.microsoft.com/en-us/library/ms719776.aspx) in der *OLE DB Programmer's Reference* für Weitere Informationen über das Schema und die Spalten.  
  
|Datenmember|OLE DB-Spalten|  
|------------------|--------------------|  
|m_szCatalog|CONSTRAINT_CATALOG|  
|m_szSchema|CONSTRAINT_SCHEMA|  
|m_szName|CONSTRAINT_NAME|  
|m_bIsDeferrable|IS_DEFERRABLE|  
|m_bInitiallyDeferred|INITIALLY_DEFERRED|  
|m_szDescription|BESCHREIBUNG|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "atldbsch.h" Einfügen  
  
## <a name="see-also"></a>Siehe auch  
 [CRestrictions-Klasse](../../data/oledb/crestrictions-class.md)