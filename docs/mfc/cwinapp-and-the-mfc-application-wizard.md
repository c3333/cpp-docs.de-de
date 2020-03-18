---
title: CWinApp und der MFC-Anwendungs-Assistent
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: 1a46842d7b4d6a588da585d63e2ad56982bb0ff8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447044"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp und der MFC-Anwendungs-Assistent

Wenn eine Skeleton-Anwendung erstellt wird, deklariert der MFC-Anwendungs-Assistent eine von [CWinApp](../mfc/reference/cwinapp-class.md)abgeleitete Anwendungsklasse. Der MFC-Anwendungs-Assistent generiert außerdem eine Implementierungs Datei, die die folgenden Elemente enthält:

- Eine Meldungs Zuordnung für die Anwendungsklasse.

- Ein leerer Klassenkonstruktor.

- Eine Variable, die das einzige Objekt der Klasse deklariert.

- Eine Standard Implementierung Ihrer `InitInstance` Member-Funktion.

Die Anwendungsklasse wird in die Projekt Kopfzeile und die Haupt Quelldateien eingefügt. Die Namen der erstellten Klasse und Dateien basieren auf dem Projektnamen, den Sie im MFC-Anwendungs-Assistenten angeben. Die einfachste Möglichkeit zum Anzeigen des Codes für diese Klassen ist die [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code).

Die bereitgestellten Standardimplementierungen und Nachrichten Zuordnungen sind für viele Zwecke ausreichend, Sie können Sie jedoch nach Bedarf ändern. Das interessanteste dieser Implementierungen ist die `InitInstance` Member-Funktion. In der Regel fügen Sie der Skelett Implementierung von `InitInstance`Code hinzu.

## <a name="see-also"></a>Weitere Informationen

[CWinApp: Die Anwendungsklasse](../mfc/cwinapp-the-application-class.md)<br/>
[Überschreibbare CWinApp-Memberfunktionen](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Spezielle CWinApp-Dienste](../mfc/special-cwinapp-services.md)
