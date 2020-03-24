---
title: Transaktion (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
ms.openlocfilehash: 49fc0e244dd4f63bd7a69d963ff2a9fbc00ddb6c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212601"
---
# <a name="transaction-odbc"></a>Transaktion (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

Bei einer Transaktion handelt es sich um eine Möglichkeit, eine Reihe von Aktualisierungen einer [Datenquelle](../../data/odbc/data-source-odbc.md) zu gruppieren oder zu gruppieren, sodass für alle ein Commit ausgeführt wird oder kein Commit ausgeführt wird, wenn ein Rollback für die Transaktion ausgeführt wird. Wenn Sie keine Transaktion verwenden, wird für Änderungen an der Datenquelle automatisch ein Commit ausgeführt, anstatt bei Bedarf ein Commit durchzuführen.

> [!NOTE]
>  Nicht alle ODBC-Datenbanktreiber unterstützen Transaktionen. Verwenden Sie die `CanTransact` Member-Funktion des [CDatabase](../../mfc/reference/cdatabase-class.md) -oder [CRecordset](../../mfc/reference/crecordset-class.md) -Objekts, um zu bestimmen, ob der Treiber Transaktionen für eine bestimmte Datenbank unterstützt. Beachten Sie, dass `CanTransact` nicht mitteilt, ob die Datenquelle vollständige Transaktionsunterstützung bereitstellt. Sie müssen auch `CDatabase::GetCursorCommitBehavior` und `CDatabase::GetCursorRollbackBehavior` nach `CommitTrans` und `Rollback`, um die Auswirkung der Transaktion auf das geöffnete `CRecordset` Objekt zu überprüfen.

Aufrufe der `AddNew`-und `Edit` Member-Funktionen eines `CRecordset`-Objekts wirken sich sofort auf die Datenquelle aus, wenn Sie `Update`aufrufen. `Delete` Aufrufe werden ebenfalls sofort wirksam. Im Gegensatz dazu können Sie eine Transaktion verwenden, die aus mehreren Aufrufen von `AddNew`, `Edit`, `Update`und `Delete`besteht, die ausgeführt werden, aber nicht committet werden, bis Sie `CommitTrans` explizit aufrufen. Durch das Einrichten einer Transaktion können Sie eine Reihe solcher Aufrufe ausführen und gleichzeitig die Möglichkeit behalten, Sie zurückzusetzen. Wenn eine kritische Ressource nicht verfügbar ist oder eine andere Bedingung verhindert, dass die gesamte Transaktion abgeschlossen ist, können Sie die Transaktion zurücksetzen, anstatt Sie zu committen. In diesem Fall wirkt sich keine der Änderungen, die der Transaktion angehören, auf die Datenquelle aus.

> [!NOTE]
>  Derzeit unterstützt Class `CRecordset` keine Updates für die Datenquelle, wenn Sie das Massen Abrufen von Zeilen implementiert haben. Dies bedeutet, dass Sie keine Aufrufe an `AddNew`, `Edit`, `Delete`oder `Update`durchführen können. Sie können jedoch eigene Funktionen schreiben, um Updates auszuführen und diese Funktionen dann innerhalb einer bestimmten Transaktion aufzurufen. Weitere Informationen zum Abrufen von Massen Zeilen finden Sie unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
>  Neben der Auswirkung ihres Recordsets wirken sich Transaktionen auf SQL-Anweisungen aus, die Sie direkt ausführen, solange Sie den ODBC- **hdbc** verwenden, der mit Ihrem `CDatabase`-Objekt verknüpft ist, oder ein ODBC- **hstmt** , das auf diesem **hdbc**basiert

Transaktionen sind besonders nützlich, wenn Sie über mehrere Datensätze verfügen, die gleichzeitig aktualisiert werden müssen. In diesem Fall sollten Sie eine halb abgeschlossene Transaktion vermeiden, z. b. Wenn eine Ausnahme ausgelöst wurde, bevor das letzte Update durchgeführt wurde. Wenn solche Updates in eine Transaktion gruppiert werden, ist eine Wiederherstellung (Rollback) der Änderungen möglich, und die Datensätze werden in den Zustand der vorab Transaktion zurückgesetzt. Wenn eine Bank z. B. Geld von Konto a an Konto B überträgt, muss sowohl die Abbuchung von a als auch die-Übertragung an b erfolgreich sein, damit das Guthaben ordnungsgemäß verarbeitet wird, oder die gesamte Transaktion muss fehlschlagen.

In den Datenbankklassen führen Sie Transaktionen durch `CDatabase`-Objekte aus. Ein `CDatabase`-Objekt stellt eine Verbindung mit einer Datenquelle dar, und ein oder mehrere Recordsets, die diesem `CDatabase`-Objekt zugeordnet sind, werden mithilfe von recordsetmember-Funktionen auf Tabellen der Datenbank angewendet.

> [!NOTE]
>  Es wird nur eine Ebene von Transaktionen unterstützt. Transaktionen können nicht geschachtelt werden, und eine Transaktion kann nicht mehrere Datenbankobjekte umfassen.

Die folgenden Themen enthalten weitere Informationen zur Durchführung von Transaktionen:

- [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [Transaktion: Wie Transaktionen sich auf Aktualisierungen auswirken (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>Weitere Informationen

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
