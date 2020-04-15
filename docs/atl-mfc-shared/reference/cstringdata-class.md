---
title: CStringData-Klasse
ms.date: 11/04/2016
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
ms.openlocfilehash: 5915d9e25588e4e35538619662281ceaf1b35ff7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317609"
---
# <a name="cstringdata-class"></a>CStringData-Klasse

Diese Klasse stellt die Daten eines Zeichenfolgenobjekts dar.

## <a name="syntax"></a>Syntax

```
struct CStringData
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[AddRef](#addref)|Inkrementiert die Referenzanzahl des Zeichenfolgendatenobjekts.|
|[Daten](#data)|Ruft die Zeichendaten eines Zeichenfolgenobjekts ab.|
|[IsLocked](#islocked)|Bestimmt, ob der Puffer des zugeordneten Zeichenfolgenobjekts gesperrt ist.|
|[IsShared](#isshared)|Bestimmt, ob der Puffer des zugeordneten Zeichenfolgenobjekts derzeit freigegeben ist.|
|[Sperre](#lock)|Sperrt den Puffer des zugeordneten Zeichenfolgenobjekts.|
|[Release](#release)|Gibt das angegebene Zeichenfolgenobjekt frei.|
|[Entsperren](#unlock)|Entsperrt den Puffer des zugeordneten Zeichenfolgenobjekts.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|[nAllocLength](#nalloclength)|Länge der zugewiesenen Daten in `XCHAR`s (ohne Kündigung null)|
|[nDataLength](#ndatalength)|Länge der aktuell `XCHAR`verwendeten Daten in s (ohne Beenden von NULL)|
|[nRefs](#nrefs)|Die aktuelle Verweisanzahl des Objekts.|
|[pStringMgr](#pstringmgr)|Ein Zeiger auf den Zeichenfolgen-Manager dieses Zeichenfolgenobjekts.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse sollte nur von Entwicklern verwendet werden, die benutzerdefinierte Zeichenfolgen-Manager implementieren. Weitere Informationen zu benutzerdefinierten Zeichenfolgen-Managern finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)

Diese Klasse kapselt verschiedene Arten von Informationen und Daten, die einem höheren Zeichenfolgenobjekt zugeordnet sind, z. B. [CStringT-](../../atl-mfc-shared/reference/cstringt-class.md), [CSimpleStringT-](../../atl-mfc-shared/reference/csimplestringt-class.md)oder [CFixedStringT-Objekte.](../../atl-mfc-shared/reference/cfixedstringt-class.md) Jedes höhere Zeichenfolgenobjekt enthält einen `CStringData` Zeiger auf das zugeordnete Objekt, sodass mehrere Zeichenfolgenobjekte auf dasselbe Zeichenfolgendatenobjekt verweisen können. Diese Beziehung wird durch die`nRefs`Referenzanzahl `CStringData` ( ) des Objekts dargestellt.

> [!NOTE]
> In bestimmten Fällen gibt ein `CFixedString`Zeichenfolgentyp (z. B. ) kein Zeichenfolgendatenobjekt für mehr als ein höheres Zeichenfolgenobjekt gemeinsam. Weitere Informationen hierzu finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

Diese Daten setzen sich zusammen aus:

- Der Speicher-Manager (vom Typ [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) der Zeichenfolge.

- Die aktuelle Länge ( [nDataLength](#ndatalength)) der Zeichenfolge.

- Die zugewiesene Länge ( [nAllocLength](#nalloclength)) der Zeichenfolge. Aus Leistungsgründen kann dies von der aktuellen Stringlänge abweichen.

- Die aktuelle Referenzanzahl ( [nRefs](#nrefs)) des `CStringData` Objekts. Dieser Wert wird verwendet, um zu bestimmen, wie viele Zeichenfolgenobjekte dasselbe `CStringData` Objekt gemeinsam verwenden.

- Der tatsächliche Zeichenpuffer ( [Daten](#data)) der Zeichenfolge.

   > [!NOTE]
   > Der eigentliche Zeichenpuffer des Zeichenfolgenobjekts wird vom Zeichenfolgen-Manager zugewiesen und an das `CStringData` Objekt angehängt.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsimpstr.h

## <a name="cstringdataaddref"></a><a name="addref"></a>CStringData::AddRef

Inkrementiert die Referenzanzahl des Zeichenfolgenobjekts.

```
void AddRef() throw();
```

### <a name="remarks"></a>Bemerkungen

Inkrementiert die Referenzanzahl des Zeichenfolgenobjekts.

> [!NOTE]
> Rufen Sie diese Methode nicht für eine Zeichenfolge mit einer negativen Verweisanzahl auf, da eine negative Anzahl angibt, dass der Zeichenfolgenpuffer gesperrt ist.

## <a name="cstringdatadata"></a><a name="data"></a>CStringData::data

Gibt einen Zeiger auf den Zeichenpuffer eines Zeichenfolgenobjekts zurück.

```
void* data() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Zeichenpuffer des Zeichenfolgenobjekts.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um den aktuellen Zeichenpuffer des zugeordneten Zeichenfolgenobjekts zurückzugeben.

> [!NOTE]
> Dieser Puffer wird nicht `CStringData` vom Objekt, sondern bei Bedarf vom Zeichenfolgen-Manager zugewiesen. Bei der Zuweisung wird der Puffer an das Zeichenfolgendatenobjekt angehängt.

## <a name="cstringdataislocked"></a><a name="islocked"></a>CStringData::IsLocked

Bestimmt, ob der Zeichenpuffer gesperrt ist.

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Puffer gesperrt ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um zu bestimmen, ob der Zeichenpuffer eines Zeichenfolgenobjekts derzeit gesperrt ist.

## <a name="cstringdataisshared"></a><a name="isshared"></a>CStringData::IsShared

Bestimmt, ob der Zeichenpuffer freigegeben ist.

```
bool IsShared() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Puffer freigegeben ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um zu bestimmen, ob der Zeichenpuffer eines Zeichenfolgendatenobjekts derzeit von mehreren Zeichenfolgenobjekten gemeinsam genutzt wird.

## <a name="cstringdatalock"></a><a name="lock"></a>CStringData::Sperren

Sperrt den Zeichenpuffer des zugeordneten Zeichenfolgenobjekts.

```
void Lock() throw();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um den Zeichenpuffer des Zeichenfolgendatenobjekts zu sperren. Sperren und Entsperren wird verwendet, wenn der Entwickler direkten Zugriff auf den Zeichenpuffer benötigt. Ein gutes Beispiel für das Sperren wird durch `CSimpleStringT`die [LockBuffer-](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) und [UnlockBuffer-Methoden](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) von demonstriert.

> [!NOTE]
> Ein Zeichenpuffer kann nur gesperrt werden, wenn der Puffer nicht von höheren Zeichenfolgenobjekten gemeinsam genutzt wird.

## <a name="cstringdatanalloclength"></a><a name="nalloclength"></a>CStringData::nAllocLength

Länge des zugewiesenen Zeichenpuffers.

```
int nAllocLength;
```

### <a name="remarks"></a>Bemerkungen

Speichert die Länge des zugewiesenen Datenpuffers in `XCHAR`s (ohne Beenden von NULL).

## <a name="cstringdatandatalength"></a><a name="ndatalength"></a>CStringData::nDataLength

Aktuelle Länge des Zeichenfolgenobjekts.

```
int nDataLength;
```

### <a name="remarks"></a>Bemerkungen

Speichert die Länge der `XCHAR`aktuell verwendeten Daten in s (ohne Beenden von NULL).

## <a name="cstringdatanrefs"></a><a name="nrefs"></a>CStringData::nRefs

Referenzanzahl des Zeichenfolgendatenobjekts.

```
long nRefs;
```

### <a name="remarks"></a>Bemerkungen

Speichert die Referenzanzahl des Zeichenfolgendatenobjekts. Diese Anzahl gibt die Anzahl der höheren Zeichenfolgenobjekte an, die dem Zeichenfolgendatenobjekt zugeordnet sind. Ein negativer Wert gibt an, dass das Zeichenfolgendatenobjekt derzeit gesperrt ist.

## <a name="cstringdatapstringmgr"></a><a name="pstringmgr"></a>CStringData::pStringMgr

Der Speicher-Manager des zugeordneten Zeichenfolgenobjekts.

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>Bemerkungen

Speichert den Speicher-Manager für das zugeordnete Zeichenfolgenobjekt. Weitere Informationen zu Speicher-Managern und Zeichenfolgen finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringdatarelease"></a><a name="release"></a>CStringData::Release

Dekrementiert die Referenzanzahl des Zeichenfolgendatenobjekts.

```
void Release() throw();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um die `CStringData` Referenzanzahl zu dekremenieren, wodurch die Struktur frei wird, wenn die Referenzanzahl null erreicht. Dies geschieht häufig, wenn ein Zeichenfolgenobjekt gelöscht wird und daher nicht mehr auf das Zeichenfolgendatenobjekt verweisen muss.

Der folgende Code würde `CStringData::Release` z. B. das `str1`Zeichenfolgendatenobjekt aufrufen, das folgenden Themen zugeordnet ist:

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

## <a name="cstringdataunlock"></a><a name="unlock"></a>CStringData::Entsperren

Entsperrt den Zeichenpuffer des zugeordneten Zeichenfolgenobjekts.

```
void Unlock() throw();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um den Zeichenpuffer des Zeichenfolgendatenobjekts zu entsperren. Sobald ein Puffer entsperrt ist, kann er gemeinsam freigegeben werden und kann als Referenz gezählt werden.

> [!NOTE]
> Jeder Aufruf `Lock` muss mit einem entsprechenden `Unlock`Aufruf von übereinstimmen.

Sperren und Entsperren wird verwendet, wenn der Entwickler sicherstellen muss, dass die Zeichenfolgendaten nicht freigegeben werden. Ein gutes Beispiel für das Sperren wird durch `CSimpleStringT`die [LockBuffer-](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) und [UnlockBuffer-Methoden](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) von demonstriert.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[FREIGEGEBENe ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
