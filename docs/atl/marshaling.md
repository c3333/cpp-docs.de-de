---
title: Marshalling
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 83cf29fb45347b7bfcfc1644546684f074061d25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319350"
---
# <a name="marshaling"></a>Marshalling

Die COM-Technik des Marshallings ermöglicht die Verwendung von Schnittstellen, die von einem Objekt in einem Prozess verfügbar gemacht werden, in einem anderen Prozess. Beim Marshalling stellt COM Code bereit (oder verwendet Code, der vom Schnittstellenimplementierer bereitgestellt wird), um sowohl die Parameter einer Methode in ein Format zu packen, das über Prozesse (sowie über den Draht hinweg zu Prozessen, die auf anderen Computern ausgeführt werden) verschoben werden kann, als auch um diese Parameter am anderen Ende zu entpacken. Ebenso muss COM die gleichen Schritte bei der Rückgabe vom Aufruf ausführen.

> [!NOTE]
> Marshalling ist in der Regel nicht erforderlich, wenn eine von einem Objekt bereitgestellte Schnittstelle im gleichen Prozess wie das Objekt verwendet wird. Es kann jedoch erforderlich sein, zwischen Threads zu marshallen.

## <a name="see-also"></a>Siehe auch

[Einführung in COM](../atl/introduction-to-com.md)<br/>
[Marshalling Details](/windows/win32/com/marshaling-details)
