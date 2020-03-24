---
title: Unterstützen von Benachrichtigungen
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- events [C++], notifications in OLE DB
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB provider templates, notifications
- OLE DB providers, notifications
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
ms.openlocfilehash: d29f84a0a5b33d55c0a04a4c758050cf9746f72a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209546"
---
# <a name="supporting-notifications"></a>Unterstützen von Benachrichtigungen

## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>Implementieren von Verbindungspunkt Schnittstellen für den Anbieter und den Consumer

Um Benachrichtigungen zu implementieren, muss eine Anbieter Klasse von [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md) und [IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md)erben.

`IRowsetNotifyCP` implementiert die Anbieter Website für die Verbindungspunkt Schnittstelle [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)). `IRowsetNotifyCP` implementiert Broadcast Funktionen, um Listener auf dem Verbindungspunkt `IID_IRowsetNotify` Änderungen am Inhalt des Rowsets zu informieren.

Sie müssen auch `IRowsetNotify` auf dem Consumer (auch als Senke bezeichnet) mithilfe von [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) implementieren und registrieren, damit der Consumer Benachrichtigungen verarbeiten kann. Weitere Informationen zum Implementieren der Verbindungspunkt Schnittstelle für den Consumer finden Sie unter [empfangen von Benachrichtigungen](../../data/oledb/receiving-notifications.md).

Außerdem muss die Klasse über eine Karte verfügen, die den Eintrag für den Verbindungspunkt definiert, wie folgt:

```cpp
BEGIN_CONNECTION_POINT_MAP
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)
END_CONNECTION_POINT_MAP
```

## <a name="adding-irowsetnotify"></a>Hinzufügen von IRowsetNotify

Zum Hinzufügen von `IRowsetNotify`müssen Sie Ihrer Vererbungs Kette `IConnectionPointContainerImpl<rowset-name>` und `IRowsetNotifyCP<rowset-name>` hinzufügen.

Hier ist beispielsweise die Vererbungs Kette für `RUpdateRowset` in [Update](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)Panel:

> [!NOTE]
> Der Beispielcode unterscheidet sich möglicherweise vom hier gezeigten Code. Betrachten Sie den Beispielcode als die aktuellere Codeversion.

```cpp
///////////////////////////////////////////////////////////////////////////
// class RUpdateRowset (in rowset.h)

class RUpdateRowset :
public CRowsetImpl< RUpdateRowset, CAgentMan, CUpdateCommand,
         CAtlArray< CAgentMan, CAtlArray<CAgentMan>>, CSimpleRow,
         IRowsetScrollImpl< RUpdateRowset, IRowsetScroll >>,
      public IRowsetUpdateImpl< RUpdateRowset, CAgentMan >,
      public IConnectionPointContainerImpl<RUpdateRowset>,
      public IRowsetNotifyCP<RUpdateRowset>
```

### <a name="setting-com-map-entries"></a>Festlegen von com-Zuordnungs Einträgen

Außerdem müssen Sie der com-Zuordnung in Ihrem Rowset Folgendes hinzufügen:

```cpp
COM_INTERFACE_ENTRY(IConnectionPointContainer)
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)
```

Diese Makros ermöglichen allen Benutzern, die `QueryInterface` für den Verbindungspunkt Container aufrufen (Basis `IRowsetNotify`), die angeforderte Schnittstelle für Ihren Anbieter zu finden. Ein Beispiel für die Verwendung von Verbindungs Punkten finden Sie im ATL POLYGON-Beispiel und im Tutorial.

### <a name="setting-connection-point-map-entries"></a>Festlegen von Zuordnungs Einträgen für Verbindungspunkte

Außerdem müssen Sie eine Karte für den Verbindungspunkt hinzufügen. Dies sollte etwa wie folgt aussehen:

```cpp
BEGIN_CONNECTION_POINT_MAP(rowset-name)
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))
END_CONNECTION_POINT_MAP()
```

Diese Verbindungspunkt Zuordnung ermöglicht einer Komponente, die nach der `IRowsetNotify`-Schnittstelle sucht, Sie in Ihrem Anbieter zu finden.

### <a name="setting-properties"></a>Festlegen von Eigenschaften

Außerdem müssen Sie dem Anbieter die folgenden Eigenschaften hinzufügen. Sie müssen die Eigenschaften nur auf Basis der von Ihnen unterstützten Schnittstellen hinzufügen.

|Eigenschaft|Hinzufügen bei Unterstützung von|
|--------------|------------------------|
|DBPROP_IConnectionPointContainer|Always|
|DBPROP_NOTIFICATIONGRANULARITY|Always|
|DBPROP_NOTIFICATIONPHASES|Always|
|DBPROP_NOTIFYCOLUMNSET|`IRowsetChange`|
|DBPROP_NOTIFYROWDELETE|`IRowsetChange`|
|DBPROP_NOTIFYROWINSERT|`IRowsetChange`|
|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|Always|
|DBPROP_NOTIFYROWFIRSTCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWSETRELEASE|Always|
|DBPROP_NOTIFYROWUNDOCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDODELETE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDOINSERT|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUPDATE|`IRowsetUpdate`|

Der größte Teil der Implementierung für die Benachrichtigungen ist bereits in die OLE DB Anbieter Vorlagen eingebettet. Wenn Sie Ihrer Vererbungs Kette `IRowsetNotifyCP` nicht hinzufügen, entfernt der Compiler den gesamten Code aus dem Kompilierungs Datenstrom, wodurch die Codegröße kleiner wird.

## <a name="see-also"></a>Weitere Informationen

[Erweiterte Anbietertechniken](../../data/oledb/advanced-provider-techniques.md)
