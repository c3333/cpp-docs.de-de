---
title: CA2WEX-Klasse
ms.date: 11/04/2016
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
ms.openlocfilehash: c9123e163ca828fa71fe217e46537ceb18e6f549
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319125"
---
# <a name="ca2wex-class"></a>CA2WEX-Klasse

Diese Klasse wird von den Zeichenfolgenkonvertierungsmakros CA2TEX, CA2CTEX, CT2WEX und CT2CWEX sowie dem typedef CA2W verwendet.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <int t_nBufferLength = 128>
class CA2WEX
```

#### <a name="parameters"></a>Parameter

*t_nBufferLength*<br/>
Die Größe des Puffers, der im Übersetzungsprozess verwendet wird. Die Standardlänge beträgt 128 Byte.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CA2WEX::CA2WEX](#ca2wex)|Der Konstruktor.|
|[CA2WEX::CA2WEX](#dtor)|Der Destruktor.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CA2WEX::operator LPWSTR](#operator_lpwstr)|Konvertierungsoperator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CA2WEX::m_psz](#m_psz)|Das Datenelement, das die Quellzeichenfolge speichert.|
|[CA2WEX::m_szBuffer](#m_szbuffer)|Der statische Puffer, der zum Speichern der konvertierten Zeichenfolge verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Verwenden Sie CA2TEX, CA2CTEX, CT2WEX, CT2CWEX oder CA2W in Ihrem Code, es sei denn, zusätzliche Funktionen sind erforderlich.

Diese Klasse enthält einen statischen Puffer fester Größe, der zum Speichern des Ergebnisses der Konvertierung verwendet wird. Wenn das Ergebnis zu groß ist, um in den statischen Puffer zu passen, weist die Klasse Speicher mithilfe von **malloc**zu, wodurch der Speicher freigegeben wird, wenn das Objekt den Gültigkeitsbereich verlässt. Dadurch wird sichergestellt, dass diese Klasse im Gegensatz zu Textkonvertierungsmakros, die in früheren Versionen von ATL verfügbar waren, sicher in Schleifen verwendet werden kann und den Stapel nicht überläuft.

Wenn die Klasse versucht, Speicher auf dem Heap `AtlThrow` zuzuweisen, und fehlschlägt, ruft sie mit dem Argument E_OUTOFMEMORY auf.

Standardmäßig verwenden die ATL-Konvertierungsklassen und Makros die ANSI-Codepage des aktuellen Threads für die Konvertierung. Wenn Sie dieses Verhalten für eine bestimmte Konvertierung überschreiben möchten, geben Sie die Codepage als zweiten Parameter für den Konstruktor für die Klasse an.

Die folgenden Makros basieren auf dieser Klasse:

- CA2TEX

- CA2CTEX

- CT2WEX

- CT2CWEX

Die folgende typedef basiert auf dieser Klasse:

- CA2W

Eine Erläuterung dieser Textkonvertierungsmakros finden Sie unter [ATL- und MFC-Zeichenfolgenkonvertierungsmakros](string-conversion-macros.md).

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung dieser Zeichenfolgenkonvertierungsmakros finden Sie unter [ATL- und MFC-Zeichenfolgenkonvertierungsmakros.](string-conversion-macros.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlconv.h

## <a name="ca2wexca2wex"></a><a name="ca2wex"></a>CA2WEX::CA2WEX

Der Konstruktor.

```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parameter

*Psz*<br/>
Die zu konvertierende Textzeichenfolge.

*nCodePage*<br/>
Die Codepage, die zum Durchführen der Konvertierung verwendet wird. Weitere Informationen finden Sie in der Diskussion über den Codepageparameter für die Windows SDK-Funktion [MultiByteToWideChar.](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)

### <a name="remarks"></a>Bemerkungen

Ordnet den puffer zu, der im Übersetzungsprozess verwendet wird.

## <a name="ca2wexca2wex"></a><a name="dtor"></a>CA2WEX::CA2WEX

Der Destruktor.

```
~CA2WEX() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt den zugewiesenen Puffer frei.

## <a name="ca2wexm_psz"></a><a name="m_psz"></a>CA2WEX::m_psz

Das Datenelement, das die Quellzeichenfolge speichert.

```
LPWSTR m_psz;
```

## <a name="ca2wexm_szbuffer"></a><a name="m_szbuffer"></a>CA2WEX::m_szBuffer

Der statische Puffer, der zum Speichern der konvertierten Zeichenfolge verwendet wird.

```
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="ca2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CA2WEX::operator LPWSTR

Konvertierungsoperator.

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Textzeichenfolge als Typ LPWSTR zurück.

## <a name="see-also"></a>Siehe auch

[CA2AEX-Klasse](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX-Klasse](../../atl/reference/ca2caex-class.md)<br/>
[CW2AEX-Klasse](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX-Klasse](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX-Klasse](../../atl/reference/cw2wex-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
