---
title: Klassen für Rahmenfenster (Architektur)
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: 483112d197b7c7211989ecda8b774deb9f30d49e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624599"
---
# <a name="frame-window-classes-architecture"></a>Klassen für Rahmenfenster (Architektur)

In Dokument-/Ansichtarchitektur sind Rahmen Fenster Fenster, die ein Ansichts Fenster enthalten. Sie unterstützen außerdem das Anfügen von Steuer leisten.

In MDI-Anwendungen (Multiple Document Interface) wird das Hauptfenster von abgeleitet `CMDIFrameWnd` . Sie enthält indirekt die Rahmen der Dokumente, bei denen es sich um- `CMDIChildWnd` Objekte handelt. Die `CMDIChildWnd` Objekte enthalten wiederum die Ansichten "Dokumente".

In SDI-Anwendungen (Single Document Interface) enthält das Hauptfenster, das von abgeleitet wird, `CFrameWnd` die Ansicht des aktuellen Dokuments.

[CFrameWnd](reference/cframewnd-class.md)<br/>
Die Basisklasse für das Hauptrahmen Fenster einer SDI-Anwendung. Auch die Basisklasse für alle anderen Frame Fenster Klassen.

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
Die Basisklasse für das Hauptrahmen Fenster einer MDI-Anwendung.

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
Die Basisklasse für die Dokument Rahmen Fenster einer MDI-Anwendung.

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
Stellt das Rahmen Fenster für eine Ansicht bereit, wenn ein Server Dokument an Ort und Stelle bearbeitet wird.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)
