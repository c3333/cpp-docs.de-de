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
ms.openlocfilehash: 2e0484698654cd14f22a92be76a80f71c0f9adf5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621841"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Trennen eines CWnd von seinem HWND

Wenn Sie die Objektbeziehung umgehen müssen `HWND` , bietet MFC eine weitere `CWnd` Member-Funktion an. [trennen](reference/cwnd-class.md#detach)Sie die Verbindung zwischen dem C++-Fenster Objekt und dem Windows-Fenster. Dadurch wird verhindert, dass der debugtor das Fenster Windows zerstört, wenn das Objekt zerstört wird.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Erstellen von Fenstern](creating-windows.md)

- [Fenster Zerstörungs Sequenz](window-destruction-sequence.md)

- [Zuordnen und Aufheben der Zuordnung von Fenster Speicher](allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Siehe auch

[Fensterobjekte](window-objects.md)
