---
title: 'Recordset: Sperren von Datensätzen (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
ms.openlocfilehash: d4e80816a131c997e9f5bfaa34f025394b05a358
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212861"
---
# <a name="recordset-locking-records-odbc"></a>Recordset: Sperren von Datensätzen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird Folgendes erläutert:

- [Die Arten von Datensatzsperren, die verfügbar sind](#_core_record.2d.locking_modes).

- [So sperren Sie Datensätze im Recordset während der Updates](#_core_locking_records_in_your_recordset).

Wenn Sie ein Recordset zum Aktualisieren eines Datensatzes in der Datenquelle verwenden, kann die Anwendung den Datensatz sperren, sodass kein anderer Benutzer den Datensatz gleichzeitig aktualisieren kann. Der Status eines Datensatzes, der von zwei Benutzern gleichzeitig aktualisiert wird, ist nicht definiert, es sei denn, das System kann garantieren, dass zwei Benutzer einen Datensatz nicht gleichzeitig aktualisieren können.

> [!NOTE]
>  Dieses Thema bezieht sich auf von `CRecordset` abgeleitete Objekte, in denen das gesammelte Abrufen von Zeilen nicht implementiert wurde. Wenn Sie das Massen Abrufen von Zeilen implementiert haben, sind einige der Informationen nicht anwendbar. Beispielsweise können Sie die Funktionen `Edit` und `Update` Member nicht aufzurufen. Weitere Informationen zum Abrufen von Massen Zeilen finden Sie unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="record-locking-modes"></a><a name="_core_record.2d.locking_modes"></a>Daten Satz Sperr Modi

Die Datenbankklassen stellen zwei Daten [Satz Sperr Modi](../../mfc/reference/crecordset-class.md#setlockingmode)bereit:

- Optimistische Sperre (Standard)

- Pessimistische Sperre

Das Aktualisieren eines Datensatzes erfolgt in drei Schritten:

1. Sie beginnen den Vorgang, indem Sie die [Edit](../../mfc/reference/crecordset-class.md#edit) Member-Funktion aufrufen.

1. Sie ändern die entsprechenden Felder des aktuellen Datensatzes.

1. Sie beenden den Vorgang – und commitden Update-– normalerweise durch Aufrufen der [Update](../../mfc/reference/crecordset-class.md#update) Member-Funktion.

Die optimistische Sperre sperrt den Datensatz nur während des `Update` Aufrufens in der Datenquelle. Wenn Sie die vollständige Sperrung in einer mehr Benutzerumgebung verwenden, sollte die Anwendung eine `Update` Fehlerbedingung verarbeiten. Das pessimistische sperren sperrt den Datensatz, sobald Sie `Edit` aufgerufen haben, und gibt ihn erst frei, wenn Sie `Update` aufgerufen haben (Fehler werden durch den `CDBException` Mechanismus angegeben, nicht durch den von `Update`zurückgegebenen Wert false). Das pessimistische sperren weist eine potenzielle Leistungs Einbuße für andere Benutzer auf, da der gleichzeitige Zugriff auf denselben Datensatz möglicherweise bis zum Abschluss des `Update` Prozesses der Anwendung gewartet werden muss.

##  <a name="locking-records-in-your-recordset"></a><a name="_core_locking_records_in_your_recordset"></a>Sperren von Datensätzen in Ihrem Recordset

Wenn Sie den [Sperrmodus](#_core_record.2d.locking_modes) eines Recordset-Objekts von der Standardeinstellung ändern möchten, müssen Sie den Modus ändern, bevor Sie `Edit`aufgerufen haben.

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>So ändern Sie den aktuellen Sperrmodus für das Recordset

1. Aufrufen der [SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode) -Member-Funktion, wobei entweder `CRecordset::pessimistic` oder `CRecordset::optimistic`angegeben wird.

Der neue Sperrmodus bleibt wirksam, bis Sie ihn erneut ändern oder das Recordset geschlossen wird.

> [!NOTE]
>  Relativ wenige ODBC-Treiber unterstützen derzeit die pessimistische Sperrung.

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Ausführen eines Join (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[Recordset: Hinzufügen, Aktualisieren und Löschen von Datensätzen (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
