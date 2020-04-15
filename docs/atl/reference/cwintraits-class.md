---
title: CWinTraits-Klasse
ms.date: 11/04/2016
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
ms.openlocfilehash: fd73f733e4eff21da92937d1e1b0cce21552a48c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330311"
---
# <a name="cwintraits-class"></a>CWinTraits-Klasse

Diese Klasse stellt eine Methode zum Standardisieren der Stile bereit, die beim Erstellen eines Fensterobjekts verwendet werden.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```

#### <a name="parameters"></a>Parameter

*t_dwStyle*<br/>
Standardfensterstile.

*t_dwExStyle*<br/>
Standardmäßige erweiterte Fensterstile.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinTraits::GetWndExStyle](#getwndexstyle)|(Statisch) Ruft die erweiterten Stile `CWinTraits` für das Objekt ab.|
|[CWinTraits::GetWndStyle](#getwndstyle)|(Statisch) Ruft die Standardstile `CWinTraits` für das Objekt ab.|

## <a name="remarks"></a>Bemerkungen

Diese [Fenstertraitsklasse](../../atl/understanding-window-traits.md) bietet eine einfache Methode zum Standardisieren der Stile, die für die Erstellung eines ATL-Fensterobjekts verwendet werden. Verwenden Sie eine Spezialisierung dieser Klasse als Vorlagenparameter für [CWindowImpl](../../atl/reference/cwindowimpl-class.md) oder eine andere von ATL-Fensterklassen, um den Standardstandard und die erweiterten Stile anzugeben, die für Instanzen dieser Fensterklasse verwendet werden.

Verwenden Sie diese Vorlage, wenn Sie Standardfensterformatvorlagen bereitstellen möchten, die nur verwendet werden, wenn im Aufruf von [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)keine anderen Formatvorlagen angegeben sind.

ATL bietet drei vordefinierte Spezialisierungen dieser Vorlage für häufig verwendete Kombinationen von Fensterstilen:

- `CControlWinTraits`

   Entwickelt für ein Standard-Steuerfenster. Es werden die folgenden Standardstile verwendet: WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN und WS_CLIPSIBLINGS. Es gibt keine erweiterten Stile.

- `CFrameWinTraits`

   Entwickelt für ein Standard-Rahmenfenster. Zu den verwendeten Standardstilen gehören: WS_OVERLAPPEDWINDOW, WS_CLIPCHILDREN und WS_CLIPSIBLINGS. Die verwendeten erweiterten Stile umfassen: WS_EX_APPWINDOW und WS_EX_WINDOWEDGE.

- `CMDIChildWinTraits`

   Entwickelt für ein standardmäßiges MDI-Kinderfenster. Zu den verwendeten Standardstilen gehören: WS_OVERLAPPEDWINDOW, WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN und WS_CLIPSIBLINGS. Zu den verwendeten erweiterten Stilen gehören: WS_EX_MDICHILD.

Wenn Sie sicherstellen möchten, dass bestimmte Stile für alle Instanzen der Fensterklasse festgelegt werden, während andere Stile pro Instanz festgelegt werden können, verwenden Sie stattdessen [CWinTraitsOR.](../../atl/reference/cwintraitsor-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="cwintraitsgetwndstyle"></a><a name="getwndstyle"></a>CWinTraits::GetWndStyle

Rufen Sie diese Funktion auf, `CWinTraits` um die Standardstile des Objekts abzurufen.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Standardstile, die zum Erstellen eines Fensters verwendet werden. Wenn *dwStyle* 0 ist, werden`t_dwStyle`die Vorlagenstilwerte ( ) zurückgegeben. Wenn *dwStyle* ungleich Null ist, wird *dwStyle* zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Die Standardfensterstile des Objekts.

## <a name="cwintraitsgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraits::GetWndExStyle

Rufen Sie diese Funktion auf, `CWinTraits` um die erweiterten Stile des Objekts abzurufen.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Parameter

*dwExStyle*<br/>
Erweiterte Stile, die zum Erstellen eines Fensters verwendet werden. Wenn *dwExStyle* 0 ist, werden`t_dwExStyle`die Vorlagenstilwerte ( ) zurückgegeben. Wenn *dwExStyle* ungleich Null ist, wird *dwExStyle* zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Die erweiterten Fensterstile des Objekts.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Verstehen von Fenstereigenschaften](../../atl/understanding-window-traits.md)
