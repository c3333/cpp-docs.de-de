---
title: 'Datensatzfeldaustausch: Verwenden von RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: dc0cdcee758f4842b0738068a8a11c4e2e404155
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367148"
---
# <a name="record-field-exchange-using-rfx"></a>Datensatzfeldaustausch: Verwenden von RFX

In diesem Thema wird erläutert, was Sie tun, um RFX in Bezug auf die Vorgänge des Frameworks zu verwenden.

> [!NOTE]
> Dieses Thema gilt für Klassen, die von [CRecordset](../../mfc/reference/crecordset-class.md) abgeleitet wurden und in denen das Abrufen von Massenzeilen nicht implementiert wurde. Wenn Sie Massenabrufen von Zeilen verwenden, wird der Massen-Datensatzfeldaustausch (Bulk-RFX) implementiert. Bulk-RFX ist RFX sehr ähnlich. Informationen zu den Unterschieden finden Sie unter [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Die folgenden Themen enthalten verwandte Informationen:

- [Datensatzaustausch: In Der Arbeit mit dem Assistentencode](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) werden die Hauptkomponenten von RFX vorgestellt und der Code erläutert, den der MFC-Anwendungs-Assistent und die **Add-Klasse** (wie unter [Hinzufügen eines MFC ODBC Consumer](../../mfc/reference/adding-an-mfc-odbc-consumer.md)beschrieben) schreiben, um RFX zu unterstützen und wie Sie den Assistentencode ändern möchten.

- [Field Exchange aufzeichnen: Mithilfe der RFX-Funktionen](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) wird `DoFieldExchange` das Schreiben von Aufrufen an die RFX-Funktionen in Ihrer Außerkraftsetzung erläutert.

Die folgende Tabelle zeigt Ihre Rolle in Bezug auf die Fürachtung des Frameworks für Sie.

### <a name="using-rfx-you-and-the-framework"></a>Verwenden von RFX: Sie und das Framework

|Sie|Das Framework|
|---------|-------------------|
|Deklarieren Sie Ihre Recordset-Klassen mit einem Assistenten. Geben Sie Namen und Datentypen von Felddatenmembern an.|Der Assistent leitet `CRecordset` eine Klasse ab und schreibt eine [DoFieldExchange-Überschreibung](../../mfc/reference/crecordset-class.md#dofieldexchange) für Sie, einschließlich eines RFX-Funktionsaufrufs für jeden Felddatenmember.|
|(Optional) Fügen Sie der Klasse manuell alle erforderlichen Parameterdatenmember hinzu. Fügen Sie manuell einen RFX-Funktionsaufruf `DoFieldExchange` für jeden Parameterdatenmember hinzu, fügen Sie einen Aufruf von [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) für die Gruppe von Parametern hinzu, und geben Sie die Gesamtzahl der Parameter in [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)an. Siehe [Recordset: Parametrierung eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).||
|(Optional) Binden Sie manuell zusätzliche Spalten an Felddatenmember. Manuelle sinimierung [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). Siehe [Recordset: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||
|Erstellen Sie ein Objekt Ihrer Recordset-Klasse. Legen Sie vor der Verwendung des Objekts ggf. die Werte seiner Parameterdatenmember fest.|Aus Effizienzgründen bindet das Framework die Parameter mithilfe von ODBC vor. Wenn Sie Parameterwerte übergeben, übergibt das Framework sie an die Datenquelle. Nur die Parameterwerte werden für erneute Abfragen gesendet, es sei denn, die Sortier- und/oder Filterzeichenfolgen haben sich geändert.|
|Öffnen Sie ein Recordset-Objekt mit [CRecordset::Open](../../mfc/reference/crecordset-class.md#open).|Führt die Abfrage des Recordsets aus, bindet Spalten an Felddatenmember `DoFieldExchange` des Recordsets und ruft Daten zwischen dem ersten ausgewählten Datensatz und den Felddatenmembern des Recordsets auf.|
|Scrollen Sie im Recordset mit [CRecordset::Move](../../mfc/reference/crecordset-class.md#move) oder einem Menü- oder Symbolleistenbefehl.|Aufrufe `DoFieldExchange` zum Übertragen von Daten an die Felddatenmember aus dem neuen aktuellen Datensatz.|
|Hinzufügen, Aktualisieren und Löschen von Datensätzen.|Aufrufe `DoFieldExchange` zum Übertragen von Daten an die Datenquelle.|

## <a name="see-also"></a>Siehe auch

[Datensatzfeldaustausch (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Datensatzfeldaustausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Recordset: Abrufen von Summen und anderen Aggregatergebnissen (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange-Klasse](../../mfc/reference/cfieldexchange-class.md)<br/>
[Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
