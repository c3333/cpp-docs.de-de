---
title: _U_MENUorID Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
ms.openlocfilehash: 419c9e79178db12efe278838ec8630e04ac3c461
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325841"
---
# <a name="_u_menuorid-class"></a>_U_MENUorID Klasse

Diese Klasse stellt Wrapper für `CreateWindow` und `CreateWindowEx`bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class _U_MENUorID
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|Der Konstruktor.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|Ein Handle für ein Menü.|

## <a name="remarks"></a>Bemerkungen

Diese Argumentadapterklasse ermöglicht die Weitergabe von IDs (UINTs) oder Menühandles (HMENUs) an eine Funktion, ohne dass eine explizite Umwandlung seitens des Aufrufers erforderlich ist.

Diese Klasse wurde für die Implementierung von Wrappern in die Windows-API entwickelt, insbesondere für die [Funktionen CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) und [CreateWindowEx,](/windows/win32/api/winuser/nf-winuser-createwindowexw) die beide ein HMENU-Argument akzeptieren, das ein untergeordneter Fensterbezeichner (UINT) und kein Menühandle sein kann. Sie können diese Klasse beispielsweise als Parameter für [CWindowImpl::Create](cwindowimpl-class.md#create)anzeigen.

Die Klasse definiert zwei Konstruktorüberladungen: eine akzeptiert ein UINT-Argument und die andere ein HMENU-Argument. Das UINT-Argument wird nur in einen HMENU im Konstruktor gegossen und das Ergebnis wird im einzelnen Datenmember der Klasse [m_hMenu](#_u_menuorid__m_hmenu)gespeichert. Das Argument für den HMENU-Konstruktor wird direkt ohne Konvertierung gespeichert.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="_u_menuoridm_hmenu"></a><a name="_u_menuorid__m_hmenu"></a>_U_MENUorID::m_hMenu

Die Klasse hält den Wert, der an einen ihrer Konstruktoren übergeben wird, als öffentliches HMENU-Datenmember.

```
HMENU m_hMenu;
```

## <a name="_u_menuorid_u_menuorid"></a><a name="_u_menuorid___u_menuorid"></a>_U_MENUorID::_U_MENUorID

Das UINT-Argument wird nur in einen HMENU im Konstruktor gegossen und das Ergebnis wird im einzelnen Datenmember der Klasse [m_hMenu](#_u_menuorid__m_hmenu)gespeichert.

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Ein untergeordneter Fensterbezeichner.

*Hmenu*<br/>
Ein Menühandle.

### <a name="remarks"></a>Bemerkungen

Das Argument für den HMENU-Konstruktor wird direkt ohne Konvertierung gespeichert.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
