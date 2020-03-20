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
ms.openlocfilehash: d03ec3f71c38f7790d66fbf6f800b7647e080147
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "79544423"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>Transaktion: Auswirkungen von Transaktionen auf Aktualisierungen (ODBC)

Aktualisierungen an der [Datenquelle](../../data/odbc/data-source-odbc.md) werden während der Transaktionen durch die Verwendung eines Bearbeitungs Puffers (dieselbe Methode, die außerhalb der Transaktionen verwendet wird) verwaltet. Die Felddatenmember eines Recordsets fungieren kollektiv als Bearbeitungs Puffer, der den aktuellen Datensatz enthält, den das Recordset während einer `AddNew` oder `Edit`vorübergehend sichert. Während eines `Delete` Vorgangs wird der aktuelle Datensatz nicht innerhalb einer Transaktion gesichert. Weitere Informationen zum Bearbeitungs Puffer und zum Speichern des aktuellen Datensatzes durch Updates finden Sie unter [Recordset: Wie Recordsets Datensätze aktualisieren (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

> [!NOTE]
>  Wenn Sie das Massen Abrufen von Zeilen implementiert haben, können Sie `AddNew`, `Edit`oder `Delete`nicht aufzurufen. Stattdessen müssen Sie eigene Funktionen schreiben, um Updates für die Datenquelle auszuführen. Weitere Informationen zum Abrufen von Massen Zeilen finden Sie unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Während der Transaktionen können für `AddNew`, `Edit`und `Delete` Vorgänge ein Commit oder ein Rollback ausgeführt werden. Die Auswirkungen von `CommitTrans` und `Rollback` können dazu führen, dass der aktuelle Datensatz nicht im Bearbeitungs Puffer wieder hergestellt wird. Um sicherzustellen, dass der aktuelle Datensatz ordnungsgemäß wieder hergestellt wird, ist es wichtig zu verstehen, wie die Funktionen `CommitTrans` und `Rollback` Member von `CDatabase` mit den Update Funktionen von `CRecordset`funktionieren.

##  <a name="how-committrans-affects-updates"></a><a name="_core_how_committrans_affects_updates"></a>Auswirkungen von CommitTrans auf Updates

In der folgenden Tabelle werden die Auswirkungen der `CommitTrans` auf Transaktionen erläutert.

### <a name="how-committrans-affects-updates"></a>Auswirkungen von CommitTrans auf Updates

|Vorgang|Status der Datenquelle|
|---------------|---------------------------|
|`AddNew` und `Update`und dann `CommitTrans`|Der Datenquelle wird ein neuer Datensatz hinzugefügt.|
|`AddNew` (ohne `Update`) und dann `CommitTrans`|Der neue Datensatz geht verloren. Der Datensatz wurde nicht der Datenquelle hinzugefügt.|
|`Edit` und `Update`und dann `CommitTrans`|Bearbeitbare Änderungen an der Datenquelle.|
|`Edit` (ohne `Update`) und dann `CommitTrans`|Änderungen an dem Datensatz gehen verloren. Der Datensatz bleibt in der Datenquelle unverändert.|
|`Delete` `CommitTrans`|Aus der Datenquelle gelöschte Datensätze.|

##  <a name="how-rollback-affects-transactions"></a><a name="_core_how_rollback_affects_updates"></a>Auswirkungen des Rollbacks auf Transaktionen

In der folgenden Tabelle werden die Auswirkungen der `Rollback` auf Transaktionen erläutert.

### <a name="how-rollback-affects-transactions"></a>Auswirkungen des Rollbacks auf Transaktionen

|Vorgang|Status des aktuellen Datensatzes|Außerdem müssen Sie|Status der Datenquelle|
|---------------|------------------------------|-------------------|---------------------------|
|`AddNew` und `Update`dann `Rollback`|Der Inhalt des aktuellen Datensatzes wird temporär gespeichert, um Platz für neuen Datensatz zu schaffen. Ein neuer Datensatz wird in den Bearbeitungs Puffer eingegeben. Nachdem `Update` aufgerufen wurde, wird der aktuelle Datensatz im Bearbeitungs Puffer wieder hergestellt.||Das Hinzufügen zu einer durch `Update` vorgenommenen Datenquelle wird umgekehrt.|
|`AddNew` (ohne `Update`), `Rollback`|Der Inhalt des aktuellen Datensatzes wird temporär gespeichert, um Platz für neuen Datensatz zu schaffen. Der Bearbeitungs Puffer enthält einen neuen Datensatz.|Wenden Sie `AddNew` erneut an, um den Bearbeitungs Puffer in einem leeren, neuen Datensatz wiederherzustellen. Oder `Move`(0), um die alten Werte im Bearbeitungs Puffer wiederherzustellen.|Da `Update` nicht aufgerufen wurde, wurden keine Änderungen an der Datenquelle vorgenommen.|
|`Edit` und `Update`dann `Rollback`|Eine nicht bearbeitete Version des aktuellen Datensatzes wird temporär gespeichert. Änderungen werden an dem Inhalt des Bearbeitungs Puffers vorgenommen. Nachdem `Update` aufgerufen wurde, wird die nicht bearbeitete Version des Datensatzes weiterhin temporär gespeichert.|*Dynaset*: Scrollen Sie nach dem aktuellen Datensatz und dann zurück, um die unveränderte Version des Datensatzes in den Bearbeitungs Puffer wiederherzustellen.<br /><br /> *Snapshot*: `Requery` aufgerufen, um das Recordset aus der Datenquelle zu aktualisieren.|Änderungen an der Datenquelle, die von `Update` vorgenommen werden, werden umgekehrt.|
|`Edit` (ohne `Update`), `Rollback`|Eine nicht bearbeitete Version des aktuellen Datensatzes wird temporär gespeichert. Änderungen werden an dem Inhalt des Bearbeitungs Puffers vorgenommen.|Wenden Sie `Edit` erneut an, um die nicht bearbeitete Version des Datensatzes im Bearbeitungs Puffer wiederherzustellen.|Da `Update` nicht aufgerufen wurde, wurden keine Änderungen an der Datenquelle vorgenommen.|
|`Delete` `Rollback`|Der Inhalt des aktuellen Datensatzes wird gelöscht.|Ruft `Requery` auf, um den Inhalt des aktuellen Datensatzes aus der Datenquelle wiederherzustellen.|Das Löschen von Daten aus der Datenquelle wird rückgängig gemacht.|

## <a name="see-also"></a>Siehe auch

[Transaktion (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[CDatabase-Klasse](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)
