---
title: Duale Schnittstellen und Ereignisse
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: 4ce5048c25bd55feb0f1eb20fc04ec6bfeead746
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319603"
---
# <a name="dual-interfaces-and-events"></a>Duale Schnittstellen und Ereignisse

Es ist zwar möglich, eine Ereignisschnittstelle als Dual zu entwerfen, es gibt jedoch eine Reihe guter Designgründe, dies nicht zu tun. Der Hauptgrund ist, dass die Quelle des Ereignisses das Ereignis `Invoke`nur über den vtable oder über, nicht über beide, ausfeuert. Wenn die Ereignisquelle das Ereignis als direkten vtable-Methodenaufruf auslöst, werden die `IDispatch` Methoden nie verwendet, und es ist klar, dass die Schnittstelle eine reine vtable-Schnittstelle hätte sein sollen. Wenn die Ereignisquelle das Ereignis `Invoke`als Aufruf von auslöst, werden die vtable-Methoden nie verwendet, und es ist klar, dass die Schnittstelle eine Dispinterface hätte sein sollen. Wenn Sie Ihre Ereignisschnittstellen als Duals definieren, müssen Clients einen Teil einer Schnittstelle implementieren, die nie verwendet wird.

> [!NOTE]
> Dieses Argument gilt im Allgemeinen nicht für duale Schnittstellen. Aus Der Implementierung summieren sich die Duals als schnelle, bequeme und gut unterstützte Möglichkeit, Schnittstellen zu implementieren, auf die eine Vielzahl von Clients zugreifen können.

Es gibt weitere Gründe, duale Ereignisschnittstellen zu vermeiden. Weder Visual Basic noch Internet Explorer unterstützen sie.

## <a name="see-also"></a>Siehe auch

[Dual E-Schnittstellen und ATL](../atl/dual-interfaces-and-atl.md)
