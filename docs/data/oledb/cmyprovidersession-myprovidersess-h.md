---
title: CCustomSession (CustomSess.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidersession
- myprovidersess.h
- ccustomsession
- customsess.h
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
- CCustomSession class in CustomSess.H
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
ms.openlocfilehash: 4775f21c1e0fa7666d24b4d6a55e099bc6ae55a2
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079759"
---
# <a name="ccustomsession-customsessh"></a>CCustomSession (CustomSess.H)

*Benutzer* definiert Sess. H enthält die Deklaration und Implementierung für das OLE DB Session-Objekt. Das Datenquellen Objekt erstellt das Sitzungs Objekt und stellt eine Konversation zwischen einem Consumer und einem Anbieter dar. Mehrere gleichzeitige Sitzungen können für eine Datenquelle geöffnet werden. Die Vererbungs Liste für `CCustomSession` folgt:

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSession
class ATL_NO_VTABLE CCustomSession :
   public CComObjectRootEx<CComSingleThreadModel>,
   public IGetDataSourceImpl<CCustomSession>,
   public IOpenRowsetImpl<CCustomSession>,
   public ISessionPropertiesImpl<CCustomSession>,
   public IObjectWithSiteSessionImpl<CCustomSession>,
   public IDBSchemaRowsetImpl<CCustomSession>,
   public IDBCreateCommandImpl<CCustomSession, CCustomCommand>
```

Das Sitzungs Objekt erbt von `IGetDataSource`, `IOpenRowset`, `ISessionProperties`und `IDBCreateCommand`. Die `IGetDataSource`-Schnittstelle ermöglicht einer Sitzung das Abrufen der Datenquelle, die Sie erstellt hat. Dies ist hilfreich, wenn Sie Eigenschaften aus der Datenquelle, die Sie erstellt haben, oder andere Informationen, die von der Datenquelle bereitgestellt werden können, erhalten müssen. Die `ISessionProperties`-Schnittstelle verarbeitet alle Eigenschaften der Sitzung. Die `IOpenRowset`-und `IDBCreateCommand`-Schnittstellen werden verwendet, um die Datenbank zu verarbeiten. Wenn der Anbieter Befehle unterstützt, wird die `IDBCreateCommand`-Schnittstelle implementiert. Sie wird verwendet, um das Command-Objekt zu erstellen, das Befehle ausführen kann. Der Anbieter implementiert immer das `IOpenRowset` Objekt. Sie wird verwendet, um ein Rowset von einem Anbieter zu generieren. Dabei handelt es sich um ein Standardrowset (z. b. `"select * from mytable"`) eines Anbieters.

Der Assistent generiert außerdem drei Sitzungs Klassen: `CCustomSessionColSchema`, `CCustomSessionPTSchema`und `CCustomSessionTRSchema`. Diese Sitzungen werden für Schemarowsets verwendet. Mit Schemarowsets kann der Anbieter Metadaten an den Consumer zurückgeben, ohne dass der Consumer eine Abfrage ausführen oder Daten abrufen muss. Das Abrufen von Metadaten kann viel schneller sein als das Auffinden der Funktionen eines Anbieters.

Die OLE DB Spezifikation erfordert, dass Anbieter, die die `IDBSchemaRowset`-Schnittstelle implementieren, drei Schemarowsettypen unterstützen: DBSCHEMA_COLUMNS, DBSCHEMA_PROVIDER_TYPES und DBSCHEMA_TABLES. Der Assistent generiert Implementierungen für jedes Schemarowset. Jede vom Assistenten generierte Klasse enthält eine `Execute`-Methode. In dieser `Execute`-Methode können Sie Daten an den Anbieter zurückgeben, welche Tabellen, Spalten und Datentypen unterstützt werden. Diese Daten sind zur Kompilierzeit bekannt.

## <a name="see-also"></a>Weitere Informationen

[Vom Anbieter-Assistenten generierte Dateien](../../data/oledb/provider-wizard-generated-files.md)<br/>
