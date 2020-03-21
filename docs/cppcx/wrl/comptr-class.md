---
title: ComPtr-Klasse
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr
- client/Microsoft::WRL::ComPtr::As
- client/Microsoft::WRL::ComPtr::AsIID
- client/Microsoft::WRL::ComPtr::AsWeak
- client/Microsoft::WRL::ComPtr::Attach
- client/Microsoft::WRL::ComPtr::ComPtr
- client/Microsoft::WRL::ComPtr::CopyTo
- client/Microsoft::WRL::ComPtr::Detach
- client/Microsoft::WRL::ComPtr::Get
- client/Microsoft::WRL::ComPtr::GetAddressOf
- client/Microsoft::WRL::ComPtr::InternalAddRef
- client/Microsoft::WRL::ComPtr::InternalRelease
- client/Microsoft::WRL::ComPtr::operator&
- client/Microsoft::WRL::ComPtr::operator->
- client/Microsoft::WRL::ComPtr::operator=
- client/Microsoft::WRL::ComPtr::operator==
- client/Microsoft::WRL::ComPtr::operator!=
- client/Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType
- client/Microsoft::WRL::ComPtr::ptr_
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
- client/Microsoft::WRL::ComPtr::Reset
- client/Microsoft::WRL::ComPtr::Swap
- client/Microsoft::WRL::ComPtr::~ComPtr
helpviewer_keywords:
- Microsoft::WRL::ComPtr class
- Microsoft::WRL::ComPtr::As method
- Microsoft::WRL::ComPtr::AsIID method
- Microsoft::WRL::ComPtr::AsWeak method
- Microsoft::WRL::ComPtr::Attach method
- Microsoft::WRL::ComPtr::ComPtr, constructor
- Microsoft::WRL::ComPtr::CopyTo method
- Microsoft::WRL::ComPtr::Detach method
- Microsoft::WRL::ComPtr::Get method
- Microsoft::WRL::ComPtr::GetAddressOf method
- Microsoft::WRL::ComPtr::InternalAddRef method
- Microsoft::WRL::ComPtr::InternalRelease method
- Microsoft::WRL::ComPtr::operator& operator
- Microsoft::WRL::ComPtr::operator-> operator
- Microsoft::WRL::ComPtr::operator= operator
- Microsoft::WRL::ComPtr::operator== operator
- Microsoft::WRL::ComPtr::operator!= operator
- Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType operator
- Microsoft::WRL::ComPtr::ptr_ data member
- Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf method
- Microsoft::WRL::ComPtr::Reset method
- Microsoft::WRL::ComPtr::Swap method
- Microsoft::WRL::ComPtr::~ComPtr, destructor
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
ms.openlocfilehash: 2881d25434291aebff6a2d3a542044e58e0e81f2
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077889"
---
# <a name="comptr-class"></a>ComPtr-Klasse

Erstellt einen *intelligenten Zeigertyp* , der die Schnittstelle darstellt, die vom Vorlagenparameter angegeben wird. `ComPtr` verwaltet automatisch einen Verweiszähler für den zugrunde liegenden Schnittstellenzeiger und gibt die Schnittstelle frei, wenn der Verweiszähler auf null geht.

## <a name="syntax"></a>Syntax

```cpp
template <typename T>
class ComPtr;

template<class T>
friend class ComPtr;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die Schnittstelle, die der `ComPtr` darstellt.

*U*<br/>
Eine Klasse, zu der der aktuelle `ComPtr` ein Freund ist. (Die Vorlage, die diesen Parameter verwendet, ist geschützt.)

## <a name="remarks"></a>Bemerkungen

`ComPtr<>` deklariert einen Typ, der den zugrunde liegenden Schnittstellen Zeiger darstellt. Verwenden Sie `ComPtr<>`, um eine Variable zu deklarieren, und verwenden Sie dann den Pfeil Element Zugriffs Operator (`->`), um auf eine Schnittstellenmember-Funktion zuzugreifen.

Weitere Informationen zu intelligenten Zeigern finden Sie im Abschnitt "com Intelligent Pointer" des Themas [com-Codierungspraktiken](/windows/win32/LearnWin32/com-coding-practices) in der MSDN Library.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name            | BESCHREIBUNG
--------------- | ---------------------------------------------------------------
`InterfaceType` | Ein Synonym für den Typ, der vom *T* -Vorlagen Parameter angegeben wird.

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                             | BESCHREIBUNG
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[Comptr:: comptr](#comptr)        | Initialisiert eine neue Instanz der `ComPtr`-Klasse. Überladungen stellen Standard-, Kopier-, Verschiebe- und Konvertierungskonstruktoren bereit.
[Comptr:: ~ comptr](#tilde-comptr) | Deinitialisiert eine Instanz von `ComPtr`.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                                      | BESCHREIBUNG
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Comptr:: As](#as)                                         | Gibt ein `ComPtr` Objekt zurück, das die Schnittstelle darstellt, die durch den angegebenen Vorlagen Parameter identifiziert wird.
[Comptr:: asiid](#asiid)                                   | Gibt ein `ComPtr` Objekt zurück, das die durch die angegebene Schnittstellen-ID identifizierte Schnittstelle darstellt.
[Comptr:: asweak](#asweak)                                 | Ruft einen schwachen Verweis (WeakReference) auf das aktuelle Objekt ab.
[Comptr:: Attach](#attach)                                 | Ordnet diese `ComPtr` dem Schnittstellentyp zu, der durch den aktuellen Template-Typparameter angegeben wird.
[Comptr:: CopyTo](#copyto)                                 | Kopiert die aktuelle oder angegebene-Schnittstelle, die diesem `ComPtr` zugeordnet ist, in den angegebenen Ausgabe Zeiger.
[Comptr::D Etach](#detach)                                 | Trennt die Zuordnung dieses `ComPtr` von der-Schnittstelle, die es darstellt.
[Comptr:: Get](#get)                                       | Ruft einen Zeiger auf die-Schnittstelle ab, die diesem `ComPtr`zugeordnet ist.
[Comptr:: getaddressof](#getaddressof)                     | Ruft die Adresse des [ptr_](#ptr) Datenmembers ab, der einen Zeiger auf die-Schnittstelle enthält, die von diesem `ComPtr`dargestellt wird.
[Comptr:: releaseandgetaddressof](#releaseandgetaddressof) | Gibt die diesem `ComPtr` zugeordnete-Schnittstelle frei und ruft dann die Adresse des [ptr_](#ptr) Datenmembers ab, der einen Zeiger auf die-Schnittstelle enthält, die freigegeben wurde.
[ComPtr::Reset](#reset)                                   | Gibt alle Verweise für den Zeiger auf die-Schnittstelle frei, die mit diesem `ComPtr`verknüpft ist.
[Comptr:: Swap](#swap)                                     | Tauscht die Schnittstelle, die vom aktuellen `ComPtr` verwaltet wird, mit der vom angegebenen `ComPtr`verwalteten Schnittstelle aus.

### <a name="protected-methods"></a>Geschützte Methoden

Name                                        | BESCHREIBUNG
------------------------------------------- | --------------------------------------------------------------------------------
[Comptr:: internaladressf](#internaladdref)   | Inkremente den Verweis Zähler der Schnittstelle, die dieser `ComPtr`zugeordnet ist.
[Comptr:: internalrelease](#internalrelease) | Führt einen com-Releasevorgang für die diesem `ComPtr`zugeordnete-Schnittstelle aus.

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                                                                           | BESCHREIBUNG
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[Comptr:: Operator-&](#operator-ampersand)                                                       | Ruft die Adresse des aktuellen `ComPtr`ab.
[Comptr:: Operator->](#operator-arrow)                                                          | Ruft einen Zeiger auf den Typ ab, der durch den aktuellen Vorlagenparameter angegeben ist.
[Comptr:: Operator =](#operator-assign)                                                          | Weist dem aktuellen `ComPtr`einen Wert zu.
[Comptr:: Operator = =](#operator-equality)                                                       | Gibt an, ob zwei `ComPtr`-Objekte gleich sind.
[Comptr:: Operator! =](#operator-inequality)                                                     | Gibt an, ob zwei `ComPtr`-Objekte ungleich sind.
[Comptr:: Operator Microsoft:: WRL::D etails:: booltype](#operator-microsoft-wrl-details-booltype) | Gibt an, ob ein `ComPtr` die Objekt Lebensdauer einer Schnittstelle verwaltet.

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                 | BESCHREIBUNG
-------------------- | ------------------------------------------------------------------------------------------
[Comptr::p tr_](#ptr) | Enthält einen Zeiger auf die-Schnittstelle, die dieser `ComPtr`zugeordnet ist und von dieser verwaltet wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ComPtr`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** client.h

**Namespace:** Microsoft::WRL

## <a name="comptrcomptr"></a><a name="tilde-comptr"></a>Comptr:: ~ comptr

Deinitialisiert eine Instanz von `ComPtr`.

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="comptras"></a><a name="as"></a>Comptr:: As

Gibt ein `ComPtr` Objekt zurück, das die Schnittstelle darstellt, die durch den angegebenen Vorlagen Parameter identifiziert wird.

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* p
) const;

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> p
) const;
```

### <a name="parameters"></a>Parameter

*U*<br/>
Die Schnittstelle, die durch den Parameter *p*dargestellt werden soll.

*p*<br/>
Ein `ComPtr`-Objekt, das die durch den Parameter *U*angegebene Schnittstelle darstellt. Der Parameter " *p* " darf nicht auf das aktuelle `ComPtr` Objekt verweisen.

### <a name="remarks"></a>Bemerkungen

Die erste Vorlage ist die Form, die Sie in Ihrem Code verwenden sollten. Die zweite Vorlage ist eine interne Hilfsspezialisierung, die C++-Sprachfeatures unterstützt, wie etwa das Schlüsselwort [auto](../../cpp/auto-cpp.md) zur Typableitung.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="comptrasiid"></a><a name="asiid"></a>Comptr:: asiid

Gibt ein `ComPtr` Objekt zurück, das die durch die angegebene Schnittstellen-ID identifizierte Schnittstelle darstellt.

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Eine Schnittstellen-ID.

*p*<br/>
Wenn das Objekt über eine Schnittstelle verfügt, deren ID gleich *riid*ist, ein doppelt indirekter Zeiger auf die Schnittstelle, die durch den *riid* -Parameter angegeben wird. andernfalls ein Zeiger auf `IUnknown`.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="comptrasweak"></a><a name="asweak"></a>Comptr:: asweak

Ruft einen schwachen Verweis (WeakReference) auf das aktuelle Objekt ab.

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>Parameter

*pweakref*<br/>
Wenn dieser Vorgang abgeschlossen ist, ein Zeiger auf ein schwaches Verweis Objekt.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="comptrattach"></a><a name="attach"></a>Comptr:: Attach

Ordnet diese `ComPtr` dem Schnittstellentyp zu, der durch den aktuellen Template-Typparameter angegeben wird.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Parameter

*other*<br/>
Ein Schnittstellentyp.

## <a name="comptrcomptr"></a><a name="comptr"></a>Comptr:: comptr

Initialisiert eine neue Instanz der `ComPtr`-Klasse. Überladungen stellen Standard-, Kopier-, Verschiebe- und Konvertierungskonstruktoren bereit.

```cpp
WRL_NOTHROW ComPtr();

WRL_NOTHROW ComPtr(
   decltype(__nullptr)
);

template<class U>
WRL_NOTHROW ComPtr(
   _In_opt_ U *other
);

WRL_NOTHROW ComPtr(
   const ComPtr& other
);

template<class U>
WRL_NOTHROW ComPtr(
   const ComPtr<U> &other,
   typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);

WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);

template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other, typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);
```

### <a name="parameters"></a>Parameter

*U*<br/>
Der Typ des *anderen* Parameters.

*other*<br/>
Ein Objekt vom Typ " *U*".

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor ist der Standardkonstruktor, der implizit ein leeres-Objekt erstellt. Der zweite Konstruktor gibt [__nullptr](../../extensions/nullptr-cpp-component-extensions.md)an, der explizit ein leeres-Objekt erstellt.

Der dritte Konstruktor erstellt ein-Objekt aus dem-Objekt, das durch einen-Zeiger angegeben wird. Der comptr besitzt jetzt den referenzierten Speicher und verwaltet einen Verweis Zähler.

Der vierte und fünfte Konstruktor sind Kopierkonstruktoren. Der fünfte Konstruktor kopiert ein Objekt, wenn es in den aktuellen Typ konvertiert werden kann.

Die sechsten und siebten Konstruktoren sind bewegungskonstruktoren. Der siebte Konstruktor verschiebt ein Objekt, wenn es in den aktuellen Typ konvertiert werden kann.

## <a name="comptrcopyto"></a><a name="copyto"></a>Comptr:: CopyTo

Kopiert die aktuelle oder angegebene-Schnittstelle, die diesem `ComPtr` zugeordnet ist, in den angegebenen Zeiger.

```cpp
HRESULT CopyTo(
   _Deref_out_ InterfaceType** ptr
);

HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ void** ptr
) const;

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
) const;
```

### <a name="parameters"></a>Parameter

*U*<br/>
Ein Typname.

*ptr*<br/>
Wenn dieser Vorgang abgeschlossen ist, ein Zeiger auf die angeforderte Schnittstelle.

*riid*<br/>
Eine Schnittstellen-ID.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das angibt, warum der implizite `QueryInterface` Vorgang fehlgeschlagen ist.

### <a name="remarks"></a>Bemerkungen

Die erste Funktion gibt eine Kopie eines Zeigers auf die-Schnittstelle zurück, die dieser `ComPtr`zugeordnet ist. Diese Funktion gibt immer S_OK zurück.

Die zweite Funktion führt einen `QueryInterface` Vorgang für die Schnittstelle aus, die dieser `ComPtr` für die durch den *riid* -Parameter angegebene Schnittstelle zugeordnet ist.

Die dritte Funktion führt einen `QueryInterface` Vorgang für die Schnittstelle aus, die dieser `ComPtr` für die zugrunde liegende Schnittstelle des *U* -Parameters zugeordnet ist.

## <a name="comptrdetach"></a><a name="detach"></a>Comptr::D Etach

Trennt dieses `ComPtr`-Objekt von der-Schnittstelle, die es darstellt.

```cpp
T* Detach();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die-Schnittstelle, die von diesem `ComPtr` Objekt dargestellt wurde.

## <a name="comptrget"></a><a name="get"></a>Comptr:: Get

Ruft einen Zeiger auf die-Schnittstelle ab, die diesem `ComPtr`zugeordnet ist.

```cpp
T* Get() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die-Schnittstelle, die mit diesem `ComPtr`verknüpft ist.

## <a name="comptrgetaddressof"></a><a name="getaddressof"></a>Comptr:: getaddressof

Ruft die Adresse des [ptr_](#ptr) Datenmembers ab, der einen Zeiger auf die-Schnittstelle enthält, die von diesem `ComPtr`dargestellt wird.

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Rückgabewert

Die Adresse einer Variablen.

## <a name="comptrinternaladdref"></a><a name="internaladdref"></a>Comptr:: internaladressf

Inkremente den Verweis Zähler der Schnittstelle, die dieser `ComPtr`zugeordnet ist.

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Bemerkungen

Diese Methode ist geschützt.

## <a name="comptrinternalrelease"></a><a name="internalrelease"></a>Comptr:: internalrelease

Führt einen com-Releasevorgang für die diesem `ComPtr`zugeordnete-Schnittstelle aus.

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode ist geschützt.

## <a name="comptroperatoramp"></a><a name="operator-ampersand"></a>Comptr:: Operator-&amp;

Gibt die diesem `ComPtr` Objekt zugeordnete-Schnittstelle frei und ruft dann die Adresse des `ComPtr` Objekts ab.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Rückgabewert

Ein schwacher Verweis auf die aktuelle `ComPtr`.

### <a name="remarks"></a>Bemerkungen

Diese Methode unterscheidet sich von [comptr:: getaddressof](#getaddressof) insofern, als diese Methode einen Verweis auf den Schnittstellen Zeiger freigibt. Verwenden Sie `ComPtr::GetAddressOf`, wenn Sie die Adresse des Schnittstellen Zeigers benötigen, diese Schnittstelle jedoch nicht freigeben möchten.

## <a name="comptroperator-gt"></a><a name="operator-arrow"></a>Comptr:: Operator-&gt;

Ruft einen Zeiger auf den Typ ab, der durch den aktuellen Vorlagenparameter angegeben ist.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Typ, der durch den Namen des aktuellen Vorlagen Typs angegeben wird.

### <a name="remarks"></a>Bemerkungen

Diese Hilfsfunktion entfernt unnötigen mehr Aufwand, der durch die Verwendung des STDMETHOD-Makros verursacht wird. Diese Funktion macht `IUnknown` Typen `private` anstelle von `virtual`.

## <a name="comptroperator"></a><a name="operator-assign"></a>Comptr:: Operator =

Weist dem aktuellen `ComPtr`einen Wert zu.

```cpp
WRL_NOTHROW ComPtr& operator=(
   decltype(__nullptr)
);
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ T *other
);
template <typename U>
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr& operator=(
   const ComPtr &other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   const ComPtr<U>& other
);
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr<U>&& other
);
```

### <a name="parameters"></a>Parameter

*U*<br/>
Eine-Klasse.

*other*<br/>
Ein Zeiger, ein Verweis oder ein rvalue-Verweis auf einen Typ oder einen anderen `ComPtr`.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf die aktuelle `ComPtr`.

### <a name="remarks"></a>Bemerkungen

Die erste Version dieses Operators weist dem aktuellen `ComPtr`einen leeren Wert zu.

Wenn in der zweiten Version der Zuweisungs Schnittstellen Zeiger nicht mit dem aktuellen `ComPtr` Schnittstellen Zeiger identisch ist, wird der zweite Schnittstellen Zeiger dem aktuellen `ComPtr`zugewiesen.

In der dritten Version wird der Zuweisungs Schnittstellen Zeiger dem aktuellen `ComPtr`zugewiesen.

Wenn in der vierten Version der Schnittstellen Zeiger des Zuweisungs Werts nicht mit dem aktuellen `ComPtr` Schnittstellen Zeiger identisch ist, wird der zweite Schnittstellen Zeiger dem aktuellen `ComPtr`zugewiesen.

Die fünfte Version ist ein Kopier Operator. ein Verweis auf eine `ComPtr` wird der aktuellen `ComPtr`zugewiesen.

Die sechste Version ist ein Kopier Operator, der Verschiebungs Semantik verwendet. ein rvalue-Verweis auf einen `ComPtr`, wenn ein beliebiger Typ eine statische Umwandlung ist und dann dem aktuellen `ComPtr`zugewiesen wird.

Die siebte Version ist ein Kopier Operator, der Verschiebungs Semantik verwendet. ein rvalue-Verweis auf eine `ComPtr` vom Typ *U* ist eine statische Umwandlung und wird der aktuellen `ComPtr`zugewiesen.

## <a name="comptroperator"></a><a name="operator-equality"></a>Comptr:: Operator = =

Gibt an, ob zwei `ComPtr`-Objekte gleich sind.

```cpp
bool operator==(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator==(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>Parameter

*a*<br/>
Ein Verweis auf ein `ComPtr`-Objekt.

*b*<br/>
Ein Verweis auf ein anderes `ComPtr`-Objekt.

### <a name="return-value"></a>Rückgabewert

Der erste Operator gibt `true` aus, wenn Objekt *a* und Objekt *b*gleich sind. Andernfalls `false`.

Der zweite und der dritte Operator ergeben `true`, wenn Objekt *a* gleich `nullptr`ist. Andernfalls `false`.

## <a name="comptroperator"></a><a name="operator-inequality"></a>Comptr:: Operator! =

Gibt an, ob zwei `ComPtr`-Objekte ungleich sind.

```cpp
bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>Parameter

*a*<br/>
Ein Verweis auf ein `ComPtr`-Objekt.

*b*<br/>
Ein Verweis auf ein anderes `ComPtr`-Objekt.

### <a name="return-value"></a>Rückgabewert

Der erste Operator gibt `true` aus, wenn Objekt *a* nicht gleich Objekt *b*ist. Andernfalls `false`.

Der zweite und der dritte Operator ergeben `true`, wenn Objekt *a* nicht gleich `nullptr`ist. Andernfalls `false`.

## <a name="comptroperator-microsoftwrldetailsbooltype"></a><a name="operator-microsoft-wrl-details-booltype"></a>Comptr:: Operator Microsoft:: WRL::D etails:: booltype

Gibt an, ob ein `ComPtr` die Objekt Lebensdauer einer Schnittstelle verwaltet.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn eine Schnittstelle mit diesem `ComPtr`verknüpft ist, ist dies die Adresse des [boolstruct:: Member](boolstruct-structure.md#member) -Datenmembers. Andernfalls `nullptr`.

## <a name="comptrptr_"></a><a name="ptr"></a>Comptr::p tr_

Enthält einen Zeiger auf die-Schnittstelle, die dieser `ComPtr`zugeordnet ist und von dieser verwaltet wird.

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Bemerkungen

`ptr_` ist ein interner, geschützter Datenmember.

## <a name="comptrreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>Comptr:: releaseandgetaddressof

Gibt die diesem `ComPtr` zugeordnete-Schnittstelle frei und ruft dann die Adresse des [ptr_](#ptr) Datenmembers ab, der einen Zeiger auf die-Schnittstelle enthält, die freigegeben wurde.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Rückgabewert

Die Adresse des [ptr_](#ptr) Datenmembers dieser `ComPtr`.

## <a name="comptrreset"></a><a name="reset"></a>Comptr:: Reset

Gibt alle Verweise für den Zeiger auf die-Schnittstelle frei, die mit diesem `ComPtr`verknüpft ist.

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der freigegeben Verweise, sofern vorhanden.

## <a name="comptrswap"></a><a name="swap"></a>Comptr:: Swap

Tauscht die Schnittstelle, die vom aktuellen `ComPtr` verwaltet wird, mit der vom angegebenen `ComPtr`verwalteten Schnittstelle aus.

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>Parameter

*r*<br/>
Ein `ComPtr`.
