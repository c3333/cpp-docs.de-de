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
ms.openlocfilehash: bf1f99b92761c84d59b6f7bfb9aef67d7e097893
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222029"
---
# <a name="memory-management-with-cstringt"></a>Speicherverwaltung mit CStringT

Class [CStringT](../atl-mfc-shared/reference/cstringt-class.md) ist eine Vorlagen Klasse, die verwendet wird, um Zeichen folgen variabler Länge zu bearbeiten. Der Arbeitsspeicher für diese Zeichen folgen wird zugeordnet und über ein Zeichen folgen-Manager-Objekt freigegeben, das jeder Instanz von zugeordnet ist `CStringT` . MFC und ATL stellen Standard Instanziierungen von, `CStringT` `CString` die als, und bezeichnet `CStringA` `CStringW` werden, die Zeichen folgen mit unterschiedlichen Zeichen Typen bearbeiten. Diese Zeichen Typen sind vom Typ TCHAR, **`char`** **`wchar_t`** bzw.. Diese standardmäßigen Zeichen folgen Typen verwenden einen Zeichen folgen-Manager, der Arbeitsspeicher aus dem Prozess Heap (in ATL) oder dem CRT-Heap (in MFC) zugeordnet. Bei typischen Anwendungen ist dieses Speicher Belegungs Schema ausreichend. Für Code, der eine intensive Verwendung von Zeichen folgen (oder Multithread-Code) durchführt, werden die Standard Speicher-Manager jedoch möglicherweise nicht optimal durchgeführt In diesem Thema wird beschrieben, wie Sie das Standardverhalten der Speicherverwaltung überschreiben `CStringT` , indem Sie Zuweisungen erstellen, die speziell für die jeweilige Aufgabe optimiert sind.

- [Implementierung eines benutzerdefinierten Zeichen folgen-Managers (Basic-Methode)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)

- [Vermeiden von Heap Konflikten](../atl-mfc-shared/avoidance-of-heap-contention.md)

- [Implementierung eines benutzerdefinierten Zeichen folgen-Managers (erweiterte Methode)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)

- [CFixedStringT: Beispiel für einen benutzerdefinierten Zeichen folgen-Manager](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)

## <a name="see-also"></a>Weitere Informationen

[Beispiel für CustomString](../overview/visual-cpp-samples.md)
