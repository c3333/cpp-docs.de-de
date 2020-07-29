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
ms.openlocfilehash: 33d471b41c8f1fd670e25626049ecd9b06b034e1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195199"
---
# <a name="allocating-and-deallocating-window-memory"></a>Reservieren und Freigeben von Fensterspeicher

Verwenden Sie nicht den C++- **`delete`** Operator, um ein Rahmen Fenster oder eine Ansicht zu zerstören. Stattdessen wird die `CWnd` Member-Funktion aufgerufen `DestroyWindow` . Rahmen Fenster sollten daher auf dem Heap mit Operator zugeordnet werden **`new`** . Seien Sie vorsichtig, wenn Sie Rahmen Fenster im Stapel Rahmen oder Global zuordnen. Andere Fenster sollten möglichst im Stapel Rahmen zugeordnet werden.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Erstellen von Fenstern](creating-windows.md)

- [Fensterzerstörungssequenz](window-destruction-sequence.md)

- [Trennen eines CWnd von seinem HWND](detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Weitere Informationen

[Zerstören von Fenster Objekten](destroying-window-objects.md)
