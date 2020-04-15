---
title: Platform::ArrayReference-Klasse
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
ms.openlocfilehash: e9dd16ad6c3f53c5562b0419197a582c06fbc642
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354792"
---
# <a name="platformarrayreference-class"></a>Platform::ArrayReference-Klasse

`ArrayReference` ist ein Optimierungstyp, den Sie als Ersatz für [Platform::Array^](../cppcx/platform-array-class.md) in den Eingabeparametern verwenden können, wenn Sie ein Array im C-Format mit Eingabedaten füllen möchten.

## <a name="syntax"></a>Syntax

```cpp
class ArrayReference
```

### <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ArrayReference::ArrayReference](#ctor)|Initialisiert eine neue Instanz der Klasse `ArrayReference`.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ArrayReference::operator() Operator](#operator-call)|Konvertiert diesen `ArrayReference` in ein `Platform::Array<T>^*`-Element.|
|[ArrayReference::operator=-Operator](#operator-assign)|Weist dieser Instanz den Inhalt von einem anderen `ArrayReference` zu.|

## <a name="exceptions"></a>Ausnahmen

### <a name="remarks"></a>Bemerkungen

Mit `ArrayReference` zum Auffüllen eines Arrays im C-Format, vermeiden Sie den zusätzlichen Kopiervorgang, der dadurch aufgerufen würde, zunächst in eine `Platform::Array` -Variable zu kopieren, und dann in einem zweiten Schritt in das Array im C-Format. Bei Verwendung von `ArrayReference`, entsteht nur ein Kopiervorgang. Ein Codebeispiel finden Sie unter [Array und WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

### <a name="requirements"></a>Anforderungen

**Mindestens unterstützter Client:** Windows 8

**Minimal unterstützter Server:** Windows Server 2012

**Namespace:** Platform

**Header:** vccorlib.h

## <a name="arrayreferencearrayreference-constructor"></a><a name="ctor"></a>ArrayReference::ArrayReference-Konstruktor

Initialisiert eine neue Instanz der [Platform::ArrayReference-Klasse.](../cppcx/platform-arrayreference-class.md)

### <a name="syntax"></a>Syntax

```cpp
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);
ArrayReference(ArrayReference&& otherArg)
```

### <a name="parameters"></a>Parameter

*dataArg*<br/>
Ein Zeiger auf die Arraydaten.

*sizeArg*<br/>
Die Anzahl von Elementen im Quellarray.

*andereArg*<br/>
Ein `ArrayReference`-Objekt, dessen Daten zum Initialisieren der neuen Instanz verschoben werden.

### <a name="remarks"></a>Bemerkungen

## <a name="arrayreferenceoperator-operator"></a><a name="operator-assign"></a>ArrayReference::operator= Operator

Weist das angegebene Objekt dem aktuellen [Platform::ArrayReference-Objekt](../cppcx/platform-arrayreference-class.md) mithilfe der Verschiebungssemantik zu.

### <a name="syntax"></a>Syntax

```cpp
ArrayReference& operator=(ArrayReference&& otherArg);
```

### <a name="parameters"></a>Parameter

*andereArg*<br/>
Das zum aktuellen `ArrayReference`-Objekt verschobene Objekt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf ein Objekt des Typs `ArrayReference`.

### <a name="remarks"></a>Bemerkungen

`Platform::ArrayReference` ist eine Standard-C++-Klassenvorlage, keine Verweisklasse.

## <a name="arrayreferenceoperator-operator"></a><a name="operator-call"></a>ArrayReference::operator() Operator

Konvertiert das aktuelle [Platform::ArrayReference-Objekt](../cppcx/platform-arrayreference-class.md) zurück in eine [Platform::Array-Klasse.](../cppcx/platform-array-class.md)

### <a name="syntax"></a>Syntax

```cpp
Array<TArg>^ operator ();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für das Objekt des Typs `Array<TArg>^`

### <a name="remarks"></a>Bemerkungen

[Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) ist eine Standardvorlage für C++-Klassen, und [Platform::Array](../cppcx/platform-array-class.md) ist eine Verweisklasse.

## <a name="see-also"></a>Siehe auch

[Plattformnamespace](../cppcx/platform-namespace-c-cx.md)
