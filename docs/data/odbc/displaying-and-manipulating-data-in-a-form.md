---
title: Anzeigen und Verändern von Daten in einem Formular
ms.date: 11/04/2016
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
ms.openlocfilehash: 6b663fabd0c87d9a2773e6f5a2796bcc8f57ce29
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213251"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>Anzeigen und Verändern von Daten in einem Formular

Viele Datenzugriffs Anwendungen wählen Daten aus und zeigen Sie in Feldern in einem Formular an. Die Datenbankklasse [CRecordView](../../mfc/reference/crecordview-class.md) gibt ein [CFormView](../../mfc/reference/cformview-class.md) -Objekt an, das direkt mit einem Recordset-Objekt verbunden ist. Die Daten Satz Ansicht verwendet den [Dialog Datenaustausch (DDX)](../../mfc/dialog-data-exchange-and-validation.md) , um die Werte der Felder des aktuellen Datensatzes aus dem Recordset in die Steuerelemente im Formular zu verschieben und aktualisierte Informationen zurück in das Recordset zu verschieben. Das Recordset verwendet wiederum Daten Satz Feld Austausch (RFX), um Daten zwischen den Felddatenmembern und den entsprechenden Spalten in einer Tabelle in der Datenquelle zu verschieben.

Sie können den MFC-Anwendungs-Assistenten oder die **Add-Klasse** (wie unter [Hinzufügen eines MFC-ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)-Consumers beschrieben) verwenden, um die Ansichts Klasse und die zugehörige Recordsetklasse in Verbindung zu erstellen.

Die Daten Satz Ansicht und das zugehörige Recordset werden beim Schließen des Dokuments zerstört. Weitere Informationen zu Daten Satz Sichten finden Sie unter [Daten Satz Ansichten](../../data/record-views-mfc-data-access.md). Weitere Informationen zu RFX finden Sie unter [Daten Satz Feld Austausch (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Weitere Informationen

[ODBC und MFC](../../data/odbc/odbc-and-mfc.md)
