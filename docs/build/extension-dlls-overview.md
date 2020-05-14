---
title: 'Erweiterungs-DLLs: Übersicht'
ms.date: 05/06/2019
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
ms.openlocfilehash: ea8e950e28907ea1a4a85c1f39392d5505f08c49
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221369"
---
# <a name="mfc-extension-dlls-overview"></a>MFC-Erweiterungs-DLLs: Übersicht

Eine MFC-Erweiterungs-DLL ist eine DLL, die typischerweise wiederverwendbare Klassen implementiert, die von bestehenden Klassen aus der Microsoft Foundation Class-Bibliothek abgeleitet wurden. MFC-Erweiterungs-DLLs werden mithilfe der DLL-Version von MFC erstellt (auch als freigegebene Version von MFC bekannt). Eine MFC-Erweiterungs-DLL kann ausschließlich von ausführbaren MFC-Dateien (entweder Anwendungen oder reguläre MFC-DLLs) verwendet werden, die mit der freigegebenen Version von MFC erstellt wurden. Mit einer MFC-Erweiterungs-DLL können Sie neue benutzerdefinierte Klassen von MFC ableiten und diese erweiterte MFC-Version anschließend Anwendungen zur Verfügung stellen, die die DLL aufrufen.

Erweiterungs-DLLs können auch dazu verwendet werden, von MFC abgeleitete Objekte zwischen Anwendung und DLL zu übergeben. Die dem übergebenen Objekt zugeordneten Memberfunktionen befinden sich in dem Modul, in dem das Objekt erstellt wurde. Da diese Funktionen bei Verwendung der freigegebenen DLL-Version von MFC ordnungsgemäß exportiert werden, können problemlos Zeiger auf MFC-Objekte oder auf von MFC abgeleitete Objekte zwischen einer Anwendung und den von ihr geladenen MFC-Erweiterungs-DLLs übergeben werden.

Ein Beispiel für eine DLL, die die grundlegenden Anforderungen an eine MFC-Erweiterungs-DLL erfüllt, finden Sie im MFC-Beispiel [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk). Sehen Sie sich insbesondere die Dateien „Testdll1.cpp“ und „Testdll2.cpp“ an.

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Initialisieren von MFC-Erweiterungs-DLLs](run-time-library-behavior.md#initializing-extension-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [MFC extension DLLs (MFC-Erweiterungs-DLLs)](extension-dlls.md)

- [Using Database, OLE, and Sockets MFC extension DLLs in regular MFC DLLs (Verwenden von Datenbank-, OLE- und Sockets-MFC-Erweiterungs-DLLs in regulären MFC-DLLs)](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [MFC-fremde DLLs: Übersicht](non-mfc-dlls-overview.md)

- [Reguläre, statisch mit MFC verknüpfte MFC-DLLs](regular-dlls-statically-linked-to-mfc.md)

- [Reguläre, dynamisch mit MFC verknüpfte MFC-DLLs](regular-dlls-dynamically-linked-to-mfc.md)

- [Erstellen einer MFC-DLL](../mfc/reference/mfc-dll-wizard.md)

## <a name="see-also"></a>Siehe auch

[Arten von DLLs](kinds-of-dlls.md)
