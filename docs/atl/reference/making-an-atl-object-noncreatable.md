---
title: Konfigurieren eines ATL-Objekts als nicht erstellbares Objekt
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.objects
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
ms.openlocfilehash: b2d0a21ec9e68f76650f0f6cb78446bd93540fa2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506958"
---
# <a name="making-an-atl-object-noncreatable"></a>Konfigurieren eines ATL-Objekts als nicht erstellbares Objekt

Sie können die Attribute eines ATL-basierten com-Objekts ändern, damit ein Client das Objekt nicht direkt erstellen kann. In diesem Fall würde das Objekt durch einen Methoden aufruffür ein anderes Objekt zurückgegeben, anstatt direkt erstellt zu werden.

## <a name="to-make-an-object-noncreatable"></a>So erstellen Sie ein Objekt als nicht erstellbar

1. Entfernen Sie die [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) für das-Objekt. Wenn Sie möchten, dass das Objekt nicht erstellbar ist, aber das Steuerelement registriert werden soll, ersetzen Sie OBJECT_ENTRY_AUTO durch [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto).

1. Fügen Sie der Co-Klasse in der IDL-Datei das [nicht](../../windows/attributes/noncreatable.md) Erstell Bare Attribut hinzu. Beispiel:

    ```
    [uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851),
    helpstring("MyObject"),
    noncreatable]
    coclass MyObject
    {
        [default] interface IMyInterface;
    }
    ```

## <a name="see-also"></a>Weitere Informationen

[ATL-Projekt-Assistent](../../atl/reference/atl-project-wizard.md)<br/>
[C++-Projektvorlagen](../../build/reference/visual-cpp-project-types.md)<br/>
[Programmieren mit ATL-und C-Lauf Zeit Code](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Grundlagen von ATL-COM-Objekten](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Standardmäßige ATL-Projekt Konfigurationen](../../atl/reference/default-atl-project-configurations.md)
