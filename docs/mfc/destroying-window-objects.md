---
title: Zerstören von Fensterobjekten
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: 22b483c1005931b229453ae229935c0e716ab726
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621865"
---
# <a name="destroying-window-objects"></a>Zerstören von Fensterobjekten

Sie müssen mit ihren eigenen untergeordneten Fenstern darauf achten, dass das C++ Window-Objekt zerstört wird, wenn der Benutzer mit dem Fenster fertig ist. Wenn diese Objekte nicht zerstört werden, wird Ihr Arbeitsspeicher von Ihrer Anwendung nicht wieder hergestellt. Glücklicherweise verwaltet das Framework die Fenster Zerstörung und die Erstellung für Rahmen Fenster, Ansichten und Dialogfelder. Wenn Sie zusätzliche Fenster erstellen, sind Sie dafür verantwortlich, Sie zu zerstören.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Fenster Zerstörungs Sequenz](window-destruction-sequence.md)

- [Zuordnen und Aufheben der Zuordnung von Fenster Speicher](allocating-and-deallocating-window-memory.md)

- [Trennen eines CWnd von seinem HWND](detaching-a-cwnd-from-its-hwnd.md)

- [Allgemeine Ablauffolge bei der Fenstererstellung](general-window-creation-sequence.md)

- [Zerstören von Rahmenfenstern](destroying-frame-windows.md)

## <a name="see-also"></a>Siehe auch

[Fensterobjekte](window-objects.md)
