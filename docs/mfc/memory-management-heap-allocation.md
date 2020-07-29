---
title: 'Speicherverwaltung: Heapbelegung'
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC], detecting leaks
- delete operator [MFC], using with debug MFC
- heap allocation [MFC], described
- memory allocation [MFC], heap memory
- memory leaks [MFC], detecting
- new operator [MFC], using with debug MFC
- heap allocation [MFC]
- detecting memory leaks [MFC]
ms.assetid: a5d949c6-1b79-476e-9c66-513a558203d9
ms.openlocfilehash: ecf60fbdd11f540d12c1bfab047bbb80a3cb83e8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228595"
---
# <a name="memory-management-heap-allocation"></a>Speicherverwaltung: Heapbelegung

Der Heap ist für die Speicher Belegungs Anforderungen des Programms reserviert. Es handelt sich um einen Bereich außer dem Programmcode und dem Stapel. Typische C-Programme verwenden die Funktionen " **malloc** " und "Free" zum Zuordnen und **Freigeben** von Heap Speicher. Die Debugversion von MFC bietet geänderte Versionen der integrierten C++-Operatoren **`new`** und **`delete`** zum Zuordnen und zum Zuweisen von Objekten im Heap Speicher.

Wenn Sie **`new`** und **`delete`** anstelle von **malloc** und **Free**verwenden, können Sie die debuggingverbesserungen der Klassenbibliothek nutzen, die beim Erkennen von Speicher Verlusten nützlich sein können. Wenn Sie das Programm mit der Releaseversion von MFC erstellen, stellen die Standardversionen **`new`** der **`delete`** Operatoren und eine effiziente Möglichkeit zum Zuordnen und Freigeben von Arbeitsspeicher bereit (die Releaseversion von MFC bietet keine geänderten Versionen dieser Operatoren).

Beachten Sie, dass die Gesamtgröße der im Heap zugeordneten Objekte nur durch den verfügbaren virtuellen Arbeitsspeicher Ihres Systems beschränkt wird.

## <a name="see-also"></a>Siehe auch

[Speicherverwaltung](memory-management.md)
