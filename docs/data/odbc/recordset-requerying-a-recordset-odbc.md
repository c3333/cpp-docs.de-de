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
ms.openlocfilehash: b7cf40ca3b0c8e415368772063aee61008a52764
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212783"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Recordset: Erneutes Abfragen eines Recordsets (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird erläutert, wie Sie ein Recordset-Objekt zum anstellen (aktualisieren) selbst aus der Datenbank verwenden können, und wann Sie dies möglicherweise mit der [Requery](../../mfc/reference/crecordset-class.md#requery) -Member-Funktion durchführen möchten.

Die Hauptgründe für die Anforderung eines Recordsets lauten:

- Bringen Sie das Recordset in Bezug auf Datensätze, die von Ihnen oder von anderen Benutzern und von anderen Benutzern gelöschten Datensätzen, die von anderen Benutzern gelöscht wurden, auf dem neuesten Stand.

- Aktualisieren Sie das Recordset basierend auf den veränderlichen Parameterwerten.

##  <a name="bringing-the-recordset-up-to-date"></a><a name="_core_bringing_the_recordset_up_to_date"></a>Das Recordset wird auf den neuesten Stand gebracht.

Häufig ist es ratsam, das Recordset-Objekt auf den neuesten Stand zu bringen. In einer mehr Benutzerdaten Bank Umgebung können andere Benutzer während der Lebensdauer des Recordsets Änderungen an den Daten vornehmen. Weitere Informationen dazu, wann das Recordset Änderungen widerspiegelt, die von anderen Benutzern vorgenommen wurden, sowie die Recordsets anderer Benutzer, die Ihre Änderungen widerspiegeln, finden Sie unter [Recordset: Wie Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) und [Dynaset](../../data/odbc/dynaset.md)ausführen.

##  <a name="requerying-based-on-new-parameters"></a><a name="_core_requerying_based_on_new_parameters"></a>Anweisen auf Grundlage neuer Parameter

Eine weitere häufige – und ebenso wichtig – die Verwendung von " [Requery](../../mfc/reference/crecordset-class.md#requery) " besteht darin, einen neuen Satz von Datensätzen basierend auf veränderlichen Parameterwerten auszuwählen.

> [!TIP]
>  Die Abfrage Geschwindigkeit ist wahrscheinlich deutlich schneller, wenn Sie `Requery` mit veränderlichen Parameterwerten aufrufen, als wenn Sie `Open` erneut aufrufen.

##  <a name="requerying-dynasets-vs-snapshots"></a><a name="_core_requerying_dynasets_vs.._snapshots"></a>Abfragen von Dynasets und Momentaufnahmen

Da Dynasets eine Reihe von Datensätzen mit dynamischen aktuellen Daten darstellen sollen, sollten Sie Dynasets häufig anweisen, wenn Sie die Ergänzungen anderer Benutzer widerspiegeln möchten. Momentaufnahmen hingegen sind nützlich, da Sie sich auf sichere Weise auf ihren statischen Inhalt verlassen können, während Sie Berichte vorbereiten, Summen berechnen usw. Dennoch kann es vorkommen, dass Sie auch eine Momentaufnahme anweisen möchten. In einer mehr Benutzerumgebung kann es vorkommen, dass Momentaufnahme Daten die Synchronisierung mit der Datenquelle verlieren, während andere Benutzer die Datenbank ändern.

#### <a name="to-requery-a-recordset-object"></a>So wird ein Recordset-Objekt angefordert

1. Ruft die [Requery](../../mfc/reference/crecordset-class.md#requery) -Member-Funktion des-Objekts auf.

Alternativ können Sie das ursprüngliche Recordset schließen und erneut öffnen. In jedem Fall stellt das neue Recordset den aktuellen Status der Datenquelle dar.

Ein Beispiel finden Sie unter [Daten Satz Ansichten: Füllen eines Listen Felds aus einem zweiten Recordset](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

> [!TIP]
>  Um die `Requery` Leistung zu optimieren, sollten Sie den [Filter](../../data/odbc/recordset-filtering-records-odbc.md) oder die [Sortierung](../../data/odbc/recordset-sorting-records-odbc.md)des Recordsets nicht ändern. Ändern Sie nur den Parameterwert, bevor Sie `Requery`aufrufen.

Wenn der `Requery`-Aufrufe fehlschlägt, können Sie den-Befehl wiederholen. Andernfalls sollte Ihre Anwendung ordnungsgemäß beendet werden. Ein `Requery` oder `Open` kann aus verschiedenen Gründen fehlschlagen. Möglicherweise kommt es zu einem Netzwerkfehler. Wenn während des Aufrufes die vorhandenen Daten freigegeben, aber bevor die neuen Daten abgerufen werden, kann ein anderer Benutzer exklusiven Zugriff erhalten. oder die Tabelle, von der das Recordset abhängt, kann gelöscht werden.

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Dynamisches Binden von Datenspalten (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Recordset: Erstellen und Schließen von Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)
