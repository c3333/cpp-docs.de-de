---
title: HStringReference-Klasse
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::Get
- corewrappers/Microsoft::WRL::Wrappers::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HStringReference class
- Microsoft::WRL::Wrappers::HStringReference::CopyTo method
- Microsoft::WRL::Wrappers::HStringReference::Get method
- Microsoft::WRL::Wrappers::HStringReference::HStringReference, constructor
- Microsoft::WRL::Wrappers::HStringReference::operator= operator
- Microsoft::WRL::Wrappers::HStringReference::operator== operator
- Microsoft::WRL::Wrappers::HStringReference::operator!= operator
- Microsoft::WRL::Wrappers::HStringReference::operator< operator
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
ms.openlocfilehash: 34a2f0530d33eb61ac50b65dc1ae123d5ea5a0be
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509483"
---
# <a name="hstringreference-class"></a>HStringReference-Klasse

Stellt ein HSTRING dar, das aus einer vorhandenen Zeichenfolge erstellt wird.

## <a name="syntax"></a>Syntax

```cpp
class HStringReference;
```

## <a name="remarks"></a>Bemerkungen

Die Lebensdauer des Sicherungs Puffers in der neuen hstring wird nicht vom Windows-Runtime verwaltet. Der Aufrufer ordnet eine Quellzeichenfolge auf dem Stapelrahmen zu, um eine Heapzuweisung zu vermeiden und das Risiko eines Speicherverlusts auszuschließen. Außerdem muss der Aufrufer sicherstellen, dass die Quellzeichenfolge während der Lebensdauer des angefügten HSTRING unverändert bleibt. Weitere Informationen finden Sie unter [windowscreatestrauch ingreferenzierungsfunktion](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference).

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                    | BESCHREIBUNG
------------------------------------------------------- | -----------------------------------------------------------
[Hstrauingreferenzierung:: hstrauingreferenzierung](#hstringreference) | Initialisiert eine neue Instanz der Klasse `HStringReference`.

### <a name="public-methods"></a>Öffentliche Methoden

Member                              | BESCHREIBUNG
----------------------------------- | ------------------------------------------------------------------
[Hstrauingreferenzierung:: CopyTo](#copyto) | Kopiert das aktuelle `HStringReference`-Objekt in ein hstring-Objekt.
[Hstrauingreferenzierung:: Get](#get)       | Ruft den Wert des zugrunde liegenden HSTRING-Handles ab.
[Hstrauingreferenzierung:: getrawbuffer](#getrawbuffer) | Ruft einen Zeiger auf die zugrunde liegenden Zeichen folgen Daten ab.

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                                  | BESCHREIBUNG
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[Hstrauingreferenzierung:: Operator =](#operator-assign)       | Verschiebt den Wert eines anderen `HStringReference` Objekts in das aktuelle `HStringReference`-Objekt.
[Hstrauingreferenzierung:: Operator = =](#operator-equality)    | Gibt an, ob die zwei Parameter gleich sind.
[Hstrauingreferenzierung:: Operator! =](#operator-inequality)  | Gibt an, ob die zwei Parameter ungleich sind.
[Hstrauingreferen:: Operator&lt;](#operator-less-than) | Gibt an, ob der erste Parameter kleiner als der zweite Parameter ist.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`HStringReference`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** corewrappers. h

**Namespace:** Microsoft:: WRL:: Wrapper

## <a name="copyto"></a>Hstrauingreferenzierung:: CopyTo

Kopiert das aktuelle `HStringReference`-Objekt in ein hstring-Objekt.

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

## <a name="get"></a>Hstrauingreferenzierung:: Get

Ruft den Wert des zugrunde liegenden HSTRING-Handles ab.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Rückgabewert

Der Wert des zugrunde liegenden hstring-Handles.

## <a name="getrawbuffer"></a>Hstrauingreferenzierung:: getrawbuffer

Ruft einen Zeiger auf die zugrunde liegenden Zeichen folgen Daten ab.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Parameter

*Länge* Zeiger auf eine **int** -Variable, die die Länge der Daten empfängt.

### <a name="return-value"></a>Rückgabewert

Ein **konstanter** Zeiger auf die zugrunde liegenden Zeichen folgen Daten.

## <a name="hstringreference"></a>Hstrauingreferenzierung:: hstrauingreferenzierung

Initialisiert eine neue Instanz der Klasse `HStringReference`.

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>Parameter

*sizedest*<br/>
Ein Vorlagen Parameter, der die Größe des Ziel `HStringReference` Puffers angibt.

*str*<br/>
Ein Verweis auf eine Zeichenfolge mit breit Zeichen.

*len*<br/>
Die maximale Länge des *Str* -Parameter Puffers, der in diesem Vorgang verwendet werden soll. Wenn der *len* -Parameter nicht angegeben wird, wird der gesamte *Str* -Parameter verwendet. Wenn *len* größer als *sizedest*ist, wird *len* auf *sizedest*-1 festgelegt.

*other*<br/>
Ein weiteres `HStringReference`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert ein neues `HStringReference`-Objekt, das die gleiche Größe wie der Parameter *Str*hat.

Der zweite Konstruktor initialisiert ein neues `HStringReference`-Objekt, das die Größe des Parameters " *len*" angibt.

Der dritte Konstruktor initialisiert ein neues `HStringReference`-Objekt mit dem Wert des *anderen* Parameters und zerstört dann den *anderen* Parameter.

## <a name="operator-assign"></a>Hstrauingreferenzierung:: Operator =

Verschiebt den Wert eines anderen `HStringReference` Objekts in das aktuelle `HStringReference`-Objekt.

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>Parameter

*other*<br/>
Ein vorhandenes `HStringReference`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der Wert des vorhandenen *anderen* Objekts wird in das aktuelle `HStringReference` Objekt kopiert, und dann wird das *andere* Objekt zerstört.

## <a name="operator-equality"></a>Hstrauingreferenzierung:: Operator = =

Gibt an, ob die zwei Parameter gleich sind.

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Der erste zu vergleichende Parameter. *LHS* können ein `HStringReference` Objekt oder ein hstring-Handle sein.

*rhs*<br/>
Der zweite Parameter, der verglichen werden soll.  bei *RHS* kann es sich um ein `HStringReference` Objekt oder ein hstring-handle handeln.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die Parameter *LHS* und *RHS* gleich sind. andernfalls **false**.

## <a name="operator-inequality"></a>Hstrauingreferenzierung:: Operator! =

Gibt an, ob die zwei Parameter ungleich sind.

```cpp
inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Der erste zu vergleichende Parameter. *LHS* können ein `HStringReference` Objekt oder ein hstring-Handle sein.

*rhs*<br/>
Der zweite Parameter, der verglichen werden soll.  bei *RHS* kann es sich um ein `HStringReference` Objekt oder ein hstring-handle handeln.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die Parameter *LHS* und *RHS* nicht gleich sind. andernfalls **false**.

## <a name="operator-less-than"></a>Hstrauingreferen:: Operator&lt;

Gibt an, ob der erste Parameter kleiner als der zweite Parameter ist.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Der erste zu vergleichende Parameter. *LHS* können ein Verweis auf einen `HStringReference`sein.

*rhs*<br/>
Der zweite Parameter, der verglichen werden soll.  bei *RHS* kann es sich um einen Verweis auf eine `HStringReference`handeln.

### <a name="return-value"></a>Rückgabewert

**true** , wenn der *LHS* -Parameter kleiner als der *RHS* -Parameter ist. andernfalls **false**.
