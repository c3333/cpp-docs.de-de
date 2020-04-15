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
ms.openlocfilehash: 6f965b90e1e0bbcfd3ad04bb5b40644d61050b2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367163"
---
# <a name="record-field-exchange-rfx"></a>Datensatzfeldaustausch (RFX)

Die MFC ODBC-Datenbankklassen automatisieren das Verschieben von Daten zwischen der Datenquelle und einem [Recordset-Objekt.](../../data/odbc/recordset-odbc.md) Wenn Sie eine Klasse von [CRecordset](../../mfc/reference/crecordset-class.md) ableiten und keine Massenzeilenabrufe verwenden, werden Daten über den RFX-Mechanismus (Record Field Exchange) übertragen.

> [!NOTE]
> Wenn Sie das Abrufen von Massenzeilen in einer abgeleiteten `CRecordset` Klasse implementiert haben, verwendet das Framework den Bulk Record Field Exchange (Bulk RFX)-Mechanismus, um Daten zu übertragen. Weitere Informationen finden Sie unter [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

RFX ähnelt dem Dialogdatenaustausch (DDX). Das Verschieben von Daten zwischen einer Datenquelle und den Felddatenmembern eines Recordsets erfordert mehrere Aufrufe der [DoFieldExchange-Funktion](../../mfc/reference/crecordset-class.md#dofieldexchange) des Recordsets und eine erhebliche Interaktion zwischen dem Framework und [ODBC](../../data/odbc/odbc-basics.md). Der RFX-Mechanismus ist typsicher und erspart Ihnen `::SQLBindCol`die Arbeit beim Aufrufen von ODBC-Funktionen wie . Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

RFX ist für Sie meist transparent. Wenn Sie Ihre Recordset-Klassen mit dem MFC-Anwendungs-Assistenten oder der **Add-Klasse** deklarieren (wie unter [Hinzufügen eines MFC ODBC Consumer](../../mfc/reference/adding-an-mfc-odbc-consumer.md)beschrieben), wird RFX automatisch in sie integriert. Ihre Recordset-Klasse muss von `CRecordset` der Basisklasse abgeleitet werden, die vom Framework bereitgestellt wird. Mit dem MFC-Anwendungs-Assistenten können Sie eine erste Recordset-Klasse erstellen. **Mit Class hinzufügen** können Sie andere Recordsetklassen bei Bedarf hinzufügen. Weitere Informationen und Beispiele finden Sie unter [Hinzufügen eines MFC ODBC Consumer](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Sie müssen manuell eine kleine Menge an RFX-Code in drei Fällen hinzufügen, wenn Sie Folgendes tun möchten:

- Verwenden Sie parametrisierte Abfragen. Weitere Informationen finden Sie unter [Recordset: Parametrieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

- Führen Sie Verknüpfungen aus (unter Verwendung eines Recordsets für Spalten aus zwei oder mehr Tabellen). Weitere Informationen finden Sie unter [Recordset: Ausführen eines Joins (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Binden Sie Datenspalten dynamisch. Dies ist weniger häufig als Parametrierung. Weitere Informationen finden Sie unter [Recordset: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Wenn Sie ein erweitertes Verständnis von RFX benötigen, finden Sie weitere Informationen unter [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

In den folgenden Themen werden die Details zur Verwendung von Recordset-Objekten erläutert:

- [Datensatzfeldaustausch: Verwenden von RFX](../../data/odbc/record-field-exchange-using-rfx.md)

- [Datensatzfeldaustausch: Verwenden der RFX-Funktionen](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [Datensatzfeldaustausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>Siehe auch

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Nutzen von MFC-ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Datenbankunterstützung, MFC-Anwendungs-Assistent](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)
