---
title: norm-Klasse
ms.date: 11/04/2016
f1_keywords:
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: b5740f33dea6aad79770f77f179803023432248a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447527"
---
# <a name="norm-class"></a>norm-Klasse

Stellt eine Norm Nummer dar. Jedes Element ist eine Gleit Komma Zahl im Bereich von [-1.0 f, 1.0 f].

## <a name="syntax"></a>Syntax

```cpp
class norm;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Norm-Konstruktor](#ctor)|Ist überladen. Der Standardkonstruktor. Initialisieren Sie den Wert 0,0 f.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|Norm:: Operator-||
|Norm:: Operator--||
|Norm:: Operator float|Konvertierungs Operator. Konvertieren der Norm Nummer in einen Gleit Komma Wert.|
|Norm:: Operator * =||
|Norm:: Operator/=||
|norm::operator++||
|norm::operator+=||
|norm::operator=||
|Norm:: Operator-=||

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`norm`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** amp_short_vectors. h

**Namespace:** Parallelität:: Grafiken

## <a name="ctor"></a>Regel

Der Standardkonstruktor. Initialisieren Sie den Wert 0,0 f.

```cpp
norm(
    void) restrict(amp,
    cpu);

explicit norm(
    float _V) restrict(amp,
    cpu);

explicit norm(
    unsigned int _V) restrict(amp,
    cpu);

explicit norm(
    int _V) restrict(amp,
    cpu);

explicit norm(
    double _V) restrict(amp,
    cpu);

norm(
    const norm& _Other) restrict(amp,
    cpu);

norm(
    const unorm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parameter

*_V*<br/>
Der Wert, der zum Initialisieren von verwendet wird.

*_Other*<br/>
Das-Objekt, das zum Initialisieren von verwendet wird.

## <a name="see-also"></a>Weitere Informationen

[Concurrency::graphics Namespace](concurrency-graphics-namespace.md)
