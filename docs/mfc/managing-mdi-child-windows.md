---
title: Verwalten von untergeordneten MDI-Fenstern
ms.date: 11/19/2018
f1_keywords:
- MDICLIENT
helpviewer_keywords:
- MDI [MFC], child windows
- child windows [MFC], and MDICLIENT window
- MDICLIENT window [MFC]
- windows [MFC], MDI
- frame windows [MFC], MDI child windows
- child windows [MFC]
- MDI [MFC], frame windows
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
ms.openlocfilehash: 6e8e3d0aa51eeea112597485a9221dcba4feda87
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618360"
---
# <a name="managing-mdi-child-windows"></a>Verwalten von untergeordneten MDI-Fenstern

MDI-Hauptrahmen Fenster (eine pro Anwendung) enthalten ein spezielles untergeordnetes Fenster, das als MDICLIENT-Fenster bezeichnet wird. Das Fenster MdiClient verwaltet den Client Bereich des Hauptrahmen Fensters und verfügt über untergeordnete Fenster: das Dokument Fenster, das von abgeleitet wird `CMDIChildWnd` . Da es sich bei den Dokument Fenstern um Rahmen Fenster handelt (untergeordnete MDI-Fenster), können Sie auch über ihre eigenen untergeordneten Elemente verfügen. In allen diesen Fällen verwaltet das übergeordnete Fenster seine untergeordneten Fenster und leitet einige Befehle an Sie weiter.

In einem MDI-Rahmen Fenster verwaltet das Rahmen Fenster das MDICLIENT-Fenster und positioniert es in Verbindung mit Steuer leisten neu. Das Fenster MdiClient verwaltet wiederum alle untergeordneten MDI-Rahmen Fenster. In der folgenden Abbildung wird die Beziehung zwischen einem MDI-Rahmen Fenster, dem MDICLIENT-Fenster und den zugehörigen untergeordneten Dokument Rahmen Fenstern veranschaulicht.

![Untergeordnete Fenster in einem MDI-Rahmenfenster](../mfc/media/vc37gb1.gif "Untergeordnete Fenster in einem MDI-Rahmenfenster") <br/>
MDI-Rahmenfenster und untergeordnete Fenster

Ein MDI-Rahmen Fenster funktioniert auch zusammen mit dem aktuellen untergeordneten MDI-Fenster, sofern vorhanden. Das MDI-Rahmen Fenster delegiert Befehls Meldungen an das untergeordnete MDI-Element, bevor es versucht, Sie selbst zu behandeln.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Erstellen von Dokument Rahmen Fenstern](creating-document-frame-windows.md)

- [Rahmen Fenster Stile](frame-window-styles-cpp.md)

## <a name="see-also"></a>Siehe auch

[Verwenden von Rahmenfenstern](using-frame-windows.md)
