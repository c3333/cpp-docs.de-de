---
title: ATL-Datenbankklassen (OLE DB-Vorlagen)
ms.date: 05/02/2019
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
ms.openlocfilehash: 5b13a27540b12e7ac1503fbf7cd0e1fe396ce8c8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501888"
---
# <a name="atl-database-classes-ole-db-templates"></a>ATL-Datenbankklassen (OLE DB-Vorlagen)

Microsoft bietet mehrere Implementierungen von OLE DB, eine Reihe von COM-Schnittstellen, die den einheitlichen Zugriff auf Daten in verschiedenen Informationsquellen und-Formaten ermöglichen.

Die OLE DB Vorlagen sind C++-Vorlagen in ATL, die die Verwendung OLE DB Datenbanktechnologie vereinfachen, indem Sie Klassen bereitstellen, die viele der häufig verwendeten OLE DB-Schnittstellen implementieren.

Diese Vorlagen Bibliothek enthält zwei Komponenten:

- [OLE DB von Consumer-Vorlagen](../data/oledb/ole-db-consumer-templates-cpp.md) Wird verwendet, um eine OLE DB Client Anwendung (Consumer) zu implementieren.

- [OLE DB Anbieter Vorlagen](../data/oledb/ole-db-provider-templates-cpp.md) Wird verwendet, um eine OLE DB Server-Anwendung (Anbieter) zu implementieren.

Außerdem stellen die [OLE DB Consumer-Attribute](../windows/attributes/ole-db-consumer-attributes.md) eine bequeme Möglichkeit zum Erstellen von OLE DB Consumern dar. Die OLE DB Attribute fügen Code auf Grundlage der OLE DB Consumervorlagen ein, um funktionierende OLE DB Consumer zu erstellen.

Beachten Sie, dass die MFC-Bibliothek eine Klasse ( [COleDBRecordView](../mfc/reference/coledbrecordview-class.md)) enthält, die Datenbankdaten Sätze in Steuerelementen anzeigt. Die Ansicht ist eine Formularansicht, die direkt mit einem `CRowset` -Objekt verbunden ist, und zeigt die Felder des `CRowset` -Objekts in den Steuerelementen der Dialogfeld Vorlage an.

Weitere Informationen finden Sie unter [OLE DB Programming](../data/oledb/ole-db-programming.md) and [OLE DB Programmer es Guide](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

## <a name="see-also"></a>Weitere Informationen

[Erstellen eines OLE DB Consumers](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[Erstellen eines OLE DB Anbieters](../data/oledb/creating-an-ole-db-provider.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Referenz zu OLE DB Anbieter Vorlagen](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Beispiele für OLE DB Vorlagen](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB)
