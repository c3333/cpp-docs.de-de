---
title: Datenaustausch für Datensatzansichten (MFC-Datenzugriff)
ms.date: 11/19/2018
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
ms.openlocfilehash: f9f460305b55a2313b64effdf4d1dbbfd9823def
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213471"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>Datenaustausch für Datensatzansichten (MFC-Datenzugriff)

Wenn Sie die Steuerelemente in der Dialogfeld Vorlagen-Ressource einer Daten Satz Ansicht mithilfe der [Add-Klasse](../mfc/reference/adding-an-mfc-odbc-consumer.md) den Feldern eines Recordsets zuordnen, verwaltet das Framework den Datenaustausch in beide Richtungen – von Recordset zu Steuerelementen und von Steuerelementen zu Recordset. Wenn Sie den DDX-Mechanismus verwenden, müssen Sie den Code zur Datenübertragung nicht selbst schreiben.

DDX für Daten Satz Sichten funktioniert in Verbindung mit [RFX](../data/odbc/record-field-exchange-rfx.md) für Recordsets der Klasse `CRecordset` (ODBC).  RFX verschiebt Daten zwischen dem aktuellen Datensatz der Datenquelle und den Felddatenmembern eines Recordset-Objekts. DDX verschiebt die Daten aus den Felddatenmembern in die Steuerelemente im Formular. Durch diese Kombination werden die Steuerelemente des Formulars am Anfang und immer dann gefüllt, wenn der Benutzer sich von Datensatz zu Datensatz bewegt. Zudem können aktualisierte Daten zurück in das Recordset und anschließend in die Datenquelle verschoben werden.

Die folgende Abbildung zeigt die Beziehung zwischen DDX und RFX für Daten Satz Ansichten.

![Dialog&#45;Datenaustausch und Daten&#45;Satz Feld Austausch](../data/media/vc37xt1.gif "Dialog&#45;Datenaustausch und Daten&#45;Satz Feld Austausch")<br/>
Dialogdatenaustausch und Datensatzfeldaustausch

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../mfc/dialog-data-exchange-and-validation.md). Weitere Informationen zu RFX finden Sie unter [Daten Satz Feld Austausch (RFX)](../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Weitere Informationen

[Datensatzansichten (MFC-Datenzugriff)](../data/record-views-mfc-data-access.md)<br/>
[Liste der ODBC-Treiber](../data/odbc/odbc-driver-list.md)
