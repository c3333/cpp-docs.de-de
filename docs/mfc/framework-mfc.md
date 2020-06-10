---
title: Framework (MFC)
ms.date: 09/17/2019
helpviewer_keywords:
- encapsulation [MFC], Win32 API
- MFC, application framework
- wrapper classes [MFC], explained
- Win32 [MFC], API encapsulation by MFC
- application framework [MFC], about MFC application framework
- APIs [MFC], encapsulation by MFC Win32
- encapsulation [MFC]
- Windows API [MFC], encapsulation by MFC
- encapsulated Win32 API [MFC]
ms.assetid: 3be0fec8-9843-4119-ae42-ece993ef500b
ms.openlocfilehash: b02d5a1862a278f46591895f20f58a97367b5ab2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618786"
---
# <a name="framework-mfc"></a>Framework (MFC)

Ihre Arbeit mit dem MFC-Bibliotheks Framework (Microsoft Foundation Class) basiert größtenteils auf einigen Hauptklassen und mehreren Visual C++ Tools. Einige Klassen Kapseln einen großen Teil der Win32-API (Application Programming Interface). Andere Klassen Kapseln Anwendungskonzepte, z. b. Dokumente, Ansichten und die Anwendung selbst. Andere kapseln OLE-Features und ODBC-und DAO-Datenzugriffs Funktionen.  (DAO wird durch Office 2013 unterstützt. DAO 3,6 ist die endgültige Version, die als veraltet eingestuft wird.)

Beispielsweise wird das Win32's-Konzept von Window von der MFC-Klasse gekapselt `CWnd` . Dies bedeutet, dass eine C++-Klasse `CWnd` mit dem Namen das Handle kapselt oder umschließt `HWND` , das ein Windows-Fenster darstellt. Ebenso `CDialog` kapselt die Klasse Win32-Dialogfelder.

Kapselung bedeutet, dass die C++-Klasse z. b. `CWnd` eine Member-Variable vom Typ enthält `HWND` , und die Member-Funktionen der Klasse Kapseln Aufrufe von Win32-Funktionen, die einen `HWND` als Parameter annehmen. Die Klassenmember-Funktionen haben normalerweise denselben Namen wie die Win32-Funktion, die Sie kapseln.

## <a name="in-this-section"></a>In diesem Abschnitt

[SDI und MDI](sdi-and-mdi.md)

[Dokumente, Ansichten und das Framework](documents-views-and-the-framework.md)

[Assistenten und Ressourcen-Editoren](wizards-and-the-resource-editors.md)

## <a name="in-related-sections"></a>In verwandten Abschnitten

[Erstellen im Framework](building-on-the-framework.md)

[So ruft das Framework Ihren Code auf](how-the-framework-calls-your-code.md)

[CWinApp: Die Anwendungsklasse](cwinapp-the-application-class.md)

[Dokumentvorlagen und der Erstellungsvorgang für Dokumente und Ansichten](document-templates-and-the-document-view-creation-process.md)

[Meldungsbehandlung und Zuordnung](message-handling-and-mapping.md)

[Fensterobjekte](window-objects.md)

## <a name="see-also"></a>Siehe auch

[Verwenden der Klassen zum Schreiben von Anwendungen für Windows](using-the-classes-to-write-applications-for-windows.md)
