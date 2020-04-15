---
title: ODBC-Klassen und Threads
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: aaf54a3a1d616cde5742dad45955bd415f612d60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368691"
---
# <a name="odbc-classes-and-threads"></a>ODBC-Klassen und Threads

Ab MFC 4.2 gibt es Multithreading-Unterstützung für die MFC ODBC-Klassen. Beachten Sie jedoch, dass MFC keine Multithreading-Unterstützung für die DAO-Klassen bietet.

Die Multithreading-Unterstützung für die ODBC-Klassen hat einige Einschränkungen. Da diese Klassen die ODBC-API umschließen, sind sie auf die Multithreading-Unterstützung der Komponenten beschränkt, auf denen sie basieren. Beispielsweise sind viele ODBC-Treiber nicht threadsicher. Daher sind die MFC ODBC-Klassen nicht threadsicher, wenn Sie sie mit einem dieser Treiber verwenden. Sie sollten überprüfen, ob Ihr bestimmter Treiber threadsicher ist.

Beim Erstellen einer Multithreadanwendung sollten Sie bei der Verwendung mehrerer Threads sehr vorsichtig sein, um dasselbe Objekt zu bearbeiten. Die Verwendung desselben `CRecordset` Objekts in zwei Threads kann z. B. Probleme beim Abrufen von Daten verursachen. Ein Abrufvorgang in einem Thread kann die im anderen Thread abgerufenen Daten überschreiben. Eine häufigere Verwendung der MFC-ODBC-Klassen in `CDatabase` separaten Threads besteht darin, ein offenes `CRecordset` Objekt für Threads freizugeben, um dieselbe ODBC-Verbindung mit einem separaten Objekt in jedem Thread zu verwenden. Beachten Sie, dass Sie `CDatabase` kein ungeöffnetes Objekt an ein Objekt in einem `CRecordset` anderen Thread übergeben sollten.

> [!NOTE]
> Wenn mehrere Threads dasselbe Objekt bearbeiten müssen, sollten Sie die entsprechenden Synchronisierungsmechanismen implementieren, z. B. kritische Abschnitte. Beachten Sie, dass bestimmte `Open`Vorgänge, z. B. , nicht geschützt sind. Sie sollten sicher sein, dass diese Vorgänge nicht gleichzeitig von separaten Threads aufgerufen werden.

Weitere Informationen zum Erstellen von Multithreadanwendungen finden Sie unter [Multithreading-Themen](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="see-also"></a>Siehe auch

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Datenzugriffsprogrammierung (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
