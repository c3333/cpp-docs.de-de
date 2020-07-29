---
title: Verweis Zählung (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: f90c818e58ae7ef6e4a0b771cb53ae5b185d1617
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224343"
---
# <a name="reference-counting"></a>Verweis Zählung

Das com selbst versucht nicht automatisch, ein Objekt aus dem Arbeitsspeicher zu entfernen, wenn es meint, dass das Objekt nicht mehr verwendet wird. Der Objekt Programmierer muss stattdessen das nicht verwendete Objekt entfernen. Der Programmierer bestimmt, ob ein Objekt basierend auf einem Verweis Zähler entfernt werden kann.

COM verwendet die `IUnknown` Methoden, [adressf](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) und [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release), um den Verweis Zähler der Schnittstellen für ein Objekt zu verwalten. Die allgemeinen Regeln zum Aufrufen dieser Methoden lauten wie folgt:

- Wenn ein Client einen Schnittstellen Zeiger empfängt, `AddRef` muss für die-Schnittstelle aufgerufen werden.

- Wenn der Client den Schnittstellen Zeiger nicht mehr verwendet, muss er aufgerufen werden `Release` .

In einer einfachen Implementierung `AddRef` dekrementierungen jeder-Rückruf, und jeder-Befehl `Release` dekremenkt eine Counter-Variable innerhalb des-Objekts. Wenn die Anzahl auf 0 (null) zurückgesetzt wird, verfügt die Schnittstelle nicht mehr über Benutzer und kann sich selbst aus dem Arbeitsspeicher entfernen.

Die Verweis Zählung kann auch so implementiert werden, dass jeder Verweis auf das Objekt (nicht auf eine einzelne Schnittstelle) gezählt wird. In diesem Fall delegiert jeder `AddRef` -und- `Release` Rückruf an eine zentrale Implementierung für das-Objekt und gibt `Release` das gesamte-Objekt frei, wenn der Verweis Zähler Null erreicht.

> [!NOTE]
> Wenn ein von `CComObject` abgeleitetes Objekt mit dem-Operator erstellt wird **`new`** , ist der Verweis Zähler 0. Daher `AddRef` muss nach der erfolgreichen Erstellung des von abgeleiteten Objekts ein-Rückruf durchgeführt werden `CComObject` .

## <a name="see-also"></a>Siehe auch

[Einführung in COM](../atl/introduction-to-com.md)<br/>
[Verwalten von Objekt Lebensdauern durch Verweis Zählung](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
