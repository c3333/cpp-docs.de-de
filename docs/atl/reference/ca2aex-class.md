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
ms.openlocfilehash: dfd8967d21005d83b38eeae36cfc147051d7beaf
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168526"
---
# <a name="ca2aex-class"></a>CA2AEX-Klasse

Diese Klasse wird von den Zeichen folgen Konvertierungs Makros CA2TEX und CT2AEX sowie von typedef CA2A verwendet.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
template <int t_nBufferLength = 128>
class CA2AEX
```

### <a name="parameters"></a>Parameter

*t_nBufferLength*<br/>
Die Größe des Puffers, der im Übersetzungsprozess verwendet wird. Die Standardlänge beträgt 128 Bytes.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CA2AEX::CA2AEX](#ca2aex)|Der Konstruktor.|
|[CA2AEX:: ~ CA2AEX](#dtor)|Der Destruktor.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CA2AEX:: Operator LPSTR](#operator_lpstr)|Konvertierungs Operator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CA2AEX:: m_psz](#m_psz)|Der Datenmember, der die Quell Zeichenfolge speichert.|
|[CA2AEX:: m_szBuffer](#m_szbuffer)|Der statische Puffer, der zum Speichern der konvertierten Zeichenfolge verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Wenn keine zusätzliche Funktionalität erforderlich ist, verwenden Sie CA2TEX, CT2AEX oder CA2A in Ihrem eigenen Code.

Diese Klasse enthält einen statischen Puffer fester Größe, der verwendet wird, um das Ergebnis der Konvertierung zu speichern. Wenn das Ergebnis zu groß für den statischen Puffer ist, ordnet die Klasse Arbeitsspeicher mithilfe von **malloc**zu und gibt den Arbeitsspeicher frei, wenn das Objekt den Gültigkeitsbereich verlässt. Dadurch wird sichergestellt, dass diese Klasse im Gegensatz zu Text Konvertierungs Makros, die in früheren Versionen von ATL verfügbar waren, sicher in Schleifen verwendet werden kann und dass der Stapel nicht überläuft.

Wenn die Klasse versucht, Arbeitsspeicher auf dem Heap zuzuordnen, und einen Fehler verursacht `AtlThrow` , wird mit dem Argument E_OUTOFMEMORY aufgerufen.

Standardmäßig wird die ANSI-Codepage des aktuellen Threads für die Konvertierung von den ATL-Konvertierungs Klassen und-Makros verwendet.

Die folgenden Makros basieren auf dieser Klasse:

- CA2TEX

- CT2AEX

Die folgende typedef basiert auf dieser Klasse:

- CA2A

Eine Erläuterung dieser Text Konvertierungs Makros finden Sie unter [ATL-und MFC-Zeichen folgen-Konvertierungs Makros](string-conversion-macros.md).

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung dieser Zeichen folgen Konvertierungs Makros finden Sie unter [ATL-und MFC-Zeichen folgen Konvertierungs Makros](string-conversion-macros.md) .

## <a name="requirements"></a>Anforderungen

**Header:** ATL-v. h

## <a name="ca2aexca2aex"></a><a name="ca2aex"></a>CA2AEX::CA2AEX

Der Konstruktor.

```cpp
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parameter

*PSZ*<br/>
Die zu konvertierende Text Zeichenfolge.

*ncodepage*<br/>
In dieser Klasse nicht verwendet.

### <a name="remarks"></a>Bemerkungen

Erstellt den für die Übersetzung erforderlichen Puffer.

## <a name="ca2aexca2aex"></a><a name="dtor"></a>CA2AEX:: ~ CA2AEX

Der Destruktor.

```cpp
~CA2AEX() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt den zugewiesenen Puffer frei.

## <a name="ca2aexm_psz"></a><a name="m_psz"></a>CA2AEX:: m_psz

Der Datenmember, der die Quell Zeichenfolge speichert.

```cpp
LPSTR m_psz;
```

## <a name="ca2aexm_szbuffer"></a><a name="m_szbuffer"></a>CA2AEX:: m_szBuffer

Der statische Puffer, der zum Speichern der konvertierten Zeichenfolge verwendet wird.

```cpp
char m_szBuffer[ t_nBufferLength];
```

## <a name="ca2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CA2AEX:: Operator LPSTR

Konvertierungs Operator.

```cpp
operator LPSTR() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Text Zeichenfolge als LPSTR-Typ zurück.

## <a name="see-also"></a>Weitere Informationen:

[CA2CAEX-Klasse](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX-Klasse](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX-Klasse](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX-Klasse](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX-Klasse](../../atl/reference/cw2wex-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
