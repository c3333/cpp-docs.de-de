---
title: CComSafeArrayBound-Klasse
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
ms.openlocfilehash: 9adee1e8b6a46c239aaf6a3c404277b34efd00e2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834751"
---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound-Klasse

Diese Klasse ist ein Wrapper für eine [SAFEARRAYBOUND](/windows/win32/api/oaidl/ns-oaidl-safearraybound) -Struktur.

## <a name="syntax"></a>Syntax

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|Funktion|Beschreibung|
|-|-|
|[CComSafeArrayBound](#ccomsafearraybound)|Der Konstruktor.|
|[GetCount](#getcount)|Mit dieser Methode wird die Anzahl der Elemente zurückgegeben.|
|[GetLowerBound](#getlowerbound)|Ruft diese Methode auf, um die untere Grenze zurückzugeben.|
|[GetUpperBound](#getupperbound)|Ruft diese Methode auf, um die obere Grenze zurückzugeben.|
|[SetCount](#setcount)|Mit dieser Methode wird die Anzahl der Elemente festgelegt.|
|[Setlowerbound](#setlowerbound)|Ruft diese Methode auf, um die untere Grenze festzulegen.|

### <a name="operators"></a>Operatoren

|Operator|Beschreibung|
|-|-|
|[Operator =](#operator_eq)|Legt den `CComSafeArrayBound` auf einen neuen Wert fest.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse ist ein Wrapper für die `SAFEARRAYBOUND` von [CComSafeArray](../../atl/reference/ccomsafearray-class.md)verwendete Struktur. Es stellt Methoden zum Abfragen und Festlegen der oberen und unteren Grenzen einer einzelnen Dimension eines `CComSafeArray` -Objekts und der Anzahl der enthaltenen Elemente bereit. Ein mehrdimensionales `CComSafeArray` Objekt verwendet ein Array von- `CComSafeArrayBound` Objekten, eines für jede Dimension. Beachten Sie daher bei der Verwendung von Methoden wie [GetCount](#getcount), dass diese Methode nicht die Gesamtanzahl von Elementen in einem mehrdimensionalen Array zurückgibt.

**Header:** atlsafe.h

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlsafe.h

## <a name="ccomsafearrayboundccomsafearraybound"></a><a name="ccomsafearraybound"></a> CComSafeArrayBound:: CComSafeArrayBound

Der Konstruktor.

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>Parameter

*ulcount*<br/>
Die Anzahl der Elemente im Array.

*llowerbound*<br/>
Die untere Grenze, von der das Array nummeriert wird.

### <a name="remarks"></a>Bemerkungen

Wenn von einem C++-Programm aus auf das Array zugegriffen werden soll, wird empfohlen, die untere Grenze als 0 (null) zu definieren. Es ist möglicherweise vorzuziehen, einen anderen niedrigeren Grenzwert zu verwenden, wenn das Array mit anderen Sprachen verwendet werden soll, z. b. Visual Basic.

## <a name="ccomsafearrayboundgetcount"></a><a name="getcount"></a> CComSafeArrayBound:: GetCount

Mit dieser Methode wird die Anzahl der Elemente zurückgegeben.

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Elemente zurück.

### <a name="remarks"></a>Bemerkungen

Wenn das zugeordnete- `CComSafeArray` Objekt ein mehrdimensionales Array darstellt, gibt diese Methode nur die Gesamtzahl der Elemente in der äußersten rechten Dimension zurück. Verwenden Sie [CComSafeArray:: GetCount](../../atl/reference/ccomsafearray-class.md#getcount) zum Abrufen der Gesamtanzahl von Elementen.

## <a name="ccomsafearrayboundgetlowerbound"></a><a name="getlowerbound"></a> CComSafeArrayBound:: GetLowerBound

Ruft diese Methode auf, um die untere Grenze zurückzugeben.

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die untere Grenze des- `CComSafeArrayBound` Objekts zurück.

## <a name="ccomsafearrayboundgetupperbound"></a><a name="getupperbound"></a> CComSafeArrayBound:: GetUpperBound

Ruft diese Methode auf, um die obere Grenze zurückzugeben.

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die obere Grenze des- `CComSafeArrayBound` Objekts zurück.

### <a name="remarks"></a>Bemerkungen

Die obere Grenze hängt von der Anzahl der Elemente und dem unteren gebundenen Wert ab. Wenn die untere Grenze beispielsweise 0 und die Anzahl der Elemente 10 ist, wird die obere Grenze automatisch auf 9 festgelegt.

## <a name="ccomsafearrayboundoperator-"></a><a name="operator_eq"></a> CComSafeArrayBound:: Operator =

Legt den `CComSafeArrayBound` auf einen neuen Wert fest.

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>Parameter

*binden*<br/>
Ein `CComSafeArrayBound`-Objekt.

*ulcount*<br/>
Die Anzahl der Elemente.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf das- `CComSafeArrayBound` Objekt zurück.

### <a name="remarks"></a>Bemerkungen

Das- `CComSafeArrayBound` Objekt kann mithilfe eines vorhandenen `CComSafeArrayBound` oder durch Angabe der Anzahl von Elementen zugewiesen werden. in diesem Fall wird die untere Grenze standardmäßig auf 0 festgelegt.

## <a name="ccomsafearrayboundsetcount"></a><a name="setcount"></a> CComSafeArrayBound:: SetCount

Mit dieser Methode wird die Anzahl der Elemente festgelegt.

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>Parameter

*ulcount*<br/>
Die Anzahl der Elemente.

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Elemente im- `CComSafeArrayBound` Objekt zurück.

## <a name="ccomsafearrayboundsetlowerbound"></a><a name="setlowerbound"></a> CComSafeArrayBound:: setlowerbound

Ruft diese Methode auf, um die untere Grenze festzulegen.

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>Parameter

*llowerbound*<br/>
Die untere Grenze.

### <a name="return-value"></a>Rückgabewert

Gibt die neue untere Grenze des- `CComSafeArrayBound` Objekts zurück.

### <a name="remarks"></a>Bemerkungen

Wenn auf das Array von einem Visual C++-Programm aus zugegriffen werden soll, wird empfohlen, die untere Grenze als 0 (null) zu definieren. Es ist möglicherweise vorzuziehen, einen anderen niedrigeren Grenzwert zu verwenden, wenn das Array mit anderen Sprachen verwendet werden soll, z. b. Visual Basic.

Die obere Grenze hängt von der Anzahl der Elemente und dem unteren gebundenen Wert ab. Wenn die untere Grenze beispielsweise 0 und die Anzahl der Elemente 10 ist, wird die obere Grenze automatisch auf 9 festgelegt.

## <a name="see-also"></a>Weitere Informationen

[Klassenübersicht](../../atl/atl-class-overview.md)
