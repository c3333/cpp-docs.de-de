---
title: Referenzzählung (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: 095f0ad2ecc1e1a870077899d61a3c594f8cc95f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321743"
---
# <a name="reference-counting"></a>Referenzzählung

COM selbst versucht nicht automatisch, ein Objekt aus dem Speicher zu entfernen, wenn es der Meinung ist, dass das Objekt nicht mehr verwendet wird. Stattdessen muss der Objektprogrammierer das nicht verwendete Objekt entfernen. Der Programmierer bestimmt anhand einer Verweisanzahl, ob ein Objekt entfernt werden kann.

COM verwendet `IUnknown` die Methoden [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) und [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release), um die Verweisanzahl von Schnittstellen für ein Objekt zu verwalten. Die allgemeinen Regeln für das Aufrufen dieser Methoden sind:

- Wenn ein Client einen Schnittstellenzeiger empfängt, `AddRef` muss er auf der Schnittstelle aufgerufen werden.

- Wenn der Client den Schnittstellenzeiger verwendet hat, muss er aufrufen. `Release`

In einer einfachen `AddRef` Implementierung wird jeder `Release` Aufruf erhöht und jeder Aufruf dekrementiert eine Zählervariable innerhalb des Objekts. Wenn die Anzahl auf Null zurückgesetzt wird, hat die Schnittstelle keine Benutzer mehr und kann sich selbst aus dem Speicher entfernen.

Die Referenzzählung kann auch so implementiert werden, dass jeder Verweis auf das Objekt (nicht auf eine einzelne Schnittstelle) gezählt wird. In diesem Fall `AddRef` `Release` delegieren und rufen Sie Delegierungen an eine zentrale Implementierung für das Objekt auf und `Release` gibt das gesamte Objekt frei, wenn die Referenzanzahl Null erreicht.

> [!NOTE]
> Wenn `CComObject`ein -derived-Objekt mit dem **neuen** Operator erstellt wird, ist die Referenzanzahl 0. Daher muss ein `AddRef` Aufruf an nach `CComObject`dem erfolgreichen Erstellen des -derived-Objekts erfolgen.

## <a name="see-also"></a>Siehe auch

[Einführung in COM](../atl/introduction-to-com.md)<br/>
[Verwalten von Objektlebensdauern durch Referenzzählung](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
