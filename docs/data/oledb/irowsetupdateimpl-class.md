---
title: IRowsetUpdateImpl-Klasse | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
dev_langs: C++
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fe93031417b8fc7717be13007b0fcfc5d08a2c40
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl-Klasse
Die OLE DB-Vorlagen-Implementierung von der [IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx) Schnittstelle.  
  
## <a name="syntax"></a>Syntax  
  
```  
template <  
   class T,   
   class Storage,   
   class UpdateArray = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>   
>  
class IRowsetUpdateImpl : public IRowsetChangeImpl<  
   T,   
   Storage,   
   IRowsetUpdate,   
   RowClass,   
   MapClass  
>  
```  
  
#### <a name="parameters"></a>Parameter  
 `T`  
 Eine abgeleitete Klasse `IRowsetUpdateImpl`.  
  
 `Storage`  
 Der Benutzerdatensatz enthält.  
  
 `UpdateArray`  
 Ein Array mit zwischengespeicherten Daten für das Rowset zu aktualisieren.  
  
 `RowClass`  
 Die Einheit für die Speicherung der **HROW**.  
  
 `MapClass`  
 Für alle Zeilenhandles, die vom Anbieter Storage-Einheit.  
  
## <a name="members"></a>Mitglieder  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Schnittstellenmethoden (mit IRowsetChange verwendet)  
  
|||  
|-|-|  
|[SetData](../../data/oledb/irowsetupdateimpl-setdata.md)|Legt Datenwerte in einer oder mehreren Spalten fest.|  
  
### <a name="interface-methods-used-with-irowsetupdate"></a>Schnittstellenmethoden (mit IRowsetUpdate verwendet)  
  
|||  
|-|-|  
|[GetOriginalData](../../data/oledb/irowsetupdateimpl-getoriginaldata.md)|Ruft die Daten zuletzt übertragen oder von der Datenquelle wird ignoriert, wenn ausstehende Änderungen erhalten hat.|  
|[GetPendingRows](../../data/oledb/irowsetupdateimpl-getpendingrows.md)|Gibt eine Liste der Zeilen mit ausstehenden Änderungen.|  
|[GetRowStatus](../../data/oledb/irowsetupdateimpl-getrowstatus.md)|Gibt den Status der angegebenen Zeilen zurück.|  
|[Rückgängig machen](../../data/oledb/irowsetupdateimpl-undo.md)|Macht alle Änderungen auf die Zeile seit der letzten Fetch oder Update.|  
|[Update (Aktualisieren)](../../data/oledb/irowsetupdateimpl-update.md)|Überträgt alle Änderungen, die auf die Zeile seit der letzten Fetch oder Update.|  
  
### <a name="implementation-methods-callback"></a>Implementierungsmethoden (Callback)  
  
|||  
|-|-|  
|[IsUpdateAllowed](../../data/oledb/irowsetupdateimpl-isupdateallowed.md)|Verwendet, um zu überprüfen und so weiter für Sicherheit, Integrität, bevor Updates zugelassen.|  
  
### <a name="data-members"></a>Datenmember  
  
|||  
|-|-|  
|[m_mapCachedData](../../data/oledb/irowsetupdateimpl-m-mapcacheddata.md)|Enthält die ursprünglichen Daten für die verzögerte Ausführung.|  
  
## <a name="remarks"></a>Hinweise  
 Sie sollten zuerst lesen und verstehen Sie die Dokumentation für [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx), da Sie alles, was es beschrieben auch hier gilt. Lesen Sie auch Kapitel 6 der *OLE DB Programmer's Reference* zum Festlegen von Daten.  
  
 `IRowsetUpdateImpl`implementiert die OLE DB- `IRowsetUpdate` -Schnittstelle, die Consumer die Übertragung von Änderungen durch verzögert ermöglicht `IRowsetChange` an die Datenquelle und vor der Übertragung Änderungen rückgängig zu machen.  
  
> [!IMPORTANT]
>  Es wird dringend empfohlen, dass Sie die folgende Dokumentation, bevor Sie versuchen, einen Anbieter implementieren lesen:  
  
-   [Erstellen eines aktualisierbaren Anbieters](../../data/oledb/creating-an-updatable-provider.md)  
  
-   Kapitel 6 der *OLE DB-Programmierreferenz*  
  
-   Siehe auch wie die `RUpdateRowset` Klasse wird verwendet, in dem UpdatePV-Beispiel  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** „atldb.h“  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Erstellen eines aktualisierbaren Anbieters](../../data/oledb/creating-an-updatable-provider.md)