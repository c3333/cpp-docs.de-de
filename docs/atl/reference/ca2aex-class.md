---
title: CA2AEX-Klasse
ms.date: 11/04/2016
f1_keywords:
- CA2AEX
- ATLCONV/ATL::CA2AEX
- ATLCONV/ATL::CA2AEX::CA2AEX
- ATLCONV/ATL::CA2AEX::m_psz
- ATLCONV/ATL::CA2AEX::m_szBuffer
helpviewer_keywords:
- CA2AEX class
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
ms.openlocfilehash: 4f8b9f91e9bc499523fe3484bc76325e2efb8140
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319182"
---
# <a name="ca2aex-class"></a>CA2AEX-Klasse

Diese Klasse wird von den Zeichenfolgenkonvertierungsmakros CA2TEX und CT2AEX sowie vom typedef CA2A verwendet.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <int t_nBufferLength = 128>
class CA2AEX
```

#### <a name="parameters"></a>Parameter

*t_nBufferLength*<br/>
Die Größe des Puffers, der im Übersetzungsprozess verwendet wird. Die Standardlänge beträgt 128 Byte.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CA2AEX::CA2AEX](#ca2aex)|Der Konstruktor.|
|[CA2AEX::CA2AEX](#dtor)|Der Destruktor.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CA2AEX::operator LPSTR](#operator_lpstr)|Konvertierungsoperator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CA2AEX::m_psz](#m_psz)|Das Datenelement, das die Quellzeichenfolge speichert.|
|[CA2AEX::m_szBuffer](#m_szbuffer)|Der statische Puffer, der zum Speichern der konvertierten Zeichenfolge verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Verwenden Sie CA2TEX, CT2AEX oder CA2A in Ihrem eigenen Code, es sei denn, zusätzliche Funktionen sind erforderlich.

Diese Klasse enthält einen statischen Puffer fester Größe, der zum Speichern des Ergebnisses der Konvertierung verwendet wird. Wenn das Ergebnis zu groß ist, um in den statischen Puffer zu passen, weist die Klasse Speicher mithilfe von **malloc**zu, wodurch der Speicher freigegeben wird, wenn das Objekt den Gültigkeitsbereich verlässt. Dadurch wird sichergestellt, dass diese Klasse im Gegensatz zu Textkonvertierungsmakros, die in früheren Versionen von ATL verfügbar waren, sicher in Schleifen verwendet werden kann und den Stapel nicht überläuft.

Wenn die Klasse versucht, Speicher auf dem Heap `AtlThrow` zuzuweisen, und fehlschlägt, ruft sie mit dem Argument E_OUTOFMEMORY auf.

Standardmäßig verwenden die ATL-Konvertierungsklassen und Makros die ANSI-Codepage des aktuellen Threads für die Konvertierung.

Die folgenden Makros basieren auf dieser Klasse:

- CA2TEX

- CT2AEX

Die folgende typedef basiert auf dieser Klasse:

- CA2A

Eine Erläuterung dieser Textkonvertierungsmakros finden Sie unter [ATL- und MFC-Zeichenfolgenkonvertierungsmakros](string-conversion-macros.md).

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung dieser Zeichenfolgenkonvertierungsmakros finden Sie unter [ATL- und MFC-Zeichenfolgenkonvertierungsmakros.](string-conversion-macros.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlconv.h

## <a name="ca2aexca2aex"></a><a name="ca2aex"></a>CA2AEX::CA2AEX

Der Konstruktor.

```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parameter

*Psz*<br/>
Die zu konvertierende Textzeichenfolge.

*nCodePage*<br/>
Nicht verwendet in dieser Klasse.

### <a name="remarks"></a>Bemerkungen

Erstellt den Puffer, der für die Übersetzung erforderlich ist.

## <a name="ca2aexca2aex"></a><a name="dtor"></a>CA2AEX::CA2AEX

Der Destruktor.

```
~CA2AEX() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt den zugewiesenen Puffer frei.

## <a name="ca2aexm_psz"></a><a name="m_psz"></a>CA2AEX::m_psz

Das Datenelement, das die Quellzeichenfolge speichert.

```
LPSTR m_psz;
```

## <a name="ca2aexm_szbuffer"></a><a name="m_szbuffer"></a>CA2AEX::m_szBuffer

Der statische Puffer, der zum Speichern der konvertierten Zeichenfolge verwendet wird.

```
char m_szBuffer[ t_nBufferLength];
```

## <a name="ca2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CA2AEX::operator LPSTR

Konvertierungsoperator.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Textzeichenfolge als Typ LPSTR zurück.

## <a name="see-also"></a>Siehe auch

[CA2CAEX-Klasse](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX-Klasse](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX-Klasse](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX-Klasse](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX-Klasse](../../atl/reference/cw2wex-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
