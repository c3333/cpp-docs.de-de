---
title: CComSafeArraybound-Klasse
ms.date: 05/06/2019
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
helpviewer_keywords:
- CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
ms.openlocfilehash: 2c2f8b787e5366ec893538a88049f6f53dc35caf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327381"
---
# <a name="ccomsafearraybound-class"></a>CComSafeArraybound-Klasse

Diese Klasse ist ein Wrapper für eine [SAFEARRAYBOUND-Struktur.](/windows/win32/api/oaidl/ns-oaidl-safearraybound)

## <a name="syntax"></a>Syntax

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[CComSafeArraybound](#ccomsafearraybound)|Der Konstruktor.|
|[GetCount](#getcount)|Rufen Sie diese Methode auf, um die Anzahl der Elemente zurückzugeben.|
|[Getlowerbound](#getlowerbound)|Rufen Sie diese Methode auf, um die untere Grenze zurückzugeben.|
|[Getupperbound](#getupperbound)|Rufen Sie diese Methode auf, um die obere Grenze zurückzugeben.|
|[SetCount](#setcount)|Rufen Sie diese Methode auf, um die Anzahl der Elemente festzulegen.|
|[SetLowerBound](#setlowerbound)|Rufen Sie diese Methode auf, um die Untergrenze festzulegen.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator =](#operator_eq)|Legt `CComSafeArrayBound` den wert auf.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse ist ein `SAFEARRAYBOUND` Wrapper für die von [CComSafeArray](../../atl/reference/ccomsafearray-class.md)verwendete Struktur. Es stellt Methoden zum Abfragen und Festlegen der oberen und `CComSafeArray` unteren Grenzen einer einzelnen Dimension eines Objekts und der Anzahl der darin enthaltenen Elemente bereit. Ein mehrdimensionales `CComSafeArray` Objekt `CComSafeArrayBound` verwendet ein Array von Objekten, eines für jede Dimension. Beachten Sie daher bei der Verwendung von Methoden wie [GetCount,](#getcount)dass diese Methode nicht die Gesamtzahl der Elemente in einem mehrdimensionalen Array zurückgibt.

**Header:** atlsafe.h

## <a name="requirements"></a>Anforderungen

**Header:** atlsafe.h

## <a name="ccomsafearrayboundccomsafearraybound"></a><a name="ccomsafearraybound"></a>CComSafeArraybound::CComSafeArraybound

Der Konstruktor.

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>Parameter

*ulCount*<br/>
Die Anzahl der Elemente im Array.

*lLowerBound*<br/>
Die untere Grenze, von der das Array nummeriert wird.

### <a name="remarks"></a>Bemerkungen

Wenn auf das Array von einem C++-Programm aus zugegriffen werden soll, wird empfohlen, die untere Grenze als 0 zu definieren. Es kann vorzuziehen sein, einen anderen unteren Grenzwert zu verwenden, wenn das Array mit anderen Sprachen wie Visual Basic verwendet werden soll.

## <a name="ccomsafearrayboundgetcount"></a><a name="getcount"></a>CComSafeArraybound::GetCount

Rufen Sie diese Methode auf, um die Anzahl der Elemente zurückzugeben.

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Elemente zurück.

### <a name="remarks"></a>Bemerkungen

Wenn das `CComSafeArray` zugeordnete Objekt ein mehrdimensionales Array darstellt, gibt diese Methode nur die Gesamtzahl der Elemente in der ganz rechts bemaßenden Dimension zurück. Verwenden Sie [CComSafeArray::GetCount,](../../atl/reference/ccomsafearray-class.md#getcount) um die Gesamtzahl der Elemente abzurufen.

## <a name="ccomsafearrayboundgetlowerbound"></a><a name="getlowerbound"></a>CComSafeArraybound::GetLowerbound

Rufen Sie diese Methode auf, um die untere Grenze zurückzugeben.

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Untergrenze `CComSafeArrayBound` des Objekts zurück.

## <a name="ccomsafearrayboundgetupperbound"></a><a name="getupperbound"></a>CComSafeArraybound::GetUpperbound

Rufen Sie diese Methode auf, um die obere Grenze zurückzugeben.

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die obere `CComSafeArrayBound` Grenze des Objekts zurück.

### <a name="remarks"></a>Bemerkungen

Die obere Grenze hängt von der Anzahl der Elemente und dem unteren Grenzwert ab. Wenn die untere Grenze z. B. 0 und die Anzahl der Elemente 10 ist, wird die obere Grenze automatisch auf 9 gesetzt.

## <a name="ccomsafearrayboundoperator-"></a><a name="operator_eq"></a>CComSafeArrayBound::Operator =

Legt `CComSafeArrayBound` den wert auf.

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>Parameter

*Gebunden*<br/>
Ein `CComSafeArrayBound` -Objekt.

*ulCount*<br/>
Die Anzahl der Elemente.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger `CComSafeArrayBound` auf das Objekt zurück.

### <a name="remarks"></a>Bemerkungen

Das `CComSafeArrayBound` Objekt kann mithilfe `CComSafeArrayBound`einer vorhandenen zugewiesen werden, oder indem die Anzahl der Elemente eingegeben wird, in diesem Fall ist die untere Grenze standardmäßig auf 0 festgelegt.

## <a name="ccomsafearrayboundsetcount"></a><a name="setcount"></a>CComSafeArraybound::SetCount

Rufen Sie diese Methode auf, um die Anzahl der Elemente festzulegen.

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>Parameter

*ulCount*<br/>
Die Anzahl der Elemente.

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der `CComSafeArrayBound` Elemente im Objekt zurück.

## <a name="ccomsafearrayboundsetlowerbound"></a><a name="setlowerbound"></a>CComSafeArraybound::SetLowerbound

Rufen Sie diese Methode auf, um die Untergrenze festzulegen.

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>Parameter

*lLowerBound*<br/>
Die untere Grenze.

### <a name="return-value"></a>Rückgabewert

Gibt die neue Untergrenze des `CComSafeArrayBound` Objekts zurück.

### <a name="remarks"></a>Bemerkungen

Wenn auf das Array von einem Visual C++-Programm aus zugegriffen werden soll, wird empfohlen, die untere Grenze als 0 zu definieren. Es kann vorzuziehen sein, einen anderen unteren Grenzwert zu verwenden, wenn das Array mit anderen Sprachen wie Visual Basic verwendet werden soll.

Die obere Grenze hängt von der Anzahl der Elemente und dem unteren Grenzwert ab. Wenn die untere Grenze z. B. 0 und die Anzahl der Elemente 10 ist, wird die obere Grenze automatisch auf 9 gesetzt.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
