---
title: Ressourcenpooling in OLE DB-Anwendungen
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
ms.openlocfilehash: 3604f6eaaf0f34a0ff7e54826923c2aa92eef4a2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209768"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>Ressourcenpooling in OLE DB-Anwendungen

Um Pooling in Ihrer Anwendung zu nutzen, müssen Sie sicherstellen, dass OLE DB Dienste aufgerufen werden, indem Sie Ihre Datenquelle über `IDataInitialize` oder `IDBPromptInitialize`erhalten. Wenn Sie `CoCreateInstance` direkt verwenden, um den Anbieter auf der Grundlage der CLSID des Anbieters aufzurufen, werden keine OLE DB Dienste aufgerufen.

Die OLE DB-Dienste behalten Pools verbundener Datenquellen, solange ein Verweis auf `IDataInitialize` oder `IDBPromptInitialize` gespeichert wird oder wenn eine Verbindung verwendet wird. Pools werden auch automatisch innerhalb einer com+ 1,0-Dienste oder Internetinformationsdienste (IIS)-Umgebung verwaltet. Wenn Ihre Anwendung das Pooling außerhalb einer com+ 1,0-Dienste oder IIS-Umgebung nutzt, sollten Sie einen Verweis auf `IDataInitialize` oder auf `IDBPromptInitialize` oder auf mindestens eine Verbindung halten. Um sicherzustellen, dass der Pool nicht zerstört wird, wenn die letzte Verbindung von der Anwendung freigegeben wird, behalten Sie den Verweis bei, oder halten Sie sich für die Lebensdauer Ihrer Anwendung auf die Verbindung.

OLE DB Dienste identifizieren den Pool, aus dem die Verbindung zu dem Zeitpunkt gezeichnet wird, zu dem `Initialize` aufgerufen wird. Nachdem die Verbindung aus einem Pool gezeichnet wurde, kann Sie nicht in einen anderen Pool verschoben werden. Vermeiden Sie daher die Durchführung von Aufgaben in Ihrer Anwendung, die Initialisierungs Informationen ändern, z. b. das Aufrufen von `UnInitialize` oder das Aufrufen von `QueryInterface` für eine anbieterspezifische Schnittstelle vor dem `Initialize`Aufrufen von Außerdem werden Verbindungen mit einem anderen Aufforderungs Wert als DBPROMPT_NOPROMPT nicht in einem Pool zusammengefasst. Die Initialisierungs Zeichenfolge, die von einer mit einer Eingabeaufforderung eingerichteten Verbindung abgerufen wird, kann jedoch verwendet werden, um zusätzliche Pool Verbindungen mit derselben Datenquelle herzustellen.

Einige Anbieter müssen für jede Sitzung eine separate Verbindung herstellen. Diese zusätzlichen Verbindungen müssen separat in der verteilten Transaktion eingetragen werden, sofern vorhanden. In OLE DB Services wird eine einzelne Sitzung pro Datenquelle zwischengespeichert und wieder verwendet. wenn die Anwendung jedoch mehr als eine Sitzung gleichzeitig aus einer einzelnen Datenquelle anfordert, stellt der Anbieter möglicherweise zusätzliche Verbindungen her und durchläuft zusätzliche Transaktions Zustellungen, die nicht in einem Pool zusammengefasst. Es ist effizienter, eine separate Datenquelle für jede Sitzung in einer gepoolten Umgebung zu erstellen, als mehrere Sitzungen aus einer einzelnen Datenquelle zu erstellen.

Da ADO automatisch OLE DB Dienste verwendet, können Sie auch ADO verwenden, um Verbindungen herzustellen, und das Pooling und die Eintragung erfolgen automatisch.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Ressourcenpooling und -Dienste](../../data/oledb/ole-db-resource-pooling-and-services.md)
