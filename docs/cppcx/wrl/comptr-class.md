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
ms.openlocfilehash: 89c09ede972f5bdd5da1dde810cad31733bdf338
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372642"
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
Die Schnittstelle, `ComPtr` die der darstellt.

*U*<br/>
Eine Klasse, zu `ComPtr` der der Strom ein Freund ist. (Die Vorlage, die diesen Parameter verwendet, ist geschützt.)

## <a name="remarks"></a>Bemerkungen

`ComPtr<>`deklariert einen Typ, der den zugrunde liegenden Schnittstellenzeiger darstellt. Verwenden `ComPtr<>` Sie diese Funktion, um eine Variable`->`zu deklarieren, und verwenden Sie dann den Pfeilmemberzugriffsoperator ( ), um auf eine Schnittstellenmemberfunktion zuzugreifen.

Weitere Informationen zu intelligenten Zeigern finden Sie im Unterabschnitt "COM Smart Pointers" des Themas [COM-Codierungspraktiken](/windows/win32/LearnWin32/com-coding-practices) in der MSDN-Bibliothek.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name            | BESCHREIBUNG
--------------- | ---------------------------------------------------------------
`InterfaceType` | Ein Synonym für den typ, der durch den *Parameter T-Vorlage* angegeben wird.

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                             | BESCHREIBUNG
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr::ComPtr](#comptr)        | Initialisiert eine neue Instanz der `ComPtr`-Klasse. Überladungen stellen Standard-, Kopier-, Verschiebe- und Konvertierungskonstruktoren bereit.
[ComPtr::'ComPtr](#tilde-comptr) | Deinitialisiert eine Instanz `ComPtr`von .

### <a name="public-methods"></a>Öffentliche Methoden

Name                                                      | BESCHREIBUNG
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr::As](#as)                                         | Gibt `ComPtr` ein Objekt zurück, das die Schnittstelle darstellt, die durch den angegebenen Vorlagenparameter identifiziert wird.
[ComPtr::AsIID](#asiid)                                   | Gibt `ComPtr` ein Objekt zurück, das die Schnittstelle darstellt, die durch die angegebene Schnittstellen-ID identifiziert wird.
[ComPtr::AsWeak](#asweak)                                 | Ruft einen schwachen Verweis (WeakReference) auf das aktuelle Objekt ab.
[ComPtr::Anfügen](#attach)                                 | Ordnet `ComPtr` dies dem Schnittstellentyp zu, der durch den aktuellen Vorlagentypparameter angegeben wird.
[ComPtr::KopierenBis](#copyto)                                 | Kopiert die ihm zugeordnete `ComPtr` aktuelle oder angegebene Schnittstelle in den angegebenen Ausgabezeiger.
[ComPtr::Detach](#detach)                                 | Entfernt dies `ComPtr` von der Schnittstelle, die es darstellt.
[ComPtr::Get](#get)                                       | Ruft einen Zeiger auf die Schnittstelle ab, die dieser `ComPtr`zugeordnet ist.
[ComPtr::GetAddressOf](#getaddressof)                     | Ruft die Adresse des [ptr_](#ptr) Datenmembers ab, der einen `ComPtr`Zeiger auf die schnittstelle enthält, die durch diese dargestellt wird.
[ComPtr::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Gibt die diesem `ComPtr` verknüpfte Schnittstelle frei und ruft dann die Adresse des ptr_-Datenmembers ab, der einen Zeiger auf die freigegebene Schnittstelle enthält. [ptr_](#ptr)
[ComPtr::Reset](#reset)                                   | Gibt alle Verweise für den Zeiger auf die `ComPtr`Schnittstelle frei, die dieser zugeordnet ist.
[ComPtr::Swap](#swap)                                     | Tauscht die vom `ComPtr` Aktuellen verwaltete Schnittstelle `ComPtr`mit der Schnittstelle aus, die von der angegebenen verwaltet wird.

### <a name="protected-methods"></a>Geschützte Methoden

Name                                        | BESCHREIBUNG
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::InternalAddRef](#internaladdref)   | Inkrementiert die Referenzanzahl der `ComPtr`Schnittstelle, die dieser zugeordnet ist.
[ComPtr::InterneFreigabe](#internalrelease) | Führt einen COM-Releasevorgang auf `ComPtr`der Schnittstelle aus, die dieser zugeordnet ist.

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                                                                           | BESCHREIBUNG
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr::Operator&](#operator-ampersand)                                                       | Ruft die Adresse der `ComPtr`aktuellen ab.
[ComPtr::Operator->](#operator-arrow)                                                          | Ruft einen Zeiger auf den Typ ab, der durch den aktuellen Vorlagenparameter angegeben ist.
[ComPtr::operator=](#operator-assign)                                                          | Weist der aktuellen `ComPtr`einen Wert zu.
[ComPtr::operator==](#operator-equality)                                                       | Gibt an, ob zwei `ComPtr`-Objekte gleich sind.
[ComPtr::operator!=](#operator-inequality)                                                     | Gibt an, ob zwei `ComPtr`-Objekte ungleich sind.
[ComPtr::operator Microsoft::WRL::Details::BoolType](#operator-microsoft-wrl-details-booltype) | Gibt an, `ComPtr` ob ein die Objektlebensdauer einer Schnittstelle verwaltet.

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                 | BESCHREIBUNG
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::ptr_](#ptr) | Enthält einen Zeiger auf die Schnittstelle, die dieser `ComPtr`zugeordnet ist und von diesem verwaltet wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ComPtr`

## <a name="requirements"></a>Anforderungen

**Header:** client.h

**Namespace:** Microsoft::WRL

## <a name="comptrcomptr"></a><a name="tilde-comptr"></a>ComPtr::'ComPtr

Deinitialisiert eine Instanz `ComPtr`von .

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="comptras"></a><a name="as"></a>ComPtr::As

Gibt `ComPtr` ein Objekt zurück, das die Schnittstelle darstellt, die durch den angegebenen Vorlagenparameter identifiziert wird.

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

*P*<br/>
Ein `ComPtr` Objekt, das die durch den Parameter *U*angegebene Schnittstelle darstellt. Parameter *p* darf nicht `ComPtr` auf das aktuelle Objekt verweisen.

### <a name="remarks"></a>Bemerkungen

Die erste Vorlage ist die Form, die Sie in Ihrem Code verwenden sollten. Die zweite Vorlage ist eine interne Hilfsspezialisierung, die C++-Sprachfeatures unterstützt, wie etwa das Schlüsselwort [auto](../../cpp/auto-cpp.md) zur Typableitung.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="comptrasiid"></a><a name="asiid"></a>ComPtr::AsIID

Gibt `ComPtr` ein Objekt zurück, das die Schnittstelle darstellt, die durch die angegebene Schnittstellen-ID identifiziert wird.

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Eine Schnittstellen-ID.

*P*<br/>
Wenn das Objekt über eine Schnittstelle verfügt, deren ID *riid*, ein doppelt indirekter Zeiger auf die durch den *riid-Parameter* angegebene Schnittstelle ist; Andernfalls ein Zeiger `IUnknown`auf .

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="comptrasweak"></a><a name="asweak"></a>ComPtr::AsWeak

Ruft einen schwachen Verweis (WeakReference) auf das aktuelle Objekt ab.

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>Parameter

*pWeakRef*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird ein Zeiger auf ein schwaches Referenzobjekt zeiger.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="comptrattach"></a><a name="attach"></a>ComPtr::Anfügen

Ordnet `ComPtr` dies dem Schnittstellentyp zu, der durch den aktuellen Vorlagentypparameter angegeben wird.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein Schnittstellentyp.

## <a name="comptrcomptr"></a><a name="comptr"></a>ComPtr::ComPtr

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

*Andere*<br/>
Ein Objekt vom Typ *U*.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor ist der Standardkonstruktor, der unvoreingenommen ein leeres Objekt erstellt. Der zweite Konstruktor gibt [__nullptr](../../extensions/nullptr-cpp-component-extensions.md)an, der explizit ein leeres Objekt erstellt.

Der dritte Konstruktor erstellt ein Objekt aus dem Objekt, das durch einen Zeiger angegeben wird. Der ComPtr besitzt nun das pointierte Gedächtnis und behält eine Referenzanzahl dafür bei.

Der vierte und fünfte Konstruktor sind Kopierkonstruktoren. Der fünfte Konstruktor kopiert ein Objekt, wenn es in den aktuellen Typ umgewandelt werden kann.

Die sechsten und siebten Konstruktoren sind Bewegungskonstruktoren. Der siebte Konstruktor verschiebt ein Objekt, wenn es in den aktuellen Typ umgewandelt werden kann.

## <a name="comptrcopyto"></a><a name="copyto"></a>ComPtr::KopierenBis

Kopiert die aktuelle oder angegebene `ComPtr` Schnittstelle, die dieser Schnittstelle zugeordnet ist, in den angegebenen Zeiger.

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

*Ptr*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird ein Zeiger auf die angeforderte Schnittstelle angezeigt.

*riid*<br/>
Eine Schnittstellen-ID.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls ein HRESULT, das `QueryInterface` angibt, warum der implizite Vorgang fehlgeschlagen ist.

### <a name="remarks"></a>Bemerkungen

Die erste Funktion gibt eine Kopie eines Zeigers `ComPtr`an die Schnittstelle zurück, die dieser zugeordnet ist. Diese Funktion gibt immer S_OK zurück.

Die zweite Funktion `QueryInterface` führt einen Vorgang `ComPtr` auf der Schnittstelle aus, die diesem für die schnittstelle zugeordnet ist, die durch den *riid-Parameter* angegeben wird.

Die dritte Funktion `QueryInterface` führt einen Vorgang `ComPtr` auf der Schnittstelle aus, die dieser Schnittstelle für die zugrunde liegende Schnittstelle des *U-Parameters* zugeordnet ist.

## <a name="comptrdetach"></a><a name="detach"></a>ComPtr::Detach

Trennt dieses `ComPtr` Objekt von der Schnittstelle, die es darstellt.

```cpp
T* Detach();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Schnittstelle, `ComPtr` die von diesem Objekt dargestellt wurde.

## <a name="comptrget"></a><a name="get"></a>ComPtr::Get

Ruft einen Zeiger auf die Schnittstelle ab, die dieser `ComPtr`zugeordnet ist.

```cpp
T* Get() const;
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf die Schnittstelle, die `ComPtr`dieser zugeordnet ist.

## <a name="comptrgetaddressof"></a><a name="getaddressof"></a>ComPtr::GetAddressOf

Ruft die Adresse des [ptr_](#ptr) Datenmembers ab, der einen `ComPtr`Zeiger auf die schnittstelle enthält, die durch diese dargestellt wird.

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Rückgabewert

Die Adresse einer Variablen.

## <a name="comptrinternaladdref"></a><a name="internaladdref"></a>ComPtr::InternalAddRef

Inkrementiert die Referenzanzahl der `ComPtr`Schnittstelle, die dieser zugeordnet ist.

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Bemerkungen

Diese Methode ist geschützt.

## <a name="comptrinternalrelease"></a><a name="internalrelease"></a>ComPtr::InterneFreigabe

Führt einen COM-Releasevorgang auf `ComPtr`der Schnittstelle aus, die dieser zugeordnet ist.

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode ist geschützt.

## <a name="comptroperatoramp"></a><a name="operator-ampersand"></a>ComPtr::Operator&amp;

Gibt die diesem `ComPtr` Objekt zugeordnete Schnittstelle frei `ComPtr` und ruft dann die Adresse des Objekts ab.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Rückgabewert

Ein schwacher Verweis `ComPtr`auf den Strom .

### <a name="remarks"></a>Bemerkungen

Diese Methode unterscheidet sich von [ComPtr::GetAddressOf](#getaddressof) dadurch, dass diese Methode einen Verweis auf den Schnittstellenzeiger freigibt. Verwenden `ComPtr::GetAddressOf` Sie diese Version, wenn Sie die Adresse des Schnittstellenzeigers benötigen, diese Schnittstelle jedoch nicht freigeben möchten.

## <a name="comptroperator-gt"></a><a name="operator-arrow"></a>ComPtr::operator-&gt;

Ruft einen Zeiger auf den Typ ab, der durch den aktuellen Vorlagenparameter angegeben ist.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf den Typ, der durch den aktuellen Vorlagentypnamen angegeben wird.

### <a name="remarks"></a>Bemerkungen

Diese Hilfsfunktion entfernt unnötigen Overhead, der durch die Verwendung des STDMETHOD-Makros verursacht wird. Diese Funktion `IUnknown` `private` macht `virtual`Typen anstelle von .

## <a name="comptroperator"></a><a name="operator-assign"></a>ComPtr::operator=

Weist der aktuellen `ComPtr`einen Wert zu.

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
Eine Klasse.

*Andere*<br/>
Ein Zeiger-, Verweis- oder rvalue-Verweis `ComPtr`auf einen Typ oder einen anderen .

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf `ComPtr`die aktuelle .

### <a name="remarks"></a>Bemerkungen

Die erste Version dieses Operators weist dem `ComPtr`aktuellen einen leeren Wert zu.

Wenn in der zweiten Version der Zuweisungsschnittstellenzeiger nicht `ComPtr` mit dem aktuellen Schnittstellenzeiger identisch ist, `ComPtr`wird der zweite Schnittstellenzeiger dem aktuellen zugewiesen.

In der dritten Version wird der zuweisende Schnittstellenzeiger dem aktuellen `ComPtr`zugewiesen.

Wenn in der vierten Version der Schnittstellenzeiger des Zuweisungswerts `ComPtr` nicht mit dem aktuellen Schnittstellenzeiger identisch ist, wird der zweite Schnittstellenzeiger dem aktuellen `ComPtr`zugewiesen.

Die fünfte Version ist ein Kopieroperator; ein Verweis `ComPtr` auf eine wird `ComPtr`dem aktuellen zugewiesen.

Die sechste Version ist ein Kopieroperator, der die Bewegungssemantik verwendet. ein rvalue-Verweis `ComPtr` auf einen, wenn ein Typ `ComPtr`statisch gegossen und dann dem aktuellen zugewiesen wird.

Die siebte Version ist ein Kopieroperator, der die Bewegungssemantik verwendet. Ein rvalue-Verweis `ComPtr` auf einen Vom Typ *U* wird `ComPtr`dann statisch gegossen und dem aktuellen zugewiesen.

## <a name="comptroperator"></a><a name="operator-equality"></a>ComPtr::operator==

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

*Eine*<br/>
Ein Verweis auf ein `ComPtr`-Objekt.

*B*<br/>
Ein Verweis `ComPtr` auf ein anderes Objekt.

### <a name="return-value"></a>Rückgabewert

Der erste Operator `true` ergibt, wenn Objekt *a* gleich Objekt *b*ist; andernfalls `false`.

Der zweite und `true` dritte Operator ergeben, `nullptr`wenn Objekt *a* gleich ist; andernfalls `false`.

## <a name="comptroperator"></a><a name="operator-inequality"></a>ComPtr::operator!=

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

*Eine*<br/>
Ein Verweis auf ein `ComPtr`-Objekt.

*B*<br/>
Ein Verweis `ComPtr` auf ein anderes Objekt.

### <a name="return-value"></a>Rückgabewert

Der erste Operator `true` ergibt, wenn Objekt *a* nicht gleich Objekt *b*ist; andernfalls `false`.

Der zweite und `true` dritte Operator ergeben, `nullptr`wenn Objekt *a* nicht gleich ist; andernfalls `false`.

## <a name="comptroperator-microsoftwrldetailsbooltype"></a><a name="operator-microsoft-wrl-details-booltype"></a>ComPtr::operator Microsoft::WRL::Details::BoolType

Gibt an, `ComPtr` ob ein die Objektlebensdauer einer Schnittstelle verwaltet.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn eine Schnittstelle mit `ComPtr`dieser verknüpft ist, wird die Adresse des [BoolStruct::Member-Datenmembers;](boolstruct-structure.md#member) andernfalls `nullptr`.

## <a name="comptrptr_"></a><a name="ptr"></a>ComPtr::ptr_

Enthält einen Zeiger auf die Schnittstelle, die dieser `ComPtr`zugeordnet ist und von diesem verwaltet wird.

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Bemerkungen

`ptr_`ist ein internes, geschütztes Datenmitglied.

## <a name="comptrreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComPtr::ReleaseAndGetAddressOf

Gibt die diesem `ComPtr` verknüpfte Schnittstelle frei und ruft dann die Adresse des ptr_-Datenmembers ab, der einen Zeiger auf die freigegebene Schnittstelle enthält. [ptr_](#ptr)

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Rückgabewert

Die Adresse des [ptr_](#ptr) Datenmitglieds dieser `ComPtr`.

## <a name="comptrreset"></a><a name="reset"></a>ComPtr::Reset

Gibt alle Verweise für den Zeiger auf die `ComPtr`Schnittstelle frei, die dieser zugeordnet ist.

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der freigegeben Verweise, sofern vorhanden.

## <a name="comptrswap"></a><a name="swap"></a>ComPtr::Swap

Tauscht die vom `ComPtr` Aktuellen verwaltete Schnittstelle `ComPtr`mit der Schnittstelle aus, die von der angegebenen verwaltet wird.

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>Parameter

*R*<br/>
Ein `ComPtr`.
