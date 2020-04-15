---
title: Platform::Agile-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
helpviewer_keywords:
- Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
ms.openlocfilehash: 0822cef10b199a5bc3b33f116065816e380bf8a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376501"
---
# <a name="platformagile-class"></a>Platform::Agile-Klasse

Stellt ein Objekt dar, das über „MashalingBehavior=Standard“ als Agile-Objekt verfügt, das die Chancen für Threadingausnahmen zur Laufzeit erheblich verringert. `Agile<T>` ermöglicht es dem Nicht-Agile-Objekt, denselben oder einen anderen Thread aufzurufen oder von diesem aufgerufen zu werden. Weitere Informationen finden Sie unter [Threading und Marshalling](../cppcx/threading-and-marshaling-c-cx.md).

## <a name="syntax"></a>Syntax

```cpp
template <typename T>
class Agile;
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typname für die Nicht-Agile-Klasse.

### <a name="remarks"></a>Bemerkungen

Die meisten Klassen in der Windows-Runtime sind agil. Ein Agile-Objekt kann ein „in-proc“- oder „out-of-proc“-Objekt in demselben oder einem anderen Thread aufrufen oder von diesem aufgerufen werden. Wenn es sich nicht um ein Agile-Objekt handelt, schließen Sie das Nicht-Agile-Objekt in ein `Agile<T>` -Objekt ein, das agil ist. Dann kann das `Agile<T>` -Objekt gemarshallt und das zugrunde liegende Nicht-Agile-Objekt verwendet werden.

Die `Agile<T>` -Klasse ist eine systemeigene C++-Standardklasse und erfordert `agile.h`. Es stellt das Nicht-Agile-Objekt und den *Kontext*des Agile-Objekts dar. Der Kontext gibt das Threadmodell und Marshallingverhalten eines Agile-Objekts an. Das Betriebssystem verwendet den Kontext, um zu ermitteln, wie ein Objekt gemarshallt wird.

### <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Agil::Agile](#ctor)|Initialisiert eine neue Instanz der Agile-Klasse.|
|[Agile::~Agile-Destruktor](#dtor)|Zerstört die aktuelle Instanz der Agile-Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Agile::Get](#get)|Gibt den Handle auf das Objekt zurück, das vom aktuellen Agile-Objekt dargestellt wird.|
|[Agile::GetAddressOf](#getaddressof)|Initialisiert das aktuelle Agile-Objekt neu und gibt dann die Adresse eines Handles für ein Objekt vom Typ `T`zurück.|
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|Gibt die Adresse eines Handles zum Objekt zurück, das vom aktuellen Agile-Objekt dargestellt wird.|
|[Agile::Release](#release)|Verwirft das Objekt und den Kontext, die dem aktuellen Agile-Objekt zugrunde liegen.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Agil::Operator->](#operator-arrow)|Ruft ein Handle auf das Objekt ab, das vom aktuellen Agile-Objekt dargestellt wird.|
|[Agile::operator=](#operator-assign)|Weist dem aktuellen Agile-Objekt den angegebenen Wert zu.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Object`

`Agile`

### <a name="requirements"></a>Anforderungen

**Mindestens unterstützter Client:** Windows 8

**Minimal unterstützter Server:** Windows Server 2012

**Namespace:** Platform

**Header:** agile.h

## <a name="agileagile-constructor"></a><a name="ctor"></a>Agil::Agile Konstruktor

Initialisiert eine neue Instanz der Agile-Klasse.

## <a name="syntax"></a>Syntax

```cpp
Agile();
Agile(T^ object);
Agile(const Agile<T>& object);
Agile(Agile<T>&& object);
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ein Typ, der durch den Typnamenparameter der Vorlage spezifiziert wird.

*Objekt*<br/>
In der zweiten Version dieses Konstruktors wird ein Objekt verwendet, um eine neue Agile-Instanz zu initialisieren. In der dritten Version das Objekt, das zur neuen Agile-Instanz kopiert wird. In der vierten Version das Objekt, das zur neuen Agile-Instanz verschoben wird.

### <a name="remarks"></a>Bemerkungen

Die erste Version dieses Konstruktors ist der Standardkonstruktor. Die zweite Version initialisiert eine neue Agile-Instanzklasse aus dem Objekt, das durch den `object`-Parameter spezifiziert wird. Die dritte Version ist der Kopierkonstruktor. Die vierte Version ist der Verschiebungskonstruktor. Dieser Konstruktor kann keine Ausnahmen auslösen.

## <a name="agileagile-destructor"></a><a name="dtor"></a>Agil::'Agile Destruktor

Zerstört die aktuelle Instanz der Agile-Klasse.

## <a name="syntax"></a>Syntax

```cpp
~Agile();
```

### <a name="remarks"></a>Bemerkungen

Dieser Destruktor gibt auch das Objekt frei, das vom aktuellen Agile-Objekt dargestellt wird.

## <a name="agileget-method"></a><a name="get"></a>Agil::Get-Methode

Gibt den Handle auf das Objekt zurück, das vom aktuellen Agile-Objekt dargestellt wird.

## <a name="syntax"></a>Syntax

```cpp
T^ Get() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle auf das Objekt, das vom aktuellen Agile-Objekt dargestellt wird.

Der Typ des Rückgabewerts ist eigentlich ein nicht genannter interner Typ. Eine bequeme Möglichkeit, den Rückgabewert zu halten, besteht darin, ihn einer Variablen zuzuweisen, die mit dem Schlüsselwort **"Auto** type deduction" deklariert wird. Beispiel: `auto x = myAgileTvariable->Get();`.

## <a name="agilegetaddressof-method"></a><a name="getaddressof"></a>Agile::GetAddressOf-Methode

Initialisiert das aktuelle Agile-Objekt neu und gibt dann die Adresse eines Handles für ein Objekt vom Typ `T`zurück.

## <a name="syntax"></a>Syntax

```cpp
T^* GetAddressOf() throw();
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ein Typ, der durch den Typnamenparameter der Vorlage spezifiziert wird.

### <a name="return-value"></a>Rückgabewert

Die Adresse eines Handles für ein Objekt des Typs `T`

### <a name="remarks"></a>Bemerkungen

Dieser Vorgang gibt die aktuelle Darstellung eines Objekts vom Typ `T` frei, sofern vorhanden. Dann werden die Datenmember des Agile-Objekts initialisiert, der aktuelle Threadingkontext abgerufen und anschließend die Adresse einer handle-to-object-Variablen zurückgegeben, die ein Nicht-Agile-Objekt darstellen kann. Um zu bewirken, dass eine Agile-Klasseninstanz ein Objekt darstellt, verwenden Sie den Zuweisungsoperator ([Agile::operator=](#operator-assign)), um das Objekt der Agile-Klasseninstanz zuzuweisen.

## <a name="agilegetaddressofforinout-method"></a><a name="getaddressofforinout"></a>Agile::GetAddressOfForInOut-Methode

Gibt die Adresse eines Handles zum Objekt zurück, das vom aktuellen Agile-Objekt dargestellt wird.

## <a name="syntax"></a>Syntax

```cpp
T^* GetAddressOfForInOut()  throw();
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ein Typ, der durch den Typnamenparameter der Vorlage spezifiziert wird.

### <a name="return-value"></a>Rückgabewert

Die Adresse eines Handles zum Objekt, das vom aktuellen Agile-Objekt dargestellt wird.

### <a name="remarks"></a>Bemerkungen

Durch diesen Vorgang wird der aktuelle Threadingkontext abgerufen und dann die Adresse eines Handles zum zugrunde liegenden Objekt zurückgegeben.

## <a name="agilerelease-method"></a><a name="release"></a>Agile::Release-Methode

Verwirft das Objekt und den Kontext, die dem aktuellen Agile-Objekt zugrunde liegen.

## <a name="syntax"></a>Syntax

```cpp
void Release() throw();
```

### <a name="remarks"></a>Bemerkungen

Das Objekt und der Kontext, die dem aktuellen Agile-Objekt zugrunde liegen, werden verworfen, falls sie vorhanden sind. Anschließend wird der Wert des Agile-Objekts auf Null gesetzt.

## <a name="agileoperator-gt-operator"></a><a name="operator-arrow"></a>Agil::Operator-&gt; Operator

Ruft ein Handle auf das Objekt ab, das vom aktuellen Agile-Objekt dargestellt wird.

## <a name="syntax"></a>Syntax

```cpp
T^ operator->() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle auf das Objekt, das vom aktuellen Agile-Objekt dargestellt wird.

Dieser Operator gibt tatsächlich einen nicht veröffentlichten internen Typ zurück. Eine bequeme Möglichkeit, den Rückgabewert zu halten, besteht darin, ihn einer Variablen zuzuweisen, die mit dem Schlüsselwort **"Auto** type deduction" deklariert wird.

## <a name="agileoperator-operator"></a><a name="operator-assign"></a>Agile::operator= Operator

Weist das angegebene Objekt dem aktuellen Agile-Objekt zu.

## <a name="syntax"></a>Syntax

```cpp
Agile<T> operator=( T^ object ) throw();
Agile<T> operator=( const Agile<T>& object ) throw();
Agile<T> operator=( Agile<T>&& object ) throw();
T^ operator=( IUnknown* lp ) throw();
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der durch den Vorlagentypnamen spezifizierte Typ.

*Objekt*<br/>
Das Objekt oder das Handle für ein Objekt, das auf das aktuelle Agile-Objekt kopiert oder verschoben wird.

*Lp*<br/>
Der IUnknown-Schnittstellenzeiger eines Objekts.

### <a name="return-value"></a>Rückgabewert

Ein Handle für ein Objekt des Typs `T`

### <a name="remarks"></a>Bemerkungen

Die erste Version des Zuweisungsoperators kopiert ein Handle für einen Verweistyp zum aktuellen Agile-Objekt. Die zweite Version kopiert einen Verweis zu einem Agile-Typ zum aktuellen Agile-Objekt. Die dritte Version verschiebt einen Agile-Typ zum aktuellen Agile-Objekt. Die vierte Version verschiebt einen Zeiger auf ein COM-Objekt zum aktuellen Agile-Objekt.

Der Zuweisungsvorgang speichert automatisch den Kontext des aktuellen Agile-Objekts.

## <a name="see-also"></a>Siehe auch

[Plattform-Namespace](platform-namespace-c-cx.md)
