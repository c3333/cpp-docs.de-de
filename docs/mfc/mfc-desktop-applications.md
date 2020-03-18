---
title: MFC-Desktopanwendungen
ms.date: 07/28/2019
f1_keywords:
- MFC
helpviewer_keywords:
- libraries, MFC
- class libraries, MFC
- MFC, about MFC
ms.assetid: 7101cb18-a681-495c-8f2b-069ad20c72f7
ms.openlocfilehash: e9921d18e9ec060f61959278b68906338f02b5b7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447708"
---
# <a name="mfc-desktop-applications"></a>MFC-Desktopanwendungen

Die MFC-Bibliothek (Microsoft Foundation Class) stellt einen objektorientierten Wrapper für den Großteil der Win32 und COM APIs bereit. Obwohl sie zum Erstellen sehr einfacher Desktopanwendungen verwendet werden kann, ist sie besonders hilfreich, wenn Sie komplexere Benutzeroberflächen mit mehreren Steuerelementen entwickeln müssen. Sie können MFC zum Erstellen von Anwendungen mit Benutzeroberflächen im Stil von Office verwenden. Dokumentation zur Windows-Plattform selbst finden Sie in der [Windows-Dokumentation](/windows/index). Informationen zum Erstellen von Windows-Anwendungen C++ in ohne MFC finden [Sie unter Erstellen von Desktop-Windows-apps mit der Win32-API](/windows/win32/index).

Die MFC-Referenz umfasst die Klassen, die globalen Funktionen sowie die globalen Variablen und Makros, aus denen die Microsoft Foundation Class Library besteht.

Die in jeder Klasse enthaltenen einzelnen Hierarchiendiagramme sind beim Suchen von Basisklassen hilfreich. Der MFC-Verweis beschreibt normalerweise keine geerbte Memberfunktionen oder geerbte Operatoren. Weitere Informationen zu diesen Funktionen finden Sie unter den Basisklassen, die in den Hierarchiendiagrammen dargestellt werden.

Die Dokumentation für jede Klasse umfasst einen Klassenüberblick, eine Memberzusammenfassung nach Kategorie und Themen für die Memberfunktionen, überladenen Operatoren und Datenmember.

Öffentliche und geschützte Klassenmember werden nur dokumentiert, wenn sie in Anwendungen oder abgeleiteten Klassen normalerweise verwendet werden. Eine vollständige Liste der Klassenmember finden Sie bei den Klassenheaderdateien.

> [!IMPORTANT]
>  Die MFC-Klassen und ihre Member können in Anwendungen, die in der Windows-Runtime Umgebung ausgeführt werden, nicht verwendet werden.
>
>  MFC-Bibliotheken (DLLs) zur Codierung in Multibyte-Zeichenfolgen (MBCS) sind nicht mehr in Visual Studio enthalten. Sie sind jedoch als Visual Studio-Add-On verfügbar. Weitere Informationen finden Sie unter [MFC MBCS DLL-Add-on](mfc-mbcs-dll-add-on.md).

## <a name="in-this-section"></a>In diesem Abschnitt

[Konzepte](mfc-concepts.md)<br/>
Konzeptionelle Artikel zu MFC-Themen.

[Hierarchiediagramm](hierarchy-chart.md)<br/>
Die Klassenbeziehungen werden visuell in der Klassenbibliothek aufgeführt.

[Klassen Übersicht](class-library-overview.md)<br/>
Die Klassen in der MFC-Bibliothek werden nach Kategorie aufgeführt.

[Exemplarische Vorgehensweisen](walkthroughs-mfc.md)<br/>
Enthält Artikel, die Sie durch verschiedene den MFC-Bibliotheksfunktionen zugeordnete Aufgaben führt.

[Technische Hinweise](mfc-technical-notes.md)<br/>
Stellt Links zu den spezialisierten Themen bereit, die vom MFC-Entwicklerteam zur Klassenbibliothek geschrieben wurden.

[Anpassung für MFC](customization-for-mfc.md)<br/>
Stellt einige Tipps für die Anpassung der MFC-Anwendung bereit.

[Klassen](reference/mfc-classes.md)<br/>
Enthält Links zu Headerdateiinformationen und für die MFC-Klassen bereit.

[Internal-Klassen](reference/internal-classes.md)<br/>
Wird von den MFC intern verwendet. Vollständigkeitshalber werden diese internen Klassen in diesem Abschnitt beschreiben. Sie sollen allerdings nicht direkt im Code verwendet werden.

[Makros und Globals](reference/mfc-macros-and-globals.md)<br/>
Stellt Links zu den Makros und globale Funktionen in der MFC-Bibliothek bereit.

[Strukturen, Stile, Rückrufe und Meldungszuordnungen](reference/structures-styles-callbacks-and-message-maps.md)<br/>
Stellt Links zu den Strukturen, Stilen, Rückrufen und den Meldungszuordnungen bereit, die von der MFC-Bibliothek verwendet werden.

[MFC-Assistenten und -Dialogfelder](reference/mfc-wizards-and-dialog-boxes.md)<br/>
Eine Anleitung für die Features in Visual Studio zum Erstellen von MFC-Anwendungen.

[Arbeiten mit Ressourcendateien](../windows/working-with-resource-files.md)<br/>
Verwenden von Ressourcendateien zum Verwalten statischer Benutzeroberflächendaten, wie z. B. UI-Zeichenfolgen und Dialogfeldlayout.

## <a name="related-sections"></a>Verwandte Abschnitte

[Hierarchiediagrammkategorien](hierarchy-chart-categories.md)<br/>
Beschreibt das MFC-Hierarchiendiagramm nach Kategorie.

[Gemeinsam genutzte ATL/MFC-Klassen](../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
Enthält Links zu den Klassen, die von MFC und ATL freigegeben werden.

[MFC-Beispiele](../overview/visual-cpp-samples.md)<br/>
Stellt Links zu Beispielen bereit, mit denen die Verwendung von MFC gezeigt wird.

[Visual C++-Bibliotheksreferenz](../standard-library/cpp-standard-library-reference.md)<br/>
Bietet Links zu den verschiedenen Bibliotheken, die mit Visual C++ bereitgestellt werden, einschließlich ATL, MFC, OLE DB-Vorlagen, der C-Laufzeitbibliothek und der C++-Standardbibliothek.

[Debuggen in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)<br/>
Stellt Links zum Visual Studio-Debugger für die Behebung logischer Fehler in Ihrer Anwendung oder in gespeicherten Prozeduren bereit.

## <a name="see-also"></a>Weitere Informationen

[MFC und ATL](mfc-and-atl.md)
