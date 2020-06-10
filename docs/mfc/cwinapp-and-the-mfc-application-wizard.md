---
title: CWinApp und der MFC-Anwendungs-Assistent
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: f57b3b2b37a97093aa6d81b59a12c8cf023e3157
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622937"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp und der MFC-Anwendungs-Assistent

Wenn eine Skeleton-Anwendung erstellt wird, deklariert der MFC-Anwendungs-Assistent eine von [CWinApp](reference/cwinapp-class.md)abgeleitete Anwendungsklasse. Der MFC-Anwendungs-Assistent generiert außerdem eine Implementierungs Datei, die die folgenden Elemente enthält:

- Eine Meldungs Zuordnung für die Anwendungsklasse.

- Ein leerer Klassenkonstruktor.

- Eine Variable, die das einzige Objekt der Klasse deklariert.

- Eine Standard Implementierung Ihrer `InitInstance` Member-Funktion.

Die Anwendungsklasse wird in die Projekt Kopfzeile und die Haupt Quelldateien eingefügt. Die Namen der erstellten Klasse und Dateien basieren auf dem Projektnamen, den Sie im MFC-Anwendungs-Assistenten angeben. Die einfachste Möglichkeit zum Anzeigen des Codes für diese Klassen ist die [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code).

Die bereitgestellten Standardimplementierungen und Nachrichten Zuordnungen sind für viele Zwecke ausreichend, Sie können Sie jedoch nach Bedarf ändern. Das interessanteste dieser Implementierungen ist die- `InitInstance` Member-Funktion. In der Regel fügen Sie der Skelett Implementierung von Code hinzu `InitInstance` .

## <a name="see-also"></a>Siehe auch

[CWinApp: Die Anwendungsklasse](cwinapp-the-application-class.md)<br/>
[Überschreibbare CWinApp-Memberfunktionen](overridable-cwinapp-member-functions.md)<br/>
[Spezielle CWinApp-Dienste](special-cwinapp-services.md)
