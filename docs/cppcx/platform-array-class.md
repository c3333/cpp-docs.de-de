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
ms.openlocfilehash: d625d80df67a3c8207467ad629afd4c2bf88db18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318654"
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

### <a name="members"></a>Member

Platform::Array erbt alle seine Methoden von [Platform::WriteOnlyArray-Klasse](../cppcx/platform-writeonlyarray-class.md) und implementiert die `Value` Eigenschaft der [Platform::IBoxArray Interface](../cppcx/platform-iboxarray-interface.md).

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Array-Konstruktoren](#ctor)|Initialisiert ein eindimensionales, veränderbares Array von Typen, die durch den Klassenvorlagenparameter *T*angegeben werden.|

### <a name="methods"></a>Methoden

Siehe [Plattform::WriteOnlyArray-Klasse](../cppcx/platform-writeonlyarray-class.md).

### <a name="properties"></a>Eigenschaften

|||
|-|-|
|[Array::Wert](#value)|Ruft ein Handle für das aktuelle Array ab.|

### <a name="remarks"></a>Bemerkungen

Die Array-Klasse wird versiegelt und kann nicht vererbt werden.

Das Windows-Runtime-Typsystem unterstützt nicht das Konzept von gezackten Arrays, und\<daher können Sie einen IVector<Platform::Array T>> als Rückgabewert oder Methodenparameter nicht übergeben. Um ein verzweigtes Array oder eine Sequenz von Sequenzen an die ABI zu übergeben, verwenden Sie `IVector<IVector<T>^>`.

Weitere Informationen dazu, wann und wie Platform::Array verwendet wird, finden Sie unter [Array und WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

Diese Klasse wird im Header "vccorlib.h" definiert, der automatisch vom Compiler eingeschlossen wird. Es ist in IntelliSense sichtbar, aber nicht im Objektbrowser, da es sich nicht um einen öffentlichen Typ handelt, der in platform.winmd definiert ist.

### <a name="requirements"></a>Anforderungen

Compileroption: **/ZW**

## <a name="array-constructors"></a><a name="ctor"></a>Arraykonstruktoren

Initialisiert ein eindimensionales, veränderbares Array von Typen, die durch den Klassenvorlagenparameter *T*angegeben werden.

## <a name="syntax"></a>Syntax

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Klassenvorlagenparameter.

*Größe*<br/>
Die Anzahl der Elemente im Array.

*Daten*<br/>
Ein Zeiger auf ein Array von Daten des Typs `T`, der verwendet wird, um dieses Arrayobjekt zu initialisieren.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zum Erstellen von Instances von Platform::Array finden Sie unter [Array und WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="arrayget-method"></a><a name="get"></a>Array::get-Methode

Ruft einen Verweis auf das Arrayelement an der angegebenen Indexposition ab.

## <a name="syntax"></a>Syntax

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>Parameter

*Index*<br/>
Ein nullbasierter Index, der ein Element im Array identifiziert. Der minimale Index ist 0, und der `size` maximale Index ist der Wert, der durch den Parameter im [Arraykonstruktor](#ctor)angegeben wird.

### <a name="return-value"></a>Rückgabewert

Das durch den `index`-Parameter spezifizierte Arrayelement.

## <a name="arrayvalue-property"></a><a name="value"></a>Array::Value-Eigenschaft

Ruft ein Handle für das aktuelle Array ab.

## <a name="syntax"></a>Syntax

```cpp
property Array^ Value;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für das aktuelle Array.

## <a name="see-also"></a>Siehe auch

[Plattformnamespace](../cppcx/platform-namespace-c-cx.md)<br/>
[Array und WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
