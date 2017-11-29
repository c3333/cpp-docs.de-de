---
title: BEGIN_ACCESSOR_MAP | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BEGIN_ACCESSOR_MAP
dev_langs: C++
helpviewer_keywords: BEGIN_ACCESSOR_MAP macro
ms.assetid: e6d6e3a4-62fa-4e49-8c53-caf8c9d20091
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 611da93ac883b9d36fe86fbcd07ca75dfe5f350a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="beginaccessormap"></a>BEGIN_ACCESSOR_MAP
Markiert den Beginn der Accessor-Zuordnungseinträge.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BEGIN_ACCESSOR_MAP(  
x  
,   
num  
 )  
  
```  
  
#### <a name="parameters"></a>Parameter  
 *x*  
 [in] Der Name der Benutzerdatensatzklasse.  
  
 *num*  
 [in] Die Anzahl der Accessoren in dieser Accessorzuordnung.  
  
## <a name="remarks"></a>Hinweise  
 Bei mehreren Accessoren für ein Rowset, müssen Sie `BEGIN_ACCESSOR_MAP` am Anfang angeben und das `BEGIN_ACCESSOR` -Makro für jeden einzelnen Accessor verwenden. Das `BEGIN_ACCESSOR` -Makro wird mit dem `END_ACCESSOR` -Makro abgeschlossen. Die Accessorzuordnung wird mit dem `END_ACCESSOR_MAP` -Makro abgeschlossen.  
  
 Wenn es nur einen Accessor im Benutzerdatensatz gibt, verwenden Sie das Makro [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).  
  
## <a name="example"></a>Beispiel  

 ```cpp  
class CArtistsAccessor
{
public:
// Data Elements
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];
   short m_nAge;

// Output binding map
BEGIN_ACCESSOR_MAP(CArtistsAccessor, 2)
   BEGIN_ACCESSOR(0, true)
      COLUMN_ENTRY(1, m_szFirstName)
      COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false) // Not an auto accessor
      COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsAccessor, L" \
   SELECT \
      FirstName, \
      LastName, \
      Age \
      FROM Artists")
};
 ```

  
## <a name="requirements"></a>Anforderungen  
 **Header:** atldbcli.h  
  
## <a name="see-also"></a>Siehe auch  
 [Makros und globale Funktionen für OLE DB-Consumervorlagen](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)