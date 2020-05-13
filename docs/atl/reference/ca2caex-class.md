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
ms.openlocfilehash: 505c1e369bc5949fea291a2172c16d5e52c75567
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168513"
---
# <a name="ca2caex-class"></a>CA2CAEX-Klasse

Diese Klasse wird von Zeichen folgen Konvertierungs Makros CA2CTEX und CT2CAEX sowie von typedef CA2CA verwendet.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
template<int t_nBufferLength = 128>
class CA2CAEX
```

### <a name="parameters"></a>Parameter

*t_nBufferLength*<br/>
Die Größe des Puffers, der im Übersetzungsprozess verwendet wird. Die Standardlänge beträgt 128 Bytes.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CA2CAEX::CA2CAEX](#ca2caex)|Der Konstruktor.|
|[CA2CAEX:: ~ CA2CAEX](#dtor)|Der Destruktor.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CA2CAEX:: Operator LPCSTR](#operator_lpcstr)|Konvertierungs Operator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CA2CAEX:: m_psz](#m_psz)|Der Datenmember, der die Quell Zeichenfolge speichert.|

## <a name="remarks"></a>Bemerkungen

Wenn keine zusätzliche Funktionalität erforderlich ist, verwenden Sie CA2CTEX, CT2CAEX oder CA2CA in Ihrem eigenen Code.

Diese Klasse kann in Schleifen sicher verwendet werden und kann den Stapel nicht überlaufen. Standardmäßig verwenden die ATL-Konvertierungsklassen und -makros für die Konvertierung die ANSI-Codeseite des aktuellen Threads.

Die folgenden Makros basieren auf dieser Klasse:

- CA2CTEX

- CT2CAEX

Die folgende typedef basiert auf dieser Klasse:

- CA2CA

Eine Erläuterung dieser Text Konvertierungs Makros finden Sie unter [ATL-und MFC-Zeichen folgen-Konvertierungs Makros](string-conversion-macros.md).

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung dieser Zeichen folgen Konvertierungs Makros finden Sie unter [ATL-und MFC-Zeichen folgen Konvertierungs Makros](string-conversion-macros.md) .

## <a name="requirements"></a>Anforderungen

**Header:** ATL-v. h

## <a name="ca2caexca2caex"></a><a name="ca2caex"></a>CA2CAEX::CA2CAEX

Der Konstruktor.

```cpp
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parameter

*PSZ*<br/>
Die zu konvertierende Text Zeichenfolge.

*ncodepage*<br/>
In dieser Klasse nicht verwendet.

### <a name="remarks"></a>Bemerkungen

Erstellt den für die Übersetzung erforderlichen Puffer.

## <a name="ca2caexca2caex"></a><a name="dtor"></a>CA2CAEX:: ~ CA2CAEX

Der Destruktor.

```cpp
~CA2CAEX() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt den zugewiesenen Puffer frei.

## <a name="ca2caexm_psz"></a><a name="m_psz"></a>CA2CAEX:: m_psz

Der Datenmember, der die Quell Zeichenfolge speichert.

```cpp
LPCSTR m_psz;
```

## <a name="ca2caexoperator-lpcstr"></a><a name="operator_lpcstr"></a>CA2CAEX:: Operator LPCSTR

Konvertierungs Operator.

```cpp
operator LPCSTR() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Text Zeichenfolge als LPCSTR-Typ zurück.

## <a name="see-also"></a>Weitere Informationen:

[CA2AEX-Klasse](../../atl/reference/ca2aex-class.md)<br/>
[CA2WEX-Klasse](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX-Klasse](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX-Klasse](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX-Klasse](../../atl/reference/cw2wex-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
