---
title: Transaktionen (MFC-Datenzugriff)
ms.date: 11/04/2016
helpviewer_keywords:
- transactions [C++], support for
- transactions [C++]
- databases [C++], transactions
ms.assetid: f80afbfe-1517-4fec-8870-9ffc70a58b05
ms.openlocfilehash: 742e95d896d107fb89b3d65f0eeb6d418f1b2057
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209065"
---
# <a name="transactions--mfc-data-access"></a>Transaktionen (MFC-Datenzugriff)

Das Konzept der Transaktionen wurde entwickelt, um Fälle zu behandeln, in denen der resultierende Status der Datenbank vom Gesamterfolg einer Reihe von Operationen abhängt. Dieses könnte vorkommen, da aufeinander folgende Operationen die Ergebnisse von vorangegangenen Operationen ändern können. Wenn eine der Operationen fehlschlägt, kann der resultierende Status in solchen Fällen unbestimmt sein.

Um dieses Problem zu lösen, gruppieren die Transaktionen eine Reihe von Operationen so, dass die Integrität des Endergebnisses sichergestellt werden kann. Alle Operationen müssen erfolgreich sein, und anschließend muss ein Commit ausgeführt werden (Schreiben in die Datenbank), oder die ganze Transaktion schägt fehl. Der Abbruch einer Transaktion wird als Rollback bezeichnet. Rollbacks ermöglichen die Wiederherstellung von Änderungen, und die Datenbank wird in den Zustand versetzt, der vor der Transaktion vorhanden war.

Wenn Sie beispielsweise bei einer automatisierten Banküberweisung Geld von Konto A auf Konto B übertragen, muss sowohl die Abbuchung von Konto A als auch die Einzahlung auf Konto B erfolgreich sein, damit die Überweisung fehlerfrei erfolgt, oder die ganze Transaktion schlägt fehl.

Eine Transaktion muss über ACID-Eigenschaften verfügen, die für Folgendes stehen:

- **Atomizität** Eine Transaktion ist eine atomarische Arbeitseinheit und wird genau einmal ausgeführt. entweder ist alles erledigt, oder es ist kein Vorgang.

- **Konsistenz** Eine Transaktion behält die Konsistenz der Daten bei und transformiert einen konsistenten Zustand von Daten in einen anderen konsistenten Daten Zustand. Durch eine Transaktion gebundene Daten müssen semantisch erhalten bleiben.

- **Isolation** Eine Transaktion ist eine Isolationseinheit, die jeweils separat und unabhängig von gleichzeitigen Transaktionen erfolgt. Eine Transaktion sollte nie die Zwischenschritte einer anderen Transaktion sehen.

- **Dauerhaftigkeit** Eine Transaktion ist eine Wiederherstellungs Einheit. Wenn eine Transaktion erfolgreich ausgeführt wird, werden die entsprechenden Aktualisierungen beibehalten, auch wenn das System abstürzt oder heruntergefahren wird. Schlägt eine Transaktion fehl, verbleibt das System in dem Zustand, der vor der Ausführung eines Commit für die Transaktion vorhanden war.

Sie können Transaktionen in OLE DB (siehe [unterstützende Transaktionen in OLE DB](../data/oledb/supporting-transactions-in-ole-db.md)) oder ODBC unterstützen (siehe [Transaktion (ODBC)](../data/odbc/transaction-odbc.md)).

Eine verteilte Transaktion ist eine Transaktion, die verteilte Daten aktualisiert. Dabei handelt es sich also um Daten, die sich auf mehreren vernetzten Computersystemen befinden. Wenn Sie Transaktionen über ein verteiltes System unterstützen möchten, sollten Sie anstelle der OLE DB Transaktionsunterstützung ADO.NET verwenden.

## <a name="see-also"></a>Weitere Informationen

[Datenzugriffsprogrammierung (MFC/ATL)](../data/data-access-programming-mfc-atl.md)
