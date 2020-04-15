---
title: CW2AEX-Klasse
ms.date: 11/04/2016
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
ms.openlocfilehash: 849cbe5c26d7c7af7a8925a26057b5777554471d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330451"
---
# <a name="cw2aex-class"></a>CW2AEX-Klasse

Diese Klasse wird von den Zeichenfolgenkonvertierungsmakros CT2AEX, CW2TEX, CW2CTEX und CT2CAEX sowie dem typedef CW2A verwendet.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<int t_nBufferLength = 128>
class CW2AEX
```

#### <a name="parameters"></a>Parameter

*t_nBufferLength*<br/>
Die Größe des Puffers, der im Übersetzungsprozess verwendet wird. Die Standardlänge beträgt 128 Byte.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|Der Konstruktor.|
|[CW2AEX::-CW2AEX](#dtor)|Der Destruktor.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CW2AEX::operator LPSTR](#operator_lpstr)|Konvertierungsoperator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CW2AEX::m_psz](#m_psz)|Das Datenelement, das die Quellzeichenfolge speichert.|
|[CW2AEX::m_szBuffer](#m_szbuffer)|Der statische Puffer, der zum Speichern der konvertierten Zeichenfolge verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Verwenden Sie CT2AEX, CW2TEX, CW2CTEX, CT2CAEX oder CW2A in Ihrem Code, es sei denn, zusätzliche Funktionen sind erforderlich.

Diese Klasse enthält einen statischen Puffer fester Größe, der zum Speichern des Ergebnisses der Konvertierung verwendet wird. Wenn das Ergebnis zu groß ist, um in den statischen Puffer zu passen, weist die Klasse Speicher mithilfe von **malloc**zu, wodurch der Speicher freigegeben wird, wenn das Objekt den Gültigkeitsbereich verlässt. Dadurch wird sichergestellt, dass diese Klasse im Gegensatz zu Textkonvertierungsmakros, die in früheren Versionen von ATL verfügbar waren, sicher in Schleifen verwendet werden kann und den Stapel nicht überläuft.

Wenn die Klasse versucht, Speicher auf dem Heap `AtlThrow` zuzuweisen, und fehlschlägt, ruft sie mit dem Argument E_OUTOFMEMORY auf.

Standardmäßig verwenden die ATL-Konvertierungsklassen und Makros die ANSI-Codepage des aktuellen Threads für die Konvertierung. Wenn Sie dieses Verhalten für eine bestimmte Konvertierung überschreiben möchten, geben Sie die Codepage als zweiten Parameter für den Konstruktor für die Klasse an.

Die folgenden Makros basieren auf dieser Klasse:

- CT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

Die folgende typedef basiert auf dieser Klasse:

- CW2A

Eine Erläuterung dieser Textkonvertierungsmakros finden Sie unter [ATL- und MFC-Zeichenfolgenkonvertierungsmakros](string-conversion-macros.md).

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung dieser Zeichenfolgenkonvertierungsmakros finden Sie unter [ATL- und MFC-Zeichenfolgenkonvertierungsmakros.](string-conversion-macros.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlconv.h

## <a name="cw2aexcw2aex"></a><a name="cw2aex"></a>CW2AEX::CW2AEX

Der Konstruktor.

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parameter

*Psz*<br/>
Die zu konvertierende Textzeichenfolge.

*nCodePage*<br/>
Die Codepage, die zum Durchführen der Konvertierung verwendet wird. Weitere Informationen finden Sie in der Diskussion über den Codepageparameter für die Windows SDK-Funktion [MultiByteToWideChar.](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)

### <a name="remarks"></a>Bemerkungen

Ordnet den puffer zu, der im Übersetzungsprozess verwendet wird.

## <a name="cw2aexcw2aex"></a><a name="dtor"></a>CW2AEX::-CW2AEX

Der Destruktor.

```
~CW2AEX() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt den zugewiesenen Puffer frei.

## <a name="cw2aexm_psz"></a><a name="m_psz"></a>CW2AEX::m_psz

Das Datenelement, das die Quellzeichenfolge speichert.

```
LPSTR m_psz;
```

## <a name="cw2aexm_szbuffer"></a><a name="m_szbuffer"></a>CW2AEX::m_szBuffer

Der statische Puffer, der zum Speichern der konvertierten Zeichenfolge verwendet wird.

```
char m_szBuffer[t_nBufferLength];
```

## <a name="cw2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CW2AEX::operator LPSTR

Konvertierungsoperator.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Textzeichenfolge als Typ LPSTR zurück.

## <a name="see-also"></a>Siehe auch

[CA2AEX-Klasse](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX-Klasse](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX-Klasse](../../atl/reference/ca2wex-class.md)<br/>
[CW2CWEX-Klasse](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX-Klasse](../../atl/reference/cw2wex-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
