---
title: Verwenden gespeicherter Prozeduren
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
ms.openlocfilehash: a7e97781d245e236c57942db15d61080d6418cfa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209273"
---
# <a name="using-stored-procedures"></a>Verwenden gespeicherter Prozeduren

Bei einer gespeicherten Prozedur handelt es sich um ein ausführbares Objekt, das in einer Datenbank gespeichert ist. Das Aufrufen einer gespeicherten Prozedur ähnelt dem Aufrufen eines SQL-Befehls. Die Verwendung gespeicherter Prozeduren in der Datenquelle (anstatt eine Anweisung in der Client Anwendung auszuführen oder vorzubereiten) bietet mehrere Vorteile, z.b. höhere Leistung, geringeren Netzwerk Aufwand und verbesserte Konsistenz und Genauigkeit.

Eine gespeicherte Prozedur kann eine beliebige Anzahl von Eingabe-oder Ausgabeparametern (einschließlich NULL) aufweisen und kann einen Rückgabewert übergeben. Sie können Parameterwerte als bestimmte Datenwerte hart codieren oder einen Parametermarker (Fragezeichen '? ') verwenden.

> [!NOTE]
>  CLR-SQL Server mithilfe von Visual C++ erstellten gespeicherten Prozeduren müssen mit der `/clr:safe`-Compileroption kompiliert werden.

Der OLE DB Anbieter für SQL Server (SQLOLEDB) unterstützt die folgenden Mechanismen, die gespeicherte Prozeduren zum Zurückgeben von Daten verwenden:

- Jede **Select** -Anweisung in der Prozedur generiert ein Resultset.

- Die Prozedur kann Daten über Ausgabeparameter zurückgeben.

- Die Prozedur kann einen ganzzahligen Rückgabecode besitzen.

> [!NOTE]
> Sie können keine gespeicherten Prozeduren mit dem OLE DB-Anbieter für Jet verwenden, da dieser Anbieter keine gespeicherten Prozeduren unterstützt. in Abfrage Zeichenfolgen sind nur Konstanten zulässig.

## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit OLE DB-Consumervorlagen](../../data/oledb/working-with-ole-db-consumer-templates.md)
