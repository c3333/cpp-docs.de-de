---
title: 'Transaktion: Auswirkungen von Transaktionen auf Aktualisierungen (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
ms.openlocfilehash: 8a87176ecb20beaf46583e1190b0ad458d508b31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376425"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>Transaktion: Auswirkungen von Transaktionen auf Aktualisierungen (ODBC)

Aktualisierungen der [Datenquelle](../../data/odbc/data-source-odbc.md) werden während Transaktionen mithilfe eines Bearbeitungspuffers (der gleichen Methode, die außerhalb von Transaktionen verwendet wird) verwaltet. Die Felddatenmember eines Recordsets dienen zusammen als Bearbeitungspuffer, der den aktuellen Datensatz enthält, `AddNew` `Edit`den das Recordset während eines oder vorübergehend zurückhält. Während `Delete` eines Vorgangs wird der aktuelle Datensatz nicht innerhalb einer Transaktion gesichert. Weitere Informationen zum Bearbeitungspuffer und zum Speichern des aktuellen Datensatzes durch Updates finden Sie unter [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

> [!NOTE]
> Wenn Sie das Abrufen von Massenzeilen `AddNew` `Edit`implementiert `Delete`haben, können Sie , oder aufrufen. Sie müssen stattdessen eigene Funktionen schreiben, um Aktualisierungen an der Datenquelle durchzuführen. Weitere Informationen zum Abrufen von Massenzeilen finden Sie unter [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Während Transaktionen `AddNew`können `Edit`, `Delete` und Vorgänge festgeschrieben oder zurückgesetzt werden. Die Auswirkungen `CommitTrans` `Rollback` des aktuellen Datensatzes und können dazu führen, dass der aktuelle Datensatz nicht im Bearbeitungspuffer wiederhergestellt wird. Um sicherzustellen, dass der aktuelle Datensatz ordnungsgemäß wiederhergestellt wird, ist `CDatabase` es wichtig zu `CRecordset`verstehen, wie die `CommitTrans` und `Rollback` Memberfunktionen von arbeiten mit den Aktualisierungsfunktionen von .

## <a name="how-committrans-affects-updates"></a><a name="_core_how_committrans_affects_updates"></a>Auswirkungen von CommitTrans auf Updates

In der folgenden Tabelle `CommitTrans` werden die Auswirkungen von Transaktionen erläutert.

### <a name="how-committrans-affects-updates"></a>Auswirkungen von CommitTrans auf Updates

|Vorgang|Status der Datenquelle|
|---------------|---------------------------|
|`AddNew`und `Update`, und dann`CommitTrans`|Neue Datensätze werden der Datenquelle hinzugefügt.|
|`AddNew`(ohne `Update`), und dann`CommitTrans`|Neuer Rekord geht verloren. Datensatz, der der Datenquelle nicht hinzugefügt wurde.|
|`Edit`und `Update`, und dann`CommitTrans`|Bearbeitungen, die an die Datenquelle gebunden sind.|
|`Edit`(ohne `Update`), und dann`CommitTrans`|Bearbeitungen des Datensatzes gehen verloren. Der Datensatz bleibt in der Datenquelle unverändert.|
|`Delete`Dann`CommitTrans`|Datensätze, die aus der Datenquelle gelöscht wurden.|

## <a name="how-rollback-affects-transactions"></a><a name="_core_how_rollback_affects_updates"></a>Auswirkungen des Rollbacks auf Transaktionen

In der folgenden Tabelle `Rollback` werden die Auswirkungen von Transaktionen erläutert.

### <a name="how-rollback-affects-transactions"></a>Auswirkungen des Rollbacks auf Transaktionen

|Vorgang|Status des aktuellen Datensatzes|Sie müssen auch|Status der Datenquelle|
|---------------|------------------------------|-------------------|---------------------------|
|`AddNew`und `Update`, dann`Rollback`|Der Inhalt des aktuellen Datensatzes wird vorübergehend gespeichert, um Platz für einen neuen Datensatz zu schaffen. Ein neuer Datensatz wird in den Bearbeitungspuffer eingegeben. Nach `Update` dem Aufruf wird der aktuelle Datensatz im Bearbeitungspuffer wiederhergestellt.||Das Hinzufügen zur `Update` Datenquelle, die durch gemacht wird, wird umgekehrt.|
|`AddNew`(ohne `Update`), dann`Rollback`|Der Inhalt des aktuellen Datensatzes wird vorübergehend gespeichert, um Platz für einen neuen Datensatz zu schaffen. Der Bearbeitungspuffer enthält einen neuen Datensatz.|Rufen `AddNew` Sie erneut auf, um den Bearbeitungspuffer in einem leeren, neuen Datensatz wiederherzustellen. Oder `Move`rufen Sie (0) auf, um die alten Werte im Bearbeitungspuffer wiederherzustellen.|Da `Update` nicht aufgerufen wurde, wurden keine Änderungen an der Datenquelle vorgenommen.|
|`Edit`und `Update`, dann`Rollback`|Eine unbearbeitete Version des aktuellen Datensatzes wird temporär gespeichert. Der Inhalt des Bearbeitungspuffers wird bearbeitet. Nach `Update` dem Aufruf wird die unbearbeitete Version des Datensatzes weiterhin temporär gespeichert.|*Dynaset*: Scrollen Sie den aktuellen Datensatz und dann wieder, um die unbearbeitete Version des Datensatzes im Bearbeitungspuffer wiederherzustellen.<br /><br /> *Snapshot*: `Requery` Aufruf zum Aktualisieren des Recordsets aus der Datenquelle.|Änderungen an der `Update` Datenquelle, die von vorgenommen wurden, werden rückgängig gemacht.|
|`Edit`(ohne `Update`), dann`Rollback`|Eine unbearbeitete Version des aktuellen Datensatzes wird temporär gespeichert. Der Inhalt des Bearbeitungspuffers wird bearbeitet.|Rufen `Edit` Sie erneut auf, um die unbearbeitete Version des Datensatzes im Bearbeitungspuffer wiederherzustellen.|Da `Update` nicht aufgerufen wurde, wurden keine Änderungen an der Datenquelle vorgenommen.|
|`Delete`Dann`Rollback`|Der Inhalt des aktuellen Datensatzes wird gelöscht.|Rufen `Requery` Sie auf, um den Inhalt des aktuellen Datensatzes aus der Datenquelle wiederherzustellen.|Das Löschen von Daten aus der Datenquelle wird rückgängig gemacht.|

## <a name="see-also"></a>Siehe auch

[Transaktion (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[CDatabase-Klasse](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)
