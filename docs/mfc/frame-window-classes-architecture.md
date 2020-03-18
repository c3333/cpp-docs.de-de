---
title: Klassen für Rahmenfenster (Architektur)
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: e3ae432c1adc881a5c67d6a6c292dc1f6a583ab3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441249"
---
# <a name="frame-window-classes-architecture"></a>Klassen für Rahmenfenster (Architektur)

In Dokument-/Ansichtarchitektur sind Rahmen Fenster Fenster, die ein Ansichts Fenster enthalten. Sie unterstützen außerdem das Anfügen von Steuer leisten.

In MDI-Anwendungen (Multiple Document Interface) wird das Hauptfenster von `CMDIFrameWnd`abgeleitet. Sie enthält indirekt die Rahmen der Dokumente, die `CMDIChildWnd`-Objekten sind. Die `CMDIChildWnd` Objekte enthalten wiederum die Ansichten "Dokumente".

In SDI-Anwendungen (Single Document Interface) enthält das Hauptfenster, das von `CFrameWnd`abgeleitet wurde, die Ansicht des aktuellen Dokuments.

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
Die Basisklasse für das Hauptrahmen Fenster einer SDI-Anwendung. Auch die Basisklasse für alle anderen Frame Fenster Klassen.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
Die Basisklasse für das Hauptrahmen Fenster einer MDI-Anwendung.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
Die Basisklasse für die Dokument Rahmen Fenster einer MDI-Anwendung.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Stellt das Rahmen Fenster für eine Ansicht bereit, wenn ein Server Dokument an Ort und Stelle bearbeitet wird.

## <a name="see-also"></a>Weitere Informationen

[Klassen Übersicht](../mfc/class-library-overview.md)
