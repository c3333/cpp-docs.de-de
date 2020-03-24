---
title: Herstellen einer Verbindung mit einer Datenquelle
ms.date: 11/04/2016
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
ms.openlocfilehash: 712910aca2622f2678b8b9d06b18a2fdbf9157e4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213342"
---
# <a name="connecting-to-a-data-source"></a>Herstellen einer Verbindung mit einer Datenquelle

Eine ODBC-Datenquelle ist eine bestimmte Gruppe von Daten, die für den Zugriff auf diese Daten erforderlichen Informationen und der Speicherort der Datenquelle, die mit einem Datenquellen Namen beschrieben werden kann. Aus Sicht des Programms enthält die Datenquelle die Daten, das DBMS, das Netzwerk (sofern vorhanden) und ODBC.

Um auf Daten zuzugreifen, die von einer Datenquelle bereitgestellt werden, muss das Programm zuerst eine Verbindung mit der Datenquelle herstellen. Der gesamte Datenzugriff wird über diese Verbindung verwaltet.

Datenquellen Verbindungen werden durch die [CDatabase](../../mfc/reference/cdatabase-class.md)-Klasse gekapselt. Wenn ein `CDatabase`-Objekt mit einer Datenquelle verbunden ist, haben Sie folgende Möglichkeiten:

- Erstellen von [Recordsets](../../mfc/reference/crecordset-class.md), bei denen Datensätze aus Tabellen oder Abfragen ausgewählt werden.

- Verwalten von [Transaktionen](../../data/odbc/transaction-odbc.md), Batch Verarbeitung von Updates, damit alle auf einmal an die Datenquelle übertragen werden (oder für die gesamte Transaktion wird ein Rollback ausgeführt, sodass die Datenquelle unverändert ist) –, wenn die Datenquelle die erforderliche Transaktionsebene unterstützt.

- [SQL](../../data/odbc/sql.md) -Anweisungen direkt ausführen.

Wenn Sie mit der Arbeit mit einer Datenquellen Verbindung fertig sind, schließen Sie das `CDatabase`-Objekt, und zerstören Sie es entweder, oder verwenden Sie es für eine neue Verbindung. Weitere Informationen zu Datenquellen Verbindungen finden Sie unter [Datenquelle (ODBC)](../../data/odbc/data-source-odbc.md).

## <a name="see-also"></a>Weitere Informationen

[ODBC und MFC](../../data/odbc/odbc-and-mfc.md)
