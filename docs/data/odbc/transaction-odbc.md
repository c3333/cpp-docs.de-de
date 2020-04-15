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
ms.openlocfilehash: 56629f8c5ff74aff4e0df589cda1e7b988fb5fd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376414"
---
# <a name="transaction-odbc"></a>Transaktion (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

Eine Transaktion ist eine Möglichkeit, eine Reihe von Aktualisierungen an einer [Datenquelle](../../data/odbc/data-source-odbc.md) zu gruppieren oder zu stapeln, sodass alle gleichzeitig festgeschrieben werden oder keine festgeschrieben werden, wenn Sie die Transaktion zurücksetzen. Wenn Sie keine Transaktion verwenden, werden Änderungen an der Datenquelle automatisch festgeschrieben, anstatt bei Bedarf festgeschrieben zu werden.

> [!NOTE]
> Nicht alle ODBC-Datenbanktreiber unterstützen Transaktionen. Rufen `CanTransact` Sie die Memberfunktion Ihres [CDatabase-](../../mfc/reference/cdatabase-class.md) oder [CRecordset-Objekts](../../mfc/reference/crecordset-class.md) auf, um zu bestimmen, ob Ihr Treiber Transaktionen für eine bestimmte Datenbank unterstützt. Beachten `CanTransact` Sie, dass Sie nicht darüber informiert werden, ob die Datenquelle vollständige Transaktionsunterstützung bietet. Sie müssen `CDatabase::GetCursorCommitBehavior` auch `CDatabase::GetCursorRollbackBehavior` `CommitTrans` aufrufen `Rollback` und nach und nach die `CRecordset` Auswirkungen der Transaktion auf das offene Objekt überprüfen.

Aufrufe der `AddNew` `Edit` und Memberfunktionen `CRecordset` eines Objekts wirken sich `Update`sofort auf die Datenquelle aus, wenn Sie aufrufen. `Delete`Anrufe werden ebenfalls sofort wirksam. Im Gegensatz dazu können Sie eine Transaktion `AddNew` `Edit`verwenden, die aus mehreren Aufrufen von , , `Update`und `Delete`, besteht, die ausgeführt, aber erst dann festgeschrieben werden, wenn Sie explizit aufrufen. `CommitTrans` Durch das Einrichten einer Transaktion können Sie eine Reihe solcher Aufrufe ausführen, während Sie die Möglichkeit behalten, sie zurückzusetzen. Wenn eine kritische Ressource nicht verfügbar ist oder eine andere Bedingung verhindert, dass die gesamte Transaktion abgeschlossen wird, können Sie ein Rollback für die Transaktion ein. In diesem Fall wirkt sich keine der änderungen, die zur Transaktion gehören, auf die Datenquelle aus.

> [!NOTE]
> Derzeit unterstützt `CRecordset` die Klasse keine Aktualisierungen der Datenquelle, wenn Sie das Abrufen von Massenzeilen implementiert haben. Dies bedeutet, dass `AddNew` `Edit`Sie `Delete`keine `Update`Aufrufe von , , oder tätigen können. Sie können jedoch eigene Funktionen schreiben, um Aktualisierungen durchzuführen, und diese Funktionen dann innerhalb einer bestimmten Transaktion aufrufen. Weitere Informationen zum Abrufen von Massenzeilen finden Sie unter [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
> Neben der Auswirkung auf Ihr Recordset wirken sich Transaktionen auf SQL-Anweisungen aus, `CDatabase` die Sie direkt ausführen, solange Sie den ODBC **HDBC** verwenden, der Ihrem Objekt zugeordnet ist, oder ein ODBC **HSTMT,** das auf **diesem HDBC**basiert.

Transaktionen sind besonders nützlich, wenn Sie über mehrere Datensätze verfügen, die gleichzeitig aktualisiert werden müssen. In diesem Fall möchten Sie eine halb abgeschlossene Transaktion vermeiden, z. B. wenn eine Ausnahme ausgelöst wurde, bevor die letzte Aktualisierung durchgeführt wurde. Das Gruppieren solcher Aktualisierungen in eine Transaktion ermöglicht eine Wiederherstellung (Rollback) aus den Änderungen und gibt die Datensätze in den Vortransaktionsstatus zurück. Wenn z. B. eine Bank Geld von Konto A auf Konto B überweist, müssen sowohl die Auszahlung von A als auch die Einzahlung an B erfolgreich sein, um die Gelder korrekt zu verarbeiten, oder die gesamte Transaktion muss fehlschlagen.

In den Datenbankklassen führen Sie `CDatabase` Transaktionen über Objekte aus. Ein `CDatabase` Objekt stellt eine Verbindung zu einer Datenquelle dar, `CDatabase` und ein oder mehrere Recordsets, die diesem Objekt zugeordnet sind, arbeiten über Recordset-Memberfunktionen auf Tabellen der Datenbank.

> [!NOTE]
> Es wird nur eine Transaktionsebene unterstützt. Sie können keine Transaktionen verschachteln, und eine Transaktion kann sich auch nicht über mehrere Datenbankobjekte erstrecken.

Die folgenden Themen enthalten weitere Informationen zur Art und Weise, wie Transaktionen ausgeführt werden:

- [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [Transaktion: Auswirkungen von Transaktionen auf Aktualisierungen (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>Siehe auch

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
