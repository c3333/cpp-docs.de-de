---
title: ODBC-Klassen und Threads
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: 8cb5df605bef31e177e976798f975bb4ca14ced7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213169"
---
# <a name="odbc-classes-and-threads"></a>ODBC-Klassen und Threads

Ab MFC 4,2 ist Multithreading-Unterstützung für die MFC-ODBC-Klassen vorhanden. Beachten Sie jedoch, dass MFC keine Multithreading-Unterstützung für die DAO-Klassen bereitstellt.

Die Multithreading-Unterstützung für die ODBC-Klassen weist einige Einschränkungen auf. Da diese Klassen die ODBC-API einbinden, sind Sie auf die Unterstützung von Multithreading der Komponenten beschränkt, auf denen Sie erstellt werden. Viele ODBC-Treiber sind z. b. nicht Thread sicher. Daher sind die MFC-ODBC-Klassen nicht Thread sicher, wenn Sie Sie mit einem dieser Treiber verwenden. Sie sollten überprüfen, ob Ihr bestimmter Treiber Thread sicher ist.

Beim Erstellen einer Multithreadanwendung sollten Sie sehr vorsichtig sein, wenn Sie mehrere Threads verwenden, um das gleiche Objekt zu bearbeiten. Beispielsweise kann das Verwenden desselben `CRecordset` Objekts in zwei Threads Probleme beim Abrufen von Daten verursachen. ein Abruf Vorgang in einem Thread kann die im anderen Thread abgerufenen Daten überschreiben. Die MFC-ODBC-Klassen in separaten Threads werden häufiger verwendet, um ein offenes `CDatabase` Objekt Thread übergreifend gemeinsam zu nutzen, um dieselbe ODBC-Verbindung mit einem separaten `CRecordset`-Objekt in jedem Thread zu verwenden. Beachten Sie, dass Sie kein ungeöffnetes `CDatabase` Objekt an ein `CRecordset` Objekt in einem anderen Thread übergeben sollten.

> [!NOTE]
>  Wenn mehrere Threads das gleiche Objekt manipulieren müssen, sollten Sie die entsprechenden Synchronisierungs Mechanismen implementieren, wie z. b. kritische Abschnitte. Beachten Sie, dass bestimmte Vorgänge, wie z. b. `Open`, nicht geschützt sind. Sie sollten sicher sein, dass diese Vorgänge nicht gleichzeitig von separaten Threads aufgerufen werden.

Weitere Informationen zum Erstellen von Multithreadanwendungen finden Sie in den [Themen zum Multithreading](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="see-also"></a>Weitere Informationen

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Datenzugriffsprogrammierung (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
