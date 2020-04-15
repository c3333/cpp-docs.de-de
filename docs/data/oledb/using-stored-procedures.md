---
title: Verwenden von gespeicherten Prozeduren
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
ms.openlocfilehash: 436c796b24b0fa498f2b3f45e848392635b22a34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376040"
---
# <a name="using-stored-procedures"></a>Verwenden von gespeicherten Prozeduren

Bei einer gespeicherten Prozedur handelt es sich um ein ausführbares Objekt, das in einer Datenbank gespeichert ist. Das Aufrufen einer gespeicherten Prozedur ähnelt dem Aufrufen eines SQL-Befehls. Die Verwendung gespeicherter Prozeduren in der Datenquelle (anstelle des Ausführens oder Vorbereitens einer Anweisung in der Clientanwendung) kann mehrere Vorteile bieten, z. B. höhere Leistung, reduzierter Netzwerkaufwand und verbesserte Konsistenz und Genauigkeit.

Eine gespeicherte Prozedur kann eine beliebige Anzahl von (einschließlich Null) Eingabe- oder Ausgabeparametern aufweisen und einen Rückgabewert übergeben. Sie können entweder Hartcodeparameterwerte als bestimmte Datenwerte verwenden oder eine Parametermarkierung verwenden (ein Fragezeichen '?').

> [!NOTE]
> Gespeicherte CLR SQL Server-Prozeduren, die mit `/clr:safe` Visual C++ erstellt wurden, müssen mit der Compileroption kompiliert werden.

Der OLE DB-Anbieter für SQL Server (SQLOLEDB) unterstützt die folgenden Mechanismen, die gespeicherte Prozeduren zum Zurückgeben von Daten verwenden:

- Jede **SELECT-Anweisung** in der Prozedur generiert ein Resultset.

- Die Prozedur kann Daten über Ausgabeparameter zurückgeben.

- Die Prozedur kann einen ganzzahligen Rückgabecode besitzen.

> [!NOTE]
> Sie können gespeicherte Prozeduren nicht mit dem OLE DB-Anbieter für Jet verwenden, da dieser Anbieter keine gespeicherten Prozeduren unterstützt. Nur Konstanten sind in Abfragezeichenfolgen zulässig.

## <a name="see-also"></a>Siehe auch

[Arbeiten mit OLE DB Consumer-Vorlagen](../../data/oledb/working-with-ole-db-consumer-templates.md)
