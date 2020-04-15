---
title: HString-Klasse
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
- corewrappers/Microsoft::WRL::Wrappers::HString::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator==
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
- corewrappers/Microsoft::WRL::Wrappers::HString::Release
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
- corewrappers/Microsoft::WRL::Wrappers::HString::~HString
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HString class
- Microsoft::WRL::Wrappers::HString::Attach method
- Microsoft::WRL::Wrappers::HString::CopyTo method
- Microsoft::WRL::Wrappers::HString::Detach method
- Microsoft::WRL::Wrappers::HString::Get method
- Microsoft::WRL::Wrappers::HString::GetAddressOf method
- Microsoft::WRL::Wrappers::HString::HString, constructor
- Microsoft::WRL::Wrappers::HString::IsValid method
- Microsoft::WRL::Wrappers::HString::MakeReference method
- Microsoft::WRL::Wrappers::HString::operator= operator
- Microsoft::WRL::Wrappers::HString::operator== operator
- Microsoft::WRL::Wrappers::HString::operator!= operator
- Microsoft::WRL::Wrappers::HString::operator< operator
- Microsoft::WRL::Wrappers::HString::Release method
- Microsoft::WRL::Wrappers::HString::Set method
- Microsoft::WRL::Wrappers::HString::~HString, destructor
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
ms.openlocfilehash: 625d7b7d6fc001a6fb63144807b5f29d3620485b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371431"
---
# <a name="hstring-class"></a>HString-Klasse

Eine Hilfsklasse zum Verwalten der Lebensdauer eines [HSTRING](/windows/win32/WinRT/hstring) mithilfe des RAII-Musters.

## <a name="syntax"></a>Syntax

```cpp
class HString;
```

## <a name="remarks"></a>Bemerkungen

Die Windows-Runtime bietet [HSTRING](/windows/win32/WinRT/hstring) Zugriff auf Zeichenfolgen über HSTRING-Handles. Die `HString` Klasse bietet Komfortfunktionen und Operatoren, um die Verwendung von HSTRING-Handles zu vereinfachen. Diese Klasse kann die Lebensdauer des HSTRING, das sie besitzt, über ein RAII-Muster verarbeiten.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                | BESCHREIBUNG
----------------------------------- | -----------------------------------------------------
[HString::HString](#hstring)        | Initialisiert eine neue Instanz der Klasse `HString`.
[HString::-HString](#tilde-hstring) | Zerstört die aktuelle Instanz `HString` der Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                     | BESCHREIBUNG
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString::Anfügen](#attach)               | Ordnet das `HString` angegebene Objekt `HString` dem aktuellen Objekt zu.
[HString::CopyTo](#copyto)               | Kopiert das `HString` aktuelle Objekt in ein HSTRING-Objekt.
[HString::Detach](#detach)               | Trennt das `HString` angegebene Objekt vom zugrunde liegenden Wert.
[HString::Get](#get)                     | Ruft den Wert des zugrunde liegenden HSTRING-Handles ab.
[HString::GetAddressOf](#getaddressof)   | Ruft einen Zeiger auf das zugrunde liegende HSTRING-Handle ab.
[HString::GetRawBuffer](#getrawbuffer)   | Ruft einen Zeiger auf die zugrunde liegenden Zeichenfolgendaten ab.
[HString::IsValid](#isvalid)             | Gibt an, `HString` ob das aktuelle Objekt gültig ist.
[HString::MakeReference](#makereference) | Erstellt `HStringReference` ein Objekt aus einem angegebenen Zeichenfolgenparameter.
[HString::Release](#release)             | Löscht den zugrunde liegenden Zeichenfolgenwert und `HString` initiiert das aktuelle Objekt auf einen leeren Wert.
[HString::Set](#set)                     | Legt den Wert `HString` des aktuellen Objekts auf `HString` die angegebene Breitzeichenzeichenfolge oder den angegebenen Parameter fest.

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                         | BESCHREIBUNG
-------------------------------------------- | ----------------------------------------------------------------------------
[HString::operator=](#operator-assign)       | Verschiebt den `HString` Wert eines `HString` anderen Objekts auf das aktuelle Objekt.
[HString::operator==](#operator-equality)    | Gibt an, ob die zwei Parameter gleich sind.
[HString::operator!=](#operator-inequality)  | Gibt an, ob die zwei Parameter ungleich sind.
[HString::Operator&lt;](#operator-less-than) | Gibt an, ob der erste Parameter kleiner als der zweite Parameter ist.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`HString`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="hstringhstring"></a><a name="tilde-hstring"></a>HString::-HString

Zerstört die aktuelle Instanz `HString` der Klasse.

```cpp
~HString() throw()
```

## <a name="hstringattach"></a><a name="attach"></a>HString::Anfügen

Ordnet das `HString` angegebene Objekt `HString` dem aktuellen Objekt zu.

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>Parameter

*hstr*<br/>
Ein vorhandenes `HString`-Objekt.

## <a name="hstringcopyto"></a><a name="copyto"></a>HString::CopyTo

Kopiert das `HString` aktuelle Objekt in ein HSTRING-Objekt.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Das HSTRING, das die Kopie erhält.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft die [WindowsDuplicateString-Funktion](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring) auf.

## <a name="hstringdetach"></a><a name="detach"></a>HString::Detach

Trennt das `HString` angegebene Objekt vom zugrunde liegenden Wert.

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>Rückgabewert

Der `HString` zugrunde liegende Wert vor dem Start des Trennvorgangs.

## <a name="hstringget"></a><a name="get"></a>HString::Get

Ruft den Wert des zugrunde liegenden HSTRING-Handles ab.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Rückgabewert

Der Wert des zugrunde liegenden HSTRING-Handles

## <a name="hstringgetaddressof"></a><a name="getaddressof"></a>HString::GetAddressOf

Ruft einen Zeiger auf das zugrunde liegende HSTRING-Handle ab.

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das zugrunde liegende HSTRING-Handle.

### <a name="remarks"></a>Bemerkungen

Nach diesem Vorgang wird der Zeichenfolgenwert des zugrunde liegenden HSTRING-Handles zerstört.

## <a name="hstringgetrawbuffer"></a><a name="getrawbuffer"></a>HString::GetRawBuffer

Ruft einen Zeiger auf die zugrunde liegenden Zeichenfolgendaten ab.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Parameter

*Länge* Zeiger auf eine **int-Variable,** die die Länge der Daten empfängt.

### <a name="return-value"></a>Rückgabewert

Ein **const-Zeiger** auf die zugrunde liegenden Zeichenfolgendaten.

## <a name="hstringhstring"></a><a name="hstring"></a>HString::HString

Initialisiert eine neue Instanz der Klasse `HString`.

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>Parameter

*hstr*<br/>
Ein HSTRING-Handle.

*Andere*<br/>
Ein vorhandenes `HString`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert `HString` ein neues Objekt, das leer ist.

Der zweite Konstruktor initialisiert `HString` ein neues Objekt auf den Wert des vorhandenen *anderen* Parameters und zerstört dann den *anderen* Parameter.

## <a name="hstringisvalid"></a><a name="isvalid"></a>HString::IsValid

Gibt an, `HString` ob das aktuelle Objekt leer ist oder nicht.

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>Parameter

**true,** wenn `HString` das aktuelle Objekt nicht leer ist; andernfalls **false**.

## <a name="hstringmakereference"></a><a name="makereference"></a>HString::MakeReference

Erstellt `HStringReference` ein Objekt aus einem angegebenen Zeichenfolgenparameter.

```cpp
template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[ sizeDest]);

    template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[sizeDest],
              unsigned int len);
```

### <a name="parameters"></a>Parameter

*sizeDest*<br/>
Ein Vorlagenparameter, der die Größe `HStringReference` des Zielpuffers angibt.

*Str*<br/>
Ein Verweis auf eine Zeichenfolge mit großen Zeichen.

*Len*<br/>
Die maximale Länge *str* des str-Parameterpuffers, der in diesem Vorgang verwendet werden soll. Wenn der *parameter len* nicht angegeben ist, wird der gesamte *str-Parameter* verwendet.

### <a name="return-value"></a>Rückgabewert

Ein `HStringReference` Objekt, dessen Wert mit dem angegebenen *str-Parameter* identisch ist.

## <a name="hstringoperator-operator"></a><a name="operator-assign"></a>HString::operator= Operator

Verschiebt den `HString` Wert eines `HString` anderen Objekts auf das aktuelle Objekt.

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein vorhandenes `HString`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der Wert des vorhandenen *anderen* Objekts `HString` wird in das aktuelle Objekt kopiert, und dann wird das *andere* Objekt zerstört.

## <a name="hstringoperator-operator"></a><a name="operator-equality"></a>HString::operator== Operator

Gibt an, ob die zwei Parameter gleich sind.

```cpp
inline bool operator==(
               const HString& lhs,
               const HString& rhs) throw()

inline bool operator==(
                const HString& lhs,
                const HStringReference& rhs) throw()

inline bool operator==(
                const HStringReference& lhs,
                const HString& rhs) throw()

inline bool operator==(
                 const HSTRING& lhs,
                 const HString& rhs) throw()

inline bool operator==(
                 const HString& lhs,
                 const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Der erste zu vergleichende Parameter. *lhs* kann `HString` ein `HStringReference` oder ein Objekt oder ein HSTRING-Handle sein.

*rhs*<br/>
Der zweite zu vergleichende Parameter. *kann* ein `HString` oder `HStringReference` ein Objekt oder ein HSTRING-Handle sein.

### <a name="return-value"></a>Rückgabewert

**true,** wenn die *Parameter lhs* und *rhs* gleich sind; andernfalls **false**.

## <a name="hstringoperator-operator"></a><a name="operator-inequality"></a>HString::operator!= Operator

Gibt an, ob die zwei Parameter ungleich sind.

```cpp
inline bool operator!=( const HString& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HStringReference& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HStringReference& rhs) throw()

inline bool operator!=( const HSTRING& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Der erste zu vergleichende Parameter. *lhs* kann `HString` ein `HStringReference` oder ein Objekt oder ein HSTRING-Handle sein.

*rhs*<br/>
Der zweite zu vergleichende Parameter. *kann* ein `HString` oder `HStringReference` ein Objekt oder ein HSTRING-Handle sein.

### <a name="return-value"></a>Rückgabewert

**true,** wenn die *Parameter lhs* und *rhs* nicht gleich sind; andernfalls **false**.

## <a name="hstringoperatorlt-operator"></a><a name="operator-less-than"></a>HString::Operator-Operator&lt;

Gibt an, ob der erste Parameter kleiner als der zweite Parameter ist.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Der erste zu vergleichende Parameter. *lhs* kann ein Verweis `HString`auf eine sein.

*rhs*<br/>
Der zweite zu vergleichende Parameter. *rhs* kann ein Verweis `HString`auf eine sein.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der *lhs-Parameter* kleiner als der *rhs-Parameter* ist; andernfalls **false**.

## <a name="hstringrelease"></a><a name="release"></a>HString::Release

Löscht den zugrunde liegenden Zeichenfolgenwert und `HString` initiiert das aktuelle Objekt auf einen leeren Wert.

```cpp
void Release() throw()
```

## <a name="hstringset"></a><a name="set"></a>HString::Set

Legt den Wert `HString` des aktuellen Objekts auf `HString` die angegebene Breitzeichenzeichenfolge oder den angegebenen Parameter fest.

```cpp
HRESULT Set(
          const wchar_t* str) throw();
HRESULT Set(
          const wchar_t* str,
          unsigned int len
           ) throw();
HRESULT Set(
          const HSTRING& hstr
           ) throw();
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Eine Breitzeichenzeichenfolge.

*Len*<br/>
Die maximale Länge des *parameters str,* `HString` der dem aktuellen Objekt zugewiesen ist.

*hstr*<br/>
Ein vorhandenes `HString`-Objekt.
