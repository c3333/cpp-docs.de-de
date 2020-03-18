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
ms.openlocfilehash: a3765da94560eb84a1d441a6b25c42822fc857bb
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509470"
---
# <a name="hstring-class"></a>HString-Klasse

Eine Hilfsklasse zum Verwalten der Lebensdauer einer [hstring](/windows/win32/WinRT/hstring) mit dem RAII-Muster.

## <a name="syntax"></a>Syntax

```cpp
class HString;
```

## <a name="remarks"></a>Bemerkungen

Der Windows-Runtime ermöglicht den Zugriff auf Zeichen folgen über [hstring](/windows/win32/WinRT/hstring) -Handles. Die `HString`-Klasse bietet Hilfsfunktionen und Operatoren, um die Verwendung von hstring-Handles zu vereinfachen. Diese Klasse kann die Lebensdauer der hstring, die Sie besitzt, über ein RAII-Muster verarbeiten.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                | BESCHREIBUNG
----------------------------------- | -----------------------------------------------------
[Hstring:: hstring](#hstring)        | Initialisiert eine neue Instanz der Klasse `HString`.
[Hstring:: ~ hstring](#tilde-hstring) | Zerstört die aktuelle Instanz der `HString`-Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                     | BESCHREIBUNG
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[Hstring:: Attach](#attach)               | Ordnet das angegebene `HString` Objekt dem aktuellen `HString`-Objekt zu.
[Hstring:: CopyTo](#copyto)               | Kopiert das aktuelle `HString`-Objekt in ein hstring-Objekt.
[Hstring::D Etach](#detach)               | Trennt die Zuordnung des angegebenen `HString` Objekts zum zugrunde liegenden Wert.
[Hstring:: Get](#get)                     | Ruft den Wert des zugrunde liegenden HSTRING-Handles ab.
[Hstring:: getaddressof](#getaddressof)   | Ruft einen Zeiger auf das zugrunde liegende HSTRING-Handle ab.
[Hstring:: getrawbuffer](#getrawbuffer)   | Ruft einen Zeiger auf die zugrunde liegenden Zeichen folgen Daten ab.
[Hstring:: IsValid](#isvalid)             | Gibt an, ob das aktuelle `HString`-Objekt gültig ist.
[Hstring:: makereferenzierung](#makereference) | Erstellt ein `HStringReference`-Objekt aus einem angegebenen Zeichen folgen Parameter.
[Hstring:: Release](#release)             | Löscht den zugrunde liegenden Zeichen folgen Wert und initialisiert das aktuelle `HString`-Objekt in einen leeren Wert.
[Hstring:: Set](#set)                     | Legt den Wert des aktuellen `HString` Objekts auf die angegebene Zeichenfolge mit breit Zeichen oder `HString` Parameter fest.

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                         | BESCHREIBUNG
-------------------------------------------- | ----------------------------------------------------------------------------
[Hstring:: Operator =](#operator-assign)       | Verschiebt den Wert eines anderen `HString` Objekts in das aktuelle `HString`-Objekt.
[Hstring:: Operator = =](#operator-equality)    | Gibt an, ob die zwei Parameter gleich sind.
[Hstring:: Operator! =](#operator-inequality)  | Gibt an, ob die zwei Parameter ungleich sind.
[Hstring:: Operator-&lt;](#operator-less-than) | Gibt an, ob der erste Parameter kleiner als der zweite Parameter ist.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`HString`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** corewrappers. h

**Namespace:** Microsoft:: WRL:: Wrapper

## <a name="tilde-hstring"></a>Hstring:: ~ hstring

Zerstört die aktuelle Instanz der `HString`-Klasse.

```cpp
~HString() throw()
```

## <a name="attach"></a>Hstring:: Attach

Ordnet das angegebene `HString` Objekt dem aktuellen `HString`-Objekt zu.

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>Parameter

*HSTR*<br/>
Ein vorhandenes `HString`-Objekt.

## <a name="copyto"></a>Hstring:: CopyTo

Kopiert das aktuelle `HString`-Objekt in ein hstring-Objekt.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parameter

*str*<br/>
Das HSTRING, das die Kopie erhält.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft die [windowsduplicatestring](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring) -Funktion auf.

## <a name="detach"></a>Hstring::D Etach

Trennt die Zuordnung des angegebenen `HString` Objekts zum zugrunde liegenden Wert.

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>Rückgabewert

Der zugrunde liegende `HString` Wert, bevor der Trennvorgang gestartet wurde.

## <a name="get"></a>Hstring:: Get

Ruft den Wert des zugrunde liegenden HSTRING-Handles ab.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Rückgabewert

Der Wert des zugrunde liegenden hstring-Handles.

## <a name="getaddressof"></a>Hstring:: getaddressof

Ruft einen Zeiger auf das zugrunde liegende HSTRING-Handle ab.

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das zugrunde liegende hstring-handle.

### <a name="remarks"></a>Bemerkungen

Nach diesem Vorgang wird der Zeichen folgen Wert des zugrunde liegenden hstring-Handles zerstört.

## <a name="getrawbuffer"></a>Hstring:: getrawbuffer

Ruft einen Zeiger auf die zugrunde liegenden Zeichen folgen Daten ab.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Parameter

*Länge* Zeiger auf eine **int** -Variable, die die Länge der Daten empfängt.

### <a name="return-value"></a>Rückgabewert

Ein **konstanter** Zeiger auf die zugrunde liegenden Zeichen folgen Daten.


## <a name="hstring"></a>Hstring:: hstring

Initialisiert eine neue Instanz der Klasse `HString`.

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>Parameter

*HSTR*<br/>
Ein hstring-handle.

*other*<br/>
Ein vorhandenes `HString`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert ein neues `HString`-Objekt, das leer ist.

Der zweite Konstruktor initialisiert ein neues `HString`-Objekt mit dem Wert des vorhandenen *anderen* Parameters und zerstört dann den *anderen* Parameter.

## <a name="isvalid"></a>Hstring:: IsValid

Gibt an, ob das aktuelle `HString`-Objekt leer ist.

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>Parameter

**true** , wenn das aktuelle `HString` Objekt nicht leer ist. andernfalls **false**.

## <a name="makereference"></a>Hstring:: makereferenzierung

Erstellt ein `HStringReference`-Objekt aus einem angegebenen Zeichen folgen Parameter.

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

*sizedest*<br/>
Ein Vorlagen Parameter, der die Größe des Ziel `HStringReference` Puffers angibt.

*str*<br/>
Ein Verweis auf eine Zeichenfolge mit breit Zeichen.

*len*<br/>
Die maximale Länge des *Str* -Parameter Puffers, der in diesem Vorgang verwendet werden soll. Wenn der *len* -Parameter nicht angegeben wird, wird der gesamte *Str* -Parameter verwendet.

### <a name="return-value"></a>Rückgabewert

Ein `HStringReference` Objekt, dessen Wert mit dem angegebenen *Str* -Parameter übereinstimmt.

## <a name="operator-assign"></a>Hstring:: Operator =-Operator

Verschiebt den Wert eines anderen `HString` Objekts in das aktuelle `HString`-Objekt.

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>Parameter

*other*<br/>
Ein vorhandenes `HString`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der Wert des vorhandenen *anderen* Objekts wird in das aktuelle `HString` Objekt kopiert, und dann wird das *andere* Objekt zerstört.

## <a name="operator-equality"></a>Hstring:: Operator = =-Operator

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

*LHS*<br/>
Der erste zu vergleichende Parameter. *LHS* können ein `HString`-oder `HStringReference`-Objekt oder ein hstring-Handle sein.

*rhs*<br/>
Der zweite Parameter, der verglichen werden soll. bei *RHS* kann es sich um ein `HString`-oder `HStringReference`-Objekt oder ein hstring-handle handeln.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die Parameter *LHS* und *RHS* gleich sind. andernfalls **false**.

## <a name="operator-inequality"></a>Hstring:: Operator! =-Operator

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

*LHS*<br/>
Der erste zu vergleichende Parameter. *LHS* können ein `HString`-oder `HStringReference`-Objekt oder ein hstring-Handle sein.

*rhs*<br/>
Der zweite Parameter, der verglichen werden soll. bei *RHS* kann es sich um ein `HString`-oder `HStringReference`-Objekt oder ein hstring-handle handeln.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die Parameter *LHS* und *RHS* nicht gleich sind. andernfalls **false**.

## <a name="operator-less-than"></a>Hstring:: Operator&lt;-Operator

Gibt an, ob der erste Parameter kleiner als der zweite Parameter ist.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Der erste zu vergleichende Parameter. *LHS* können ein Verweis auf einen `HString`sein.

*rhs*<br/>
Der zweite Parameter, der verglichen werden soll. bei *RHS* kann es sich um einen Verweis auf eine `HString`handeln.

### <a name="return-value"></a>Rückgabewert

**true** , wenn der *LHS* -Parameter kleiner als der *RHS* -Parameter ist. andernfalls **false**.

## <a name="release"></a>Hstring:: Release

Löscht den zugrunde liegenden Zeichen folgen Wert und initialisiert das aktuelle `HString`-Objekt in einen leeren Wert.

```cpp
void Release() throw()
```

## <a name="set"></a>Hstring:: Set

Legt den Wert des aktuellen `HString` Objekts auf die angegebene Zeichenfolge mit breit Zeichen oder `HString` Parameter fest.

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

*str*<br/>
Eine Zeichenfolge mit breit Zeichen.

*len*<br/>
Die maximale Länge des *Str* -Parameters, der dem aktuellen `HString`-Objekt zugewiesen ist.

*HSTR*<br/>
Ein vorhandenes `HString`-Objekt.
