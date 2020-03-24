---
title: ODBC und die Datenbankklassen
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 7c69f49cbe233eb0782fdaa9767ea55f4d04203c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213176"
---
# <a name="odbc-and-the-database-classes"></a>ODBC und die Datenbankklassen

Die MFC-ODBC-Datenbankklassen Kapseln die ODBC-API-Funktionsaufrufe, die Sie normalerweise selbst in den Member-Funktionen der [CDatabase](../../mfc/reference/cdatabase-class.md) -und [CRecordset](../../mfc/reference/crecordset-class.md) -Klassen vornehmen würden. Beispielsweise werden die komplexen ODBC-Aufrufsequenzen, die Bindung der zurückgegebenen Datensätze an Speicherorte, die Behandlung von Fehlerbedingungen und andere Vorgänge von den Datenbankklassen verwaltet. Daher verwenden Sie eine wesentlich einfachere Klassen Schnittstelle, um Datensätze über ein Recordset-Objekt zu bearbeiten.

> [!NOTE]
>  Auf ODBC-Datenquellen können Sie über die MFC-ODBC-Klassen zugreifen, wie in diesem Thema beschrieben, oder über die MFC-Datenzugriffsobjekt-Klassen (DAO-Klassen).

Obwohl die Datenbankklassen ODBC-Funktionen Kapseln, bieten Sie keine eins-zu-Eins-Zuordnung von ODBC-API-Funktionen. Die Datenbankklassen bieten eine höhere Abstraktions Ebene, die nach den Datenzugriffs Objekten in Microsoft Access und Microsoft Visual Basic modelliert wird. Weitere Informationen finden Sie unter [ODBC und MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Weitere Informationen

[Grundlagen zu ODBC](../../data/odbc/odbc-basics.md)
