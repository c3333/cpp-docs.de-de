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
ms.openlocfilehash: 208749438f40eef746a638dd12373397c426d454
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368669"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC: Direktes Aufrufen von ODBC-API-Funktionen

Die Datenbankklassen stellen eine einfachere Schnittstelle zu einer [Datenquelle](../../data/odbc/data-source-odbc.md) bereit als ODBC. Daher kapseln die Klassen nicht die gesamte ODBC-API. Für alle Funktionen, die außerhalb der Fähigkeiten der Klassen stehen, müssen Sie ODBC-API-Funktionen direkt aufrufen. Sie müssen z. B. die`::SQLColumns`ODBC-Katalogfunktionen ( , `::SQLProcedures`, `::SQLTables`, und andere) direkt aufrufen.

> [!NOTE]
> Auf ODBC-Datenquellen können Sie über die MFC-ODBC-Klassen zugreifen, wie in diesem Thema beschrieben, oder über die MFC-Datenzugriffsobjekt-Klassen (DAO-Klassen).

Um eine ODBC-API-Funktion direkt aufzurufen, müssen Sie die gleichen Schritte ausführen, die Sie ausführen würden, wenn Sie die Aufrufe ohne das Framework ausführen würden. Sie sind:

- Weisen Sie Speicher für alle Ergebnisse zu, die der Aufruf zurückgibt.

- Übergeben Sie `HDBC` einen `HSTMT` ODBC oder ein Handle, abhängig von der Parametersignatur der Funktion. Verwenden Sie das [Makro AFXGetHENV,](../../mfc/reference/database-macros-and-globals.md#afxgethenv) um das ODBC-Handle abzurufen.

   Membervariablen `CDatabase::m_hdbc` `CRecordset::m_hstmt` und sind verfügbar, so dass Sie diese nicht selbst zuordnen und initialisieren müssen.

- Rufen Sie möglicherweise zusätzliche ODBC-Funktionen auf, um den Hauptanruf vorzubereiten oder zu verfolgen.

- Deallocate-Speicher, wenn Sie fertig sind.

Weitere Informationen zu diesen Schritten finden Sie im [ODBC-SDK (Open Database Connectivity)](/sql/odbc/microsoft-open-database-connectivity-odbc) in der MSDN-Dokumentation.

Zusätzlich zu diesen Schritten müssen Sie zusätzliche Schritte ausführen, um Die Wertrückgabewerte der Funktion zu überprüfen, sicherzustellen, dass das Programm nicht auf den Abschluss eines asynchronen Aufrufs wartet usw. Sie können diese letzten Schritte vereinfachen, indem Sie die AFX_SQL_ASYNC- und AFX_SQL_SYNC-Makros verwenden. Weitere Informationen finden Sie unter [Makros und Globale in](../../mfc/reference/mfc-macros-and-globals.md) der *MFC-Referenz*.

## <a name="see-also"></a>Siehe auch

[ODBC Grundlagen](../../data/odbc/odbc-basics.md)
