---
title: CW2WEX-Klasse
ms.date: 11/04/2016
f1_keywords:
- CW2WEX
- ATLCONV/ATL::CW2WEX
- ATLCONV/ATL::CW2WEX::CW2WEX
- ATLCONV/ATL::CW2WEX::m_psz
- ATLCONV/ATL::CW2WEX::m_szBuffer
helpviewer_keywords:
- CW2WEX class
ms.assetid: 46262e56-e0d2-41fe-855b-0b67ecc8fcd7
ms.openlocfilehash: b116775a595f9fb3612d46e19526cf1396f85002
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330347"
---
# <a name="cw2wex-class"></a>CW2WEX-Klasse

Diese Klasse wird von den Zeichenfolgenkonvertierungsmakros CW2TEX und CT2WEX sowie vom typedef CW2W verwendet.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <int t_nBufferLength = 128>
class CW2WEX
```

#### <a name="parameters"></a>Parameter

*t_nBufferLength*<br/>
Die Größe des Puffers, der im Übersetzungsprozess verwendet wird. Die Standardlänge beträgt 128 Byte.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CW2WEX::CW2WEX](#cw2wex)|Der Konstruktor.|
|[CW2WEX::-CW2WEX](#dtor)|Der Destruktor.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CW2WEX::operator LPWSTR](#operator_lpwstr)|Konvertierungsoperator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CW2WEX::m_psz](#m_psz)|Das Datenelement, das die Quellzeichenfolge speichert.|
|[CW2WEX::m_szBuffer](#m_szbuffer)|Der statische Puffer, der zum Speichern der konvertierten Zeichenfolge verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Verwenden Sie CW2TEX, CT2WEX oder CW2W in Ihrem Code, es sei denn, zusätzliche Funktionen sind erforderlich.

Diese Klasse enthält einen statischen Puffer fester Größe, der zum Speichern des Ergebnisses der Konvertierung verwendet wird. Wenn das Ergebnis zu groß ist, um in den statischen Puffer zu passen, weist die Klasse Speicher mithilfe von **malloc**zu, wodurch der Speicher freigegeben wird, wenn das Objekt den Gültigkeitsbereich verlässt. Dadurch wird sichergestellt, dass diese Klasse im Gegensatz zu Textkonvertierungsmakros, die in früheren Versionen von ATL verfügbar waren, sicher in Schleifen verwendet werden kann und den Stapel nicht überläuft.

Wenn die Klasse versucht, Speicher auf dem Heap `AtlThrow` zuzuweisen, und fehlschlägt, ruft sie mit dem Argument E_OUTOFMEMORY auf.

Standardmäßig verwenden die ATL-Konvertierungsklassen und Makros die ANSI-Codepage des aktuellen Threads für die Konvertierung.

Die folgenden Makros basieren auf dieser Klasse:

- CW2TEX

- CT2WEX

Die folgende typedef basiert auf dieser Klasse:

- CW2W

Eine Erläuterung dieser Textkonvertierungsmakros finden Sie unter [ATL- und MFC-Zeichenfolgenkonvertierungsmakros](string-conversion-macros.md).

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung dieser Zeichenfolgenkonvertierungsmakros finden Sie unter [ATL- und MFC-Zeichenfolgenkonvertierungsmakros.](string-conversion-macros.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlconv.h

## <a name="cw2wexcw2wex"></a><a name="cw2wex"></a>CW2WEX::CW2WEX

Der Konstruktor.

```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```

### <a name="parameters"></a>Parameter

*Psz*<br/>
Die zu konvertierende Textzeichenfolge.

*nCodePage*<br/>
Die Codepage. Wird in dieser Klasse nicht verwendet.

### <a name="remarks"></a>Bemerkungen

Erstellt den Puffer, der für die Übersetzung erforderlich ist.

## <a name="cw2wexcw2wex"></a><a name="dtor"></a>CW2WEX::-CW2WEX

Der Destruktor..

```
~CW2WEX() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt den zugewiesenen Puffer frei.

## <a name="cw2wexm_psz"></a><a name="m_psz"></a>CW2WEX::m_psz

Das Datenelement, das die Quellzeichenfolge speichert.

```
LPWSTR m_psz;
```

## <a name="cw2wexm_szbuffer"></a><a name="m_szbuffer"></a>CW2WEX::m_szBuffer

Der statische Puffer, der zum Speichern der konvertierten Zeichenfolge verwendet wird.

```
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="cw2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CW2WEX::operator LPWSTR

Cast-Operator.

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Textzeichenfolge als Typ LPWSTR zurück.

## <a name="see-also"></a>Siehe auch

[CA2AEX-Klasse](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX-Klasse](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX-Klasse](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX-Klasse](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX-Klasse](../../atl/reference/cw2cwex-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
