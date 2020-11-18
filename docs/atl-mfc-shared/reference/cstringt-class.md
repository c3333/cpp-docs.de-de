---
title: '**`CStringT`** Klassi'
description: API-Referenz für die Microsoft ATL- **`CStringT`** Klasse
ms.date: 11/13/2020
f1_keywords:
- CStringT
- ATLSTR/ATL::CStringT
- ATLSTR/ATL::CStringT::CStringT
- ATLSTR/ATL::CStringT::AllocSysString
- ATLSTR/ATL::CStringT::AnsiToOem
- ATLSTR/ATL::CStringT::AppendFormat
- ATLSTR/ATL::CStringT::Collate
- ATLSTR/ATL::CStringT::CollateNoCase
- ATLSTR/ATL::CStringT::Compare
- ATLSTR/ATL::CStringT::CompareNoCase
- ATLSTR/ATL::CStringT::Delete
- ATLSTR/ATL::CStringT::Find
- ATLSTR/ATL::CStringT::FindOneOf
- ATLSTR/ATL::CStringT::Format
- ATLSTR/ATL::CStringT::FormatMessage
- ATLSTR/ATL::CStringT::FormatMessageV
- ATLSTR/ATL::CStringT::FormatV
- ATLSTR/ATL::CStringT::GetEnvironmentVariable
- ATLSTR/ATL::CStringT::Insert
- ATLSTR/ATL::CStringT::Left
- ATLSTR/ATL::CStringT::LoadString
- ATLSTR/ATL::CStringT::MakeLower
- ATLSTR/ATL::CStringT::MakeReverse
- ATLSTR/ATL::CStringT::MakeUpper
- ATLSTR/ATL::CStringT::Mid
- ATLSTR/ATL::CStringT::OemToAnsi
- ATLSTR/ATL::CStringT::Remove
- ATLSTR/ATL::CStringT::Replace
- ATLSTR/ATL::CStringT::ReverseFind
- ATLSTR/ATL::CStringT::Right
- ATLSTR/ATL::CStringT::SetSysString
- ATLSTR/ATL::CStringT::SpanExcluding
- ATLSTR/ATL::CStringT::SpanIncluding
- ATLSTR/ATL::CStringT::Tokenize
- ATLSTR/ATL::CStringT::Trim
- ATLSTR/ATL::CStringT::TrimLeft
- ATLSTR/ATL::CStringT::TrimRight
- CSTRINGT/CStringT
- CSTRINGT/CStringT::CStringT
- CSTRINGT/CStringT::AllocSysString
- CSTRINGT/CStringT::AnsiToOem
- CSTRINGT/CStringT::AppendFormat
- CSTRINGT/CStringT::Collate
- CSTRINGT/CStringT::CollateNoCase
- CSTRINGT/CStringT::Compare
- CSTRINGT/CStringT::CompareNoCase
- CSTRINGT/CStringT::Delete
- CSTRINGT/CStringT::Find
- CSTRINGT/CStringT::FindOneOf
- CSTRINGT/CStringT::Format
- CSTRINGT/CStringT::FormatMessage
- CSTRINGT/CStringT::FormatMessageV
- CSTRINGT/CStringT::FormatV
- CSTRINGT/CStringT::GetEnvironmentVariable
- CSTRINGT/CStringT::Insert
- CSTRINGT/CStringT::Left
- CSTRINGT/CStringT::LoadString
- CSTRINGT/CStringT::MakeLower
- CSTRINGT/CStringT::MakeReverse
- CSTRINGT/CStringT::MakeUpper
- CSTRINGT/CStringT::Mid
- CSTRINGT/CStringT::OemToAnsi
- CSTRINGT/CStringT::Remove
- CSTRINGT/CStringT::Replace
- CSTRINGT/CStringT::ReverseFind
- CSTRINGT/CStringT::Right
- CSTRINGT/CStringT::SetSysString
- CSTRINGT/CStringT::SpanExcluding
- CSTRINGT/CStringT::SpanIncluding
- CSTRINGT/CStringT::Tokenize
- CSTRINGT/CStringT::Trim
- CSTRINGT/CStringT::TrimLeft
- CSTRINGT/CStringT::TrimRight
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.openlocfilehash: 80ea59b5f50fc9f430aa588a37e73d4526e3fd94
ms.sourcegitcommit: 07408df5f4b2cbf070d9bb4bb40d821bfd5d8a62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703510"
---
# <a name="cstringt-class"></a>CStringT-Klasse

Diese Klasse stellt ein- **`CStringT`** Objekt dar.

## <a name="syntax"></a>Syntax

```cpp
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>Parameter

*`BaseType`*\
Der Zeichentyp der Zeichen folgen Klasse. Dabei kann es sich um eine der folgenden Methoden handeln:

- **`char`** (für ANSI-Zeichen folgen).

- **`wchar_t`** (für Unicode-Zeichen folgen).

- **`TCHAR`** (für ANSI-und Unicode-Zeichen folgen).

*`StringTraits`*\
Bestimmt, ob die Zeichen folgen Klasse Unterstützung für C Run-Time (CRT)-Bibliothek und Speicherort von Zeichen folgen Ressourcen benötigt. Dabei kann es sich um eine der folgenden Methoden handeln:

- **`StrTraitATL<wchar_t | char | TCHAR, ChTraitsCRT<wchar_t | char | TCHAR>>`**

   Die-Klasse erfordert CRT-Unterstützung und sucht nach Ressourcen Zeichenfolgen in dem Modul, das von angegeben wird `m_hInstResource` (ein Member der Modul Klasse der Anwendung).

- **`StrTraitATL<wchar_t | char | TCHAR, ChTraitsOS<wchar_t | char |TCHAR>>`**

   Die-Klasse erfordert keine CRT-Unterstützung und sucht nach Ressourcen Zeichenfolgen in dem Modul, das von angegeben wird `m_hInstResource` (ein Member der Modul Klasse der Anwendung).

- **`StrTraitMFC<wchar_t | char | TCHAR, ChTraitsCRT<wchar_t | char | TCHAR>>`**

   Die-Klasse erfordert CRT-Unterstützung und sucht mithilfe des standardmäßigen MFC-Suchalgorithmus nach Ressourcen Zeichenfolgen.

- **`StrTraitMFC<wchar_t | char | TCHAR, ChTraitsOS<wchar_t | char | TCHAR>>`**

   Die-Klasse erfordert keine CRT-Unterstützung und sucht mithilfe des standardmäßigen MFC-Suchalgorithmus nach Ressourcen Zeichenfolgen.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[`CStringT::CStringT`](#cstringt)|Erstellt ein- **`CStringT`** Objekt auf verschiedene Weise.|
|[`CStringT::~CStringT`](#_dtorcstringt)|Zerstört ein- **`CStringT`** Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[`CStringT::AllocSysString`](#allocsysstring)|Ordnet einen `BSTR` aus **`CStringT`** Daten zu.|
|[`CStringT::AnsiToOem`](#ansitooem)|Führt eine direkte Konvertierung vom ANSI-Zeichensatz in den OEM-Zeichensatz aus.|
|[`CStringT::AppendFormat`](#appendformat)|Fügt formatierte Daten an ein vorhandenes- **`CStringT`** Objekt an.|
|[`CStringT::Collate`](#collate)|Vergleicht zwei Zeichen folgen (Unterscheidung nach Groß-/Kleinschreibung, verwendet Gebiets Schema spezifische Informationen).|
|[`CStringT::CollateNoCase`](#collatenocase)|Vergleicht zwei Zeichen folgen (ohne Berücksichtigung der Groß-/Kleinschreibung, verwendet Gebiets Schema spezifische Informationen).|
|[`CStringT::Compare`](#compare)|Vergleicht zwei Zeichen folgen (Groß-/Kleinschreibung wird beachtet).|
|[`CStringT::CompareNoCase`](#comparenocase)|Vergleicht zwei Zeichen folgen (Groß-/Kleinschreibung nicht beachtet).|
|[`CStringT::Delete`](#delete)|Löscht ein Zeichen oder Zeichen aus einer Zeichenfolge.|
|[`CStringT::Find`](#find)|Sucht ein Zeichen oder eine Teil Zeichenfolge in einer größeren Zeichenfolge.|
|[`CStringT::FindOneOf`](#findoneof)|Sucht das erste übereinstimmende Zeichen aus einer Menge.|
|[`CStringT::Format`](#format)|Formatiert die Zeichenfolge wie `sprintf` .|
|[`CStringT::FormatMessage`](#formatmessage)|Formatiert eine Nachrichten Zeichenfolge.|
|[`CStringT::FormatMessageV`](#formatmessagev)|Formatiert eine Meldungs Zeichenfolge mithilfe einer Variablen Argumentliste.|
|[`CStringT::FormatV`](#formatv)|Formatiert die Zeichenfolge mithilfe einer Variablen Liste von Argumenten.|
|[`CStringT::GetEnvironmentVariable`](#getenvironmentvariable)|Legt die Zeichenfolge auf den Wert der angegebenen Umgebungsvariablen fest.|
|[`CStringT::Insert`](#insert)|Fügt ein einzelnes Zeichen oder eine Teil Zeichenfolge am angegebenen Index innerhalb der Zeichenfolge ein.|
|[`CStringT::Left`](#left)|Extrahiert den linken Teil einer Zeichenfolge.|
|[`CStringT::LoadString`](#loadstring)|Lädt ein vorhandenes- **`CStringT`** Objekt aus einer Windows-Ressource.|
|[`CStringT::MakeLower`](#makelower)|Konvertiert alle Zeichen in dieser Zeichenfolge in Kleinbuchstaben.|
|[`CStringT::MakeReverse`](#makereverse)|Kehrt die Zeichenfolge um.|
|[`CStringT::MakeUpper`](#makeupper)|Konvertiert alle Zeichen in dieser Zeichenfolge in Großbuchstaben.|
|[`CStringT::Mid`](#mid)|Extrahiert den mittleren Teil einer Zeichenfolge.|
|[`CStringT::OemToAnsi`](#oemtoansi)|Führt eine direkte Konvertierung vom OEM-Zeichensatz in den ANSI-Zeichensatz aus.|
|[`CStringT::Remove`](#remove)|Entfernt die gekennzeichneten Zeichen aus einer Zeichenfolge.|
|[`CStringT::Replace`](#replace)|Ersetzt die gekennzeichneten Zeichen durch andere Zeichen.|
|[`CStringT::ReverseFind`](#reversefind)|Findet ein Zeichen innerhalb einer größeren Zeichenfolge; beginnt am Ende.|
|[`CStringT::Right`](#right)|Extrahiert den rechten Teil einer Zeichenfolge.|
|[`CStringT::SetSysString`](#setsysstring)|Legt ein vorhandenes- `BSTR` Objekt mit Daten aus einem- **`CStringT`** Objekt fest.|
|[`CStringT::SpanExcluding`](#spanexcluding)|Extrahiert Zeichen aus der Zeichenfolge, beginnend mit dem ersten Zeichen, das nicht in der von identifizierten Zeichen Gruppe enthalten ist `pszCharSet` .|
|[`CStringT::SpanIncluding`](#spanincluding)|Extrahiert eine Teil Zeichenfolge, die nur die Zeichen in einer Menge enthält.|
|[`CStringT::Tokenize`](#tokenize)|Extrahiert angegebene Token in einer Ziel Zeichenfolge.|
|[`CStringT::Trim`](#trim)|Entfernt alle führenden und nachfolgenden Leerzeichen aus der Zeichenfolge.|
|[`CStringT::TrimLeft`](#trimleft)|Entfernt führende Leerzeichen aus der Zeichenfolge.|
|[`CStringT::TrimRight`](#trimright)|Entfernt nachfolgende Leerzeichen aus der Zeichenfolge.|

### <a name="operators"></a>Operatoren

|Name|BESCHREIBUNG|
|-|-|
|[`CStringT::operator =`](#operator_eq)|Weist einem-Objekt einen neuen Wert zu **`CStringT`** .|
|[`CStringT::operator +`](#operator_add)|Verkettet zwei Zeichen folgen, ein Zeichen und eine Zeichenfolge.|
|[`CStringT::operator +=`](#operator_add_eq)|Verkettet eine neue Zeichenfolge am Ende einer vorhandenen Zeichenfolge.|
|[`CStringT::operator ==`](#operator_eq_eq)|Bestimmt, ob zwei Zeichen folgen logisch gleich sind.|
|[`CStringT::operator !=`](#operator_neq)|Bestimmt, ob zwei Zeichen folgen nicht logisch gleich sind.|
|[`CStringT::operator <`](#operator_lt)|Bestimmt, ob die Zeichenfolge links vom Operator kleiner als die Zeichenfolge auf der rechten Seite ist.|
|[`CStringT::operator >`](#operator_gt)|Bestimmt, ob die Zeichenfolge links vom Operator größer als die Zeichenfolge auf der rechten Seite ist.|
|[`CStringT::operator <=`](#operator_lt_eq)|Bestimmt, ob die Zeichenfolge links vom Operator kleiner als oder gleich der Zeichenfolge auf der rechten Seite ist.|
|[`CStringT::operator >=`](#operator_gt_eq)|Bestimmt, ob die Zeichenfolge links vom Operator größer oder gleich der Zeichenfolge auf der rechten Seite ist.|

## <a name="remarks"></a>Hinweise

**`CStringT`** erbt von der [CSimpleStringT-Klasse](../../atl-mfc-shared/reference/csimplestringt-class.md). Erweiterte Funktionen, wie z. b. Zeichen Bearbeitung, Reihenfolge und Suche, werden von implementiert **`CStringT`** .

> [!NOTE]
> **`CStringT`** -Objekte können Ausnahmen auslösen. Dies tritt auf, wenn ein- **`CStringT`** Objekt aus irgendeinem Grund nicht über genügend Arbeitsspeicher verfügt.

Ein- **`CStringT`** Objekt besteht aus einer Sequenz von Zeichen variabler Länge. **`CStringT`** stellt Funktionen und Operatoren mit Syntax ähnlich der von Basic bereit. Verkettungs-und Vergleichs Operatoren machen zusammen mit der vereinfachten Speicherverwaltung die **`CStringT`** Verwendung von Objekten einfacher als normale Zeichen Arrays.

> [!NOTE]
> Obwohl es möglich ist, Instanzen zu erstellen, **`CStringT`** die eingebettete NULL-Zeichen enthalten, empfiehlt es sich, diese zu erstellen. Das Aufrufen von Methoden und Operatoren für **`CStringT`** Objekte, die eingebettete NULL-Zeichen enthalten, kann unbeabsichtigte Ergebnisse verursachen.

Durch die Verwendung verschiedener Kombinationen aus den `BaseType` `StringTraits` Parametern und **`CStringT`** können Objekte in den folgenden Typen enthalten sein, die von den ATL-Bibliotheken vordefiniert wurden.

Wenn Sie in einer ATL-Anwendung verwenden:

`CString`, `CStringA` und `CStringW` werden aus der MFC-DLL (MFC90.DLL) exportiert, niemals aus den Benutzer-DLLs. Dies geschieht, um zu verhindern, **`CStringT`** dass mehrmals definiert wird.

> [!NOTE]
> Wenn Ihr Code die Problem Umgehung für Linker-Fehler enthält, die unter [Exportieren von Zeichen folgen Klassen mithilfe von CStringT](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md)beschrieben ist, sollten Sie diesen Code entfernen. Es wird nicht mehr benötigt.

Die folgenden Zeichen folgen Typen sind in MFC-basierten Anwendungen verfügbar:

|CStringT-Typ|Deklaration|
|-------------------|-----------------|
|`CStringA`|Eine Zeichenfolge des ANSI-Zeichen Typs mit CRT-Unterstützung.|
|`CStringW`|Eine Zeichenfolge des Unicode-Zeichen Typs mit CRT-Unterstützung.|
|`CString`|ANSI-und Unicode-Zeichen Typen mit CRT-Unterstützung.|

Die folgenden Zeichen folgen Typen sind in Projekten verfügbar, in denen `ATL_CSTRING_NO_CRT` definiert ist:

|CStringT-Typ|Deklaration|
|-------------------|-----------------|
|`CAtlStringA`|Eine Zeichenfolge des ANSI-Zeichen Typs ohne CRT-Unterstützung.|
|`CAtlStringW`|Eine Zeichenfolge des Unicode-Zeichen Typs ohne CRT-Unterstützung.|
|`CAtlString`|ANSI-und Unicode-Zeichen Typen ohne CRT-Unterstützung.|

Die folgenden Zeichen folgen Typen sind in Projekten verfügbar, in denen `ATL_CSTRING_NO_CRT` nicht definiert ist:

|CStringT-Typ|Deklaration|
|-------------------|-----------------|
|`CAtlStringA`|Eine Zeichenfolge des ANSI-Zeichen Typs mit CRT-Unterstützung.|
|`CAtlStringW`|Eine Zeichenfolge des Unicode-Zeichen Typs mit CRT-Unterstützung.|
|`CAtlString`|ANSI-und Unicode-Zeichen Typen mit CRT-Unterstützung.|

`CString` Objekte haben außerdem die folgenden Eigenschaften:

- **`CStringT`** Objekte können aufgrund von Verkettungs Vorgängen vergrößert werden.

- **`CStringT`** Objekte folgen "Wert Semantik". Stellen **`CStringT`** Sie sich ein-Objekt als tatsächliche Zeichenfolge vor, nicht als Zeiger auf eine Zeichenfolge.

- Sie können **`CStringT`** Objekte für `PCXSTR` Funktionsargumente frei ersetzen.

- Benutzerdefinierte Speicherverwaltung für Zeichen folgen Puffer. Weitere Informationen finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringt-predefined-types"></a>CStringT vordefinierte Typen

Da **`CStringT`** ein Vorlagen Argument verwendet, um den Zeichentyp (entweder [wchar_t](../../c-runtime-library/standard-types.md) oder [char](../../c-runtime-library/standard-types.md)) zu definieren, können Methoden Parametertypen manchmal kompliziert sein. Um dieses Problem zu vereinfachen, wird ein Satz vordefinierter Typen definiert und in der gesamten **`CStringT`** Klasse verwendet. In der folgenden Tabelle sind die verschiedenen Typen aufgelistet:

|Name|BESCHREIBUNG|
|----------|-----------------|
|`XCHAR`|Ein einzelnes Zeichen (entweder **`wchar_t`** oder **`char`** ) mit dem gleichen Zeichentyp wie das- **`CStringT`** Objekt.|
|`YCHAR`|Ein einzelnes Zeichen (entweder **`wchar_t`** oder **`char`** ) mit dem umgekehrten Zeichentyp als **`CStringT`** Objekt.|
|`PXSTR`|Ein Zeiger auf eine Zeichenfolge (entweder **`wchar_t`** oder **`char`** ) mit dem gleichen Zeichentyp wie das * * * * * * * *- `CStringT` Objekt.|
|`PYSTR`|Ein Zeiger auf eine Zeichenfolge (entweder **`wchar_t`** oder **`char`** ) mit dem umgekehrten Zeichentyp als- **`CStringT`** Objekt.|
|`PCXSTR`|Ein Zeiger auf eine **`const`** Zeichenfolge (entweder **`wchar_t`** oder **`char`** ) mit dem gleichen Zeichentyp wie das- **`CStringT`** Objekt.|
|`PCYSTR`|Ein Zeiger auf eine **`const`** Zeichenfolge (entweder **`wchar_t`** oder **`char`** ) mit dem umgekehrten Zeichentyp als- **`CStringT`** Objekt.|

> [!NOTE]
> Code, der zuvor nicht dokumentierte Methoden von (z. b.) verwendet hat, `CString` `AssignCopy` muss durch Code ersetzt werden, der die folgenden dokumentierten Methoden von verwendet **`CStringT`** (z `GetBuffer` . b `ReleaseBuffer` . oder). Diese Methoden werden von geerbt `CSimpleStringT` .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

**`CStringT`**

## <a name="requirements"></a>Requirements (Anforderungen)

|Header|Zweck|
|------------|-------------|
|CStringT. h|Nur-MFC-Zeichen folgen Objekte|
|atlstr. h|Nicht-MFC-Zeichen folgen Objekte|

## <a name="cstringtallocsysstring"></a><a name="allocsysstring"></a> `CStringT::AllocSysString`

Ordnet eine Automation-kompatible Zeichenfolge des Typs `BSTR` zu und kopiert den Inhalt des- **`CStringT`** Objekts hinein, einschließlich des abschließenden NULL-Zeichens.

```cpp
BSTR AllocSysString() const;
```

### <a name="return-value"></a>Rückgabewert

Die neu zugeordnete Zeichenfolge.

### <a name="remarks"></a>Hinweise

In MFC-Programmen wird eine [cmemoryexception-Klasse](../../mfc/reference/cmemoryexception-class.md) ausgelöst, wenn nicht genügend Arbeitsspeicher vorhanden ist. In ATL-Programmen wird eine ""- [Ausnahme](../../atl/reference/catlexception-class.md) ausgelöst. Diese Funktion wird normalerweise verwendet, um Zeichen folgen für die Automatisierung zurückzugeben.

Wenn diese Zeichenfolge als Parameter an eine com-Funktion übergeben wird, muss der Aufrufer `[in]` diese Zeichenfolge in der Regel freigeben. Dies kann mithilfe von [sysfrestring](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)erfolgen, wie im Windows SDK beschrieben. Weitere Informationen finden Sie unter [zuordnen und Freigeben von Arbeitsspeicher für ein BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).

Weitere Informationen zu OLE-Zuordnungs Funktionen in Windows finden Sie unter [SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) in der Windows SDK.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CStringT::AllocSysString`.

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

## <a name="cstringtansitooem"></a><a name="ansitooem"></a> `CStringT::AnsiToOem`

Konvertiert alle Zeichen in diesem- **`CStringT`** Objekt aus dem ANSI-Zeichensatz in den OEM-Zeichensatz.

```cpp
void AnsiToOem();
```

### <a name="remarks"></a>Hinweise

Die-Funktion ist nicht verfügbar, wenn `_UNICODE` definiert ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

## <a name="cstringtappendformat"></a><a name="appendformat"></a> `CStringT::AppendFormat`

Fügt formatierte Daten an ein vorhandenes- **`CStringT`** Objekt an.

```cpp
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>Parameter

*`pszFormat`*\
Eine Format Steuerelement Zeichenfolge.

*`nFormatID`*\
Der Zeichen folgen Ressourcen Bezeichner, der die Format Steuerelement-Zeichenfolge enthält.

*`argument`*\
Optionale Argumente.

### <a name="remarks"></a>Hinweise

Diese Funktion formatiert und fügt eine Reihe von Zeichen und Werten in der ein **`CStringT`** . Jedes optionale Argument (sofern vorhanden) wird entsprechend der entsprechenden Format Spezifikation in *`pszFormat`* oder aus der durch identifizierten Zeichen folgen Ressource konvertiert und angefügt *`nFormatID`* .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

## <a name="cstringtcollate"></a><a name="collate"></a> `CStringT::Collate`

Vergleicht zwei Zeichen folgen mithilfe der Funktion "Generic-Text" `_tcscoll` .

```cpp
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parameter

*`psz`*\
Die andere Zeichenfolge, die für den Vergleich verwendet wird.

### <a name="return-value"></a>Rückgabewert

0 (null), wenn die Zeichen folgen identisch sind, < 0, wenn dieses- **`CStringT`** Objekt kleiner als ist *`psz`* , oder > 0, wenn dieses- **`CStringT`** Objekt größer als ist *`psz`* .

### <a name="remarks"></a>Hinweise

Die `_tcscoll` in Tchar definierte generische Textfunktion. H, wird entweder `strcoll` , `wcscoll` oder zugeordnet `_mbscoll` , abhängig vom Zeichensatz, der zur Kompilierzeit definiert ist. Jede Funktion führt einen Vergleich der Zeichen folgen nach Groß-und Kleinschreibung entsprechend der derzeit verwendeten Codepage durch. Weitere Informationen finden Sie unter "_mbscoll", "", "_strcoll_l", " [_wcscoll_l _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)".

## <a name="cstringtcollatenocase"></a><a name="collatenocase"></a> `CStringT::CollateNoCase`

Vergleicht zwei Zeichen folgen mithilfe der Funktion "Generic-Text" `_tcscoll` .

```cpp
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parameter

*`psz`*\
Die andere Zeichenfolge, die für den Vergleich verwendet wird.

### <a name="return-value"></a>Rückgabewert

0 (null), wenn die Zeichen folgen identisch sind (die Groß-/Kleinschreibung wird ignoriert), < 0, wenn dieses **`CStringT`** Objekt kleiner als ist *`psz`* (die Groß-/Kleinschreibung wird ignoriert) oder > 0, wenn dieses **`CStringT`** Objekt größer als *`psz`*

### <a name="remarks"></a>Hinweise

Die `_tcscoll` in Tchar definierte generische Textfunktion. H, wird entweder `stricoll` , `wcsicoll` oder zugeordnet `_mbsicoll` , abhängig vom Zeichensatz, der zur Kompilierzeit definiert ist. Jede Funktion führt einen Vergleich der Zeichen folgen ohne Beachtung der Groß-/Kleinschreibung aus, entsprechend der derzeit verwendeten Codepage. Weitere Informationen finden Sie unter "_mbscoll", "", "_strcoll_l", " [_wcscoll_l _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)".

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

## <a name="cstringtcompare"></a><a name="compare"></a> `CStringT::Compare`

Vergleicht zwei Zeichen folgen (Groß-/Kleinschreibung wird beachtet).

```cpp
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>Parameter

*`psz`*\
Die andere Zeichenfolge, die für den Vergleich verwendet wird.

### <a name="return-value"></a>Rückgabewert

0 (null), wenn die Zeichen folgen identisch sind, < 0, wenn dieses- **`CStringT`** Objekt kleiner als ist *`psz`* , oder > 0, wenn dieses- **`CStringT`** Objekt größer als ist *`psz`* .

### <a name="remarks"></a>Hinweise

Die `_tcscmp` in Tchar definierte generische Textfunktion. H, wird entweder `strcmp` , `wcscmp` oder zugeordnet `_mbscmp` , abhängig vom Zeichensatz, der zur Kompilierzeit definiert ist. Jede Funktion führt einen Vergleich der Zeichen folgen unter Beachtung der Groß-und Kleinschreibung durch und ist nicht vom Gebiets Schema betroffen Weitere Informationen finden Sie unter " [straucmp, wcscmp", "_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)".

Wenn die Zeichenfolge eingebettete Nullen enthält, wird die Zeichenfolge für den Vergleich beim ersten eingebetteten NULL-Zeichen als abgeschnitten betrachtet.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CStringT::Compare`.

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

## <a name="cstringtcomparenocase"></a><a name="comparenocase"></a> `CStringT::CompareNoCase`

Vergleicht zwei Zeichen folgen (Groß-/Kleinschreibung nicht beachtet).

```cpp
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parameter

*`psz`*\
Die andere Zeichenfolge, die für den Vergleich verwendet wird.

### <a name="return-value"></a>Rückgabewert

0 (null), wenn die Zeichen folgen identisch sind (die Groß-/Kleinschreibung wird ignoriert), <0, wenn dieses **`CStringT`** Objekt kleiner als ist *`psz`* (die Groß-/Kleinschreibung wird ignoriert) oder >0, wenn dieses **`CStringT`** Objekt größer als *`psz`*

### <a name="remarks"></a>Hinweise

Die `_tcsicmp` in Tchar definierte generische Textfunktion. H, wird entweder oder zugeordnet, `_stricmp` `_wcsicmp` `_mbsicmp` abhängig vom Zeichensatz, der zum Zeitpunkt der Kompilierung definiert wird. Jede Funktion führt einen Vergleich der Zeichen folgen ohne Beachtung der Groß-und Kleinschreibung durch. Der Vergleich hängt vom LC_CTYPE Aspekt des Gebiets Schemas ab, aber nicht von LC_COLLATE. Weitere Informationen finden Sie unter [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

## <a name="cstringtcstringt"></a><a name="cstringt"></a> `CStringT::CStringT`

Erstellt ein- **`CStringT`** Objekt.

```cpp
CStringT() throw() :
    CThisSimpleString(StringTraits::GetDefaultManager());

explicit CStringT(IAtlStringMgr* pStringMgr) throw() :
    CThisSimpleString( pStringMgr);

CStringT(const VARIANT& varSrc);

CStringT(const VARIANT& varSrc, IAtlStringMgr* pStringMgr);

CStringT(const CStringT& strSrc) :
    CThisSimpleString( strSrc);

operator CSimpleStringT<
                    BaseType,
                    !_CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>
                    :: c_bIsMFCDLLTraits> &()

template <bool bMFCDLL>
CStringT(const CSimpleStringT<BaseType, bMFCDLL>& strSrc) :
    CThisSimpleString( strSrc);

template <class SystemString>
CStringT(SystemString^ pString) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(const YCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(LPCSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CStringT(LPCWSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(const unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

/*CSTRING_EXPLICIT*/ CStringT(char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const unsigned char* pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(char ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength) :
    CThisSimpleString( pch, nLength, StringTraits::GetDefaultManager());

CStringT(const YCHAR* pch, int nLength) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength, AtlStringMgr* pStringMgr) :
    CThisSimpleString( pch, nLength, pStringMgr);

CStringT(const YCHAR* pch, int nLength, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);
```

### <a name="parameters"></a>Parameter

*`pch`*\
Ein Zeiger auf ein Array von Zeichen der Länge *nlength*, nicht NULL-terminiert.

*`nLength`*\
Gibt die Anzahl der Zeichen in *PCH* an.

*`ch`*\
Ein einzelnes Zeichen.

*`pszSrc`*\
Eine mit NULL endende Zeichenfolge, die in dieses-Objekt kopiert werden soll **`CStringT`** .

*`pStringMgr`*\
Ein Zeiger auf den Speicher-Manager für das- **`CStringT`** Objekt. Weitere Informationen zur `IAtlStringMgr` -und-Speicherverwaltung für finden Sie unter **`CStringT`** [Speicherverwaltung mit CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

*`strSrc`*\
Ein vorhandenes- **`CStringT`** Objekt, das in dieses-Objekt kopiert werden soll **`CStringT`** . Weitere Informationen zu `CThisString` und `CThisSimpleString` finden Sie im Abschnitt "Hinweise".

*`varSrc`*\
Ein Variant-Objekt, das in dieses-Objekt kopiert werden soll **`CStringT`** .

*`BaseType`*\
Der Zeichentyp der Zeichen folgen Klasse. Dabei kann es sich um eine der folgenden Methoden handeln:

**`char`** (für ANSI-Zeichen folgen).

**`wchar_t`** (für Unicode-Zeichen folgen).

`TCHAR` (für ANSI-und Unicode-Zeichen folgen).

*`bMFCDLL`*\
Boolescher Wert, der angibt, ob das Projekt eine MFC-DLL ( `TRUE` ) oder nicht ( `FALSE` ) ist.

*`SystemString`*\
Muss sein `System::String` , und das Projekt muss mit kompiliert werden `/clr` .

*`pString`*\
Ein Handle für ein- **`CStringT`** Objekt.

### <a name="remarks"></a>Hinweise

Da die Konstruktoren die Eingabedaten in neuen zugeordneten Speicher kopieren, können Arbeitsspeicher Ausnahmen entstehen. Einige dieser Konstruktoren fungieren als Konvertierungs Funktionen. So können Sie beispielsweise einen ersetzen, **`LPTSTR`** in dem ein- **`CStringT`** Objekt erwartet wird.

- **`CStringT`**( `LPCSTR` `lpsz` ): Erstellt einen Unicode **`CStringT`** aus einer ANSI-Zeichenfolge. Sie können diesen Konstruktor auch verwenden, um eine Zeichen folgen Ressource zu laden, wie im folgenden Beispiel gezeigt.

- `CStringT(``LPCWSTR` `lpsz` ): Erstellt einen **`CStringT`** aus einer Unicode-Zeichenfolge.

- **`CStringT`**( `const unsigned char*` `psz` ): Ermöglicht das Erstellen eines **`CStringT`** von einem Zeiger auf **`unsigned char`** .

> [!NOTE]
> Definieren ` _CSTRING_DISABLE_NARROW_WIDE_CONVERSION` Sie das Makro, um die implizite Zeichen folgen Konvertierung zwischen ANSI-und Unicode-Zeichen folgen zu deaktivieren. Das-Makro schließt Kompilierungs Konstruktoren aus, die Konvertierungen unterstützen.

Der- *`strSrc`* Parameter kann entweder ein- **`CStringT`** oder-Objekt sein `CThisSimpleString` . Verwenden Sie für eine **`CStringT`** der Standard Instanziierungen ( `CString` , `CStringA` oder `CStringW` ), und verwenden Sie für `CThisSimpleString` einen- **`this`** Zeiger. `CThisSimpleString` deklariert eine Instanz der [CSimpleStringT-Klasse](../../atl-mfc-shared/reference/csimplestringt-class.md), die eine kleinere Zeichen folgen Klasse mit weniger integrierter Funktionalität als die- **`CStringT`** Klasse ist.

Der Überladungs Operator erstellt `CSimpleStringT<>&()` ein- **`CStringT`** Objekt aus einer- `CSimpleStringT` Deklaration.

> [!NOTE]
> Obwohl es möglich ist, Instanzen zu erstellen, **`CStringT`** die eingebettete NULL-Zeichen enthalten, empfiehlt es sich, diese zu erstellen. Das Aufrufen von Methoden und Operatoren für **`CStringT`** Objekte, die eingebettete NULL-Zeichen enthalten, kann unbeabsichtigte Ergebnisse verursachen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

## <a name="cstringtcstringt"></a><a name="_dtorcstringt"></a> `CStringT::~CStringT`

Zerstört das- **`CStringT`** Objekt.

```cpp
~CStringT() throw();
```

### <a name="remarks"></a>Hinweise

Zerstört das- **`CStringT`** Objekt.

## <a name="cstringtdelete"></a><a name="delete"></a> `CStringT::Delete`

Löscht ein Zeichen oder Zeichen aus einer Zeichenfolge, beginnend mit dem Zeichen am angegebenen Index.

```cpp
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>Parameter

*`iIndex`*\
Der null basierte Index des ersten Zeichens im **`CStringT`** zu löschenden-Objekt.

*`nCount`*\
Die Anzahl der zu entfernenden Zeichen.

### <a name="return-value"></a>Rückgabewert

Die Länge der geänderten Zeichenfolge.

### <a name="remarks"></a>Hinweise

Wenn *`nCount`* länger als die Zeichenfolge ist, wird der Rest der Zeichenfolge entfernt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

## <a name="cstringtfind"></a><a name="find"></a> `CStringT::Find`

Durchsucht diese Zeichenfolge nach der ersten Entsprechung eines Zeichens oder einer Teil Zeichenfolge.

```cpp
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>Parameter

*`pszSub`*\
Eine zu suchende Teil Zeichenfolge.

*`iStart`*\
Der Index des Zeichens in der Zeichenfolge, mit dem mit der Suche begonnen werden soll, oder 0, um von Anfang an zu beginnen.

*`ch`*\
Ein einzelnes Zeichen, nach dem gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Der null basierte Index des ersten Zeichens in diesem- **`CStringT`** Objekt, das mit der angeforderten Teil Zeichenfolge übereinstimmt, oder-1, wenn die Teil Zeichenfolge oder das Zeichen nicht gefunden wurde.

### <a name="remarks"></a>Hinweise

Die-Funktion ist überladen, sodass beide einzelnen Zeichen (ähnlich der Lauf Zeitfunktion `strchr` ) und Zeichen folgen (ähnlich wie) akzeptiert werden `strstr` .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

## <a name="cstringtfindoneof"></a><a name="findoneof"></a> `CStringT::FindOneOf`

Durchsucht diese Zeichenfolge nach dem ersten Zeichen, das mit jedem in enthaltenen Zeichen übereinstimmt *`pszCharSet`* .

```cpp
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>Parameter

*`pszCharSet`*\
Zeichenfolge mit Zeichen für den Abgleich.

### <a name="return-value"></a>Rückgabewert

Der null basierte Index des ersten Zeichens in dieser Zeichenfolge, das auch in ist *`pszCharSet`* ,-1, wenn keine Entsprechung vorhanden ist.

### <a name="remarks"></a>Hinweise

Sucht das erste Vorkommen eines der Zeichen in *`pszCharSet`* .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

## <a name="cstringtformat"></a><a name="format"></a> `CStringT::Format`

Schreibt formatierte Daten auf **`CStringT`** dieselbe Weise wie [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) Formatieren von Daten in ein Zeichen Array im C-Format.

```cpp
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>Parameter

*`nFormatID`*\
Der Zeichen folgen Ressourcen Bezeichner, der die Format Steuerelement-Zeichenfolge enthält.

*`pszFormat`*\
Eine Format Steuerelement Zeichenfolge.

*`argument`*\
Optionale Argumente.

### <a name="remarks"></a>Hinweise

Diese Funktion formatiert und speichert eine Reihe von Zeichen und Werten im **`CStringT`** . Jedes optionale Argument (sofern vorhanden) wird entsprechend der entsprechenden Format Spezifikation in *`pszFormat`* oder aus der durch identifizierten Zeichen folgen Ressource konvertiert und ausgegeben *`nFormatID`* .

Der-Befehl schlägt fehl, wenn das Zeichen folgen Objekt selbst als Parameter für angeboten wird `Format` . Der folgende Code führt z. b. zu unvorhersehbaren Ergebnissen:

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

Weitere Informationen finden Sie unter [Format Specification Syntax: printf and wprintf Functions (Syntax der Formatangabe: printf- und wprintf-Funktionen)](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

## <a name="cstringtformatmessage"></a><a name="formatmessage"></a> `CStringT::FormatMessage`

Formatiert eine Nachrichten Zeichenfolge.

```cpp
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>Parameter

*`nFormatID`*\
Der Zeichen folgen Ressourcen Bezeichner, der den unformatierten Meldungs Text enthält.

*`pszFormat`*\
Verweist auf die Format Steuerelement Zeichenfolge. Sie wird auf Einfügungen überprüft und entsprechend formatiert. Die Format Zeichenfolge ähnelt der Format Zeichenfolge im *printf*-Format der Lauf Zeitfunktion, mit dem Unterschied, dass die Parameter in beliebiger Reihenfolge eingefügt werden können.

*`argument`*\
Optionale Argumente.

### <a name="remarks"></a>Hinweise

Die-Funktion erfordert eine Nachrichten Definition als Eingabe. Die Nachrichten Definition wird von *`pszFormat`* oder von der durch identifizierten Zeichen folgen Ressource bestimmt *`nFormatID`* . Die-Funktion kopiert den formatierten Meldungs Text in das- **`CStringT`** Objekt und verarbeitet alle eingebetteten INSERT-Sequenzen, wenn dies angefordert wird.

> [!NOTE]
> `FormatMessage` versucht, den Systemspeicher für die neu formatierte Zeichenfolge zuzuweisen. Wenn dieser Versuch fehlschlägt, wird automatisch eine Speicher Ausnahme ausgelöst.

Jede Einfügung muss über einen entsprechenden Parameter nach dem- *`pszFormat`* Parameter oder dem- *`nFormatID`* Parameter verfügen. Im Nachrichtentext werden mehrere Escapesequenzen für die dynamische Formatierung der Nachricht unterstützt. Weitere Informationen finden Sie unter der Windows- [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) -Funktion in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

## <a name="cstringtformatmessagev"></a><a name="formatmessagev"></a> `CStringT::FormatMessageV`

Formatiert eine Meldungs Zeichenfolge mithilfe einer Variablen Argumentliste.

```cpp
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>Parameter

*`pszFormat`*\
Verweist auf die Format Steuerelement Zeichenfolge. Sie wird auf Einfügungen überprüft und entsprechend formatiert. Die Format Zeichenfolge ähnelt Lauf Zeit Funktions `printf` Format-Zeichen folgen, mit dem Unterschied, dass die Parameter in beliebiger Reihenfolge eingefügt werden können.

*`pArgList`*\
Zeiger auf eine Liste von Argumenten.

### <a name="remarks"></a>Hinweise

Die-Funktion erfordert eine Nachrichten Definition als Eingabe, die durch bestimmt wird *`pszFormat`* . Die-Funktion kopiert den formatierten Meldungs Text und eine Variablen Liste von Argumenten in das- **`CStringT`** Objekt und verarbeitet dabei alle eingebetteten INSERT-Sequenzen, wenn dies angefordert wird.

> [!NOTE]
> `FormatMessageV` Ruft [CStringT:: FormatMessage](#formatmessage)auf, das versucht, Systemspeicher für die neu formatierte Zeichenfolge zuzuweisen. Wenn dieser Versuch fehlschlägt, wird automatisch eine Speicher Ausnahme ausgelöst.

Weitere Informationen finden Sie unter der Windows- [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) -Funktion in der Windows SDK.

## <a name="cstringtformatv"></a><a name="formatv"></a> `CStringT::FormatV`

Formatiert eine Meldungs Zeichenfolge mithilfe einer Variablen Argumentliste.

```cpp
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>Parameter

*`pszFormat`*\
Verweist auf die Format Steuerelement Zeichenfolge. Sie wird auf Einfügungen überprüft und entsprechend formatiert. Die Format Zeichenfolge ähnelt Lauf Zeit Funktions `printf` Format-Zeichen folgen, mit dem Unterschied, dass die Parameter in beliebiger Reihenfolge eingefügt werden können.

*`args`*\
Zeiger auf eine Liste von Argumenten.

### <a name="remarks"></a>Hinweise

Schreibt eine formatierte Zeichenfolge und eine Variablen Liste von Argumenten **`CStringT`** in eine Zeichenfolge auf die gleiche Weise wie `vsprintf_s` Daten in ein Zeichen Array im C-Format.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

## <a name="cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a> `CStringT::GetEnvironmentVariable`

Legt die Zeichenfolge auf den Wert der angegebenen Umgebungsvariablen fest.

```cpp
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>Parameter

*`pszVar`*\
Zeiger auf eine mit NULL endenden Zeichenfolge, die die Umgebungsvariable angibt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Ruft den Wert der angegebenen Variablen aus dem Umgebungsblock des aufrufenden Prozesses ab. Der Wert wird in Form einer auf NULL endenden Zeichenfolge angezeigt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

## <a name="cstringtinsert"></a><a name="insert"></a> `CStringT::Insert`

Fügt ein einzelnes Zeichen oder eine Teil Zeichenfolge am angegebenen Index innerhalb der Zeichenfolge ein.

```cpp
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>Parameter

*`iIndex`*\
Der Index des Zeichens, vor dem die Einfügung stattfinden soll.

*`psz`*\
Ein Zeiger auf die einzufügende Teil Zeichenfolge.

*`ch`*\
Das einzufügende Zeichen.

### <a name="return-value"></a>Rückgabewert

Die Länge der geänderten Zeichenfolge.

### <a name="remarks"></a>Hinweise

Der- *`iIndex`* Parameter identifiziert das erste Zeichen, das verschoben wird, um Platz für das Zeichen oder die Teil Zeichenfolge zu schaffen. Wenn *nIndex* 0 (null) ist, wird die Einfügung vor der gesamten Zeichenfolge ausgeführt. Wenn *nIndex* höher als die Länge der Zeichenfolge ist, verkettet die Funktion die vorhandene Zeichenfolge und das neue Material, das entweder von oder bereitgestellt wird *`ch`* *`psz`* .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

## <a name="cstringtleft"></a><a name="left"></a> `CStringT::Left`

Extrahiert die äußersten linken *`nCount`* Zeichen aus diesem **`CStringT`** -Objekt und gibt eine Kopie der extrahierten Teil Zeichenfolge zurück.

```cpp
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>Parameter

*`nCount`*\
Die Anzahl der Zeichen, die aus diesem-Objekt extrahiert werden sollen **`CStringT`** .

### <a name="return-value"></a>Rückgabewert

Ein- **`CStringT`** Objekt, das eine Kopie des angegebenen Zeichen Bereichs enthält. Das zurückgegebene **`CStringT`** Objekt ist möglicherweise leer.

### <a name="remarks"></a>Hinweise

Wenn *`nCount`* die Zeichen folgen Länge überschreitet, wird die gesamte Zeichenfolge extrahiert. `Left` ähnelt der `Left`-Funktion von ///Visual Basic.

Behandelt bei Multibyte-Zeichensätzen (MBCS) *`nCount`* jede 8-Bit-Sequenz als Zeichen, sodass *`nCount`* die Anzahl von Multibytezeichen mit zwei multipliziert wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

## <a name="cstringtloadstring"></a><a name="loadstring"></a> `CStringT::LoadString`

Liest eine durch *NID* identifizierte Windows-Zeichen folgen Ressource in ein vorhandenes- **`CStringT`** Objekt.

```cpp
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>Parameter

*`hInstance`*\
Ein Handle für die Instanz des Moduls.

*`nID`*\
Eine Windows-Zeichen folgen Ressourcen-ID.

*`wLanguageID`*\
Die Sprache der Zeichen folgen Ressource.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn der Ressourcen Ladevorgang erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Hinweise

Lädt die Zeichen folgen Ressource (*NID*) aus dem angegebenen Modul (*HINSTANCE*) unter Verwendung der angegebenen Sprache (*wlanguage*).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

## <a name="cstringtmakelower"></a><a name="makelower"></a> `CStringT::MakeLower`

Konvertiert das- **`CStringT`** Objekt in eine Zeichenfolge in Kleinbuchstaben.

```cpp
CStringT& MakeLower();
```

### <a name="return-value"></a>Rückgabewert

Die resultierende Zeichenfolge in Kleinbuchstaben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

## <a name="cstringtmakereverse"></a><a name="makereverse"></a> `CStringT::MakeReverse`

Kehrt die Reihenfolge der Zeichen im- **`CStringT`** Objekt um.

```cpp
CStringT& MakeReverse();
```

### <a name="return-value"></a>Rückgabewert

Die resultierende umgekehrte Zeichenfolge.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

## <a name="cstringtmakeupper"></a><a name="makeupper"></a> `CStringT::MakeUpper`

Konvertiert das- **`CStringT`** Objekt in eine Zeichenfolge in Großbuchstaben.

```cpp
CStringT& MakeUpper();
```

### <a name="return-value"></a>Rückgabewert

Die resultierende Zeichenfolge in Großbuchstaben.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

## <a name="cstringtmid"></a><a name="mid"></a> `CStringT::Mid`

Extrahiert eine Teil Zeichenfolge von Längen *`nCount`* Zeichen aus diesem- **`CStringT`** Objekt, beginnend an der Position *`iFirst`* (null basiert).

```cpp
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>Parameter

*`iFirst`*\
Der null basierte Index des ersten Zeichens in diesem- **`CStringT`** Objekt, das in die extrahierte Teil Zeichenfolge eingeschlossen werden soll.

*`nCount`*\
Die Anzahl der Zeichen, die aus diesem-Objekt extrahiert werden sollen **`CStringT`** . Wenn dieser Parameter nicht angegeben wird, wird der Rest der Zeichenfolge extrahiert.

### <a name="return-value"></a>Rückgabewert

Ein- **`CStringT`** Objekt, das eine Kopie des angegebenen Zeichen Bereichs enthält. Das zurückgegebene **`CStringT`** Objekt ist möglicherweise leer.

### <a name="remarks"></a>Hinweise

Die-Funktion gibt eine Kopie der extrahierten Teil Zeichenfolge zurück. `Mid` ähnelt der grundlegenden Mid-Funktion (mit dem Unterschied, dass Indizes in Basic ein einbasiertes sind).

Bezieht sich bei Multibytezeichen-Zeichensätzen (MBCS) *`nCount`* auf jedes 8-Bit-Zeichen, d. h., ein Lead-und ein nachfolgendes Byte in einem Multibytezeichen werden als zwei Zeichen gezählt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

## <a name="cstringtoemtoansi"></a><a name="oemtoansi"></a> `CStringT::OemToAnsi`

Konvertiert alle Zeichen in diesem- **`CStringT`** Objekt aus dem OEM-Zeichensatz in den ANSI-Zeichensatz.

```cppcpp
void OemToAnsi();
```

### <a name="remarks"></a>Hinweise

Diese Funktion ist nicht verfügbar, wenn `_UNICODE` definiert ist.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CStringT:: ansian OEM](#ansitooem).

## <a name="cstringtoperator-"></a><a name="operator_eq"></a> `CStringT::operator =`

Weist der Zeichenfolge einen neuen Wert zu.

```cpp
CStringT& operator=(const CStringT& strSrc);

template<bool bMFCDLL>
CStringT& operator=(const CSimpleStringT<BaseType, bMFCDLL>& str);
CStringT& operator=(PCXSTR pszSrc);
CStringT& operator=(PCYSTR pszSrc);
CStringT& operator=(const unsigned char* pszSrc);
CStringT& operator=(XCHAR ch);
CStringT& operator=(YCHAR ch);
CStringT& operator=(const VARIANT& var);
```

### <a name="parameters"></a>Parameter

*`strSrc`*\
Ein **`CStringT`** , der dieser Zeichenfolge zugewiesen werden soll.

*`str`*\
Ein Verweis auf ein `CThisSimpleString`-Objekt.

*`bMFCDLL`*\
Ein boolescher Wert, der angibt, ob es sich bei dem Projekt um eine MFC-DLL handelt.

*`BaseType`*\
Der Zeichen folgen-Basistyp.

*`var`*\
Ein Variant-Objekt, das dieser Zeichenfolge zugewiesen werden soll.

*`ch`*\
Ein ANSI-oder Unicode-Zeichen, das der Zeichenfolge zugewiesen werden soll.

*`pszSrc`*\
Ein Zeiger auf die Original Zeichenfolge, die zugewiesen wird.

### <a name="remarks"></a>Hinweise

Der Zuweisungs Operator akzeptiert ein anderes **`CStringT`** Objekt, einen Zeichen Zeiger oder ein einzelnes Zeichen. Arbeitsspeicher Ausnahmen können immer auftreten, wenn Sie diesen Operator verwenden, da neuer Speicher zugeordnet werden kann.

Weitere Informationen zu `CThisSimpleString` finden Sie im Abschnitt "Hinweise" unter [CStringT:: CStringT](#cstringt).

> [!NOTE]
> Obwohl es möglich ist, Instanzen zu erstellen, **`CStringT`** die eingebettete NULL-Zeichen enthalten, empfiehlt es sich, diese zu erstellen. Das Aufrufen von Methoden und Operatoren für **`CStringT`** Objekte, die eingebettete NULL-Zeichen enthalten, kann unbeabsichtigte Ergebnisse verursachen.

## <a name="cstringtoperator-"></a><a name="operator_add"></a> `CStringT::operator +`

Verkettet zwei Zeichen folgen oder ein Zeichen und eine Zeichenfolge.

```cpp
friend CStringT operator+(const CStringT& str1, const CStringT& str2);
friend CStringT operator+(const CStringT& str1, PCXSTR psz2);
friend CStringT operator+(PCXSTR psz1, const CStringT& str2,);
friend CStringT operator+(char ch1, const CStringT& str2,);
friend CStringT operator+(const CStringT& str1, char ch2);
friend CStringT operator+(const CStringT& str1, wchar_t ch2);
friend CStringT operator+(wchar_t ch1, const CStringT& str2,);
```

### <a name="parameters"></a>Parameter

*`ch1`*\
Ein ANSI-oder Unicode-Zeichen, das mit einer Zeichenfolge verkettet werden soll.

*`ch2`*\
Ein ANSI-oder Unicode-Zeichen, das mit einer Zeichenfolge verkettet werden soll.

*`str1`*\
Ein **`CStringT`** , der mit einer Zeichenfolge oder einem Zeichen verkettet werden soll.

*`str2`*\
Ein **`CStringT`** , der mit einer Zeichenfolge oder einem Zeichen verkettet werden soll.

*`psz1`*\
Ein Zeiger auf eine mit NULL endenden Zeichenfolge, die mit einer Zeichenfolge oder einem Zeichen verkettet werden soll.

*`psz2`*\
Ein Zeiger auf eine Zeichenfolge, die mit einer Zeichenfolge oder einem Zeichen verkettet werden soll.

### <a name="remarks"></a>Hinweise

Es gibt sieben Überladungs Formen der `CStringT::operator+` Funktion. Die erste Version verkettet zwei vorhandene **`CStringT`** Objekte. Die nächsten beiden verketten ein **`CStringT`** -Objekt und eine mit NULL endenden Zeichenfolge. Die nächsten beiden verketten ein **`CStringT`** -Objekt und ein ANSI-Zeichen. Die letzten beiden verketten ein **`CStringT`** -Objekt und ein Unicode-Zeichen.

> [!NOTE]
> Obwohl es möglich ist, Instanzen zu erstellen, **`CStringT`** die eingebettete NULL-Zeichen enthalten, empfiehlt es sich, diese zu erstellen. Das Aufrufen von Methoden und Operatoren für **`CStringT`** Objekte, die eingebettete NULL-Zeichen enthalten, kann unbeabsichtigte Ergebnisse verursachen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_add_eq"></a> `CStringT::operator +=`

Verkettet Zeichen bis zum Ende der Zeichenfolge.

```cpp
CStringT& operator+=(const CThisSimpleString& str);

template<bool bMFCDLL>
CStringT& operator+=(const const CSimpleStringT<BaseType, bMFCDLL>& str);

template<int t_nSize>
CStringT& operator+=(const CStaticString<XCHAR, t_nSize>& strSrc);
CStringT& operator+=(PCXSTR pszSrc);
CStringT& operator+=(PCYSTR pszSrc);
CStringT& operator+=(char ch);
CStringT& operator+=(unsigned char ch);
CStringT& operator+=(wchar_t ch);
CStringT& operator+=(const VARIANT& var);
```

### <a name="parameters"></a>Parameter

*`str`*\
Ein Verweis auf ein `CThisSimpleString`-Objekt.

*`bMFCDLL`*\
Ein boolescher Wert, der angibt, ob es sich bei dem Projekt um eine MFC-DLL handelt.

*`BaseType`*\
Der Zeichen folgen-Basistyp.

*`var`*\
Ein Variant-Objekt, das mit dieser Zeichenfolge verkettet werden soll.

*`ch`*\
Ein ANSI-oder Unicode-Zeichen, das mit einer Zeichenfolge verkettet werden soll.

*`pszSrc`*\
Ein Zeiger auf die ursprüngliche zu verkettende Zeichenfolge.

*`strSrc`*\
Eine **`CStringT`** , die mit dieser Zeichenfolge verkettet werden soll.

### <a name="remarks"></a>Hinweise

Der Operator akzeptiert ein anderes **`CStringT`** Objekt, einen Zeichen Zeiger oder ein einzelnes Zeichen. Arbeitsspeicher Ausnahmen können immer auftreten, wenn Sie diesen Verkettungs Operator verwenden, da neuer Speicher für Zeichen zugeordnet werden kann, die diesem-Objekt hinzugefügt werden **`CStringT`** .

Weitere Informationen zu `CThisSimpleString` finden Sie im Abschnitt "Hinweise" unter [CStringT:: CStringT](#cstringt).

> [!NOTE]
> Obwohl es möglich ist, Instanzen zu erstellen, **`CStringT`** die eingebettete NULL-Zeichen enthalten, empfiehlt es sich, diese zu erstellen. Das Aufrufen von Methoden und Operatoren für **`CStringT`** Objekte, die eingebettete NULL-Zeichen enthalten, kann unbeabsichtigte Ergebnisse verursachen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_eq_eq"></a> `CStringT::operator ==`

Bestimmt, ob zwei Zeichen folgen logisch gleich sind.

```cpp
friend bool operator==(const CStringT& str1, const CStringT& str2) throw();
friend bool operator==(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator==(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator==(const CStringT& str1, XCHAR ch2) throw();
friend bool operator==(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator==(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator==(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>Parameter

*`ch1`*\
Ein ANSI-oder Unicode-Zeichen für den Vergleich.

*`ch2`*\
Ein ANSI-oder Unicode-Zeichen für den Vergleich.

*`str1`*\
Ein **`CStringT`** für den Vergleich.

*`str2`*\
Ein **`CStringT`** für den Vergleich.

*`psz1`*\
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

*`psz2`*\
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

### <a name="remarks"></a>Hinweise

Testet, ob eine Zeichenfolge oder ein Zeichen auf der linken Seite gleich einer Zeichenfolge oder eines Zeichens auf der rechten Seite ist, und gibt `TRUE` oder `FALSE` entsprechend zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_neq"></a> `CStringT::operator !=`

Bestimmt, ob zwei Zeichen folgen logisch nicht gleich sind.

```cpp
friend bool operator!=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator!=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator!=(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator!=(const CStringT& str1, XCHAR ch2) throw();
friend bool operator!=(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator!=(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator!=(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>Parameter

*`ch1`*\
Ein ANSI-oder Unicode-Zeichen, das mit einer Zeichenfolge verkettet werden soll.

*`ch2`*\
Ein ANSI-oder Unicode-Zeichen, das mit einer Zeichenfolge verkettet werden soll.

*`str1`*\
Ein **`CStringT`** für den Vergleich.

*`str2`*\
Ein **`CStringT`** für den Vergleich.

*`psz1`*\
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

*`psz2`*\
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

### <a name="remarks"></a>Hinweise

Testet, ob eine Zeichenfolge oder ein Zeichen auf der linken Seite gleich einer Zeichenfolge oder eines Zeichens auf der rechten Seite ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_lt"></a> `CStringT::operator <`

Bestimmt, ob die Zeichenfolge links vom Operator kleiner als die Zeichenfolge auf der rechten Seite ist.

```cpp
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parameter

*`str1`*\
Ein **`CStringT`** für den Vergleich.

*`str2`*\
Ein **`CStringT`** für den Vergleich.

*`psz1`*\
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

*`psz2`*\
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

### <a name="remarks"></a>Hinweise

Ein lexikografischer Vergleich zwischen Zeichen folgen, Zeichen nach Zeichen bis:

- Er zwei korrespondierende ungleiche Zeichen findet, und deren Vergleich als Ergebnis des Vergleichs zweier Zeichenfolgen genommen wird.

- Er keine Ungleichheiten findet, aber eine Zeichenfolge mehr Zeichen hat als die andere und die kürzere Zeichenfolge als kleiner als die längere Zeichenfolge betrachtet wird.

- Er keine Ungleichheiten findet und feststellt, dass die Zeichenfolgen die gleiche Anzahl von Zeichen haben und daher gleich sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_gt"></a> `CStringT::operator >`

Bestimmt, ob die Zeichenfolge links vom Operator größer als die Zeichenfolge auf der rechten Seite ist.

```cpp
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parameter

*`str1`*\
Ein **`CStringT`** für den Vergleich.

*`str2`*\
Ein **`CStringT`** für den Vergleich.

*`psz1`*\
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

*`psz2`*\
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

### <a name="remarks"></a>Hinweise

Ein lexikografischer Vergleich zwischen Zeichen folgen, Zeichen nach Zeichen bis:

- Er zwei korrespondierende ungleiche Zeichen findet, und deren Vergleich als Ergebnis des Vergleichs zweier Zeichenfolgen genommen wird.

- Er keine Ungleichheiten findet, aber eine Zeichenfolge mehr Zeichen hat als die andere und die kürzere Zeichenfolge als kleiner als die längere Zeichenfolge betrachtet wird.

- Er keine Ungleichheiten findet und feststellt, dass die Zeichenfolgen die gleiche Anzahl von Zeichen haben und daher gleich sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_lt_eq"></a> `CStringT::operator <=`

Bestimmt, ob die Zeichenfolge links vom Operator kleiner als oder gleich der Zeichenfolge auf der rechten Seite ist.

```cpp
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parameter

*`str1`*\
Ein **`CStringT`** für den Vergleich.

*`str2`*\
Ein **`CStringT`** für den Vergleich.

*`psz1`*\
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

*`psz2`*\
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

### <a name="remarks"></a>Hinweise

Ein lexikografischer Vergleich zwischen Zeichen folgen, Zeichen nach Zeichen bis:

- Er zwei korrespondierende ungleiche Zeichen findet, und deren Vergleich als Ergebnis des Vergleichs zweier Zeichenfolgen genommen wird.

- Er keine Ungleichheiten findet, aber eine Zeichenfolge mehr Zeichen hat als die andere und die kürzere Zeichenfolge als kleiner als die längere Zeichenfolge betrachtet wird.

- Er keine Ungleichheiten findet und feststellt, dass die Zeichenfolgen die gleiche Anzahl von Zeichen haben und daher gleich sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_gt_eq"></a> `CStringT::operator >=`

Bestimmt, ob die Zeichenfolge links vom Operator größer oder gleich der Zeichenfolge auf der rechten Seite ist.

```cpp
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parameter

*`str1`*\
Ein **`CStringT`** für den Vergleich.

*`str2`*\
Ein **`CStringT`** für den Vergleich.

*`psz1`*\
Ein Zeiger auf eine Zeichenfolge für den Vergleich.

*`psz2`*\
Ein Zeiger auf eine Zeichenfolge für den Vergleich.

### <a name="remarks"></a>Hinweise

Ein lexikografischer Vergleich zwischen Zeichen folgen, Zeichen nach Zeichen bis:

- Er zwei korrespondierende ungleiche Zeichen findet, und deren Vergleich als Ergebnis des Vergleichs zweier Zeichenfolgen genommen wird.

- Er keine Ungleichheiten findet, aber eine Zeichenfolge mehr Zeichen hat als die andere und die kürzere Zeichenfolge als kleiner als die längere Zeichenfolge betrachtet wird.

- Er keine Ungleichheiten findet und feststellt, dass die Zeichenfolgen die gleiche Anzahl von Zeichen haben und daher gleich sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

## <a name="cstringtremove"></a><a name="remove"></a> `CStringT::Remove`

Entfernt alle Instanzen des angegebenen Zeichens aus der Zeichenfolge.

```cpp
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>Parameter

*`chRemove`*\
Das Zeichen, das aus einer Zeichenfolge entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Zeichen, die aus der Zeichenfolge entfernt wurden. NULL, wenn die Zeichenfolge nicht geändert wird.

### <a name="remarks"></a>Hinweise

Bei Vergleichen für das Zeichen wird die Groß-/Kleinschreibung beachtet.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

## <a name="cstringtreplace"></a><a name="replace"></a> `CStringT::Replace`

Es gibt zwei Versionen von `Replace` . Die erste Version ersetzt eine oder mehrere Kopien einer Teil Zeichenfolge durch eine andere Teil Zeichenfolge. Beide Teil Zeichenfolgen werden mit Null beendet. Die zweite Version ersetzt eine oder mehrere Kopien eines Zeichens durch ein anderes Zeichen. Beide Versionen arbeiten mit den Zeichendaten, die in gespeichert sind **`CStringT`** .

```cpp
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>Parameter

*`pszOld`*\
Ein Zeiger auf eine mit NULL endende Zeichenfolge, die durch ersetzt werden soll *`pszNew`* .

*`pszNew`*\
Ein Zeiger auf eine NULL-terminierte Zeichenfolge, die ersetzt *`pszOld`* .

*`chOld`*\
Das Zeichen, durch das ersetzt werden soll *`chNew`* .

*`chNew`*\
Das Zeichen, das ersetzt *`chOld`* .

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der ersetzten Instanzen des Zeichens oder der Teil Zeichenfolge zurück, oder NULL, wenn die Zeichenfolge nicht geändert wird.

### <a name="remarks"></a>Hinweise

`Replace` kann die Zeichen folgen Länge ändern *`pszNew`* , da und *`pszOld`* nicht die gleiche Länge aufweisen müssen und mehrere Kopien der alten Teil Zeichenfolge in die neue geändert werden können. Bei der-Funktion wird die Groß-/Kleinschreibung beachtet.

Beispiele für **`CStringT`** -Instanzen sind `CString` , `CStringA` und `CStringW` .

Für `CStringA` `Replace` funktioniert mit ANSI-oder Multibytezeichen-Zeichen (MBCS). Für `CStringW` `Replace` funktioniert mit breit Zeichen.

Für `CString` wird der Zeichen Datentyp zur Kompilierzeit ausgewählt, je nachdem, ob die Konstanten in der folgenden Tabelle definiert sind.

|Definierte Konstante|Zeichen Datentyp|
|----------------------|-------------------------|
|`_UNICODE`|Breitzeichen|
|`_MBCS`|Mehr Byte Zeichen|
|Neither|Einzel Byte Zeichen|
|Beide|Nicht definiert|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

## <a name="cstringtreversefind"></a><a name="reversefind"></a> `CStringT::ReverseFind`

Durchsucht dieses- **`CStringT`** Objekt nach der letzten Entsprechung eines Zeichens.

```cpp
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>Parameter

*`ch`*\
Das zu suchende Zeichen.

### <a name="return-value"></a>Rückgabewert

Der null basierte Index des letzten Zeichens in diesem- **`CStringT`** Objekt, das mit dem angeforderten Zeichen übereinstimmt, oder-1, wenn das Zeichen nicht gefunden wurde.

### <a name="remarks"></a>Hinweise

Die-Funktion ähnelt der-Lauf Zeitfunktion `strrchr` .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

## <a name="cstringtright"></a><a name="right"></a> `CStringT::Right`

Extrahiert die letzten Zeichen (d. h. ganz rechts) *`nCount`* aus diesem **`CStringT`** -Objekt und gibt eine Kopie der extrahierten Teil Zeichenfolge zurück.

```cpp
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>Parameter

*`nCount`*\
Die Anzahl der Zeichen, die aus diesem-Objekt extrahiert werden sollen **`CStringT`** .

### <a name="return-value"></a>Rückgabewert

Ein- **`CStringT`** Objekt, das eine Kopie des angegebenen Zeichen Bereichs enthält. Das zurückgegebene **`CStringT`** Objekt kann leer sein.

### <a name="remarks"></a>Hinweise

Wenn *`nCount`* die Zeichen folgen Länge überschreitet, wird die gesamte Zeichenfolge extrahiert. `Right` ähnelt der Basic- `Right` Funktion (mit der Ausnahme, dass Indizes in Basic Null basiert).

Bezieht sich bei Multibytezeichen-Zeichensätzen (MBCS) *`nCount`* auf jedes 8-Bit-Zeichen, d. h., ein Lead-und ein nachfolgendes Byte in einem Multibytezeichen werden als zwei Zeichen gezählt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

## <a name="cstringtsetsysstring"></a><a name="setsysstring"></a> `CStringT::SetSysString`

Ordnet den, **`BSTR`** auf den verwiesen *`pbstr`* wird, neu zu und kopiert den Inhalt des- **`CStringT`** Objekts in diesen, einschließlich des NULL-Zeichens.

```cpp
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>Parameter

*`pbstr`*\
Ein Zeiger auf eine Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Die neue Zeichenfolge.

### <a name="remarks"></a>Hinweise

Abhängig vom Inhalt des- **`CStringT`** Objekts kann sich der Wert von, auf den verweist, **`BSTR`** *`pbstr`* ändern. Die Funktion löst eine aus, `CMemoryException` Wenn nicht genügend Arbeitsspeicher vorhanden ist.

Diese Funktion wird normalerweise verwendet, um den Wert von Zeichen folgen zu ändern, die als Verweis für die Automatisierung verwendet werden

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

## <a name="cstringtspanexcluding"></a><a name="spanexcluding"></a> `CStringT::SpanExcluding`

Extrahiert Zeichen aus der Zeichenfolge, beginnend mit dem ersten Zeichen, das nicht in der von identifizierten Zeichen Gruppe enthalten ist *`pszCharSet`* .

```cpp
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parameter

*`pszCharSet`*\
Eine Zeichenfolge, die als Zeichensatz interpretiert wird.

### <a name="return-value"></a>Rückgabewert

Eine Teil Zeichenfolge, die Zeichen in der Zeichenfolge enthält, die nicht in enthalten *`pszCharSet`* sind, beginnend mit dem ersten Zeichen in der Zeichenfolge und mit dem ersten Zeichen in der Zeichenfolge, die sich ebenfalls in befindet (d. h. *`pszCharSet`* beginnend mit dem ersten Zeichen in der Zeichenfolge und bis bis zu dem ersten Zeichen in der gefundenen Zeichenfolge *`pszCharSet`* ). Die gesamte Zeichenfolge wird zurückgegeben, wenn *`pszCharSet`* in der Zeichenfolge kein Zeichen in gefunden wird.

### <a name="remarks"></a>Hinweise

`SpanExcluding` extrahiert und gibt alle Zeichen zurück, die dem ersten Vorkommen eines Zeichens aus *`pszCharSet`* vorangestellt sind (d. h., das Zeichen aus *`pszCharSet`* und alle Zeichen, die in der Zeichenfolge darauf folgen, werden nicht zurückgegeben). Wenn kein Zeichen aus *`pszCharSet`* in der Zeichenfolge gefunden wird, wird `SpanExcluding` die gesamte Zeichenfolge zurückgegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

## <a name="cstringtspanincluding"></a><a name="spanincluding"></a> `CStringT::SpanIncluding`

Extrahiert Zeichen aus der Zeichenfolge, beginnend mit dem ersten Zeichen, das sich in dem von identifizierten Zeichensatz befinden *`pszCharSet`* .

```cpp
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parameter

*`pszCharSet`*\
Eine Zeichenfolge, die als Zeichensatz interpretiert wird.

### <a name="return-value"></a>Rückgabewert

Eine Teil Zeichenfolge, die Zeichen in der Zeichenfolge enthält, die in enthalten sind *`pszCharSet`* , beginnend mit dem ersten Zeichen in der Zeichenfolge und endende, wenn ein Zeichen in der Zeichenfolge gefunden wird, die nicht in ist *`pszCharSet`* `SpanIncluding` gibt eine leere Teil Zeichenfolge zurück, wenn das erste Zeichen in der Zeichenfolge nicht in der angegebenen Menge ist.

### <a name="remarks"></a>Hinweise

Wenn das erste Zeichen der Zeichenfolge nicht im Zeichensatz ist, wird `SpanIncluding` eine leere Zeichenfolge zurückgegeben. Andernfalls wird eine Sequenz von aufeinander folgenden Zeichen zurückgegeben, die in der Menge enthalten sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

## <a name="cstringttokenize"></a><a name="tokenize"></a> `CStringT::Tokenize`

Sucht das nächste Token in einer Ziel Zeichenfolge.

```cpp
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>Parameter

*`pszTokens`*\
Eine Zeichenfolge, die Tokentrennzeichen enthält. Die Reihenfolge dieser Trennzeichen ist nicht wichtig.

*`iStart`*\
Der null basierte Index, an dem mit der Suche begonnen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein- **`CStringT`** Objekt, das den aktuellen Tokenwert enthält.

### <a name="remarks"></a>Hinweise

Die- `Tokenize` Funktion sucht das nächste Token in der Ziel Zeichenfolge. Der Satz von Zeichen in *psztokens* gibt mögliche Trennzeichen des gefundenen Tokens an. Bei jedem Aufrufe `Tokenize` der-Funktion beginnt bei *`iStart`* , überspringt führende Trennzeichen und gibt ein- **`CStringT`** Objekt zurück, das das aktuelle Token enthält, das die Zeichenfolge bis zum nächsten Trennzeichen ist. Der Wert von *`iStart`* wird aktualisiert, um die Position nach dem endtrennzeichen zu sein, oder-1, wenn das Ende der Zeichenfolge erreicht wurde. Weitere Token können aus dem Rest der Ziel Zeichenfolge durch eine Reihe von Aufrufen von getrennt werden `Tokenize` , wobei verwendet wird, *`iStart`* um nachzuverfolgen, wo in der Zeichenfolge das nächste Token gelesen werden soll. Wenn keine weiteren Token vorhanden sind, gibt die Funktion eine leere Zeichenfolge zurück und *`iStart`* wird auf-1 festgelegt.

Anders als die CRT-versehen-Funktionen wie [`strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l`](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md) , wird `Tokenize` die Ziel Zeichenfolge nicht geändert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>Hinweise

Die Ausgabe dieses Beispiels lautet wie folgt:

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

## <a name="cstringttrim"></a><a name="trim"></a> `CStringT::Trim`

Entfernt führende und nachfolgende Zeichen aus der Zeichenfolge.

```cpp
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>Parameter

*`chTarget`*\
Das zu gekürzte Ziel Zeichen.

*`pszTargets`*\
Ein Zeiger auf eine Zeichenfolge, die die zu gekürzten Ziel Zeichen enthält. Alle führenden und nachfolgenden Vorkommen von Zeichen in werden *`pszTargets`* aus dem- **`CStringT`** Objekt abgeschnitten.

### <a name="return-value"></a>Rückgabewert

Gibt die gekürzte Zeichenfolge zurück.

### <a name="remarks"></a>Hinweise

Entfernt alle führenden und nachfolgenden Vorkommen einer der folgenden:

- Das durch angegebene Zeichen *`chTarget`* .

- Alle Zeichen, die in der durch angegebenen Zeichenfolge gefunden werden *`pszTargets`* .

- Leerzeichen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>Hinweise

Die Ausgabe dieses Beispiels lautet wie folgt:

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

## <a name="cstringttrimleft"></a><a name="trimleft"></a> `CStringT::TrimLeft`

Entfernt führende Zeichen aus der Zeichenfolge.

```cpp
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>Parameter

*`chTarget`*\
Das zu gekürzte Ziel Zeichen.

*`pszTargets`*\
Ein Zeiger auf eine Zeichenfolge, die die zu gekürzten Ziel Zeichen enthält. Alle führenden Vorkommen von Zeichen in werden *`pszTargets`* aus dem- **`CStringT`** Objekt abgeschnitten.

### <a name="return-value"></a>Rückgabewert

Die resultierende gekürzte Zeichenfolge.

### <a name="remarks"></a>Hinweise

Entfernt alle führenden und nachfolgenden Vorkommen einer der folgenden:

- Das durch angegebene Zeichen *`chTarget`* .

- Alle Zeichen, die in der durch angegebenen Zeichenfolge gefunden werden *`pszTargets`* .

- Leerzeichen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

## <a name="cstringttrimright"></a><a name="trimright"></a> `CStringT::TrimRight`

Entfernt nachfolgende Zeichen aus der Zeichenfolge.

```cpp
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>Parameter

*`chTarget`*\
Das zu gekürzte Ziel Zeichen.

*`pszTargets`*\
Ein Zeiger auf eine Zeichenfolge, die die zu gekürzten Ziel Zeichen enthält. Alle nachfolgenden Vorkommen von Zeichen in werden *`pszTargets`* aus dem- **`CStringT`** Objekt abgeschnitten.

### <a name="return-value"></a>Rückgabewert

Gibt das- **`CStringT`** Objekt zurück, das die gekürzte Zeichenfolge enthält.

### <a name="remarks"></a>Hinweise

Entfernt nachfolgende Vorkommen einer der folgenden:

- Das durch angegebene Zeichen *`chTarget`* .

- Alle Zeichen, die in der durch angegebenen Zeichenfolge gefunden werden *`pszTargets`* .

- Leerzeichen.

Die `CStringT& TrimRight(XCHAR chTarget)` Version akzeptiert einen Zeichen Parameter und entfernt alle Kopien dieses Zeichens aus dem Ende der **`CStringT`** Zeichen folgen Daten. Sie beginnt am Ende der Zeichenfolge und funktioniert im Vordergrund. Sie wird beendet, wenn ein anderes Zeichen gefunden wird oder wenn **`CStringT`** keine Zeichendaten mehr zur Anwendung kommt.

Die `CStringT& TrimRight(PCXSTR pszTargets)` Version akzeptiert eine NULL-terminierte Zeichenfolge, die alle unterschiedlichen Zeichen enthält, nach denen gesucht werden soll. Es entfernt alle Kopien dieser Zeichen im- **`CStringT`** Objekt. Sie beginnt am Ende der Zeichenfolge und funktioniert im Vordergrund. Sie wird beendet, wenn ein Zeichen gefunden wird, das sich nicht in der Ziel Zeichenfolge befindet, oder wenn **`CStringT`** nicht mehr Zeichendaten ausführt. Es wird nicht versucht, die gesamte Ziel Zeichenfolge mit einer Teil Zeichenfolge am Ende von abzugleichen **`CStringT`** .

Die `CStringT& TrimRight()` Version erfordert keine Parameter. Alle nachfolgenden Leerzeichen werden vom Ende der **`CStringT`** Zeichenfolge entfernt. Leerzeichen können Zeilenumbrüche, Leerzeichen oder Registerkarten sein.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>Siehe auch

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)\
[Gemeinsam genutzte ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)\
[CSimpleStringT-Klasse](../../atl-mfc-shared/reference/csimplestringt-class.md)
