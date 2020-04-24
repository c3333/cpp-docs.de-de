---
title: Platform::Guid-Wertklasse
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 7c3b89ff238b1cb5ee9fbb71e83d20f571e656a3
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031536"
---
# <a name="platformguid-value-class"></a>Platform::Guid-Wertklasse

Represents a [GUID](/windows/win32/api/guiddef/ns-guiddef-guid type in the Windows Runtime type system.

## <a name="syntax"></a>Syntax

```cpp
public value struct Guid
```

### <a name="members"></a>Member

`Platform::Guid`hat `Equals()`die `GetHashCode()`, `ToString()` und Methoden, die von der `GetTypeCode()` [Platform::Object Class](../cppcx/platform-object-class.md)abgeleitet sind, und die von der [Platform::Type-Klasse](../cppcx/platform-type-class.md)abgeleitete Methode . `Platform::Guid`hat auch die folgenden Mitglieder.

|Member|BESCHREIBUNG|
|------------|-----------------|
|[Guid](#ctor)|Initialisiert eine neue Instanz von `Platform::Guid`.|
|[Betreiber== Einzelnachweise ==](#operator-equality)|Gleich-Operator.|
|[Operator!=](#operator-inequality)|Ungleich-Operator.|
|[Operator&lt;](#operator-less)|Kleiner als-Operator.|
|[Operator()](#operator-call)|Konvertiert ein `Platform::Guid` -Element in ein `GUID`-Element.|

### <a name="remarks"></a>Bemerkungen

Um eine `Platform::Guid`neue zu generieren, verwenden Sie die [statische Windows::Foundation::GuidHelper::CreateNewGuid-Methode.](/uwp/api/windows.foundation.guidhelper.createnewguid)

### <a name="requirements"></a>Requirements (Anforderungen)

**Mindestens unterstützter Client:** Windows 8

**Minimal unterstützter Server:** Windows Server 2012

**Namespace:** Platform

**Metadaten:** platform.winmd

## <a name="guidguid-constructors"></a><a name="ctor"></a>Guid::Guid-Konstruktoren

Initialisiert eine neue Instanz von `Platform::Guid`.

### <a name="syntax"></a>Syntax

```cpp
Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    unsigned char d,
    unsigned char e,
    unsigned char f,
    unsigned char g,
    unsigned char h,
    unsigned char i,
    unsigned char j,
    unsigned char k );

Guid(GUID m);

Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    Array<unsigned char>^ n );
```

### <a name="parameters"></a>Parameter

*Eine*<br/>
Die ersten 4 `GUID`Bytes der .

*B*<br/>
Die nächsten 2 `GUID`Bytes der .

*C*<br/>
Die nächsten 2 `GUID`Bytes der .

*D*<br/>
Das nächste Byte der `GUID`.

*E*<br/>
Das nächste Byte der `GUID`.

*F*<br/>
Das nächste Byte der `GUID`.

*G*<br/>
Das nächste Byte der `GUID`.

*H*<br/>
Das nächste Byte der `GUID`.

*Ⅰ*<br/>
Das nächste Byte der `GUID`.

*J*<br/>
Das nächste Byte der `GUID`.

*K*<br/>
Das nächste Byte der `GUID`.

*M*<br/>
A `GUID` in Form einer [GUID-Struktur](/windows/win32/api/guiddef/ns-guiddef-guid).

*n*<br/>
Die restlichen 8 `GUID`Bytes der .

## <a name="guidoperator-operator"></a><a name="operator-equality"></a>Guid::operator== Operator

Überprüft zwei `Platform::Guid`-Instanzen auf Gleichheit.

### <a name="syntax"></a>Syntax

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parameter

*guid1*<br/>
Der erste zu vergleichende `Platform::Guid`.

*guid2*<br/>
Der zweite zu vergleichende `Platform::Guid`.

### <a name="return-value"></a>Rückgabewert

True, wenn `Platform::Guid` die beiden Instanzen gleich sind.

### <a name="remarks"></a>Bemerkungen

Bevorzugen Sie `==` die Verwendung des Operators anstelle der [Windows::Foundation::GuidHelper::Equals](/uwp/api/windows.foundation.guidhelper.equals) statische Methode.

## <a name="guidoperator-operator"></a><a name="operator-inequality"></a>Guid::operator!= Operator

Überprüft zwei `Platform::Guid`-Instanzen auf Ungleichheit.

### <a name="syntax"></a>Syntax

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parameter

*guid1*<br/>
Der erste zu vergleichende `Platform::Guid`.

*guid2*<br/>
Der zweite zu vergleichende `Platform::Guid`.

### <a name="return-value"></a>Rückgabewert

True, wenn `Platform::Guid` die beiden Instanzen nicht gleich sind.

## <a name="guidoperatorlt-operator"></a><a name="operator-less"></a>Guid::operator&lt; Operator

Vergleicht `Platform::Guid` zwei Instanzen für die Reihenfolge.

### <a name="syntax"></a>Syntax

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parameter

*guid1*<br/>
Der erste zu vergleichende `Platform::Guid`.

*guid2*<br/>
Der zweite zu vergleichende `Platform::Guid`.

### <a name="return-value"></a>Rückgabewert

True, wenn *guid1* vor *guid2*bestellt wird. Die Reihenfolge ist lexikographisch, nachdem jeder von ihnen `Platform::Guid` behandelt wurde, als ob es sich um ein Array von vier 32-Bit-Werten ohne Vorzeichen handelt. Dies ist weder die Reihenfolge, die von SQL Server oder .NET Framework verwendet wird, noch ist es die gleiche wie die lexikographische Reihenfolge nach Zeichenfolgendarstellung.

Dieser Operator wird `Guid` bereitgestellt, damit Objekte von der C++-Standardbibliothek leichter genutzt werden können.

## <a name="guidoperator-operator"></a><a name="operator-call"></a>Guid::operator() Operator

Konvertiert implizit eine `Platform::Guid` in eine [GUID-Struktur](/windows/win32/api/guiddef/ns-guiddef-guid).

### <a name="syntax"></a>Syntax

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>Rückgabewert

Eine [GUID-Struktur](/windows/win32/api/guiddef/ns-guiddef-guid).

## <a name="see-also"></a>Weitere Informationen

[Plattformnamespace](../cppcx/platform-namespace-c-cx.md)
