---
title: Beziehung zum C-Sprachen-API
ms.date: 11/04/2016
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
ms.openlocfilehash: 1fbd4d332f5ade1cb9415448b138ac5bc838307d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372825"
---
# <a name="relationship-to-the-c-language-api"></a>Beziehung zum C-Sprachen-API

Das einzelne Merkmal, das die Microsoft Foundation Class (MFC)-Bibliothek von anderen Klassenbibliotheken für Windows unterscheidet, ist die sehr enge Zuordnung zur Windows-API, die in der C-Sprache geschrieben wurde. Darüber hinaus können Sie Aufrufe der Klassenbibliothek in der Regel frei mit direkten Aufrufen der Windows-API mischen. Dieser direkte Zugriff bedeutet jedoch nicht, dass die Klassen eine vollständige Ersetzung für diese API sind. Entwickler müssen immer noch gelegentlich direkte Aufrufe von einigen Windows-Funktionen tätigen, z. [B. SetCursor](/windows/win32/api/winuser/nf-winuser-setcursor) und [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics). Eine Windows-Funktion wird nur dann von einer Klassenmemberfunktion umschlossen, wenn dies einen klaren Vorteil hat.

Da Sie manchmal systemeigene Windows-Funktionsaufrufe ausführen müssen, sollten Sie Zugriff auf die C-Sprache-Windows-API-Dokumentation haben. Diese Dokumentation ist in Microsoft Visual C++ enthalten.

> [!NOTE]
> Eine Übersicht über die Funktionsweise des MFC-Bibliotheksframeworks finden Sie unter [Verwenden der Klassen zum Schreiben](../mfc/using-the-classes-to-write-applications-for-windows.md)von Anwendungen für Windows .

## <a name="see-also"></a>Siehe auch

[Allgemeine Prinzipien für den Klassenentwurf](../mfc/general-class-design-philosophy.md)
