---
title: Speicherverwaltung mit CStringT
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
ms.openlocfilehash: af042c80b9e3e0de872261f89255a26728b218cd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440504"
---
# <a name="memory-management-with-cstringt"></a>Speicherverwaltung mit CStringT

Class [CStringT](../atl-mfc-shared/reference/cstringt-class.md) ist eine Vorlagen Klasse, die verwendet wird, um Zeichen folgen variabler Länge zu bearbeiten. Der Arbeitsspeicher, der diese Zeichen folgen enthalten soll, wird über ein Zeichen folgen-Manager-Objekt zugeordnet und freigegeben, das jeder Instanz von `CStringT`zugeordnet ist MFC und ATL stellen Standard Instanziierungen von `CStringT`, die als `CString`, `CStringA`und `CStringW`bezeichnet werden, die Zeichen folgen mit unterschiedlichen Zeichen Typen bearbeiten. Diese Zeichen Typen sind vom Typ "TCHAR", " **char**" und "`wchar_t`". Diese standardmäßigen Zeichen folgen Typen verwenden einen Zeichen folgen-Manager, der Arbeitsspeicher aus dem Prozess Heap (in ATL) oder dem CRT-Heap (in MFC) zugeordnet. Bei typischen Anwendungen ist dieses Speicher Belegungs Schema ausreichend. Für Code, der eine intensive Verwendung von Zeichen folgen (oder Multithread-Code) durchführt, werden die Standard Speicher-Manager jedoch möglicherweise nicht optimal durchgeführt In diesem Thema wird beschrieben, wie Sie das standardmäßige Speicher Verwaltungsverhalten von `CStringT`außer Kraft setzen und Zuweisungen erstellen, die speziell für die jeweilige Aufgabe optimiert sind.

- [Implementierung eines benutzerdefinierten Zeichenfolgenmanagers (grundlegende Methode)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)

- [Vermeiden von Heapkonflikten](../atl-mfc-shared/avoidance-of-heap-contention.md)

- [Implementierung eines benutzerdefinierten Zeichenfolgenmanagers (fortgeschrittene Methode)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)

- [CFixedStringT: Beispiel für einen benutzerdefinierten Zeichen folgen-Manager](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)

## <a name="see-also"></a>Weitere Informationen

[Beispiel für CustomString](../overview/visual-cpp-samples.md)
