---
title: COleControlModule-Klasse
ms.date: 11/04/2016
f1_keywords:
- OleControlModule
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
ms.openlocfilehash: f6d486c7bacb897d70d85414ac3d0bd0d13e447b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310395"
---
# <a name="colecontrolmodule-class"></a>COleControlModule-Klasse

Die Basisklasse, von der ein OLE-Steuerelementmodul-Objekt abgeleitet wird.

## <a name="syntax"></a>Syntax

```
class COleControlModule : public CWinApp
```

## <a name="remarks"></a>Hinweise

Diese Klasse bietet Memberfunktionen zum Initialisieren von Ihrem Moduls an. Jedes Modul der OLE-Steuerelement, die Microsoft Foundation Classes verwendet darf nur ein Objekt abgeleitet `COleControlModule`. Dieses Objekt wird erstellt, wenn es sich bei anderen globalen C++-Objekte erstellt werden. Deklarieren Ihrer abgeleiteten `COleControlModule` Objekt auf globaler Ebene.

Weitere Informationen zur Verwendung der `COleControlModule` Klasse, finden Sie unter der [CWinApp](../../mfc/reference/cwinapp-class.md) -Klasse und den Artikel [ActiveX-Steuerelemente](../../mfc/mfc-activex-controls.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

[CWinApp](../../mfc/reference/cwinapp-class.md)

`COleControlModule`

## <a name="requirements"></a>Anforderungen

**Header:** afxctl.h

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel TESTHELP](../../overview/visual-cpp-samples.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
