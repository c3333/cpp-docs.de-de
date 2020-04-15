---
title: CWndClassInfo-Klasse
ms.date: 11/04/2016
f1_keywords:
- CWndClassInfo
- ATLWIN/ATL::CWndClassInfo
- ATLWIN/ATL::Register
- ATLWIN/ATL::m_atom
- ATLWIN/ATL::m_bSystemCursor
- ATLWIN/ATL::m_lpszCursorID
- ATLWIN/ATL::m_lpszOrigName
- ATLWIN/ATL::m_szAutoName
- ATLWIN/ATL::m_wc
- ATLWIN/ATL::pWndProc
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
ms.openlocfilehash: 01706bf61c3b977c28998325ece68724cfbc7452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330336"
---
# <a name="cwndclassinfo-class"></a>CWndClassInfo-Klasse

Diese Klasse stellt Methoden zum Registrieren von Informationen für eine Fensterklasse bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CWndClassInfo
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|[Registrieren](#register)|Registriert die Fensterklasse.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|[m_atom](#m_atom)|Identifiziert die registrierte Fensterklasse eindeutig.|
|[m_bSystemCursor](#m_bsystemcursor)|Gibt an, ob sich die Cursorressource auf einen Systemcursor oder auf einen Cursor bezieht, der in einer Modulressource enthalten ist.|
|[m_lpszCursorID](#m_lpszcursorid)|Gibt den Namen der Cursorressource an.|
|[m_lpszOrigName](#m_lpszorigname)|Enthält den Namen einer vorhandenen Fensterklasse.|
|[m_szAutoName](#m_szautoname)|Enthält einen ATL-generierten Namen der Fensterklasse.|
|[m_wc](#m_wc)|Verwaltet Fensterklasseninformationen `WNDCLASSEX` in einer Struktur.|
|[pWndProc](#pwndproc)|Zeigt auf die Fensterprozedur einer vorhandenen Fensterklasse.|

## <a name="remarks"></a>Bemerkungen

`CWndClassInfo`verwaltet die Informationen einer Fensterklasse. Sie verwenden `CWndClassInfo` in der Regel eines von drei Makros, DECLARE_WND_CLASS, DECLARE_WND_CLASS_EX oder DECLARE_WND_SUPERCLASS, wie in der folgenden Tabelle beschrieben:

|Makro|BESCHREIBUNG|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo`registriert Informationen für eine neue Fensterklasse.|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo`registriert Informationen für eine neue Fensterklasse, einschließlich der Klassenparameter.|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo`registriert Informationen für eine Fensterklasse, die auf einer vorhandenen Klasse basiert, aber eine andere Fensterprozedur verwendet. Diese Technik wird als Superclassing bezeichnet.|

Standardmäßig enthält [CWindowImpl](../../atl/reference/cwindowimpl-class.md) `DECLARE_WND_CLASS` das Makro, um ein Fenster basierend auf einer neuen Fensterklasse zu erstellen. DECLARE_WND_CLASS stellt Standardstile und Hintergrundfarbe für das Steuerelement bereit. Wenn Sie den Stil und die Hintergrundfarbe selbst `CWindowImpl` angeben möchten, leiten Sie die Klasse ab, und fügen Sie das DECLARE_WND_CLASS_EX Makro in die Klassendefinition ein.

Wenn Sie ein Fenster basierend auf einer vorhandenen Fensterklasse `CWindowImpl` erstellen möchten, leiten Sie die Klasse ab, und fügen Sie das DECLARE_WND_SUPERCLASS-Makro in Ihre Klassendefinition ein. Beispiel:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

Weitere Informationen zu Fensterklassen finden Sie unter [Fensterklassen](/windows/win32/winmsg/window-classes) im Windows SDK.

Weitere Informationen zur Verwendung von Fenstern in ATL finden Sie im Artikel [ATL Window Classes](../../atl/atl-window-classes.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="cwndclassinfom_atom"></a><a name="m_atom"></a>CWndClassInfo::m_atom

Enthält den eindeutigen Bezeichner für die registrierte Fensterklasse.

```
ATOM m_atom;
```

## <a name="cwndclassinfom_bsystemcursor"></a><a name="m_bsystemcursor"></a>CWndClassInfo::m_bSystemCursor

Wenn TRUE, wird die Systemcursorressource geladen, wenn die Fensterklasse registriert wird.

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>Bemerkungen

Andernfalls wird die in Ihrem Modul enthaltene Cursorressource geladen.

`CWndClassInfo`wird `m_bSystemCursor` nur verwendet, wenn die [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (der Standardwert in [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) oder das [DECLARE_WND_CLASS_EX-Makro](window-class-macros.md#declare_wnd_class_ex) angegeben ist. In diesem `m_bSystemCursor` Fall wird auf TRUE initialisiert. Weitere Informationen finden Sie in der [CWndClassInfo-Übersicht.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinfom_lpszcursorid"></a><a name="m_lpszcursorid"></a>CWndClassInfo::m_lpszCursorID

Gibt entweder den Namen der Cursorressource oder den Ressourcenbezeichner im Wort niedriger Ordnung und Null im Wort hoher Ordnung an.

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>Bemerkungen

Wenn die Fensterklasse registriert ist, wird `m_lpszCursorID` das Handle für den Cursor, der von identifiziert wird, abgerufen und von [m_wc](#m_wc)gespeichert.

`CWndClassInfo`wird `m_lpszCursorID` nur verwendet, wenn die [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (der Standardwert in [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) oder das [DECLARE_WND_CLASS_EX-Makro](window-class-macros.md#declare_wnd_class_ex) angegeben ist. In diesem `m_lpszCursorID` Fall wird IDC_ARROW initialisiert. Weitere Informationen finden Sie in der [CWndClassInfo-Übersicht.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinfom_lpszorigname"></a><a name="m_lpszorigname"></a>CWndClassInfo::m_lpszOrigName

Enthält den Namen einer vorhandenen Fensterklasse.

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>Bemerkungen

`CWndClassInfo`wird `m_lpszOrigName` nur verwendet, wenn Sie das [DECLARE_WND_SUPERCLASS-Makro](window-class-macros.md#declare_wnd_superclass) in Ihre Klassendefinition aufnehmen. In diesem `CWndClassInfo` Fall registriert eine Fensterklasse basierend `m_lpszOrigName`auf der Klasse, die von benannt ist. Weitere Informationen finden Sie in der [CWndClassInfo-Übersicht.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinfom_szautoname"></a><a name="m_szautoname"></a>CWndClassInfo::m_szAutoName

Enthält den Namen der Fensterklasse.

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>Bemerkungen

`CWndClassInfo`wird `m_szAutoName` nur verwendet, wenn `WndClassName` NULL für den Parameter an [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)übergeben wird, die [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) oder [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass). ATL erstellt einen Namen, wenn die Fensterklasse registriert ist.

## <a name="cwndclassinfom_wc"></a><a name="m_wc"></a>CWndClassInfo::m_wc

Behält die Fensterklasseninformationen in einer [WNDCLASSEX-Struktur](/windows/win32/api/winuser/ns-winuser-wndclassexw) bei.

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie die [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (standardin [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) oder `m_wc` das [DECLARE_WND_CLASS_EX-Makro](window-class-macros.md#declare_wnd_class_ex) angegeben haben, enthält dies Informationen zu einer neuen Fensterklasse.

Wenn Sie das [DECLARE_WND_SUPERCLASS-Makro](window-class-macros.md#declare_wnd_superclass) angegeben haben, `m_wc` enthält informationen zu einer übergeordneten Klasse – einer Fensterklasse, die auf einer vorhandenen Klasse basiert, aber eine andere Fensterprozedur verwendet. [m_lpszOrigName](#m_lpszorigname) und [pWndProc](#pwndproc) speichern den Namen bzw. die Fensterprozedur der vorhandenen Fensterklasse.

## <a name="cwndclassinfopwndproc"></a><a name="pwndproc"></a>CWndClassInfo::pWndProc

Zeigt auf die Fensterprozedur einer vorhandenen Fensterklasse.

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>Bemerkungen

`CWndClassInfo`wird `pWndProc` nur verwendet, wenn Sie das [DECLARE_WND_SUPERCLASS-Makro](window-class-macros.md#declare_wnd_superclass) in Ihre Klassendefinition aufnehmen. In diesem `CWndClassInfo` Fall registriert eine Fensterklasse, die auf einer vorhandenen Klasse basiert, aber eine andere Fensterprozedur verwendet. Die Fensterprozedur der vorhandenen Fensterklasse `pWndProc`wird in gespeichert. Weitere Informationen finden Sie in der [CWndClassInfo-Übersicht.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinforegister"></a><a name="register"></a>CWndClassInfo::Registrieren

Wird von [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create) aufgerufen, um die Fensterklasse zu registrieren, wenn sie noch nicht registriert wurde.

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>Parameter

*pProc*<br/>
[out] Gibt die ursprüngliche Fensterprozedur einer vorhandenen Fensterklasse an.

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, ein Atom, das die registrierte Fensterklasse eindeutig identifiziert. Andernfalls ist es 0.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (standardin [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) oder `Register` das [DECLARE_WND_CLASS_EX-Makro](window-class-macros.md#declare_wnd_class_ex) angegeben haben, registriert eine neue Fensterklasse. In diesem Fall wird der *Parameter pProc* nicht verwendet.

Wenn Sie das [DECLARE_WND_SUPERCLASS-Makros](window-class-macros.md#declare_wnd_superclass) angegeben haben, `Register` registriert eine übergeordnete Klasse – eine Fensterklasse, die auf einer vorhandenen Klasse basiert, aber eine andere Fensterprozedur verwendet. Die Fensterprozedur der vorhandenen Fensterklasse wird in *pProc*zurückgegeben.

## <a name="see-also"></a>Siehe auch

[CComControl-Klasse](../../atl/reference/ccomcontrol-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
