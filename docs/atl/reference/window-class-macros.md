---
title: Fensterklassenmakros
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: 18c0912c506bc52421b18d36346204b557c0fc5c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325735"
---
# <a name="window-class-macros"></a>Fensterklassenmakros

Diese Makros definieren Fensterklassendienstprogramme.

|||
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|Ermöglicht es Ihnen, den Namen einer neuen Fensterklasse anzugeben.|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) Hier können Sie den Namen einer neuen Fensterklasse und die einschließende Klasse angeben, deren Fensterprozedur die neue Klasse verwendet.|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Hier können Sie den Namen einer vorhandenen Fensterklasse angeben, auf der eine neue Fensterklasse basiert.|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Ermöglicht es Ihnen, die Parameter einer Klasse anzugeben.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="declare_wnd_class"></a><a name="declare_wnd_class"></a>DECLARE_WND_CLASS

Ermöglicht es Ihnen, den Namen einer neuen Fensterklasse anzugeben. Platzieren Sie dieses Makro in der Steuerelementklasse eines ATL ActiveX-Steuerelements.

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>Parameter

*WndClassName*<br/>
[in] Der Name der neuen Fensterklasse. Wenn NULL, generiert ATL einen Fensterklassennamen.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die Option /permissive- compiler verwenden, wird DECLARE_WND_CLASS einen Compilerfehler verursachen. verwenden Sie stattdessen DECLARE_WND_CLASS2.

mit DECLARE_WND_CLASS können Sie den Namen einer neuen Fensterklasse angeben, deren Informationen von [CWndClassInfo](cwndclassinfo-class.md)verwaltet werden. DECLARE_WND_CLASS definiert die neue Fensterklasse, indem die folgende statische Funktion implementiert wird:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS gibt die folgenden Formatvorlagen für das neue Fenster an:

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS gibt auch die Hintergrundfarbe des Standardfensters an. Verwenden [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) Sie das DECLARE_WND_CLASS_EX-Makro, um eigene Stile und Hintergrundfarben bereitzustellen.

[CWindowImpl](cwindowimpl-class.md) verwendet das DECLARE_WND_CLASS-Makro, um ein Fenster basierend auf einer neuen Fensterklasse zu erstellen. Um dieses Verhalten zu überschreiben, verwenden Sie das [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) Makro, oder stellen Sie eine eigene Implementierung der [GetWndClassInfo-Funktion](cwindowimpl-class.md#getwndclassinfo) bereit.

Weitere Informationen zur Verwendung von Fenstern in ATL finden Sie im Artikel [ATL Window Classes](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class2"></a><a name="declare_wnd_class2"></a>DECLARE_WND_CLASS2

(Visual Studio 2017) Ähnlich wie DECLARE_WND_CLASS, jedoch mit einem zusätzlichen Parameter, der einen abhängigen Namensfehler beim Kompilieren mit der Option /permissive- vermeidet.

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>Parameter

*WndClassName*<br/>
[in] Der Name der neuen Fensterklasse. Wenn NULL, generiert ATL einen Fensterklassennamen.

*EnclosingClass*<br/>
[in] Der Name der Fensterklasse, die die neue Fensterklasse umschließt. Lässt keine NULL-Werte zu.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die Option /permissive- verwenden, verursacht DECLARE_WND_CLASS einen Kompilierungsfehler, da er einen abhängigen Namen enthält. DECLARE_WND_CLASS2 erfordert, dass Sie die Klasse, in der dieses Makro verwendet wird, explizit benennen und den Fehler unter dem Flag /permissive- nicht verursachen.
Andernfalls ist dieses Makro mit [DECLARE_WND_CLASS](#declare_wnd_class)identisch.

## <a name="declare_wnd_superclass"></a><a name="declare_wnd_superclass"></a>DECLARE_WND_SUPERCLASS

Ermöglicht es Ihnen, die Parameter einer Klasse anzugeben. Platzieren Sie dieses Makro in der Steuerelementklasse eines ATL ActiveX-Steuerelements.

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>Parameter

*WndClassName*<br/>
[in] Der Name der Fensterklasse, die *OrigWndClassName*überklassen wird. Wenn NULL, generiert ATL einen Fensterklassennamen.

*OrigWndClassName*<br/>
[in] Der Name einer vorhandenen Fensterklasse.

### <a name="remarks"></a>Bemerkungen

Mit diesem Makro können Sie den Namen einer Fensterklasse angeben, die eine vorhandene Fensterklasse überklassen. [CWndClassInfo](cwndclassinfo-class.md) verwaltet die Informationen der Superklasse.

DECLARE_WND_SUPERCLASS implementiert die folgende statische Funktion:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Standardmäßig verwendet [CWindowImpl](cwindowimpl-class.md) das [DECLARE_WND_CLASS-Makro,](#declare_wnd_class) um ein Fenster basierend auf einer neuen Fensterklasse zu erstellen. Durch Die Angabe des `CWindowImpl`DECLARE_WND_SUPERCLASS-Makros in einer -derived-Klasse basiert die Fensterklasse auf einer vorhandenen Klasse, verwendet jedoch die Fensterprozedur. Diese Technik wird als Superclassing bezeichnet.

Neben der Verwendung der DECLARE_WND_CLASS- und DECLARE_WND_SUPERCLASS-Makros können Sie die [GetWndClassInfo-Funktion](cwindowimpl-class.md#getwndclassinfo) mit Ihrer eigenen Implementierung überschreiben.

Weitere Informationen zur Verwendung von Fenstern in ATL finden Sie im Artikel [ATL Window Classes](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class_ex"></a><a name="declare_wnd_class_ex"></a>DECLARE_WND_CLASS_EX

Hier können Sie den Namen einer vorhandenen Fensterklasse angeben, auf der eine neue Fensterklasse basiert. Platzieren Sie dieses Makro in der Steuerelementklasse eines ATL ActiveX-Steuerelements.

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>Parameter

*WndClassName*<br/>
[in] Der Name der neuen Fensterklasse. Wenn NULL, generiert ATL einen Fensterklassennamen.

*Stil*<br/>
[in] Der Stil des Fensters.

*bkgnd*<br/>
[in] Die Hintergrundfarbe des Fensters.

### <a name="remarks"></a>Bemerkungen

Mit diesem Makro können Sie die Klassenparameter einer neuen Fensterklasse angeben, deren Informationen von [CWndClassInfo](cwndclassinfo-class.md)verwaltet werden. DECLARE_WND_CLASS_EX definiert die neue Fensterklasse, indem die folgende statische Funktion implementiert wird:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Wenn Sie die Standardstile und die Hintergrundfarbe verwenden möchten, verwenden Sie das [Makro DECLARE_WND_CLASS.](#declare_wnd_class) Weitere Informationen zur Verwendung von Fenstern in ATL finden Sie im Artikel [ATL Window Classes](../../atl/atl-window-classes.md).

## <a name="see-also"></a>Siehe auch

[Makros](atl-macros.md)
