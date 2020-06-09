---
title: Reservieren und Freigeben von Fensterspeicher
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
ms.openlocfilehash: 02546559183d0e14973bc2e5ccb26a4570a39b1e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623266"
---
# <a name="allocating-and-deallocating-window-memory"></a>Reservieren und Freigeben von Fensterspeicher

Verwenden Sie nicht den C++ **Delete** -Operator, um ein Rahmen Fenster oder eine Ansicht zu zerstören. Stattdessen wird die `CWnd` Member-Funktion aufgerufen `DestroyWindow` . Rahmen Fenster sollten daher auf dem Heap mit dem **New**-Operator zugeordnet werden. Seien Sie vorsichtig, wenn Sie Rahmen Fenster im Stapel Rahmen oder Global zuordnen. Andere Fenster sollten möglichst im Stapel Rahmen zugeordnet werden.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Erstellen von Fenstern](creating-windows.md)

- [Fenster Zerstörungs Sequenz](window-destruction-sequence.md)

- [Trennen eines CWnd von seinem HWND](detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Siehe auch

[Zerstören von Fensterobjekten](destroying-window-objects.md)
