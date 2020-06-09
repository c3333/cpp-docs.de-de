---
title: Rahmenfensterklassen
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], about frame window classes
- frame window classes [MFC]
- windows [MFC], MDI
- document frame windows [MFC], classes
- single document interface (SDI), frame windows
- window classes [MFC], frame
- MFC, frame windows
- MDI [MFC], frame windows
- classes [MFC], window
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
ms.openlocfilehash: ffa5b966ee042120213896dc7ad9d81c048ef928
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625809"
---
# <a name="frame-window-classes"></a>Rahmenfensterklassen

Jede Anwendung verfügt über ein "Hauptrahmen Fenster", ein Desktop Fenster, das in der Regel den Anwendungsnamen enthält. Jedes Dokument weist normalerweise ein Dokument Rahmen Fenster auf. Ein Dokument Rahmen Fenster enthält mindestens eine Ansicht, in der die Daten des Dokuments dargestellt werden.

## <a name="frame-windows-in-sdi-and-mdi-applications"></a>Rahmen Fenster in SDI-und MDI-Anwendungen

Bei einer SDI-Anwendung gibt es ein Rahmen Fenster, das von der [CFrameWnd](reference/cframewnd-class.md)-Klasse abgeleitet ist. Dieses Fenster ist sowohl das Hauptrahmen Fenster als auch das Dokument Rahmen Fenster. Bei einer MDI-Anwendung wird das Hauptrahmen Fenster von der [CMDIFrameWnd](reference/cmdiframewnd-class.md)-Klasse abgeleitet, und die Dokument Rahmen Fenster, bei denen es sich um untergeordnete MDI-Fenster handelt, werden von der Klasse [CMDIChildWnd](reference/cmdichildwnd-class.md)abgeleitet.

## <a name="use-the-frame-window-class-or-derive-from-it"></a>Verwenden Sie die Frame-Window-Klasse, oder leiten Sie davon ab.

Diese Klassen stellen den größten Teil der Rahmen Fenster Funktionalität bereit, die Sie für Ihre Anwendungen benötigen. Unter normalen Umständen werden die von Ihnen bereitgestellten Standardverhalten und-Darstellungen Ihren Anforderungen entsprechend angepasst. Wenn Sie zusätzliche Funktionen benötigen, leiten Sie von diesen Klassen ab.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Vom Anwendungs-Assistenten erstellte Rahmen Fenster Klassen](frame-window-classes-created-by-the-application-wizard.md)

- [Rahmen Fenster Stile](frame-window-styles-cpp.md)

- [Ändern der Stile eines mit MFC erstellten Fensters](changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>Siehe auch

[Rahmenfenster](frame-windows.md)
