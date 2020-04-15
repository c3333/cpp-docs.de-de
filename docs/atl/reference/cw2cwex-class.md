---
title: CW2CWEX-Klasse
ms.date: 11/04/2016
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
ms.openlocfilehash: 07dd0319586054403d8ed0c8efc813b4061e355a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330438"
---
# <a name="cw2cwex-class"></a>CW2CWEX-Klasse

Diese Klasse wird von den Zeichenfolgenkonvertierungsmakros CW2CTEX und CT2CWEX sowie vom typedef CW2W verwendet.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<int t_nBufferLength = 128>
class CW2CWEX
```

#### <a name="parameters"></a>Parameter

*t_nBufferLength*<br/>
Die Größe des Puffers, der im Übersetzungsprozess verwendet wird. Die Standardlänge beträgt 128 Byte.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CW2CWEX::CW2CWEX](#cw2cwex)|Der Konstruktor.|
|[CW2CWEX::-CW2CWEX](#dtor)|Der Destruktor.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CW2CWEX::operator LPCWSTR](#operator_lpcwstr)|Konvertierungsoperator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CW2CWEX::m_psz](#m_psz)|Das Datenelement, das die Quellzeichenfolge speichert.|

## <a name="remarks"></a>Bemerkungen

Verwenden Sie CW2CTEX, CT2CWEX oder CW2W in Ihrem Code, es sei denn, zusätzliche Funktionen sind erforderlich.

Diese Klasse ist sicher in Schleifen zu verwenden und überläuft den Stapel nicht. Standardmäßig verwenden die ATL-Konvertierungsklassen und Makros die ANSI-Codepage des aktuellen Threads für die Konvertierung.

Die folgenden Makros basieren auf dieser Klasse:

- CW2CTEX

- CT2CWEX

Die folgende typedef basiert auf dieser Klasse:

- CW2W

Eine Erläuterung dieser Textkonvertierungsmakros finden Sie unter [ATL- und MFC-Zeichenfolgenkonvertierungsmakros](string-conversion-macros.md).

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung dieser Zeichenfolgenkonvertierungsmakros finden Sie unter [ATL- und MFC-Zeichenfolgenkonvertierungsmakros.](string-conversion-macros.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlconv.h

## <a name="cw2cwexcw2cwex"></a><a name="cw2cwex"></a>CW2CWEX::CW2CWEX

Der Konstruktor.

```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2CWEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parameter

*Psz*<br/>
Die zu konvertierende Textzeichenfolge.

*nCodePage*<br/>
Die Codepage. Wird in dieser Klasse nicht verwendet.

### <a name="remarks"></a>Bemerkungen

Ordnet den puffer zu, der im Übersetzungsprozess verwendet wird.

## <a name="cw2cwexcw2cwex"></a><a name="dtor"></a>CW2CWEX::-CW2CWEX

Der Destruktor.

```
~CW2CWEX() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt den zugewiesenen Puffer frei.

## <a name="cw2cwexm_psz"></a><a name="m_psz"></a>CW2CWEX::m_psz

Das Datenelement, das die Quellzeichenfolge speichert.

```
LPCWSTR m_psz;
```

## <a name="cw2cwexoperator-lpcwstr"></a><a name="operator_lpcwstr"></a>CW2CWEX::operator LPCWSTR

Konvertierungsoperator.

```
operator LPCWSTR() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Textzeichenfolge als Typ LPCWSTR zurück.

## <a name="see-also"></a>Siehe auch

[CA2AEX-Klasse](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX-Klasse](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX-Klasse](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX-Klasse](../../atl/reference/cw2aex-class.md)<br/>
[CW2WEX-Klasse](../../atl/reference/cw2wex-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
