---
title: 'Recordset: Erneutes Abfragen eines Recordsets (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
ms.openlocfilehash: cdae28f81eebe8427bc829072e0d9a83c6ec1722
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366943"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Recordset: Erneutes Abfragen eines Recordsets (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird erläutert, wie Sie ein Recordset-Objekt verwenden können, um sich selbst aus der Datenbank erneut zu abfragen (d. h., aktualisieren) und wann Sie dies mit der [Requery-Memberfunktion](../../mfc/reference/crecordset-class.md#requery) tun möchten.

Die Hauptgründe für die erneute Abfrage eines Recordsets sind:

- Bringen Sie das Recordset in Bezug auf Datensätze, die von Ihnen oder anderen Benutzern hinzugefügt wurden, und Datensätze, die von anderen Benutzern gelöscht wurden (die von Ihnen gelöschten Datensätze werden bereits im Recordset widergespiegelt).

- Aktualisieren Sie das Recordset basierend auf sich ändernden Parameterwerten.

## <a name="bringing-the-recordset-up-to-date"></a><a name="_core_bringing_the_recordset_up_to_date"></a>Recordset auf den neuesten Stand bringen

Häufig sollten Sie Das Recordset-Objekt erneut abfragen, um es auf den neuesten Stand zu bringen. In einer Mehrbenutzerdatenbankumgebung können andere Benutzer während der Lebensdauer des Recordsets Änderungen an den Daten vornehmen. Weitere Informationen darüber, wann Ihr Recordset Änderungen anderer Benutzer wiedergibt und wann die Recordsets anderer Benutzer Ihre Änderungen widerspiegeln, finden Sie unter [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) und [Dynaset](../../data/odbc/dynaset.md).

## <a name="requerying-based-on-new-parameters"></a><a name="_core_requerying_based_on_new_parameters"></a>Requerying basierend auf neuen Parametern

Eine weitere häufige – und ebenso wichtige – Verwendung von [Requery](../../mfc/reference/crecordset-class.md#requery) besteht darin, einen neuen Satz von Datensätzen auszuwählen, die auf sich ändernden Parameterwerten basieren.

> [!TIP]
> Die Abfragegeschwindigkeit ist wahrscheinlich `Requery` deutlich schneller, wenn Sie `Open` mit sich ändernden Parameterwerten aufrufen, als wenn Sie erneut aufrufen.

## <a name="requerying-dynasets-vs-snapshots"></a><a name="_core_requerying_dynasets_vs.._snapshots"></a>Requerying von Dynasets im Vergleich zu Snapshots

Da Dynasets eine Reihe von Datensätzen mit dynamischen aktuellen Daten darstellen sollen, möchten Sie Dynasets häufig neu abfragen, wenn Sie die Hinzufügungen anderer Benutzer widerspiegeln möchten. Snapshots sind hingegen nützlich, da Sie sich beim Vorbereiten von Berichten, berechnen von Summen usw. sicher auf ihren statischen Inhalt verlassen können. Dennoch möchten Sie manchmal auch einen Snapshot erneut abfragen. In einer Mehrbenutzerumgebung verlieren Snapshotdaten möglicherweise die Synchronisierung mit der Datenquelle, da andere Benutzer die Datenbank ändern.

#### <a name="to-requery-a-recordset-object"></a>So stellen Sie ein Recordset-Objekt erneut ab

1. Rufen Sie die [Requery-Memberfunktion](../../mfc/reference/crecordset-class.md#requery) des Objekts auf.

Alternativ können Sie das ursprüngliche Recordset schließen und erneut öffnen. In beiden Fällen stellt das neue Recordset den aktuellen Status der Datenquelle dar.

Ein Beispiel finden Sie unter [Datensatzansichten: Ausfüllen eines Listenfelds aus einem zweiten Recordset](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

> [!TIP]
> Um `Requery` die Leistung zu optimieren, vermeiden Sie es, den [Filter](../../data/odbc/recordset-filtering-records-odbc.md) oder die Sortierung des Recordsets zu [ändern.](../../data/odbc/recordset-sorting-records-odbc.md) Ändern Sie nur den `Requery`Parameterwert, bevor Sie aufrufen.

Wenn `Requery` der Aufruf fehlschlägt, können Sie den Aufruf wiederholen. Andernfalls sollte Ihre Anwendung ordnungsgemäß beendet werden. Ein Aufruf `Requery` `Open` an oder kann aus einem der gründe, aus einer Reihe von Gründen fehlschlagen. Möglicherweise tritt ein Netzwerkfehler auf. oder während des Anrufs, nachdem die vorhandenen Daten freigegeben wurden, aber bevor die neuen Daten abgerufen werden, kann ein anderer Benutzer exklusiven Zugriff erhalten; oder die Tabelle, von der Ihr Recordset abhängt, kann gelöscht werden.

## <a name="see-also"></a>Siehe auch

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Dynamisches Binden von Datenspalten (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Recordset: Erstellen und Schließen von Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)
