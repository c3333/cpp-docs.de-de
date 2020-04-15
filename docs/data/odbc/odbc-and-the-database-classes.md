---
title: ODBC und die Datenbankklassen
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 6511aab9bb048882fe9c3398dd17f769eb16220c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320065"
---
# <a name="odbc-and-the-database-classes"></a>ODBC und die Datenbankklassen

Die MFC ODBC-Datenbankklassen kapseln die ODBC-API-Funktionsaufrufe, die Sie normalerweise in den Memberfunktionen der [Klassen CDatabase](../../mfc/reference/cdatabase-class.md) und [CRecordset](../../mfc/reference/crecordset-class.md) verwenden würden. Beispielsweise werden die komplexen ODBC-Aufrufsequenzen, die Bindung zurückgegebener Datensätze an Speicherorte, die Behandlung von Fehlerbedingungen und andere Vorgänge von den Datenbankklassen für Sie verwaltet. Daher verwenden Sie eine wesentlich einfachere Klassenschnittstelle, um Datensätze über ein Recordset-Objekt zu bearbeiten.

> [!NOTE]
> Auf ODBC-Datenquellen können Sie über die MFC-ODBC-Klassen zugreifen, wie in diesem Thema beschrieben, oder über die MFC-Datenzugriffsobjekt-Klassen (DAO-Klassen).

Obwohl die Datenbankklassen DIE ODBC-Funktionalität kapseln, stellen sie keine 1:1-Zuordnung der ODBC-API-Funktionen bereit. Die Datenbankklassen bieten eine höhere Abstraktionsebene, die nach Datenzugriffsobjekten in Microsoft Access und Microsoft Visual Basic modelliert ist. Weitere Informationen finden Sie unter [ODBC und MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Siehe auch

[ODBC Grundlagen](../../data/odbc/odbc-basics.md)
