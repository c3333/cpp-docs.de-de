---
title: Testen des Anbieters
ms.date: 10/29/2018
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
ms.openlocfilehash: b1f068c928abd0a6656bed0702422d9bda843208
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209500"
---
# <a name="testing-your-provider"></a>Testen des Anbieters

Vor dem Freigeben eines Anbieters sollten Sie die folgenden Tests in der angegebenen Reihenfolge ausführen. Diese Tests zeigen, dass der Anbieter für die meisten potenziellen Benutzer ordnungsgemäß funktioniert.

1. Testen Sie den Anbieter mithilfe einer Consumeranwendung, die mit den [OLE DB Consumer-](../../data/oledb/creating-an-ole-db-consumer.md) Vorlagen geschrieben wurde. Der Testconsumer sollte alle Funktionsbereiche Ihres Anbieters abdecken (sämtlichen Code, den Sie hinzugefügt oder geändert haben).

1. Testen Sie den Anbieter mithilfe einer Consumer-Anwendung, die mit ADO geschrieben wurde. Die meisten Entwickler (insbesondere Microsoft Visual Basic und C# Microsoft-Entwickler) verwenden ADO oder ADO.net für Consumer-Anwendungen. Der Testconsumer sollte alle Funktionsbereiche Ihres Anbieters abdecken. Ein Beispiel für eine ADO-Consumeranwendung finden Sie [unter ADO-Code Beispiele in Microsoft Visual Basic](/previous-versions/ms807514(v=msdn.10)).

1. Führen Sie die OLE DB Übereinstimmungs Tests (einschließlich ADO-Konformitätstests) aus, um anzuzeigen, dass Ihr Anbieter den Standardwert der Ebene 0 für OLE DB Anbieter erfüllt. (Eine Erläuterung der Ebene 0 finden Sie in [OLE DB Programmierer-Anleitung](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)nach **OLE DB Konformitäts Tests der Ebene 0** . Diese Tests und die zugehörige Dokumentation sind in C++ Visual im Data Access SDK enthalten. Anhand dieser Tests können Sie auch anzeigen, dass der Anbieter gut ausgeführt wird, wenn er von anderen [Dienstanbietern](../../data/oledb/ole-db-resource-pooling-and-services.md) aggregiert wird. Dies ist besonders nützlich, wenn Sie Eigenschaften ändern oder hinzufügen. Weitere Informationen zu den Konformitätstests finden Sie in der Infodatei für das Datenzugriffs-SDK, das sich auf einer der Visual Studio-CDs befindet.

## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit OLE DB-Anbietervorlagen](../../data/oledb/working-with-ole-db-provider-templates.md)
