---
title: Vorlagen, Attribute und andere Implementierungen von OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
ms.openlocfilehash: 217db304c7d0b5723b7af383e07290f160cc9465
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500916"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>Vorlagen, Attribute und andere Implementierungen von OLE DB

## <a name="atl-ole-db-templates"></a>ATL-OLE DB Vorlagen

Die OLE DB Vorlagen, die Teil von ATL (Active Template Library) sind, erleichtern die Verwendung der leistungsstarken OLE DB Datenbanktechnologie, indem Sie Klassen bereitstellen, die viele der häufig verwendeten OLE DB Schnittstellen implementieren. Zusammen mit dieser Vorlagen Bibliothek wird der Assistent zum Erstellen von OLE DB Starter-Anwendungen unterstützt.

Diese Vorlagen Bibliothek enthält zwei Komponenten:

- **OLE DB von Consumer-Vorlagen** Wird verwendet, um eine OLE DB Client Anwendung (Consumer) zu implementieren.

- **OLE DB Anbieter Vorlagen** Wird verwendet, um eine OLE DB Server-Anwendung (Anbieter) zu implementieren.

Sie sollten mit C++-Vorlagen, COM und den OLE DB-Schnittstellen vertraut sein, um OLE DB-Vorlagen verwenden zu können. Wenn Sie mit OLE DB nicht vertraut sind, finden Sie weitere Informationen unter [OLE DB Programmer es Reference](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

Weitere Informationen finden Sie unter:

- Lesen Sie die Themen über die [OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md) oder [OLE DB Anbieter Vorlagen](../../data/oledb/ole-db-provider-templates-cpp.md).

- Erstellen Sie einen [OLE DB Consumer](../../data/oledb/creating-an-ole-db-consumer.md) oder [OLE DB Anbieter](../../data/oledb/creating-an-ole-db-provider.md).

- Sehen Sie sich die Liste der [OLE DB Consumerklassen](../../data/oledb/ole-db-consumer-templates-reference.md) oder [OLE DB Anbieter Klassen](../../data/oledb/ole-db-provider-templates-reference.md)an.

- Sehen Sie sich die Liste der [OLE DB Vorlagen Beispiele](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB)an.

- Weitere Informationen finden Sie [OLE DB Programmierer-Referenz](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) (in der Windows SDK).

## <a name="ole-db-attributes"></a>OLE DB Attribute

Die [OLE DB Consumerattribute](../../windows/attributes/ole-db-consumer-attributes.md) stellen eine bequeme Möglichkeit zum Erstellen von OLE DB Consumern dar. Die OLE DB Attribute fügen Code auf Grundlage der [OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md) ein, um funktionierende OLE DB-Consumer und-Anbieter zu erstellen. Wenn Sie Funktionen angeben müssen, die von den Attributen nicht unterstützt werden, können Sie die OLE DB Vorlagen in Verbindung mit den Attributen in Ihrem Code verwenden.

## <a name="mfc-ole-db-classes"></a>MFC-OLE DB Klassen

Die MFC-Bibliothek verfügt über eine Klasse, [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), die Datenbankdaten Sätze in Steuerelementen anzeigt. Die Ansicht ist eine Formularansicht, die direkt mit einem `CRowset` -Objekt verbunden ist und die Felder des `CRowset` -Objekts in den Steuerelementen der Dialogfeld Vorlage anzeigt. Außerdem stellt Sie eine Standard Implementierung für den Wechsel zum ersten, nächsten, vorherigen oder letzten Datensatz und eine Schnittstelle zum Aktualisieren des Datensatzes bereit, der derzeit in der Ansicht angezeigt wird. Weitere Informationen finden Sie unter `COleDBRecordView`.

## <a name="ole-db-sdk-interfaces"></a>OLE DB SDK-Schnittstellen

In Fällen, in denen die OLE DB Vorlagen OLE DB Funktionalität nicht unterstützen, müssen Sie die OLE DB Schnittstellen selbst verwenden. Weitere Informationen finden Sie unter [OLE DB Programmierer-Referenz](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) im Windows SDK.

## <a name="see-also"></a>Weitere Informationen

[OLE DB Programmierung](../../data/oledb/ole-db-programming.md)<br/>
[Übersicht über OLE DB Programmierung](../../data/oledb/ole-db-programming-overview.md)
