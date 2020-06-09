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
ms.openlocfilehash: 1f0b07a0a3439faba71078af1e2d7d1559a42b41
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626283"
---
# <a name="memory-management-heap-allocation"></a>Speicherverwaltung: Heapbelegung

Der Heap ist für die Speicher Belegungs Anforderungen des Programms reserviert. Es handelt sich um einen Bereich außer dem Programmcode und dem Stapel. Typische C-Programme verwenden die Funktionen " **malloc** " und "Free" zum Zuordnen und **Freigeben** von Heap Speicher. Die Debugversion von MFC bietet geänderte Versionen der integrierten C++-Operatoren **New** und **Delete** , um Objekte im Heap Speicher zuzuordnen und deren Zuteilung zu entfernen.

Wenn Sie " **New** " und " **Delete** " anstelle von " **malloc** " und " **Free**" verwenden, können Sie die debuggingerweiterungen der Klassenbibliothek nutzen, die bei der Erkennung von Speicher Verlusten nützlich sein können. Wenn Sie das Programm mit der Releaseversion von MFC erstellen, stellen die Standardversionen der **New** -und **Delete** -Operatoren eine effiziente Möglichkeit zum Zuordnen und Freigeben von Speicher bereit (die Releaseversion von MFC bietet keine geänderten Versionen dieser Operatoren).

Beachten Sie, dass die Gesamtgröße der im Heap zugeordneten Objekte nur durch den verfügbaren virtuellen Arbeitsspeicher Ihres Systems beschränkt wird.

## <a name="see-also"></a>Siehe auch

[Speicherverwaltung](memory-management.md)
