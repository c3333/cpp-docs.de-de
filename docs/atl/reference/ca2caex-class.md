---
title: CA2CAEX-Klasse
ms.date: 11/04/2016
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
ms.openlocfilehash: e6c727993b2907aaa551421a5d2d23e372b68917
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319143"
---
# <a name="ca2caex-class"></a>CA2CAEX-Klasse

Diese Klasse wird von den Zeichenfolgenkonvertierungsmakros CA2CTEX und CT2CAEX sowie dem typedef CA2CA verwendet.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<int t_nBufferLength = 128>
class CA2CAEX
```

#### <a name="parameters"></a>Parameter

*t_nBufferLength*<br/>
Die Größe des Puffers, der im Übersetzungsprozess verwendet wird. Die Standardlänge beträgt 128 Byte.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CA2CAEX::CA2CAEX](#ca2caex)|Der Konstruktor.|
|[CA2CAEX::CA2CAEX](#dtor)|Der Destruktor.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CA2CAEX::operator LPCSTR](#operator_lpcstr)|Konvertierungsoperator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CA2CAEX::m_psz](#m_psz)|Das Datenelement, das die Quellzeichenfolge speichert.|

## <a name="remarks"></a>Bemerkungen

Verwenden Sie CA2CTEX, CT2CAEX oder CA2CA in Ihrem eigenen Code, es sei denn, zusätzliche Funktionen sind erforderlich.

Diese Klasse ist sicher in Schleifen zu verwenden und überläuft den Stapel nicht. Standardmäßig verwenden die ATL-Konvertierungsklassen und -makros für die Konvertierung die ANSI-Codeseite des aktuellen Threads.

Die folgenden Makros basieren auf dieser Klasse:

- CA2CTEX

- CT2CAEX

Die folgende typedef basiert auf dieser Klasse:

- CA2CA

Eine Erläuterung dieser Textkonvertierungsmakros finden Sie unter [ATL- und MFC-Zeichenfolgenkonvertierungsmakros](string-conversion-macros.md).

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung dieser Zeichenfolgenkonvertierungsmakros finden Sie unter [ATL- und MFC-Zeichenfolgenkonvertierungsmakros.](string-conversion-macros.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlconv.h

## <a name="ca2caexca2caex"></a><a name="ca2caex"></a>CA2CAEX::CA2CAEX

Der Konstruktor.

```
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parameter

*Psz*<br/>
Die zu konvertierende Textzeichenfolge.

*nCodePage*<br/>
Nicht verwendet in dieser Klasse.

### <a name="remarks"></a>Bemerkungen

Erstellt den Puffer, der für die Übersetzung erforderlich ist.

## <a name="ca2caexca2caex"></a><a name="dtor"></a>CA2CAEX::CA2CAEX

Der Destruktor.

```
~CA2CAEX() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt den zugewiesenen Puffer frei.

## <a name="ca2caexm_psz"></a><a name="m_psz"></a>CA2CAEX::m_psz

Das Datenelement, das die Quellzeichenfolge speichert.

```
LPCSTR m_psz;
```

## <a name="ca2caexoperator-lpcstr"></a><a name="operator_lpcstr"></a>CA2CAEX::operator LPCSTR

Konvertierungsoperator.

```
operator LPCSTR() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Textzeichenfolge als Typ LPCSTR zurück.

## <a name="see-also"></a>Siehe auch

[CA2AEX-Klasse](../../atl/reference/ca2aex-class.md)<br/>
[CA2WEX-Klasse](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX-Klasse](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX-Klasse](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX-Klasse](../../atl/reference/cw2wex-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
