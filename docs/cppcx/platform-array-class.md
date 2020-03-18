---
title: Platform::Array-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Array
- VCCORLIB/Platform::Array::Value
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
ms.openlocfilehash: 7d9fca4de954b5ba9c7cbcb3bdfce0fe3263dbd7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445795"
---
# <a name="platformarray-class"></a>Platform::Array-Klasse

Stellt ein änderbares, eindimensionales Array dar, das über die Anwendungsbinärdateischnittstelle (ABI) empfangen und übergeben werden kann.

## <a name="syntax"></a>Syntax

```cpp
template <typename T>
private ref class Array<TArg, 1> :
    public WriteOnlyArray<TArg, 1>,
    public IBoxArray<TArg>
```

### <a name="members"></a>Members

Platform:: Array erbt all seine Methoden von der [Platform:: Write](../cppcx/platform-writeonlyarray-class.md) Sample-Klasse und implementiert die `Value`-Eigenschaft der [Platform:: iboxarray-Schnittstelle](../cppcx/platform-iboxarray-interface.md).

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Array-Konstruktoren](#ctor)|Initialisiert ein eindimensionales, änderbares Array von Typen, die vom Klassen Vorlagen Parameter *T*angegeben werden.|

### <a name="methods"></a>Methoden

Siehe [Platform:: Beschreib teonlyarray-Klasse](../cppcx/platform-writeonlyarray-class.md).

### <a name="properties"></a>Eigenschaften

|||
|-|-|
|[Array:: Value](#value)|Ruft ein Handle für das aktuelle Array ab.|

### <a name="remarks"></a>Bemerkungen

Die Array-Klasse wird versiegelt und kann nicht vererbt werden.

Das Windows-Runtime-Typsystem unterstützt das Konzept von verzweigten Arrays nicht. Daher können Sie ein IVector < Platform:: Array\<t-> > nicht als Rückgabewert oder Methoden Parameter übergeben. Um ein verzweigtes Array oder eine Sequenz von Sequenzen an die ABI zu übergeben, verwenden Sie `IVector<IVector<T>^>`.

Weitere Informationen dazu, wann und wie Platform:: Array verwendet wird, finden Sie unter [Array und beschreiteonlyarray](../cppcx/array-and-writeonlyarray-c-cx.md).

Diese Klasse wird im Header "vccorlib.h" definiert, der automatisch vom Compiler eingeschlossen wird. Es ist in IntelliSense, aber nicht in Objektkatalog sichtbar, da es sich nicht um einen in Platform. winmd definierten öffentlichen Typ handelt.

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: **/ZW**

## <a name="ctor"></a>Array-Konstruktoren

Initialisiert ein eindimensionales, änderbares Array von Typen, die vom Klassen Vorlagen Parameter *T*angegeben werden.

## <a name="syntax"></a>Syntax

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Klassenvorlagenparameter.

*size*<br/>
Die Anzahl der Elemente im Array.

*data*<br/>
Ein Zeiger auf ein Array von Daten des Typs `T`, der verwendet wird, um dieses Arrayobjekt zu initialisieren.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zum Erstellen von Instanzen von Platform:: Array finden Sie unter [Array und beschreiteonlyarray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="get"></a>Array:: Get-Methode

Ruft einen Verweis auf das Arrayelement an der angegebenen Indexposition ab.

## <a name="syntax"></a>Syntax

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>Parameter

*Index*<br/>
Ein nullbasierter Index, der ein Element im Array identifiziert. Der minimale Index ist 0, und der maximale Index ist der Wert, der vom `size`-Parameter im [Arraykonstruktor](#ctor)angegeben wird.

### <a name="return-value"></a>Rückgabewert

Das durch den `index`-Parameter spezifizierte Arrayelement.

## <a name="value"></a>Array:: Value-Eigenschaft

Ruft ein Handle für das aktuelle Array ab.

## <a name="syntax"></a>Syntax

```cpp
property Array^ Value;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für das aktuelle Array.

## <a name="see-also"></a>Weitere Informationen

[Plattformnamespace](../cppcx/platform-namespace-c-cx.md)<br/>
[Array und WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
