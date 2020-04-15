---
title: Schnittstellen (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 56d5a010bc28257dce181ee33e0ddf74655ccd3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319387"
---
# <a name="interfaces-atl"></a>Schnittstellen (ATL)

Eine Schnittstelle ist die Art und Weise, wie ein Objekt seine Funktionalität nach außen verfügbar macht. In COM ist eine Schnittstelle eine Tabelle von Zeigern (wie eine C++-vtable) auf Funktionen, die vom Objekt implementiert werden. Die Tabelle stellt die Schnittstelle dar, und die Funktionen, auf die sie verweist, sind die Methoden dieser Schnittstelle. Ein Objekt kann bezweckt, dass bedienviele Schnittstellen verfügbar gemacht werden.

Jede Schnittstelle basiert auf der grundlegenden COM-Schnittstelle [IUnknown](../atl/iunknown.md). Die Methoden `IUnknown` zum Zulassen der Navigation zu anderen Schnittstellen, die vom Objekt verfügbar gemacht werden.

Außerdem erhält jede Schnittstelle eine eindeutige Schnittstellen-ID (IID). Diese Einzigartigkeit macht es einfach, die Schnittstellenversionierung zu unterstützen. Eine neue Version einer Schnittstelle ist einfach eine neue Schnittstelle mit einer neuen IID.

> [!NOTE]
> IIDs für die Standard-COM- und OLE-Schnittstellen sind vordefiniert.

## <a name="see-also"></a>Siehe auch

[Einführung in COM](../atl/introduction-to-com.md)<br/>
[COM-Objekte und -Schnittstellen](/windows/win32/com/com-objects-and-interfaces)
