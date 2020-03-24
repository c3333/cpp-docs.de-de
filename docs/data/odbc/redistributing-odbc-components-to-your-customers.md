---
title: Weitervertrieb von ODBC-Komponenten an Kunden
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
ms.openlocfilehash: 0d4d3948add665c54be3d3b0596a7a6fc0e414f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212731"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>Weitervertrieb von ODBC-Komponenten an Kunden

Wenn Sie die Funktionalität der ODBC-Administrator Programme in Ihre Anwendung einbinden, müssen Sie die Dateien, die diese Programme ausführen, auch an die Benutzer verteilen. Diese ODBC-Dateien befinden sich im Verzeichnis "\OS\System" C++ der Visual CD-ROM. Die Datei redistraub. WRI und der Lizenzvertrag in demselben Verzeichnis enthalten eine Liste der ODBC-Dateien, die Sie weiterverteilen können.

Informieren Sie sich in der Dokumentation über alle ODBC-Treiber, die Sie versenden möchten. Sie müssen bestimmen, welche DLLs und anderen Dateien ausgeliefert werden sollen. Lesen Sie außerdem die Informationen zum [erneuten Verteilen von ODBC-Komponenten an Ihre Kunden](../../data/odbc/redistributing-odbc-components-to-your-customers.md), in dem erläutert wird, wie Sie ODBC-Komponenten neu verteilen

Außerdem müssen Sie in den meisten Fällen eine andere Datei einschließen. Odbccr32. dll ist die ODBC-Cursor Bibliothek. Diese Bibliothek gibt den Treibern der Ebene 1 die Möglichkeit, vorwärts und Rückwärtsscrollen zu können. Außerdem bietet es die Möglichkeit, Momentaufnahmen zu unterstützen. Weitere Informationen zur ODBC-Cursor Bibliothek finden Sie unter [ODBC: die ODBC-Cursor Bibliothek](../../data/odbc/odbc-the-odbc-cursor-library.md).

Die folgenden Themen enthalten weitere Informationen zur Verwendung von ODBC mit den Datenbankklassen:

- [ODBC: Die ODBC-Cursorbibliothek](../../data/odbc/odbc-the-odbc-cursor-library.md)

- [ODBC: Konfigurieren einer ODBC-Datenquelle](../../data/odbc/odbc-configuring-an-odbc-data-source.md)

- [ODBC: Direktes Aufrufen von ODBC-API-Funktionen](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)

## <a name="see-also"></a>Weitere Informationen

[Grundlagen zu ODBC](../../data/odbc/odbc-basics.md)<br/>
[ODBC-Administrator](../../data/odbc/odbc-administrator.md)
