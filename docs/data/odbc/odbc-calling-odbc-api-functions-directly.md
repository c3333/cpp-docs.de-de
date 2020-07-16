---
title: 'ODBC: Direktes Aufrufen von ODBC-API-Funktionen'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC API functions [C++], calling
- ODBC [C++], catalog functions
- ODBC API functions [C++]
- APIs [C++], calling
- ODBC classes [C++], vs. ODBC API
- direct ODBC API calls
- catalog functions (ODBC)
- catalog functions (ODBC), calling
- ODBC [C++], API functions
ms.assetid: 4295f1d9-4528-4d2e-bd6a-c7569953c7fa
ms.openlocfilehash: e1cb5df4a93fc642ccf4d500a5eb93690b0b3d75
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403820"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC: Direktes Aufrufen von ODBC-API-Funktionen

Die Datenbankklassen stellen eine einfachere Schnittstelle zu einer [Datenquelle](../../data/odbc/data-source-odbc.md) dar als ODBC. Folglich Kapseln die Klassen nicht die gesamte ODBC-API. Für alle Funktionen, die außerhalb der Fähigkeiten der Klassen liegen, müssen Sie ODBC-API-Funktionen direkt aufzurufen. Beispielsweise müssen Sie die ODBC-Katalog Funktionen ( `::SQLColumns` ,, `::SQLProcedures` `::SQLTables` und andere) direkt abrufen.

> [!NOTE]
> Auf ODBC-Datenquellen können Sie über die MFC-ODBC-Klassen zugreifen, wie in diesem Thema beschrieben, oder über die MFC-Datenzugriffsobjekt-Klassen (DAO-Klassen).

Um eine ODBC-API-Funktion direkt aufzurufen, müssen Sie dieselben Schritte ausführen, die Sie ausführen würden, wenn Sie die Aufrufe ohne das Framework durchführen würden. Folgende Schritte sind erforderlich:

- Zuordnen von Speicher für alle vom Rückruf zurückgegebenen Ergebnisse.

- Übergeben Sie `HDBC` `HSTMT` abhängig von der Parameter Signatur der Funktion ein ODBC-oder-handle. Verwenden Sie das [AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv) -Makro, um das ODBC-Handle abzurufen.

   Element Variablen `CDatabase::m_hdbc` und `CRecordset::m_hstmt` sind verfügbar, sodass Sie diese nicht selbst zuordnen und initialisieren müssen.

- Weitere ODBC-Funktionen können aufgerufen werden, um den Haupt-oder Nachverfolgung des Haupt Aufrufes vorzubereiten.

- Freigabe der Speicherfreigabe, wenn Sie fertig sind.

Weitere Informationen zu diesen Schritten finden Sie in der [ODBC Programmer es Reference](/sql/odbc/reference/odbc-programmer-s-reference).

Zusätzlich zu diesen Schritten müssen Sie zusätzliche Schritte ausführen, um Funktions Rückgabewerte zu überprüfen, sicherzustellen, dass das Programm nicht auf den Abschluss eines asynchronen Aufrufes wartet usw. Sie können diese letzten Schritte mithilfe der Makros AFX_SQL_ASYNC und AFX_SQL_SYNC vereinfachen. Weitere Informationen finden Sie unter [MFC-Makros und Globals](../../mfc/reference/mfc-macros-and-globals.md).

## <a name="see-also"></a>Weitere Informationen

[ODBC-Grundlagen](../../data/odbc/odbc-basics.md)
