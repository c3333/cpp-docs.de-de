---
title: 'CRowset:: FindNextRow | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset.FindNextRow
- CRowset<TAccessor>.FindNextRow
- ATL::CRowset::FindNextRow
- CRowset::FindNextRow
- CRowset<TAccessor>::FindNextRow
- CRowset.FindNextRow
- ATL.CRowset<TAccessor>.FindNextRow
- ATL::CRowset<TAccessor>::FindNextRow
- FindNextRow
dev_langs: C++
helpviewer_keywords: FindNextRow method
ms.assetid: 36484df9-3625-4f15-bf69-db73a8d91c55
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9a7b3e68ef75344b6ee0e612fb104c9a21ea1bde
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetfindnextrow"></a>CRowset::FindNextRow
Sucht das nächste übereinstimmende Zeile nach dem angegebenen Lesezeichen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      HRESULT FindNextRow(   
   DBCOMPAREOP op,   
   BYTE* pData,   
   DBTYPE wType,   
   DBLENGTH nLength,   
   BYTE bPrecision,   
   BYTE bScale,   
   BOOL bSkipCurrent = TRUE,   
   CBookmarkBase* pBookmark = NULL    
) throw( );  
```  
  
#### <a name="parameters"></a>Parameter  
 `op`  
 [in] Der Vorgang zum Vergleichen von Zeilenwerten verwenden. Werte, finden Sie unter [irowsetfind:: FindNextRow](https://msdn.microsoft.com/en-us/library/ms723091.aspx).  
  
 `pData`  
 [in] Ein Zeiger auf den Wert verglichen werden.  
  
 `wType`  
 [in] Gibt den Datentyp, der der Wertteil des Puffers an. Informationen zu typindikatoren finden Sie unter [Datentypen](https://msdn.microsoft.com/en-us/library/ms723969.aspx) in der *OLE DB Programmer's Reference* im Windows SDK.  
  
 `nLength`  
 [in] Die Länge in Bytes, der Consumer-Datenstruktur, die für den Datenwert zugeordnet. Weitere Informationen finden Sie unter der Beschreibung der **CbMaxLen** in [DBBINDING-Strukturen](https://msdn.microsoft.com/en-us/library/ms716845.aspx) in die *OLE DB Programmer's Reference.*  
  
 `bPrecision`  
 [in] Die maximale Genauigkeit, die beim Abrufen von Daten verwendet wird. Verwendet nur, wenn `wType` ist `DBTYPE_NUMERIC`. Weitere Informationen finden Sie unter [Konvertierungen, die im Zusammenhang mit DBTYPE_NUMERIC oder DBTYPE_DECIMAL](https://msdn.microsoft.com/en-us/library/ms719714.aspx) in der *OLE DB Programmer's Reference*.  
  
 `bScale`  
 [in] Die Dezimalstellen, die beim Abrufen von Daten verwendet wird. Verwendet nur, wenn `wType` ist `DBTYPE_NUMERIC` oder **DBTYPE_DECIMAL**. Weitere Informationen finden Sie unter [Konvertierungen, die im Zusammenhang mit DBTYPE_NUMERIC oder DBTYPE_DECIMAL](https://msdn.microsoft.com/en-us/library/ms719714.aspx) in der *OLE DB Programmer's Reference*.  
  
 *bSkipCurrent*  
 [in] Die Anzahl der Zeilen aus das Lesezeichen, bei dem eine Suche zu starten.  
  
 `pBookmark`  
 [in] Das Lesezeichen für die Position, an der mit eine Suche begonnen werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Standard `HRESULT`-Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Bei dieser Methode muss die optionale Schnittstelle **IRowsetFind**, die möglicherweise nicht auf allen Anbietern unterstützt, wenn dies der Fall ist, gibt die Methode **E_NOINTERFACE**. Sie müssen auch festlegen **DBPROP_IRowsetFind** auf `VARIANT_TRUE` vor dem Aufruf **öffnen** für die Tabelle oder einen Befehl, der das Rowset enthält.  
  
 Informationen zur Verwendung von Lesezeichen in Consumer finden Sie unter [mithilfe von Lesezeichen](../../data/oledb/using-bookmarks.md).  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** atldbcli.h  
  
## <a name="see-also"></a>Siehe auch  
 [CRowset-Klasse](../../data/oledb/crowset-class.md)   
 [DBBINDING-Strukturen](https://msdn.microsoft.com/en-us/library/ms716845.aspx)