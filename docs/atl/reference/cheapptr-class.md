---
title: CHeapPtr-Klasse
ms.date: 11/04/2016
f1_keywords:
- CHeapPtr
- ATLCORE/ATL::CHeapPtr
- ATLCORE/ATL::CHeapPtr::CHeapPtr
- ATLCORE/ATL::CHeapPtr::Allocate
- ATLCORE/ATL::CHeapPtr::Reallocate
helpviewer_keywords:
- CHeapPtr class
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
ms.openlocfilehash: a512aa974cb57072915f887f0c2a20ed1263ffa3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326914"
---
# <a name="cheapptr-class"></a>CHeapPtr-Klasse

Eine intelligente Zeigerklasse zum Verwalten von Heapzeigern.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<typename T, class Allocator=CCRTAllocator>
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Objekttyp, der auf dem Heap gespeichert werden soll.

*Zuweisung*<br/>
Die zu verwendende Speicherzuweisungsklasse.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHeapPtr::CHeapPtr](#cheapptr)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHeapPtr::Zuweisen](#allocate)|Rufen Sie diese Methode auf, um Speicher auf dem Heap zum Speichern von Objekten zuzuweisen.|
|[CHeapPtr::Neuzuordnen](#reallocate)|Rufen Sie diese Methode auf, um den Speicher auf dem Heap neu zuzuweisen.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHeapPtr::operator =](#operator_eq)|Der Zuweisungsoperator.|

## <a name="remarks"></a>Bemerkungen

`CHeapPtr`wird von [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) abgeleitet und verwendet standardmäßig die CRT-Routinen (in [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)), um Speicher zuzuweisen und freizugeben. Die Klasse [CHeapPtrList](../../atl/reference/cheapptrlist-class.md) kann verwendet werden, um eine Liste von Heapzeigern zu erstellen. Siehe auch [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), das COM-Speicherzuweisungsroutinen verwendet.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcore.h

## <a name="cheapptrallocate"></a><a name="allocate"></a>CHeapPtr::Zuweisen

Rufen Sie diese Methode auf, um Speicher auf dem Heap zum Speichern von Objekten zuzuweisen.

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>Parameter

*nElements*<br/>
Die Anzahl der Elemente, die zum Berechnen der zuzuweisenden Speichermenge verwendet werden. Der Standardwert ist 1.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Speicher erfolgreich zugewiesen wurde, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Die Zuweisungsroutinen werden verwendet, um genügend Speicher auf dem Heap zu reservieren, um *nElement-Objekte* eines im Konstruktor definierten Typs zu speichern.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

## <a name="cheapptrcheapptr"></a><a name="cheapptr"></a>CHeapPtr::CHeapPtr

Der Konstruktor.

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein vorhandener Heapzeiger oder `CHeapPtr`.

### <a name="remarks"></a>Bemerkungen

Der Heapzeiger kann optional mit einem vorhandenen Zeiger `CHeapPtr` oder einem Objekt erstellt werden. Wenn dies `CHeapPtr` der Zuspruch bereits der Falle ist, übernimmt das neue Objekt die Verantwortung für die Verwaltung des neuen Zeigers und der neuen Ressourcen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

## <a name="cheapptroperator-"></a><a name="operator_eq"></a>CHeapPtr::operator =

Zuweisungsoperator.

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein vorhandenes `CHeapPtr`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis `CHeapPtr`auf die aktualisierte zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

## <a name="cheapptrreallocate"></a><a name="reallocate"></a>CHeapPtr::Neuzuordnen

Rufen Sie diese Methode auf, um den Speicher auf dem Heap neu zuzuweisen.

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>Parameter

*nElements*<br/>
Die neue Anzahl von Elementen, die zum Berechnen der zuzuweisenden Speichermenge verwendet werden.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Speicher erfolgreich zugewiesen wurde, false bei einem Fehler.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>Siehe auch

[CHeapPtrBase-Klasse](../../atl/reference/cheapptrbase-class.md)<br/>
[CCRTAllocator-Klasse](../../atl/reference/ccrtallocator-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
