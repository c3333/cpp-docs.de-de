---
title: CHeapPtrBase-Klasse
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
helpviewer_keywords:
- CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
ms.openlocfilehash: 62cabf281473cdf21fe260fa23082bc55f339849
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326907"
---
# <a name="cheapptrbase-class"></a>CHeapPtrBase-Klasse

Diese Klasse bildet die Grundlage für mehrere intelligente Heapzeigerklassen.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class T, class Allocator = CCRTAllocator>
class CHeapPtrBase
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Objekttyp, der auf dem Heap gespeichert werden soll.

*Zuweisung*<br/>
Die zu verwendende Speicherzuweisungsklasse. Standardmäßig werden CRT-Routinen verwendet, um Speicher zuzuweisen und freizugeben.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHeapPtrBase::'CHeapPtrBase](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHeapPtrBase::AllocateBytes](#allocatebytes)|Rufen Sie diese Methode auf, um Speicher zuzuweisen.|
|[CHeapPtrBase::Anfügen](#attach)|Rufen Sie diese Methode auf, um die Besitzverhältnisse eines vorhandenen Zeigers zu übernehmen.|
|[CHeapPtrBase::Detach](#detach)|Rufen Sie diese Methode auf, um den Besitz eines Zeigers freizugeben.|
|[CHeapPtrBase::Kostenlos](#free)|Rufen Sie diese Methode auf, `CHeapPtrBase`um ein Objekt zu löschen, auf das von einem verwiesen wird.|
|[CHeapPtrBase::ReallocateBytes](#reallocatebytes)|Rufen Sie diese Methode auf, um Denspeicher neu zuzuweisen.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHeapPtrBase::operator T*](#operator_t_star)|Der Gussoperator.|
|[CHeapPtrBase::Operator &](#operator_amp)|Der Operator &.|
|[CHeapPtrBase::operator ->](#operator_ptr)|Der Zeiger-zu-Member-Operator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHeapPtrBase::m_pData](#m_pdata)|Die Zeigerdatenmembervariable.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse bildet die Grundlage für mehrere intelligente Heapzeigerklassen. Die abgeleiteten Klassen, z. B. [CHeapPtr](../../atl/reference/cheapptr-class.md) und [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), fügen eigene Konstruktoren und Operatoren hinzu. In diesen Klassen finden Sie Implementierungsbeispiele.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcore.h

## <a name="cheapptrbaseallocatebytes"></a><a name="allocatebytes"></a>CHeapPtrBase::AllocateBytes

Rufen Sie diese Methode auf, um Speicher zuzuweisen.

```
bool AllocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Parameter

*nBytes*<br/>
Die Anzahl der zuzuweisenden Bytes an Arbeitsspeicher.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Speicher erfolgreich zugewiesen wurde, andernfalls false.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn die [Membervariable CHeapPtrBase::m_pData](#m_pdata) derzeit auf einen vorhandenen Wert verweist. das heißt, es ist nicht gleich NULL.

## <a name="cheapptrbaseattach"></a><a name="attach"></a>CHeapPtrBase::Anfügen

Rufen Sie diese Methode auf, um die Besitzverhältnisse eines vorhandenen Zeigers zu übernehmen.

```
void Attach(T* pData) throw();
```

### <a name="parameters"></a>Parameter

*pData*<br/>
Das `CHeapPtrBase` Objekt übernimmt den Besitz dieses Zeigers.

### <a name="remarks"></a>Bemerkungen

Wenn `CHeapPtrBase` ein Objekt den Besitz eines Zeigers übernimmt, löscht es automatisch den Zeiger und alle zugeordneten Daten, wenn es den Gültigkeitsbereich verlässt.

In Debugbuilds tritt ein Assertionsfehler auf, wenn die [Membervariable CHeapPtrBase::m_pData](#m_pdata) derzeit auf einen vorhandenen Wert verweist. das heißt, es ist nicht gleich NULL.

## <a name="cheapptrbasecheapptrbase"></a><a name="dtor"></a>CHeapPtrBase::'CHeapPtrBase

Der Destruktor.

```
~CHeapPtrBase() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei.

## <a name="cheapptrbasedetach"></a><a name="detach"></a>CHeapPtrBase::Detach

Rufen Sie diese Methode auf, um den Besitz eines Zeigers freizugeben.

```
T* Detach() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt eine Kopie des Zeigers zurück.

### <a name="remarks"></a>Bemerkungen

Gibt den Besitz eines Zeigers frei, legt die [Membervariable CHeapPtrBase::m_pData](#m_pdata) auf NULL fest und gibt eine Kopie des Zeigers zurück.

## <a name="cheapptrbasefree"></a><a name="free"></a>CHeapPtrBase::Kostenlos

Rufen Sie diese Methode auf, `CHeapPtrBase`um ein Objekt zu löschen, auf das von einem verwiesen wird.

```
void Free() throw();
```

### <a name="remarks"></a>Bemerkungen

Das Objekt, auf `CHeapPtrBase` das der zeigt, wird freigegeben, und die Membervariable [CHeapPtrBase::m_pData](#m_pdata) wird auf NULL gesetzt.

## <a name="cheapptrbasem_pdata"></a><a name="m_pdata"></a>CHeapPtrBase::m_pData

Die Zeigerdatenmembervariable.

```
T* m_pData;
```

### <a name="remarks"></a>Bemerkungen

Diese Membervariable enthält die Zeigerinformationen.

## <a name="cheapptrbaseoperator-amp"></a><a name="operator_amp"></a>CHeapPtrBase::Operator&amp;

Der Operator &.

```
T** operator&() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Adresse des Objekts `CHeapPtrBase` zurück, auf das das Objekt zeigt.

## <a name="cheapptrbaseoperator--gt"></a><a name="operator_ptr"></a>CHeapPtrBase::Operator -&gt;

Der Zeiger-zu-Member-Operator.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Wert der [Membervariablen CHeapPtrBase::m_pData](#m_pdata) zurück.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Operator, um eine Methode `CHeapPtrBase` in einer Klasse aufzurufen, auf die das Objekt zeigt. In Debugbuilds tritt ein Assertionsfehler auf, wenn die `CHeapPtrBase` Punkte auf NULL gesetzt werden.

## <a name="cheapptrbaseoperator-t"></a><a name="operator_t_star"></a>CHeapPtrBase::operator T*

Der Gussoperator.

```
operator T*() const throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt [CHeapPtrBase::m_pData](#m_pdata)zurück.

## <a name="cheapptrbasereallocatebytes"></a><a name="reallocatebytes"></a>CHeapPtrBase::ReallocateBytes

Rufen Sie diese Methode auf, um Denspeicher neu zuzuweisen.

```
bool ReallocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Parameter

*nBytes*<br/>
Die neue Speichermenge, die in Bytes zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Speicher erfolgreich zugewiesen wurde, andernfalls false.

## <a name="see-also"></a>Siehe auch

[CHeapPtr-Klasse](../../atl/reference/cheapptr-class.md)<br/>
[CComHeapPtr-Klasse](../../atl/reference/ccomheapptr-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
