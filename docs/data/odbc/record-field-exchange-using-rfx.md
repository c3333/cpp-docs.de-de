---
title: 'Datensatzfeldaustausch: Verwenden von RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: 70197d2a9130388e86bb94f0d670360bb35febeb
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075866"
---
# <a name="record-field-exchange-using-rfx"></a>Datensatzfeldaustausch: Verwenden von RFX

In diesem Thema wird erläutert, was Sie tun, um RFX in Bezug auf die Funktionsweise des Frameworks zu verwenden.

> [!NOTE]
>  Dieses Thema bezieht sich auf Klassen, die von [CRecordset](../../mfc/reference/crecordset-class.md) abgeleitet sind, in dem das Abrufen von Massen Zeilen nicht implementiert wurde. Wenn Sie Massenabrufen von Zeilen verwenden, wird der Massen-Datensatzfeldaustausch (Bulk-RFX) implementiert. Bulk-RFX ist RFX sehr ähnlich. Informationen zu den Unterschieden finden Sie unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Die folgenden Themen enthalten Verwandte Informationen:

- [Daten Satz Feld Austausch: beim Arbeiten mit dem Assistenten Code](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) werden die Hauptkomponenten von RFX eingeführt und der Code erläutert, den der MFC-Anwendungs-Assistent und die **Add-Klasse** (wie unter [Hinzufügen eines MFC-ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)-Consumers beschrieben) zum unterstützen von RFX und wie Sie den Assistenten Code ändern möchten.

- [Daten Satz Feld Austausch: die Verwendung der RFX-Funktionen erläutert das](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) Schreiben von Aufrufen der RFX-Funktionen in ihrer `DoFieldExchange` Überschreibung.

In der folgenden Tabelle wird die Rolle in Bezug auf die Funktionsweise des Frameworks angezeigt.

### <a name="using-rfx-you-and-the-framework"></a>Verwenden von RFX: Sie und das Framework

|Sie|Das Framework|
|---------|-------------------|
|Deklarieren Sie die Recordset-Klassen mit einem Assistenten. Geben Sie Namen und Datentypen von Felddatenmembern an.|Der Assistent leitet eine `CRecordset`-Klasse ab und schreibt eine [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) -außer Kraft setzung für Sie, einschließlich eines RFX-Funktions Aufrufes für jedes Felddatenmember.|
|Optionale Fügen Sie der Klasse manuell alle benötigten Parameter Datenmember hinzu. Fügen Sie für jeden Parameter Datenmember manuell einen RFX-Funktions Aufruf`DoFieldExchange` hinzu, fügen Sie einen [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) -Befehl für die Gruppe von Parametern hinzu, und geben Sie die Gesamtzahl der Parameter in [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)an. Weitere Informationen finden Sie unter [Recordset: parametrialisieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).||
|Optionale Binden Sie zusätzliche Spalten manuell an Felddatenmember. Manuelles Inkrement [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). Weitere Informationen finden Sie unter [Recordset: Dynamisches Binden von Datenspalten (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||
|Erstellen Sie ein Objekt ihrer Recordset-Klasse. Bevor Sie das-Objekt verwenden, legen Sie die Werte der Parameter Datenmember fest, sofern vorhanden.|Aus Effizienzgründen werden die Parameter vom Framework mithilfe von ODBC vorab gebunden. Wenn Sie Parameterwerte übergeben, übergibt das Framework Sie an die Datenquelle. Nur die Parameterwerte werden für requeries gesendet, es sei denn, die Sortier-und/oder Filter Zeichenfolgen wurden geändert.|
|Öffnen Sie ein Recordset-Objekt mithilfe von [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open).|Führt die Abfrage des Recordsets aus, bindet Spalten an Felddatenmember des Recordsets und ruft `DoFieldExchange` auf, um Daten zwischen dem ersten ausgewählten Datensatz und den Felddatenmembern des Recordsets auszutauschen.|
|Scrollen Sie im Recordset mit [CRecordset:: Move](../../mfc/reference/crecordset-class.md#move) oder einem Menü-oder Symbolleisten Befehl.|Ruft `DoFieldExchange` auf, um Daten aus dem neuen aktuellen Datensatz an die Felddatenmember zu übertragen.|
|Hinzufügen, aktualisieren und Löschen von Datensätzen.|Ruft `DoFieldExchange` auf, um Daten an die Datenquelle zu übertragen.|

## <a name="see-also"></a>Weitere Informationen

[Datensatzfeldaustausch (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Datensatzfeldaustausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Recordset: Abrufen von Summen und anderen Aggregatergebnissen (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange-Klasse](../../mfc/reference/cfieldexchange-class.md)<br/>
[Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
