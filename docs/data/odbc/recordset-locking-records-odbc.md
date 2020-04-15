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
ms.openlocfilehash: abd5f817ad321241df2d8565bd6bf346c0792088
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366964"
---
# <a name="recordset-locking-records-odbc"></a>Recordset: Sperren von Datensätzen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird Folgendes erläutert:

- [Die Arten der Datensatzsperrung verfügbar](#_core_record.2d.locking_modes).

- [So sperren Sie Datensätze in Ihrem Recordset während der Aktualisierungen](#_core_locking_records_in_your_recordset).

Wenn Sie ein Recordset verwenden, um einen Datensatz in der Datenquelle zu aktualisieren, kann die Anwendung den Datensatz sperren, sodass kein anderer Benutzer den Datensatz gleichzeitig aktualisieren kann. Der Status eines Datensatzes, der von zwei Benutzern gleichzeitig aktualisiert wird, ist nicht definiert, es sei denn, das System kann garantieren, dass zwei Benutzer einen Datensatz nicht gleichzeitig aktualisieren können.

> [!NOTE]
> Dieses Thema bezieht sich auf von `CRecordset` abgeleitete Objekte, in denen das gesammelte Abrufen von Zeilen nicht implementiert wurde. Wenn Sie das Abrufen von Massenzeilen implementiert haben, gelten einige der Informationen nicht. Sie können z. `Edit` B. die und `Update` Memberfunktionen nicht aufrufen. Weitere Informationen zum Abrufen von Massenzeilen finden Sie unter [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="record-locking-modes"></a><a name="_core_record.2d.locking_modes"></a>Record-Locking-Modi

Die Datenbankklassen bieten zwei [Datensatzsperrmodi:](../../mfc/reference/crecordset-class.md#setlockingmode)

- Optimistische Sperrung (Standard)

- Pessimistische Verriegelung

Das Aktualisieren eines Datensatzes erfolgt in drei Schritten:

1. Sie beginnen den Vorgang, indem Sie die [Funktion Member bearbeiten](../../mfc/reference/crecordset-class.md#edit) aufrufen.

1. Sie ändern die entsprechenden Felder des aktuellen Datensatzes.

1. Sie beenden den Vorgang – und übertragen [Update](../../mfc/reference/crecordset-class.md#update) normalerweise die Aktualisierung – indem Sie die Update-Memberfunktion aufrufen.

Die optimistische Sperrung sperrt den `Update` Datensatz auf der Datenquelle nur während des Aufrufs. Wenn Sie eine optimistische Sperrung in einer Mehrbenutzerumgebung verwenden, sollte die Anwendung eine `Update` Fehlerbedingung verarbeiten. Pessimistische sperren den Datensatz, sobald `Edit` Sie aufrufen, und `Update` geben ihn erst `CDBException` los, wenn Sie aufrufen (Fehler werden durch den Mechanismus angezeigt, nicht durch einen Von `Update`zurückgegebenen Wert von FALSE ). Pessimistische sperren hat eine potenzielle Leistungseinbußen für andere Benutzer, da gleichzeitiger Zugriff auf `Update` denselben Datensatz möglicherweise bis zum Abschluss des Anwendungsprozesses warten muss.

## <a name="locking-records-in-your-recordset"></a><a name="_core_locking_records_in_your_recordset"></a>Sperren von Datensätzen in Ihrem Recordset

Wenn Sie den [Sperrmodus](#_core_record.2d.locking_modes) eines Recordset-Objekts von der Standardeinstellung ändern `Edit`möchten, müssen Sie den Modus ändern, bevor Sie aufrufen.

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>So ändern Sie den aktuellen Sperrmodus für Ihr Recordset

1. Rufen Sie die [SetLockingMode-Memberfunktion](../../mfc/reference/crecordset-class.md#setlockingmode) auf und geben Sie entweder `CRecordset::pessimistic` oder `CRecordset::optimistic`an.

Der neue Sperrmodus bleibt so lange in Kraft, bis Sie ihn erneut ändern oder das Recordset geschlossen wird.

> [!NOTE]
> Relativ wenige ODBC-Treiber unterstützen derzeit pessimistische Sperren.

## <a name="see-also"></a>Siehe auch

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Ausführen einer Verknüpfung (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[Recordset: Hinzufügen, Aktualisieren und Löschen von Datensätzen (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
