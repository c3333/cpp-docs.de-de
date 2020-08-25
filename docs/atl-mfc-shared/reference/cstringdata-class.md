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
ms.openlocfilehash: 140836f45ed2f4088bc0baed67676f93cb268d01
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832112"
---
# <a name="cstringdata-class"></a>CStringData-Klasse

Diese Klasse stellt die Daten eines Zeichen folgen Objekts dar.

## <a name="syntax"></a>Syntax

```
struct CStringData
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|Name|Beschreibung|
|-|-|
|[AddRef](#addref)|Erhöht den Verweis Zähler des Zeichen folgen-Datenobjekts.|
|[data](#data)|Ruft die Zeichendaten eines Zeichen folgen Objekts ab.|
|[IsLocked](#islocked)|Bestimmt, ob der Puffer des zugeordneten Zeichen folgen Objekts gesperrt ist.|
|[IsShared](#isshared)|Bestimmt, ob der Puffer des zugeordneten Zeichen folgen Objekts zurzeit freigegeben ist.|
|[Sperre](#lock)|Sperrt den Puffer des zugeordneten Zeichen folgen Objekts.|
|[Release](#release)|Gibt das angegebene Zeichen folgen Objekt frei.|
|[Entsperren](#unlock)|Entsperrt den Puffer des zugeordneten Zeichen folgen Objekts.|

### <a name="data-members"></a>Datenelemente

|Name|Beschreibung|
|-|-|
|[nzuweisung](#nalloclength)|Länge der zugeordneten Daten in `XCHAR` s (ohne abschließende Null)|
|[ndatalength](#ndatalength)|Länge der derzeit verwendeten Daten in `XCHAR` s (ohne abschließende Null)|
|[nrefs](#nrefs)|Der aktuelle Verweis Zähler des Objekts.|
|[pstringmgr](#pstringmgr)|Ein Zeiger auf den Zeichen folgen-Manager dieses Zeichen folgen Objekts.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse sollte nur von Entwicklern verwendet werden, die benutzerdefinierte Zeichen folgen-Manager implementieren. Weitere Informationen über benutzerdefinierte Zeichen folgen-Manager finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)

Diese Klasse kapselt verschiedene Typen von Informationen und Daten, die einem höheren Zeichen folgen Objekt zugeordnet sind, z. b. [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)-, [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)-oder [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) -Objekte. Jedes höhere Zeichen folgen Objekt enthält einen Zeiger auf das zugeordnete- `CStringData` Objekt, sodass mehrere Zeichen folgen Objekte auf dasselbe Zeichen folgen Datenobjekt verweisen können. Diese Beziehung wird durch den Verweis Zähler ( `nRefs` ) des- `CStringData` Objekts dargestellt.

> [!NOTE]
> In bestimmten Fällen wird ein Zeichen folgen- `CFixedString` Datenobjekt (z. b.) nicht von einem Zeichen folgen-Datenobjekt mit mehr als einem höheren Zeichen folgen Objekt gemeinsam verwendet. Weitere Informationen hierzu finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

Diese Daten bestehen aus:

- Der Speicher-Manager (vom Typ [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) der Zeichenfolge.

- Die aktuelle Länge ( [ndatalength](#ndatalength)) der Zeichenfolge.

- Die zugeordnete Länge ( [nzuordnungs](#nalloclength)Element) der Zeichenfolge. Aus Leistungsgründen kann sich dies von der aktuellen Zeichen folgen Länge unterscheiden.

- Der aktuelle Verweis Zähler ( [nrefs](#nrefs)) des- `CStringData` Objekts. Dieser Wert wird verwendet, um zu bestimmen, wie viele Zeichen folgen Objekte dasselbe Objekt gemeinsam verwenden `CStringData` .

- Der tatsächliche Zeichen Puffer ( [Daten](#data)) der Zeichenfolge.

   > [!NOTE]
   > Der tatsächliche Zeichen Puffer des Zeichen folgen Objekts wird vom Zeichen folgen-Manager zugeordnet und an das- `CStringData` Objekt angehängt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlsimpstr. h

## <a name="cstringdataaddref"></a><a name="addref"></a> CStringData:: adressf

Inkremente den Verweis Zähler für das Zeichen folgen Objekt.

```cpp
void AddRef() throw();
```

### <a name="remarks"></a>Bemerkungen

Inkremente den Verweis Zähler für das Zeichen folgen Objekt.

> [!NOTE]
> Diese Methode darf nicht für eine Zeichenfolge mit einem negativen Verweis Zähler aufgerufen werden, da eine negative Anzahl angibt, dass der Zeichen folgen Puffer gesperrt ist.

## <a name="cstringdatadata"></a><a name="data"></a> CStringData::d ATA

Gibt einen Zeiger auf den Zeichen Puffer eines Zeichen folgen Objekts zurück.

```cpp
void* data() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Zeichen Puffer des Zeichen folgen Objekts.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird aufgerufen, um den aktuellen Zeichen Puffer des zugeordneten Zeichen folgen Objekts zurückzugeben.

> [!NOTE]
> Dieser Puffer wird nicht durch das- `CStringData` Objekt zugeordnet, sondern durch den Zeichen folgen-Manager bei Bedarf. Wenn die Zuordnung erfolgt, wird der Puffer an das Zeichen folgen Datenobjekt angehängt.

## <a name="cstringdataislocked"></a><a name="islocked"></a> CStringData:: IsLocked

Bestimmt, ob der Zeichen Puffer gesperrt ist.

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt "true" zurück, wenn der Puffer gesperrt ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion wird ermittelt, ob der Zeichen Puffer eines Zeichen folgen Objekts zurzeit gesperrt ist.

## <a name="cstringdataisshared"></a><a name="isshared"></a> CStringData:: IsShared

Bestimmt, ob der Zeichen Puffer freigegeben ist.

```
bool IsShared() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Puffer freigegeben ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion wird ermittelt, ob der Zeichen Puffer eines Zeichen folgen-Datenobjekts derzeit von mehreren Zeichen folgen Objekten gemeinsam genutzt wird.

## <a name="cstringdatalock"></a><a name="lock"></a> CStringData:: Lock

Sperrt den Zeichen Puffer des zugeordneten Zeichen folgen Objekts.

```cpp
void Lock() throw();
```

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion wird der Zeichen Puffer des Zeichen folgen Datenobjekts gesperrt. Sperren und entsperren werden verwendet, wenn der Entwickler den direkten Zugriff auf den Zeichen Puffer benötigt. Ein gutes Beispiel für Sperren wird durch die [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) -Methode und die [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) -Methode von veranschaulicht `CSimpleStringT` .

> [!NOTE]
> Ein Zeichen Puffer kann nur gesperrt werden, wenn der Puffer nicht von höheren Zeichen folgen Objekten gemeinsam genutzt wird.

## <a name="cstringdatanalloclength"></a><a name="nalloclength"></a> CStringData:: nzuweisung

Länge des zugeordneten Zeichen Puffers.

```
int nAllocLength;
```

### <a name="remarks"></a>Bemerkungen

Speichert die Länge des zugeordneten Daten Puffers in `XCHAR` s (ohne das abschließende Null-Zeichen).

## <a name="cstringdatandatalength"></a><a name="ndatalength"></a> CStringData:: ndatalength

Die aktuelle Länge des Zeichen folgen Objekts.

```
int nDataLength;
```

### <a name="remarks"></a>Bemerkungen

Speichert die Länge der aktuell verwendeten Daten in `XCHAR` s (ohne das abschließende Null-Zeichen).

## <a name="cstringdatanrefs"></a><a name="nrefs"></a> CStringData:: nrefs

Verweis Zähler des Zeichen folgen-Datenobjekts.

```
long nRefs;
```

### <a name="remarks"></a>Bemerkungen

Speichert den Verweis Zähler des Zeichen folgen Datenobjekts. Diese Anzahl gibt die Anzahl der höheren Zeichen folgen Objekte an, die dem Zeichen folgen Datenobjekt zugeordnet sind. Ein negativer Wert gibt an, dass das Zeichen folgen Datenobjekt zurzeit gesperrt ist.

## <a name="cstringdatapstringmgr"></a><a name="pstringmgr"></a> CStringData::p stringmgr

Der Speicher-Manager des zugeordneten Zeichen folgen Objekts.

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>Bemerkungen

Speichert den Speicher-Manager für das zugeordnete String-Objekt. Weitere Informationen zu Speicher Managern und Zeichen folgen finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringdatarelease"></a><a name="release"></a> CStringData:: Release

Dekremente den Verweis Zähler des Zeichen folgen-Datenobjekts.

```cpp
void Release() throw();
```

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion wird der Verweis Zähler verringert, und die Struktur wird freigegeben, `CStringData` Wenn der Verweis Zähler Null erreicht. Dies erfolgt in der Regel, wenn ein Zeichen folgen Objekt gelöscht wird und daher nicht mehr auf das Zeichen folgen Datenobjekt verweisen muss.

Der folgende Code ruft beispielsweise `CStringData::Release` für das Zeichen folgen Datenobjekt, das zugeordnet ist, auf `str1` :

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

## <a name="cstringdataunlock"></a><a name="unlock"></a> CStringData:: Unlock

Entsperrt den Zeichen Puffer des zugeordneten Zeichen folgen Objekts.

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion wird der Zeichen Puffer des Zeichen folgen Datenobjekts entsperrt. Nachdem ein Puffer entsperrt wurde, ist er frei zugänglich und kann Verweis Zähler sein.

> [!NOTE]
> Jeder-Rückruf `Lock` muss mit einem entsprechenden-Befehl abgeglichen werden `Unlock` .

Sperren und entsperren werden verwendet, wenn der Entwickler sicherstellen muss, dass die Zeichen folgen Daten nicht freigegeben werden. Ein gutes Beispiel für Sperren wird durch die [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) -Methode und die [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) -Methode von veranschaulicht `CSimpleStringT` .

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Gemeinsam genutzte ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
