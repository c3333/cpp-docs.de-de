---
title: CDefaultCharTraits-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
ms.openlocfilehash: 40c4d107d05e6d7b610e7c46be920d91d8fe6086
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327095"
---
# <a name="cdefaultchartraits-class"></a>CDefaultCharTraits-Klasse

Diese Klasse bietet zwei statische Funktionen zum Konvertieren von Zeichen zwischen Groß- und Kleinbuchstaben.

## <a name="syntax"></a>Syntax

```
template <typename T>
class CDefaultCharTraits
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der Daten, die in der Auflistung gespeichert werden sollen.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDefaultCharTraits::CharToLower](#chartolower)|(Statisch) Rufen Sie diese Funktion auf, um ein Zeichen in Großbuchstaben zu konvertieren.|
|[CDefaultCharTraits::CharToUpper](#chartoupper)|(Statisch) Rufen Sie diese Funktion auf, um ein Zeichen in Kleinbuchstaben zu konvertieren.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt Funktionen bereit, die von der Klasse [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)verwendet werden.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="cdefaultchartraitschartolower"></a><a name="chartolower"></a>CDefaultCharTraits::CharToLower

Rufen Sie diese Funktion auf, um ein Zeichen in Kleinbuchstaben zu konvertieren.

```
static wchar_t CharToLower(wchar_t x);
static char CharToLower(char x);
```

### <a name="parameters"></a>Parameter

*X*<br/>
Das in einen Kleinbuchstaben umzuwandelnde Zeichen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]

## <a name="cdefaultchartraitschartoupper"></a><a name="chartoupper"></a>CDefaultCharTraits::CharToUpper

Rufen Sie diese Funktion auf, um ein Zeichen in Großbuchstaben zu konvertieren.

```
static wchar_t CharToUpper(wchar_t x);
static char CharToUpper(char x);
```

### <a name="parameters"></a>Parameter

*X*<br/>
Das in einen Großbuchstaben umzuwandelnde Zeichen.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
