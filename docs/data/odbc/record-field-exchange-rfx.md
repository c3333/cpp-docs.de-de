---
title: Datensatzfeldaustausch (RFX)
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
ms.openlocfilehash: e1ba9f29ebf2cb3b1f94620e815882c850bbc7cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213056"
---
# <a name="record-field-exchange-rfx"></a>Datensatzfeldaustausch (RFX)

Die MFC-ODBC-Datenbankklassen automatisieren das Verschieben von Daten zwischen der Datenquelle und einem [Recordset](../../data/odbc/recordset-odbc.md) -Objekt. Wenn Sie eine Klasse von [CRecordset](../../mfc/reference/crecordset-class.md) ableiten und kein Massen Abruf von Zeilen verwenden, werden die Daten vom RFX-Mechanismus (Record Field Exchange) übertragen.

> [!NOTE]
>  Wenn Sie das Massen Abrufen von Zeilen in einer abgeleiteten `CRecordset` Klasse implementiert haben, verwendet das Framework den Bulk-Daten Satz Feld Austausch (Bulk RFX)-Mechanismus, um Daten zu übertragen. Weitere Informationen finden Sie unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

RFX ähnelt dem Dialog Datenaustausch (Dialog Data Exchange, DDX). Das Verschieben von Daten zwischen einer Datenquelle und den Felddatenmembern eines Recordsets erfordert mehrere Aufrufe der [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) -Funktion des Recordsets und eine beträchtliche Interaktion zwischen Framework und [ODBC](../../data/odbc/odbc-basics.md). Der RFX-Mechanismus ist typsicher und speichert das Aufrufen von ODBC-Funktionen, wie z. b. `::SQLBindCol`. Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

RFX ist größtenteils für Sie transparent. Wenn Sie Ihre recordsetklassen mit dem MFC-Anwendungs-Assistenten oder der **Add-Klasse** deklarieren (wie unter [Hinzufügen eines MFC-ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)-Consumers beschrieben), wird RFX automatisch in Sie integriert. Die Recordset-Klasse muss von der Basisklasse abgeleitet `CRecordset`, die vom Framework bereitgestellt wird. Mit dem MFC-Anwendungs-Assistenten können Sie eine anfängliche Recordset-Klasse erstellen. Durch **Hinzufügen einer Klasse** können Sie weitere recordsetklassen hinzufügen, wenn Sie Sie benötigen. Weitere Informationen und Beispiele finden Sie unter [Hinzufügen eines MFC-ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)-Consumers.

Sie müssen eine kleine Menge von RFX-Code in drei Fällen manuell hinzufügen, wenn Sie die folgenden Schritte ausführen möchten:

- Parametrisierte Abfragen verwenden. Weitere Informationen finden Sie unter [Recordset: parametrialisieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

- Führt Joins aus (unter Verwendung eines Recordsets für Spalten aus zwei oder mehr Tabellen). Weitere Informationen finden Sie unter [Recordset: Ausführen einer Verknüpfung (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Dynamisches Binden von Datenspalten. Dies ist weniger häufig als bei der Parametrisierung. Weitere Informationen finden Sie unter [Recordset: Dynamisches Binden von Datenspalten (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Wenn Sie ein erweitertes Verständnis von RFX benötigen, finden Sie weitere Informationen unter [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

In den folgenden Themen werden die Details der Verwendung von Recordset-Objekten erläutert:

- [Datensatzfeldaustausch: Verwenden von RFX](../../data/odbc/record-field-exchange-using-rfx.md)

- [Datensatzfeldaustausch: Verwenden der RFX-Funktionen](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [Datensatzfeldaustausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>Weitere Informationen

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Nutzen von MFC-ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Datenbankunterstützung, MFC-Anwendungs-Assistent](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)
