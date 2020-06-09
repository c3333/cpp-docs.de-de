---
title: Ausnahmeklassen
ms.date: 11/04/2016
f1_keywords:
- vc.classes.exception
helpviewer_keywords:
- exception classes [MFC]
- exception handling [MFC], exception classes
- MFC, exceptions
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
ms.openlocfilehash: 907b34b12ffdaa70c4377a1012a66662fbba12d0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619520"
---
# <a name="exception-classes"></a>Ausnahmeklassen

Die Klassenbibliothek stellt einen Mechanismus zur Ausnahmebehandlung bereit, der auf der-Klasse basiert `CException` . Das Anwendungs Framework verwendet Ausnahmen im Code. Sie können Sie auch in ihrer verwenden. Weitere Informationen finden Sie im Artikel [Ausnahmen](exception-handling-in-mfc.md). Sie können eigene Ausnahme Typen von ableiten `CException` .

MFC stellt eine Ausnahme Klasse bereit, von der Sie Ihre eigene Ausnahme und Ausnahme Klassen für alle unterstützten Ausnahmen ableiten können.

[CException](reference/cexception-class.md)<br/>
Die Basisklasse für Ausnahmen.

[CArchiveException](reference/carchiveexception-class.md)<br/>
Eine Archiv Ausnahme.

[CDaoException](reference/cdaoexception-class.md)<br/>
Eine Ausnahme, die sich aus einem Fehler in einem DAO-Daten Bank Vorgang ergibt.

[CDBException](reference/cdbexception-class.md)<br/>
Eine Ausnahme, die sich aus einem Fehler bei der ODBC-Daten Bank Verarbeitung ergibt.

[CFileException](reference/cfileexception-class.md)<br/>
Eine Datei orientierte Ausnahme.

[CMemoryException](reference/cmemoryexception-class.md)<br/>
Nicht genügend Arbeitsspeicher.

[CNotSupportedException](reference/cnotsupportedexception-class.md)<br/>
Eine Ausnahme, die sich aus der Verwendung eines nicht unterstützten Features ergibt.

[COleException](reference/coleexception-class.md)<br/>
Eine Ausnahme, die sich aus einem Fehler bei der OLE-Verarbeitung ergibt. Diese Klasse wird sowohl von Containern als auch von Servern verwendet.

[COleDispatchException](reference/coledispatchexception-class.md)<br/>
Eine Ausnahme, die sich aus einem Fehler während der Automatisierung ergibt. Automation-Ausnahmen werden von Automation-Servern ausgelöst und von Automatisierungs Clients abgefangen.

[CResourceException](reference/cresourceexception-class.md)<br/>
Eine Ausnahme, die sich aus dem Fehler beim Laden einer Windows-Ressource ergibt.

[CUserException](reference/cuserexception-class.md)<br/>
Eine Ausnahme, die verwendet wird, um einen vom Benutzer initiierten Vorgang zu beenden. In der Regel wird der Benutzer über das Problem benachrichtigt, bevor diese Ausnahme ausgelöst wird.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)
