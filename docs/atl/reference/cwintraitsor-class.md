---
title: CWinTraitsOR-Klasse
ms.date: 11/04/2016
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
ms.openlocfilehash: 825f79190c6f68cd1372154e4e02f430f545aa48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330286"
---
# <a name="cwintraitsor-class"></a>CWinTraitsOR-Klasse

Diese Klasse stellt eine Methode zum Standardisieren der Stile bereit, die beim Erstellen eines Fensterobjekts verwendet werden.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0,
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
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
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|Ruft die erweiterten Stile `CWinTraitsOR` für das Objekt ab.|
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|Ruft die Standardstile `CWinTraitsOR` für das Objekt ab.|

## <a name="remarks"></a>Bemerkungen

Diese [Fenstertraitsklasse](../../atl/understanding-window-traits.md) bietet eine einfache Methode zum Standardisieren der Stile, die für die Erstellung eines ATL-Fensterobjekts verwendet werden. Verwenden Sie eine Spezialisierung dieser Klasse als Vorlagenparameter für [CWindowImpl](../../atl/reference/cwindowimpl-class.md) oder eine andere von ATL-Fensterklassen, um den Minimalsatz von Standard- und erweiterten Stilen anzugeben, die für Instanzen dieser Fensterklasse verwendet werden sollen.

Verwenden Sie eine Spezialisierung dieser Vorlage, wenn Sie sicherstellen möchten, dass bestimmte Formatvorlagen für alle Instanzen der Fensterklasse festgelegt werden, während andere Stile auf Instanzbasis beim Aufruf von [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)festgelegt werden können.

Wenn Sie Standardfensterstile bereitstellen möchten, die nur verwendet werden, wenn `CWindowImpl::Create`im Aufruf von keine anderen Formatvorlagen angegeben sind, verwenden Sie stattdessen [CWinTraits.](../../atl/reference/cwintraits-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="cwintraitsorgetwndstyle"></a><a name="getwndstyle"></a>CWinTraitsOR::GetWndStyle

Rufen Sie diese Funktion auf, um eine Kombination (mit `CWinTraits` dem logischen ODER-Operator) der Standardstile des Objekts und der von *t_dwStyle*angegebenen Standardstile abzurufen.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Stile, die zum Erstellen eines Fensters verwendet werden.

### <a name="return-value"></a>Rückgabewert

Eine Kombination von Stilen, die in *dwStyle* `t_dwStyle`übergeben werden, und den standarddefinierten Stilen, die von angegeben werden, mit dem logischen OR-Operator.

## <a name="cwintraitsorgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraitsOR::GetWndExStyle

Rufen Sie diese Funktion auf, um eine Kombination (mit `CWinTraits` dem logischen ODER-Operator) der erweiterten Stile des Objekts und der von `t_dwStyle`angegebenen Standardstile abzurufen.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Parameter

*dwExStyle*<br/>
Erweiterte Stile, die zum Erstellen eines Fensters verwendet werden.

### <a name="return-value"></a>Rückgabewert

Eine Kombination aus erweiterten Stilen, die in *dwExStyle* übergeben werden, und Standardstilen, die von `t_dwExStyle`angegeben werden, mit dem logischen OR-Operator

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Verstehen von Fenstereigenschaften](../../atl/understanding-window-traits.md)
