---
title: Zugreifen auf ODBC und SQL
ms.date: 11/04/2016
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
ms.openlocfilehash: 0b590ce9309cbbe95285001cc5befe70a1d1961f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213329"
---
# <a name="access-to-odbc-and-sql"></a>Zugreifen auf ODBC und SQL

Der Microsoft Foundation Class-Bibliothek kapselt viele Windows-API-Aufrufe ein und ermöglicht es Ihnen weiterhin, jede Windows-API-Funktion direkt aufzurufen. Die Datenbankklassen bieten Ihnen die gleiche Flexibilität in Bezug auf die ODBC-API. Obwohl die Datenbankklassen von vielen der Komplexität von ODBC geschützt werden, können Sie ODBC-API-Funktionen direkt von jedem beliebigen Ort in Ihrem Programm aus aufrufen.

Entsprechend können Sie mithilfe der Datenbankklassen nicht viel mit [SQL](../../data/odbc/sql.md)arbeiten, aber Sie können SQL direkt verwenden, wenn Sie möchten. Sie können Recordset-Objekte anpassen, indem Sie eine benutzerdefinierte SQL-Anweisung übergeben (oder Teile der default-Anweisung festlegen), wenn Sie das Recordset öffnen. Sie können SQL-Aufrufe auch direkt mithilfe der [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) -Member-Funktion der [CDatabase](../../mfc/reference/cdatabase-class.md)-Klasse ausführen.

Weitere Informationen finden Sie unter [ODBC: direktes Aufrufen von ODBC-API-Funktionen](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) und [SQL: Durchführen direkter SQL-Aufrufe (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md).

## <a name="see-also"></a>Weitere Informationen

[ODBC und MFC](../../data/odbc/odbc-and-mfc.md)
