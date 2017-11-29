---
title: SET_PARAM_TYPE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SET_PARAM_TYPE
dev_langs: C++
helpviewer_keywords: SET_PARAM_TYPE macro
ms.assetid: 85979070-2d55-4c67-94b1-9b9058babc59
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b8fb0ab344f5ee9e34c1157d661bced369afac41
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="setparamtype"></a>SET_PARAM_TYPE
Gibt `COLUMN_ENTRY` -Makros an, die der `SET_PARAM_TYPE` -Makroeingabe-, -ausgabe- oder -ein-/-ausgabe folgen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET_PARAM_TYPE(  
type  
 )  
  
```  
  
#### <a name="parameters"></a>Parameter  
 `type`  
 [in] Der für den Parameter festzulegende Typ.  
  
## <a name="remarks"></a>Hinweise  
 Anbieter unterstützen nur Parametereingabe-/-ausgabetypen, die von der zugrunde liegenden Datenquelle unterstützt werden. Der Typ ist eine Kombination aus einem oder mehreren **DBPARAMIO** -Werten (siehe [DBBINDING-Strukturen](https://msdn.microsoft.com/en-us/library/ms716845.aspx) in der *OLE DB-Programmierreferenz*):  
  
-   **DBPARAMIO_NOTPARAM** Der Accessor hat keine Parameter. In der Regel legen Sie **eParamIO** auf diesen Wert in Zeilenaccessoren fest, um den Benutzer daran zu erinnern, dass Parameter ignoriert werden.  
  
-   **DBPARAMIO_INPUT** Ein Eingabeparameter.  
  
-   **DBPARAMIO_OUTPUT** Ein Ausgabeparameter.  
  
-   **DBPARAMIO_INPUT &#124; DBPARAMIO_OUTPUT** der Parameter ist sowohl Eingabe-als auch ein Output-Parameter.  
  
## <a name="example"></a>Beispiel  
```cpp  
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

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

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
``` 
  
## <a name="requirements"></a>Anforderungen  
 **Header:** atldbcli.h  
  
## <a name="see-also"></a>Siehe auch  
 [Makros und globale Funktionen für OLE-Consumervorlagen](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)