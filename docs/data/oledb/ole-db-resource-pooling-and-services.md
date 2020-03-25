---
title: OLE DB-Ressourcenpooling und -Dienste
ms.date: 10/29/2018
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
ms.openlocfilehash: 67eeffff2bf165a5ccbdbaa546ad5b9ca9a57914
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210027"
---
# <a name="ole-db-resource-pooling-and-services"></a>OLE DB-Ressourcenpooling und -Dienste

Damit Sie gut mit OLE DB Pooling oder mit einem beliebigen OLE DB Dienst zusammenarbeiten können, muss der Anbieter die Aggregation aller Objekte unterstützen. Dies ist eine Voraussetzung für alle OLE DB 1,5-Anbieter oder höher. Es ist wichtig für die Nutzung von Diensten. Anbieter, die keine Aggregationen unterstützen, können nicht in einem Pool zusammengefasst werden.

Um in einem Pool zusammengefasst zu werden, müssen Anbieter das kostenlose Thread Modell unterstützen. Der Ressourcenpool bestimmt das Thread Modell des Anbieters entsprechend der DBPROP_THREADMODEL-Eigenschaft.

Wenn der Anbieter über einen globalen Verbindungsstatus verfügt, der sich ändern kann, während sich die Datenquelle in einem initialisierten Zustand befindet, sollte Sie die neue DBPROP_RESETDATASOURCE-Eigenschaft unterstützen. Diese Eigenschaft wird aufgerufen, bevor eine Verbindung wieder verwendet wird, und gibt dem Anbieter die Möglichkeit, den Zustand vor der nächsten Verwendung zu bereinigen. Wenn der Anbieter einen Zustand, der der Verbindung zugeordnet ist, nicht bereinigen kann, kann er DBPROPSTATUS_NOTSETTABLE für die Eigenschaft zurückgeben, und die Verbindung wird nicht wieder verwendet.

Anbieter, die eine Verbindung mit einer Remote Datenbank herstellen und erkennen können, ob diese Verbindung möglicherweise verloren geht, sollten die DBPROP_CONNECTIONSTATUS-Eigenschaft unterstützen. Diese Eigenschaft gibt dem OLE DB-Diensten die Möglichkeit, unzustellbare Verbindungen zu erkennen und sicherzustellen, dass Sie nicht an den Pool zurückgegeben werden.

Zum Schluss funktioniert die automatische Transaktions Eintragung in der Regel nur, wenn Sie auf der gleichen Ebene wie das Pooling implementiert wird. Anbieter, die die automatische Transaktions Eintragung unterstützen, sollten die Deaktivierung dieser Eintragung unterstützen, indem Sie die DBPROP_INIT_OLEDBSERVICES-Eigenschaft verfügbar machen und die Eintragung deaktivieren, wenn die DBPROPVAL_OS_TXNENLISTMENT deaktiviert wird.

## <a name="see-also"></a>Weitere Informationen

[Erweiterte Anbietertechniken](../../data/oledb/advanced-provider-techniques.md)
