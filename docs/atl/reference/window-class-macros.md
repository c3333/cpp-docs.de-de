---
title: Fenster Klassen Makros
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: ca19eba1632ef3754b704c82ad5a872160ae0c91
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834465"
---
# <a name="window-class-macros"></a>Fenster Klassen Makros

Diese Makros definieren Fenster Klassen Hilfsprogramme.

|Name|Beschreibung|
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|Ermöglicht es Ihnen, den Namen einer neuen Fenster Klasse anzugeben.|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) Ermöglicht es Ihnen, den Namen einer neuen Fenster Klasse und die einschließende Klasse anzugeben, deren Fenster Prozedur von der neuen Klasse verwendet wird.|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Ermöglicht das Angeben des Namens einer vorhandenen Fenster Klasse, auf der eine neue Fenster Klasse basiert.|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Ermöglicht es Ihnen, die Parameter einer Klasse anzugeben.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="declare_wnd_class"></a><a name="declare_wnd_class"></a> DECLARE_WND_CLASS

Ermöglicht es Ihnen, den Namen einer neuen Fenster Klasse anzugeben. Platzieren Sie dieses Makro in der Steuerelement Klasse eines ATL-ActiveX-Steuer Elements.

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>Parameter

*Wndclassname*<br/>
in Der Name der neuen Fenster Klasse. Wenn der Wert NULL ist, generiert ATL einen Fenster Klassennamen.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die/permissive--Compileroption verwenden, verursacht DECLARE_WND_CLASS einen Compilerfehler. Verwenden Sie stattdessen DECLARE_WND_CLASS2.

Mit DECLARE_WND_CLASS können Sie den Namen einer neuen Fenster Klasse angeben, deren Informationen von [CWndClassInfo](cwndclassinfo-class.md)verwaltet werden. DECLARE_WND_CLASS die neue Fenster Klasse definiert, indem die folgende statische Funktion implementiert wird:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS gibt die folgenden Stile für das neue Fenster an:

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS gibt auch die Hintergrundfarbe des Standard Fensters an. Verwenden Sie das [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) -Makro, um Ihre eigenen Stile und Hintergrundfarbe anzugeben.

[CWindowImpl](cwindowimpl-class.md) verwendet das DECLARE_WND_CLASS-Makro, um ein Fenster zu erstellen, das auf einer neuen Fenster Klasse basiert. Um dieses Verhalten zu überschreiben, verwenden Sie das [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) -Makro, oder stellen Sie eine eigene Implementierung der [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) -Funktion bereit.

Weitere Informationen zur Verwendung von Windows in ATL finden Sie im Artikel [ATL-Fenster Klassen](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class2"></a><a name="declare_wnd_class2"></a> DECLARE_WND_CLASS2

(Visual Studio 2017) Vergleichbar mit DECLARE_WND_CLASS, aber mit einem zusätzlichen Parameter, der einen abhängigen Namensfehler beim Kompilieren mit der/permissive--Option vermeidet.

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>Parameter

*Wndclassname*<br/>
in Der Name der neuen Fenster Klasse. Wenn der Wert NULL ist, generiert ATL einen Fenster Klassennamen.

*EnclosingClass*<br/>
in Der Name der Fenster Klasse, die die neue Fenster Klasse einschließt. Lässt keine NULL-Werte zu.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die/permissive--Option verwenden, wird DECLARE_WND_CLASS einen Kompilierungsfehler verursachen, da er einen abhängigen Namen enthält. DECLARE_WND_CLASS2 erfordert, dass Sie die Klasse explizit benennen, in der dieses Makro verwendet wird, und den Fehler unter dem/permissive--Flag nicht verursacht.
Andernfalls ist dieses Makro mit [DECLARE_WND_CLASS](#declare_wnd_class)identisch.

## <a name="declare_wnd_superclass"></a><a name="declare_wnd_superclass"></a> DECLARE_WND_SUPERCLASS

Ermöglicht es Ihnen, die Parameter einer Klasse anzugeben. Platzieren Sie dieses Makro in der Steuerelement Klasse eines ATL-ActiveX-Steuer Elements.

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>Parameter

*Wndclassname*<br/>
in Der Name der Fenster Klasse, die *origwndclassname*der übergeordneten Klasse ist. Wenn der Wert NULL ist, generiert ATL einen Fenster Klassennamen.

*Origwndclassname*<br/>
in Der Name einer vorhandenen Fenster Klasse.

### <a name="remarks"></a>Bemerkungen

Mit diesem Makro können Sie den Namen einer Fenster Klasse angeben, die eine vorhandene Fenster Klasse als übergeordnete Klasse verwendet. [CWndClassInfo](cwndclassinfo-class.md) verwaltet die Informationen der übergeordneten Klasse.

DECLARE_WND_SUPERCLASS implementiert die folgende statische Funktion:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Standardmäßig verwendet [CWindowImpl](cwindowimpl-class.md) das [DECLARE_WND_CLASS](#declare_wnd_class) -Makro, um ein Fenster zu erstellen, das auf einer neuen Fenster Klasse basiert. Wenn Sie das DECLARE_WND_SUPERCLASS-Makro in einer von `CWindowImpl` abgeleiteten Klasse angeben, wird die Fenster Klasse auf einer vorhandenen Klasse basieren, verwendet jedoch die Fenster Prozedur. Dieses Verfahren wird als superclassingmethode bezeichnet.

Sie können die [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) -Funktion nicht nur mit der DECLARE_WND_CLASS-und DECLARE_WND_SUPERCLASS-Makros, sondern auch mit ihrer eigenen Implementierung überschreiben.

Weitere Informationen zur Verwendung von Windows in ATL finden Sie im Artikel [ATL-Fenster Klassen](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class_ex"></a><a name="declare_wnd_class_ex"></a> DECLARE_WND_CLASS_EX

Ermöglicht das Angeben des Namens einer vorhandenen Fenster Klasse, auf der eine neue Fenster Klasse basiert. Platzieren Sie dieses Makro in der Steuerelement Klasse eines ATL-ActiveX-Steuer Elements.

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>Parameter

*Wndclassname*<br/>
in Der Name der neuen Fenster Klasse. Wenn der Wert NULL ist, generiert ATL einen Fenster Klassennamen.

*style*<br/>
in Der Stil des Fensters.

*Hintergrund*<br/>
in Die Hintergrundfarbe des Fensters.

### <a name="remarks"></a>Bemerkungen

Mit diesem Makro können Sie die Klassen Parameter einer neuen Fenster Klasse angeben, deren Informationen von [CWndClassInfo](cwndclassinfo-class.md)verwaltet werden. DECLARE_WND_CLASS_EX die neue Fenster Klasse definiert, indem die folgende statische Funktion implementiert wird:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Wenn Sie die Standard Stile und die Hintergrundfarbe verwenden möchten, verwenden Sie das [DECLARE_WND_CLASS](#declare_wnd_class) -Makro. Weitere Informationen zur Verwendung von Windows in ATL finden Sie im Artikel [ATL-Fenster Klassen](../../atl/atl-window-classes.md).

## <a name="see-also"></a>Weitere Informationen

[Makros](atl-macros.md)
