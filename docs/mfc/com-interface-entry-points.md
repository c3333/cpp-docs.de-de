---
title: Einstiegspunkte für COM-Schnittstellen
ms.date: 03/27/2019
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
ms.openlocfilehash: 132dd7394119081dcaeb098c2088782ff5d40ae4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619344"
---
# <a name="com-interface-entry-points"></a>Einstiegspunkte für COM-Schnittstellen

Verwenden Sie für Element Funktionen einer COM-Schnittstelle das- `METHOD_PROLOGUE` Makro, um den richtigen globalen Zustand beizubehalten, wenn Methoden einer exportierten Schnittstelle aufgerufen werden.

In der Regel verwenden Element Funktionen von Schnittstellen, die von von `CCmdTarget` abgeleiteten Objekten implementiert werden, dieses Makro, um die automatische Initialisierung des `pThis` Zeigers bereitzustellen. Beispiel:

[!code-cpp[NVC_MFCConnectionPoints#5](codesnippet/cpp/com-interface-entry-points_1.cpp)]

Weitere Informationen finden Sie in der [technischen Notiz 38](tn038-mfc-ole-iunknown-implementation.md) für die MFC/OLE- `IUnknown` Implementierung.

Das- `METHOD_PROLOGUE` Makro wird wie folgt definiert:

```cpp
#define METHOD_PROLOGUE(theClass, localClass) \
    theClass* pThis = \
    ((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \
    AFX_MANAGE_STATE(pThis->m_pModuleState) \
```

Der Teil des Makros, der sich mit der Verwaltung des globalen Zustands beschäftigt, ist:

`AFX_MANAGE_STATE( pThis->m_pModuleState )`

In diesem Ausdruck wird angenommen, dass es sich bei *m_pModuleState* um eine Member-Variable des enthaltenden Objekts handelt. Sie wird von der `CCmdTarget` -Basisklasse implementiert und mit dem entsprechenden Wert initialisiert `COleObjectFactory` , wenn das-Objekt instanziiert wird.

## <a name="see-also"></a>Siehe auch

[Verwalten der Statusdaten von MFC-Modulen](managing-the-state-data-of-mfc-modules.md)
