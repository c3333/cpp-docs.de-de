---
title: Platform::WriteOnlyArray-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WriteOnlyArray::begin
- VCCORLIB/Platform::WriteOnlyArray::Data
- VCCORLIB/Platform::WriteOnlyArray::end
- VCCORLIB/Platform::WriteOnlyArray::FastPass
- VCCORLIB/Platform::WriteOnlyArray::Length
- VCCORLIB/Platform::WriteOnlyArray::set
helpviewer_keywords:
- Platform::WriteOnlyArray Class
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
ms.openlocfilehash: d06ed19b7c041f9ae73f862ba521449a206aa321
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374648"
---
# <a name="platformwriteonlyarray-class"></a>Platform::WriteOnlyArray-Klasse

Stellt ein eindimensionales Array dar, das als Eingabeparameter verwendet wird, wenn der Aufrufer ein Array für die zu füllende Methode übergibt.

Diese Verweisklasse wird als privat in vccorlib.h deklariert. Daher wird sie nicht in Metadaten ausgegeben und kann nur von C++ verwendet werden. Diese Klasse ist nur zur Verwendung als Eingabeparameter vorgesehen, der ein Array empfängt, das der Aufrufer zugeordnet hat. Sie ist nicht vom Benutzercode konstruierbar. Sie ermöglicht es einer C++-Methode, direkt in dieses Array zu schreiben – ein Muster, das als *FillArray* -Muster bezeichnet wird. Weitere Informationen finden Sie unter [Array und WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="syntax"></a>Syntax

```cpp
private ref class WriteOnlyArray<T, 1>
```

### <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

Diese Methoden verfügen über interne Zugreifbarkeit, das heißt, sie sind nur innerhalb der C++-App oder -Komponente zugänglich.

|Name|BESCHREIBUNG|
|----------|-----------------|
|[WriteOnlyArray::begin](#begin)|Ein Iterator, der auf das erste Element des Arrays zeigt.|
|[WriteOnlyArray::Data](#data)|Ein Zeiger auf den Datenpuffer.|
|[WriteOnlyArray::end](#end)|Ein Iterator, der auf einen Punkt hinter dem letzten Element im Array zeigt.|
|[WriteOnlyArray::FastPass](#fastpass)|Gibt an, ob das Array den FastPass-Mechanismus verwenden kann. Dieser stellt eine Optimierung dar, die transparent vom System ausgeführt wird. Verwenden Sie dies nicht in Ihrem Code|
|[WriteOnlyArray::Länge](#length)|Gibt die Anzahl der Elemente des Arrays zurück.|
|[WriteOnlyArray::set](#set)|Legt das angegebene Element auf den angegebenen Wert fest.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`WriteOnlyArray`

### <a name="requirements"></a>Anforderungen

Compileroption: **/ZW**

**Metadaten:** platform.winmd

**Namespace:** Platform

## <a name="writeonlyarraybegin-method"></a><a name="begin"></a>WriteOnlyArray::begin-Methode

Gibt einen Zeiger auf das erste Element im Array zurück.

### <a name="syntax"></a>Syntax

```cpp
T* begin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das erste Element im Array.

### <a name="remarks"></a>Bemerkungen

Dieser Iterator kann mit STL-Algorithmen wie `std::sort` verwendet werden, um Vorgänge auf Elemente im Array auszuführen.

## <a name="writeonlyarraydata-property"></a><a name="data"></a>WriteOnlyArray::Data-Eigenschaft

Zeiger auf den Datenpuffer.

### <a name="syntax"></a>Syntax

```cpp
property T* Data{
   T* get() const;
}
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf unformatierte Arraybytes.

## <a name="writeonlyarrayend-method"></a><a name="end"></a>WriteOnlyArray::end-Methode

Gibt einen Zeiger auf einen Punkt hinter dem letzten Element im Array zurück.

### <a name="syntax"></a>Syntax

```cpp
T* end() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeigeriterator auf einen Punkt hinter dem letzten Element im Array.

### <a name="remarks"></a>Bemerkungen

Dieser Iterator kann mit STL-Algorithmen verwendet werden, um Vorgänge wie `std::sort` auf die Array-Elemente auszuführen.

## <a name="writeonlyarrayfastpass-property"></a><a name="fastpass"></a>WriteOnlyArray::FastPass-Eigenschaft

Gibt an, ob die interne FastPass-Optimierung ausgeführt werden kann. Ist nicht für die Verwendung in Benutzercode bestimmt.

### <a name="syntax"></a>Syntax

```cpp
property bool FastPass{
   bool get() const;
}
```

### <a name="return-value"></a>Rückgabewert

Boolescher Wert, der angibt, ob das Array FastPass ist.

## <a name="writeonlyarrayget-method"></a><a name="get"></a>WriteOnlyArray::get-Methode

Gibt das Element am angegebenen Index zurück.

### <a name="syntax"></a>Syntax

```cpp
T& get(unsigned int indexArg) const;
```

### <a name="parameters"></a>Parameter

*indexArg*<br/>
Der zu verwendende Index.

### <a name="return-value"></a>Rückgabewert

## <a name="writeonlyarraylength-property"></a><a name="length"></a>WriteOnlyArray::Length-Eigenschaft

Gibt die Anzahl der Elemente im vom Aufrufer reservierten Array zurück.

### <a name="syntax"></a>Syntax

```cpp
property unsigned int Length{
   unsigned int get() const;
}
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Array.

## <a name="writeonlyarrayset-function"></a><a name="set"></a>WriteOnlyArray::set-Funktion

Legt den angegebenen Wert am angegebenen Index im Array fest.

### <a name="syntax"></a>Syntax

```cpp
T& set(
   unsigned int indexArg,
   T valueArg);
```

### <a name="parameters"></a>Parameter

*indexArg*<br/>
Der Index des festzulegenden Elements.

*valueArg*<br/>
Der bei `indexArg` festzulegende Wert.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das Element, das gerade festgelegt wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zum Interpretieren des HRESULT-Werts finden Sie unter [Struktur von COM-Fehlercodes](/windows/win32/com/structure-of-com-error-codes).

## <a name="see-also"></a>Siehe auch

[Plattform-Namespace](platform-namespace-c-cx.md)<br/>
[Erstellen von Windows-Runtime-Komponenten in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
