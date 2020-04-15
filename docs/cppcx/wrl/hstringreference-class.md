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
ms.openlocfilehash: fd064f97081fad1a9df9de0865bb7c46ad5b4484
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371420"
---
# <a name="hstringreference-class"></a>HStringReference-Klasse

Stellt ein HSTRING dar, das aus einer vorhandenen Zeichenfolge erstellt wird.

## <a name="syntax"></a>Syntax

```cpp
class HStringReference;
```

## <a name="remarks"></a>Bemerkungen

Die Lebensdauer des Sicherungspuffers im neuen HSTRING wird nicht von der Windows-Runtime verwaltet. Der Aufrufer ordnet eine Quellzeichenfolge auf dem Stapelrahmen zu, um eine Heapzuweisung zu vermeiden und das Risiko eines Speicherverlusts auszuschließen. Außerdem muss der Aufrufer sicherstellen, dass die Quellzeichenfolge während der Lebensdauer des angefügten HSTRING unverändert bleibt. Weitere Informationen finden Sie unter [WindowsCreateStringReference-Funktion](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference).

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                    | BESCHREIBUNG
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference::HStringReference](#hstringreference) | Initialisiert eine neue Instanz der Klasse `HStringReference`.

### <a name="public-methods"></a>Öffentliche Methoden

Member                              | BESCHREIBUNG
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | Kopiert das `HStringReference` aktuelle Objekt in ein HSTRING-Objekt.
[HStringReference::Get](#get)       | Ruft den Wert des zugrunde liegenden HSTRING-Handles ab.
[HStringReference::GetRawBuffer](#getrawbuffer) | Ruft einen Zeiger auf die zugrunde liegenden Zeichenfolgendaten ab.

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                                  | BESCHREIBUNG
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference::operator=](#operator-assign)       | Verschiebt den `HStringReference` Wert eines `HStringReference` anderen Objekts auf das aktuelle Objekt.
[HStringReference::operator==](#operator-equality)    | Gibt an, ob die zwei Parameter gleich sind.
[HStringReference::operator!=](#operator-inequality)  | Gibt an, ob die zwei Parameter ungleich sind.
[HStringReference::operator&lt;](#operator-less-than) | Gibt an, ob der erste Parameter kleiner als der zweite Parameter ist.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`HStringReference`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="hstringreferencecopyto"></a><a name="copyto"></a>HStringReference::CopyTo

Kopiert das `HStringReference` aktuelle Objekt in ein HSTRING-Objekt.

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

## <a name="hstringreferenceget"></a><a name="get"></a>HStringReference::Get

Ruft den Wert des zugrunde liegenden HSTRING-Handles ab.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Rückgabewert

Der Wert des zugrunde liegenden HSTRING-Handles.

## <a name="hstringreferencegetrawbuffer"></a><a name="getrawbuffer"></a>HStringReference::GetRawBuffer

Ruft einen Zeiger auf die zugrunde liegenden Zeichenfolgendaten ab.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Parameter

*Länge* Zeiger auf eine **int-Variable,** die die Länge der Daten empfängt.

### <a name="return-value"></a>Rückgabewert

Ein **const-Zeiger** auf die zugrunde liegenden Zeichenfolgendaten.

## <a name="hstringreferencehstringreference"></a><a name="hstringreference"></a>HStringReference::HStringReference

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

*sizeDest*<br/>
Ein Vorlagenparameter, der die Größe `HStringReference` des Zielpuffers angibt.

*Str*<br/>
Ein Verweis auf eine Zeichenfolge mit großen Zeichen.

*Len*<br/>
Die maximale Länge *str* des str-Parameterpuffers, der in diesem Vorgang verwendet werden soll. Wenn der *parameter len* nicht angegeben ist, wird der gesamte *str-Parameter* verwendet. Wenn *len* größer als *sizeDest*ist, wird *len* auf *sizeDest*-1 gesetzt.

*Andere*<br/>
Ein `HStringReference` weiteres Objekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert `HStringReference` ein neues Objekt, das die gleiche Größe wie der Parameter *str*hat.

Der zweite Konstruktor initialisiert `HStringReference` ein neues Objekt, das die Größe durch Parameter *len*spezifeid .

Der dritte Konstruktor initialisiert `HStringReference` ein neues Objekt auf den Wert des *anderen* Parameters und zerstört dann den *anderen* Parameter.

## <a name="hstringreferenceoperator"></a><a name="operator-assign"></a>HStringReference::operator=

Verschiebt den `HStringReference` Wert eines `HStringReference` anderen Objekts auf das aktuelle Objekt.

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein vorhandenes `HStringReference`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der Wert des vorhandenen *anderen* Objekts `HStringReference` wird in das aktuelle Objekt kopiert, und dann wird das *andere* Objekt zerstört.

## <a name="hstringreferenceoperator"></a><a name="operator-equality"></a>HStringReference::operator==

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

*Lhs*<br/>
Der erste zu vergleichende Parameter. *lhs* kann `HStringReference` ein Objekt oder ein HSTRING-Handle sein.

*rhs*<br/>
Der zweite zu vergleichende Parameter.  *können* ein `HStringReference` Objekt oder ein HSTRING-Handle sein.

### <a name="return-value"></a>Rückgabewert

**true,** wenn die *Parameter lhs* und *rhs* gleich sind; andernfalls **false**.

## <a name="hstringreferenceoperator"></a><a name="operator-inequality"></a>HStringReference::operator!=

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

*Lhs*<br/>
Der erste zu vergleichende Parameter. *lhs* kann `HStringReference` ein Objekt oder ein HSTRING-Handle sein.

*rhs*<br/>
Der zweite zu vergleichende Parameter.  *können* ein `HStringReference` Objekt oder ein HSTRING-Handle sein.

### <a name="return-value"></a>Rückgabewert

**true,** wenn die *Parameter lhs* und *rhs* nicht gleich sind; andernfalls **false**.

## <a name="hstringreferenceoperatorlt"></a><a name="operator-less-than"></a>HStringReference::operator&lt;

Gibt an, ob der erste Parameter kleiner als der zweite Parameter ist.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Der erste zu vergleichende Parameter. *lhs* kann ein Verweis `HStringReference`auf eine sein.

*rhs*<br/>
Der zweite zu vergleichende Parameter.  *rhs* kann ein Verweis `HStringReference`auf eine sein.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der *lhs-Parameter* kleiner als der *rhs-Parameter* ist; andernfalls **false**.
