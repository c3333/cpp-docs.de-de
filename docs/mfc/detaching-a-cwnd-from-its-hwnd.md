---
title: Trennen eines CWnd von seinem HWND
ms.date: 11/04/2016
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
ms.openlocfilehash: f7a6f97ba9f1dd3a928a5450c1a899ce09a4ac5f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446959"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Trennen eines CWnd von seinem HWND

Wenn Sie die Beziehung zwischen Objekt`HWND` umgehen müssen, bietet MFC eine weitere `CWnd` Member-Funktion an. [trennen](../mfc/reference/cwnd-class.md#detach)Sie die Verbindung zwischen C++ dem Fenster Objekt und dem Windows-Fenster. Dadurch wird verhindert, dass der debugtor das Fenster Windows zerstört, wenn das Objekt zerstört wird.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Erstellen von Fenstern](../mfc/creating-windows.md)

- [Fenster Zerstörungs Sequenz](../mfc/window-destruction-sequence.md)

- [Zuordnen und Aufheben der Zuordnung von Fenster Speicher](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Weitere Informationen

[Fensterobjekte](../mfc/window-objects.md)
