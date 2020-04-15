---
title: Ausnahmebehandlung in MFC
ms.date: 11/19/2019
helpviewer_keywords:
- DAO [MFC], exceptions
- assertions [MFC], When to use exceptions
- exception handling [MFC], MFC
- resource allocation exception
- resources [MFC], allocating
- keywords [MFC], exception handling
- errors [MFC], detected by assertions
- ODBC exceptions [MFC]
- serialization [MFC], exceptions
- Automation [MFC], exceptions
- exception macros [MFC]
- predefined exceptions [MFC]
- C++ exception handling [MFC], enabling
- C++ exception handling [MFC], MFC applications
- requests for unsupported services [MFC]
- database exceptions [MFC]
- archive exceptions [MFC]
- MFC, exceptions
- C++ exception handling [MFC], types of
- macros [MFC], exception handling
- abnormal program execution [MFC]
- OLE exceptions [MFC], MFC exception handling
- error handling [MFC], exceptions and
- class libraries [MFC], exception support
- exceptions [MFC], MFC macros vs. C++ keywords
- memory [MFC], out-of-memory exceptions
- Windows [MFC], resource allocation exceptions
- macros [MFC], MFC exception macros
- function calls [MFC], results
- out-of-memory exceptions [MFC]
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
ms.openlocfilehash: d339ec98dabc6cb24fc7106c4c7238cd6a14a71b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365533"
---
# <a name="exception-handling-in-mfc"></a>Ausnahmebehandlung in MFC

In diesem Artikel werden die in MFC verfügbaren Mechanismen zur Ausnahmebehandlung erläutert. Es stehen zwei Mechanismen zur Verfügung:

- C++-Ausnahmen, verfügbar in MFC Version 3.0 und höher

- Die MFC-Ausnahmemakros, verfügbar in MFC-Versionen 1.0 und höher

Wenn Sie eine neue Anwendung mit MFC schreiben, sollten Sie den C++-Mechanismus verwenden. Sie können den makrobasierten Mechanismus verwenden, wenn Ihre vorhandene Anwendung diesen Mechanismus bereits ausgiebig verwendet.

Sie können vorhandenen Code problemlos konvertieren, um C++-Ausnahmen anstelle der MFC-Ausnahmemakros zu verwenden. Die Vorteile der Konvertierung Ihres Codes und Richtlinien dafür werden im Artikel [Ausnahmen: Konvertieren aus MFC-Ausnahmemakros](../mfc/exceptions-converting-from-mfc-exception-macros.md)beschrieben.

Wenn Sie bereits eine Anwendung mit den MFC-Ausnahmemakros entwickelt haben, können Sie diese Makros weiterhin in Ihrem vorhandenen Code verwenden, während Sie C++-Ausnahmen in Ihrem neuen Code verwenden. Der Artikel [Ausnahmen: Änderungen an Ausnahmemakros in Version 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) gibt Richtlinien dafür.

> [!NOTE]
> Um die C++-Ausnahmebehandlung in Ihrem Code zu aktivieren, wählen Sie C++-Ausnahmen aktivieren auf der Seite Codegenerierung im C/C++-Ordner des Dialogfelds [Eigenschaftenseiten](../build/reference/property-pages-visual-cpp.md) des Projekts aus, oder verwenden Sie die Compileroption [/EHsc.](../build/reference/eh-exception-handling-model.md)

In diesem Artikel werden die folgenden Themen behandelt:

- [Ausnahmen verwenden](#_core_when_to_use_exceptions)

- [MFC-Ausnahmeunterstützung](#_core_mfc_exception_support)

- [Weitere Lektüre zu Ausnahmen](#_core_further_reading_about_exceptions)

## <a name="when-to-use-exceptions"></a><a name="_core_when_to_use_exceptions"></a>Verwendung von Ausnahmen

Drei Kategorien von Ergebnissen können auftreten, wenn eine Funktion während der Programmausführung aufgerufen wird: normale Ausführung, fehlerhafte Ausführung oder abnormale Ausführung. Jede Kategorie wird unten beschrieben.

- Normale Ausführung

   Die Funktion kann normal ausgeführt und zurückgegeben werden. Einige Funktionen geben einen Ergebniscode an den Aufrufer zurück, der das Ergebnis der Funktion angibt. Die möglichen Ergebniscodes sind für die Funktion genau definiert und stellen den Bereich möglicher Ergebnisse der Funktion dar. Der Ergebniscode kann auf Erfolg oder Misserfolg oder sogar auf einen bestimmten Fehlertyp hinweisen, der im normalen Bereich der Erwartungen liegt. Beispielsweise kann eine Dateistatusfunktion einen Code zurückgeben, der angibt, dass die Datei nicht vorhanden ist. Beachten Sie, dass der Begriff "Fehlercode" nicht verwendet wird, da ein Ergebniscode eines von vielen erwarteten Ergebnissen darstellt.

- Fehlerhafte Ausführung

   Der Aufrufer macht einen Fehler beim Übergeben von Argumenten an die Funktion oder ruft die Funktion in einem unangemessenen Kontext auf. Diese Situation verursacht einen Fehler, und es sollte von einer Assertion während der Programmentwicklung erkannt werden. (Weitere Informationen zu Assertionen finden Sie unter [C/C++-Assertionen](/visualstudio/debugger/c-cpp-assertions).)

- Abnormale Ausführung

   Die abnormale Ausführung umfasst Situationen, in denen Bedingungen außerhalb der Programmsteuerung, z. B. Speichermangel oder E/A-Fehler, das Ergebnis der Funktion beeinflussen. Ungewöhnliche Situationen sollten durch Fangen und Auslösen von Ausnahmen behandelt werden.

Die Verwendung von Ausnahmen ist besonders für ungewöhnliche Ausführung geeignet.

## <a name="mfc-exception-support"></a><a name="_core_mfc_exception_support"></a>MFC-Ausnahmeunterstützung

Unabhängig davon, ob Sie die C++-Ausnahmen direkt oder die MFC-Ausnahmemakros verwenden, verwenden Sie [CException Class-](../mfc/reference/cexception-class.md) oder `CException`-derived-Objekte, die vom Framework oder von Ihrer Anwendung ausgelöst werden können.

Die folgende Tabelle zeigt die vordefinierten Ausnahmen, die von MFC bereitgestellt werden.

|Ausnahmeklasse|Bedeutung|
|---------------------|-------------|
|[CMemoryException-Klasse](../mfc/reference/cmemoryexception-class.md)|Nicht-Speicher|
|[CFileException-Klasse](../mfc/reference/cfileexception-class.md)|Dateiausnahme|
|[CArchiveException-Klasse](../mfc/reference/carchiveexception-class.md)|Archiv-/Serialisierungsausnahme|
|[CNotSupportedException-Klasse](../mfc/reference/cnotsupportedexception-class.md)|Antwort auf Anforderung für nicht unterstützten Dienst|
|[CResourceException-Klasse](../mfc/reference/cresourceexception-class.md)|Windows-Ressourcenzuordnungsausnahme|
|[CDaoException-Klasse](../mfc/reference/cdaoexception-class.md)|Datenbankausnahmen (DAO-Klassen)|
|[CDBException-Klasse](../mfc/reference/cdbexception-class.md)|Datenbankausnahmen (ODBC-Klassen)|
|[COleException-Klasse](../mfc/reference/coleexception-class.md)|OLE-Ausnahmen|
|[COleDispatchException-Klasse](../mfc/reference/coledispatchexception-class.md)|Dispatch-Ausnahmen (Automatisierung)|
|[CUserException-Klasse](../mfc/reference/cuserexception-class.md)|Ausnahme, die den Benutzer mit einem Meldungsfeld warnt und dann eine generische [CException-Klasse](../mfc/reference/cexception-class.md) auslöst|

Seit Version 3.0 verwendet MFC C++-Ausnahmen, unterstützt jedoch weiterhin die älteren Ausnahmebehandlungsmakros, deren Form der von C++-Ausnahmen ähnelt. Obwohl diese Makros nicht für neue Programmierungen empfohlen werden, werden sie weiterhin zu Zwecken der Abwärtskompatibilität unterstützt. In Programmen, die bereits die Makros verwenden, können Sie C++-Ausnahmen ebenfalls problemlos verwenden. Während der Vorverarbeitung werten die Makros die in der MSVC-Implementierung der C++-Version definierten Schlüsselwörter zur Ausnahmebehandlung ab, die ab Visual C++-Version 2.0 definiert sind. Sie können vorhandene Ausnahmemakros beibehalten, während Sie beginnen, C++-Ausnahmen zu verwenden. Informationen zum Mischen von Makros und C++-Ausnahmebehandlung und zum Konvertieren von altem Code zur Verwendung des neuen Mechanismus finden Sie in den Artikeln [Ausnahmen: Verwenden von MFC-Makros und C++-Ausnahmen](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) und [Ausnahmen: Konvertieren aus MFC-Ausnahmemakros](../mfc/exceptions-converting-from-mfc-exception-macros.md). Bei älteren MFC-Ausnahmemakros, sofern Sie diese noch verwenden, werden C++-Ausnahmeschlüsselwörter ausgewertet. Siehe [Ausnahmen: Änderungen an Ausnahmemakros in Version 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md). MFC unterstützt nicht direkt strukturierte Windows NT-Ausnahmehandler (SEH), wie unter [Structured Exception Handling](/windows/win32/debug/structured-exception-handling)erläutert.

## <a name="further-reading-about-exceptions"></a><a name="_core_further_reading_about_exceptions"></a>Weitere Lektüre über Ausnahmen

In den folgenden Artikeln wird die Verwendung der MFC-Bibliothek für die Ausnahmeübergabe erläutert:

- [Ausnahmen: Abfangen und Löschen von Ausnahmen](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [Ausnahmen: Untersuchen von Ausnahmeinhalten](../mfc/exceptions-examining-exception-contents.md)

- [Ausnahmen: Freigeben von Objekten in Ausnahmen](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [Ausnahmen: Ausnahmen in eigenen Funktionen auslösen](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [Ausnahmen: Datenbankausnahmen](../mfc/exceptions-database-exceptions.md)

- [Ausnahmen: OLE-Ausnahmen](../mfc/exceptions-ole-exceptions.md)

In den folgenden Artikeln werden die MFC-Ausnahmemakros mit den C++-Ausnahmeschlüsselwörtern verglichen und erläutert, wie Sie Ihren Code anpassen können:

- [Ausnahmen: Änderungen für Ausnahmemakros in Version 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [Ausnahmen: Umwandeln von MFC-Ausnahmemakros](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [Ausnahmen: Verwenden von MFC-Makros und C++-Ausnahmen](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>Siehe auch

[Moderne C++-Best Practices für Ausnahmen und Fehlerbehandlung](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Wie kann ich: Erstellen Sie meine eigenen benutzerdefinierten Ausnahmeklassen](https://go.microsoft.com/fwlink/p/?linkid=128045)
