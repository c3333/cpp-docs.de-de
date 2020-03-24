---
title: Empfangen von Benachrichtigungen
ms.date: 10/24/2018
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- receiving notifications in OLE DB
- events [C++], notifications in OLE DB
- notifications [C++], events
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB providers, notifications
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
ms.openlocfilehash: 4b630a9728770a5e35e6d6300cf465b90238350c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209780"
---
# <a name="receiving-notifications"></a>Empfangen von Benachrichtigungen

OLE DB stellt Schnittstellen zum Empfangen von Benachrichtigungen bereit, wenn Ereignisse auftreten. Diese werden in [OLE DB Objekt Benachrichtigungen](/previous-versions/windows/desktop/ms725406(v=vs.85)) in der **OLE DB Programmierer-Referenz**beschrieben. Das Setup dieser Ereignisse verwendet den Standard-com-Verbindungspunkt Mechanismus. Beispielsweise implementiert ein ATL-Objekt, das Ereignisse über `IRowsetNotify` abrufen möchte, die `IRowsetNotify`-Schnittstelle, indem der von der Klasse abgeleiteten Liste `IRowsetNotify` hinzugefügt und durch ein COM_INTERFACE_ENTRY Makro verfügbar gemacht wird.

`IRowsetNotify` verfügt über drei Methoden, die zu verschiedenen Zeitpunkten aufgerufen werden können. Wenn Sie nur auf eine dieser Methoden reagieren möchten, können Sie die [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) -Klasse verwenden, die E_NOTIMPL für die Methoden zurückgibt, an denen Sie nicht interessiert sind.

Wenn Sie das Rowset erstellen, müssen Sie dem Anbieter mitteilen, dass das zurückgegebene Rowsetobjekt `IConnectionPointContainer`unterstützen soll, das zum Einrichten der Benachrichtigung erforderlich ist.

Der folgende Code zeigt, wie Sie das Rowset aus einem ATL-Objekt öffnen und die-`AtlAdvise`-Funktion verwenden, um die Benachrichtigungs Senke einzurichten. `AtlAdvise` gibt ein Cookie zurück, das beim Abrufen von `AtlUnadvise`verwendet wird.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_IConnectionPointContainer, true);
```

Anschließend wird der folgende Code verwendet:

```cpp
product.Open(session, _T("Products"), &propset);

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);
```

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Zugriffsmethoden](../../data/oledb/using-accessors.md)
