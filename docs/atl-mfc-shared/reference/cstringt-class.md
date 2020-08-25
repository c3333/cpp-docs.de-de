---
title: CStringT-Klasse
ms.date: 03/27/2019
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
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
ms.openlocfilehash: 3e6d61bdf296e85bee5d41ec2131fa3d83122c2b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832086"
---
# <a name="cstringt-class"></a>CStringT-Klasse

Diese Klasse stellt ein- `CStringT` Objekt dar.

## <a name="syntax"></a>Syntax

```
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>Parameter

*BaseType*<br/>
Der Zeichentyp der Zeichen folgen Klasse. Dabei kann es sich um eine der folgenden Methoden handeln:

- **`char`** (für ANSI-Zeichen folgen).

- **`wchar_t`** (für Unicode-Zeichen folgen).

- Tchar (für ANSI-und Unicode-Zeichen folgen).

*Stringmerkmalen*<br/>
Bestimmt, ob die Zeichen folgen Klasse die Unterstützung der C-Lauf Zeit Bibliothek (CRT) und den Speicherort der Zeichen folgen Ressourcen benötigt. Dabei kann es sich um eine der folgenden Methoden handeln:

- **< wchar_t** &#124; **`char`** &#124; **TCHAR, chtraitscrt<** wchar_t &#124; &#124; **`char`** **TCHAR > >**

   Die-Klasse erfordert CRT-Unterstützung und sucht nach Ressourcen Zeichenfolgen in dem Modul, das von angegeben wird `m_hInstResource` (ein Member der Modul Klasse der Anwendung).

- **< wchar_t** &#124; **`char`** &#124; **TCHAR, chtraitsos<** wchar_t &#124; **`char`** &#124; **TCHAR > >**

   Die-Klasse erfordert keine CRT-Unterstützung und sucht nach Ressourcen Zeichenfolgen in dem Modul, das von angegeben wird `m_hInstResource` (ein Member der Modul Klasse der Anwendung).

- **< wchar_t** &#124; **`char`** &#124; **TCHAR, chtraitscrt<** wchar_t &#124; &#124; **`char`** **TCHAR > >**

   Die-Klasse erfordert CRT-Unterstützung und sucht mithilfe des standardmäßigen MFC-Suchalgorithmus nach Ressourcen Zeichenfolgen.

- **< wchar_t** &#124; **`char`** &#124; **TCHAR, chtraitsos<** wchar_t &#124; **`char`** &#124; **TCHAR > >**

   Die-Klasse erfordert keine CRT-Unterstützung und sucht mithilfe des standardmäßigen MFC-Suchalgorithmus nach Ressourcen Zeichenfolgen.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[CStringT:: CStringT](#cstringt)|Erstellt ein- `CStringT` Objekt auf verschiedene Weise.|
|[CStringT:: ~ CStringT](#_dtorcstringt)|Zerstört ein `CStringT` -Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CStringT:: Zuordnung](#allocsysstring)|Ordnet ein BSTR aus `CStringT` Daten zu.|
|[CStringT:: ansian OEM](#ansitooem)|Führt eine direkte Konvertierung vom ANSI-Zeichensatz in den OEM-Zeichensatz aus.|
|[CStringT:: AppendFormat](#appendformat)|Fügt formatierte Daten an ein vorhandenes- `CStringT` Objekt an.|
|[CStringT:: COLLATE](#collate)|Vergleicht zwei Zeichen folgen (Groß-/Kleinschreibung beachtet, verwendet Gebiets Schema spezifische Informationen).|
|[CStringT:: collatsocase](#collatenocase)|Vergleicht zwei Zeichen folgen (ohne Berücksichtigung der Groß-/Kleinschreibung, verwendet Gebiets Schema spezifische Informationen)|
|[CStringT:: Compare](#compare)|Vergleicht zwei Zeichen folgen (Groß-/Kleinschreibung beachten)|
|[CStringT:: comparoocase](#comparenocase)|Vergleicht zwei Zeichen folgen (Groß-/Kleinschreibung nicht beachtet|
|[CStringT::D Elete](#delete)|Löscht ein Zeichen oder Zeichen aus einer Zeichenfolge.|
|[CStringT:: Find](#find)|Sucht ein Zeichen oder eine Teil Zeichenfolge in einer größeren Zeichenfolge.|
|[CStringT:: findoneof](#findoneof)|Sucht das erste übereinstimmende Zeichen aus einer Menge.|
|[CStringT:: Format](#format)|Formatiert die Zeichenfolge wie `sprintf` .|
|[CStringT:: FormatMessage](#formatmessage)|Formatiert eine Nachrichten Zeichenfolge.|
|[CStringT:: formatmessagev](#formatmessagev)|Formatiert eine Meldungs Zeichenfolge mithilfe einer Variablen Argumentliste.|
|[CStringT:: formatv](#formatv)|Formatiert die Zeichenfolge mithilfe einer Variablen Liste von Argumenten.|
|[CStringT:: GetEnvironmentVariable](#getenvironmentvariable)|Legt die Zeichenfolge auf den Wert der angegebenen Umgebungsvariablen fest.|
|[CStringT:: INSERT](#insert)|Fügt ein einzelnes Zeichen oder eine Teil Zeichenfolge am angegebenen Index innerhalb der Zeichenfolge ein.|
|[CStringT:: Left](#left)|Extrahiert den linken Teil einer Zeichenfolge.|
|[CStringT:: loadstring](#loadstring)|Lädt ein vorhandenes- `CStringT` Objekt aus einer Windows-Ressource.|
|[CStringT:: makelower](#makelower)|Konvertiert alle Zeichen in dieser Zeichenfolge in Kleinbuchstaben.|
|[CStringT:: makereverse](#makereverse)|Kehrt die Zeichenfolge um.|
|[CStringT:: makeUpper](#makeupper)|Konvertiert alle Zeichen in dieser Zeichenfolge in Großbuchstaben.|
|[CStringT:: Mid](#mid)|Extrahiert den mittleren Teil einer Zeichenfolge.|
|[CStringT:: oemto ANSI](#oemtoansi)|Führt eine direkte Konvertierung vom OEM-Zeichensatz in den ANSI-Zeichensatz aus.|
|[CStringT:: Remove](#remove)|Entfernt die gekennzeichneten Zeichen aus einer Zeichenfolge.|
|[CStringT:: Replace](#replace)|Ersetzt die gekennzeichneten Zeichen durch andere Zeichen.|
|[CStringT:: reverstellen suchen](#reversefind)|Findet ein Zeichen innerhalb einer größeren Zeichenfolge; beginnt am Ende.|
|[CStringT:: Right](#right)|Extrahiert den rechten Teil einer Zeichenfolge.|
|[CStringT:: SetSysString](#setsysstring)|Legt ein vorhandenes BSTR-Objekt mit Daten aus einem- `CStringT` Objekt fest.|
|[CStringT:: Span Ausschluss](#spanexcluding)|Extrahiert Zeichen aus der Zeichenfolge, beginnend mit dem ersten Zeichen, die nicht in dem von identifizierten Zeichensatz enthalten sind `pszCharSet` .|
|[CStringT:: Span einschließen](#spanincluding)|Extrahiert eine Teil Zeichenfolge, die nur die Zeichen in einer Menge enthält.|
|[CStringT:: tokenize](#tokenize)|Extrahiert angegebene Token in einer Ziel Zeichenfolge.|
|[CStringT:: Trim](#trim)|Entfernt alle führenden und nachfolgenden Leerzeichen aus der Zeichenfolge.|
|[CStringT:: TrimLeft](#trimleft)|Entfernt führende Leerzeichen aus der Zeichenfolge.|
|[CStringT:: TrimRight](#trimright)|Entfernt nachfolgende Leerzeichen aus der Zeichenfolge.|

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[CStringT:: Operator =](#operator_eq)|Weist einem-Objekt einen neuen Wert zu `CStringT` .|
|[CStringT:: Operator +](#operator_add)|Verkettet zwei Zeichen folgen oder ein Zeichen und eine Zeichenfolge.|
|[CStringT:: Operator + =](#operator_add_eq)|Verkettet eine neue Zeichenfolge am Ende einer vorhandenen Zeichenfolge.|
|[CStringT:: Operator = =](#operator_eq_eq)|Bestimmt, ob zwei Zeichen folgen logisch gleich sind.|
|[CStringT:: Operator! =](#operator_neq)|Bestimmt, ob zwei Zeichen folgen logisch nicht gleich sind.|
|[CStringT:: Operator &lt;](#operator_lt)|Bestimmt, ob die Zeichenfolge links vom Operator kleiner als die Zeichenfolge auf der rechten Seite ist.|
|[CStringT:: Operator &gt;](#operator_gt)|Bestimmt, ob die Zeichenfolge links vom Operator größer als die Zeichenfolge auf der rechten Seite ist.|
|[CStringT:: Operator &lt;=](#operator_lt_eq)|Bestimmt, ob die Zeichenfolge links vom Operator kleiner als oder gleich der Zeichenfolge auf der rechten Seite ist.|
|[CStringT:: Operator &gt;=](#operator_gt_eq)|Bestimmt, ob die Zeichenfolge links vom Operator größer oder gleich der Zeichenfolge auf der rechten Seite ist.|

## <a name="remarks"></a>Bemerkungen

`CStringT` erbt von der [CSimpleStringT-Klasse](../../atl-mfc-shared/reference/csimplestringt-class.md). Erweiterte Funktionen, wie z. b. Zeichen Bearbeitung, Reihenfolge und Suche, werden von implementiert `CStringT` .

> [!NOTE]
> `CStringT` -Objekte können Ausnahmen auslösen. Dies tritt auf, wenn ein- `CStringT` Objekt aus irgendeinem Grund nicht über genügend Arbeitsspeicher verfügt.

Ein- `CStringT` Objekt besteht aus einer Sequenz von Zeichen variabler Länge. `CStringT` stellt Funktionen und Operatoren mit Syntax ähnlich der von Basic bereit. Verkettungs-und Vergleichs Operatoren machen zusammen mit der vereinfachten Speicherverwaltung die `CStringT` Verwendung von Objekten einfacher als normale Zeichen Arrays.

> [!NOTE]
> Obwohl es möglich ist, Instanzen zu erstellen, `CStringT` die eingebettete NULL-Zeichen enthalten, empfiehlt es sich, diese zu erstellen. Das Aufrufen von Methoden und Operatoren für `CStringT` Objekte, die eingebettete NULL-Zeichen enthalten, kann unbeabsichtigte Ergebnisse verursachen.

Durch die Verwendung verschiedener Kombinationen aus den `BaseType` `StringTraits` Parametern und `CStringT` können Objekte in den folgenden Typen enthalten sein, die von den ATL-Bibliotheken vordefiniert wurden.

Wenn Sie in einer ATL-Anwendung verwenden:

`CString`, `CStringA` und `CStringW` werden aus der MFC-DLL (MFC90.DLL) exportiert, niemals aus den Benutzer-DLLs. Dies geschieht, um zu verhindern, `CStringT` dass eine Multiplikation definiert wird.

> [!NOTE]
> Wenn Ihr Code die Problem Umgehung für Linker-Fehler enthält, die unter [Exportieren von Zeichen folgen Klassen mithilfe von CStringT](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md)beschrieben ist, sollten Sie diesen Code entfernen. Es wird nicht mehr benötigt.

Die folgenden Zeichen folgen Typen sind in MFC-basierten Anwendungen verfügbar:

|CStringT-Typ|Deklaration|
|-------------------|-----------------|
|`CStringA`|Eine Zeichenfolge des ANSI-Zeichen Typs mit CRT-Unterstützung.|
|`CStringW`|Eine Zeichenfolge des Unicode-Zeichen Typs mit CRT-Unterstützung.|
|`CString`|ANSI-und Unicode-Zeichen Typen mit CRT-Unterstützung.|

Die folgenden Zeichen folgen Typen sind in Projekten verfügbar, in denen ATL_CSTRING_NO_CRT definiert ist:

|CStringT-Typ|Deklaration|
|-------------------|-----------------|
|`CAtlStringA`|Eine Zeichenfolge des ANSI-Zeichen Typs ohne CRT-Unterstützung.|
|`CAtlStringW`|Eine Zeichenfolge des Unicode-Zeichen Typs ohne CRT-Unterstützung.|
|`CAtlString`|ANSI-und Unicode-Zeichen Typen ohne CRT-Unterstützung.|

Die folgenden Zeichen folgen Typen sind in Projekten verfügbar, in denen ATL_CSTRING_NO_CRT nicht definiert ist:

|CStringT-Typ|Deklaration|
|-------------------|-----------------|
|`CAtlStringA`|Eine Zeichenfolge des ANSI-Zeichen Typs mit CRT-Unterstützung.|
|`CAtlStringW`|Eine Zeichenfolge des Unicode-Zeichen Typs mit CRT-Unterstützung.|
|`CAtlString`|ANSI-und Unicode-Zeichen Typen mit CRT-Unterstützung.|

`CString` Objekte haben außerdem die folgenden Eigenschaften:

- `CStringT` Objekte können aufgrund von Verkettungs Vorgängen vergrößert werden.

- `CStringT` Objekte folgen "Wert Semantik". Stellen `CStringT` Sie sich ein-Objekt als tatsächliche Zeichenfolge vor, nicht als Zeiger auf eine Zeichenfolge.

- Sie können `CStringT` Objekte für `PCXSTR` Funktionsargumente frei ersetzen.

- Benutzerdefinierte Speicherverwaltung für Zeichen folgen Puffer. Weitere Informationen finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringt-predefined-types"></a>CStringT vordefinierte Typen

Da `CStringT` ein Vorlagen Argument verwendet, um den Zeichentyp (entweder [wchar_t](../../c-runtime-library/standard-types.md) oder [char](../../c-runtime-library/standard-types.md)) zu definieren, können Methoden Parametertypen manchmal kompliziert sein. Um dieses Problem zu vereinfachen, wird ein Satz vordefinierter Typen definiert und in der gesamten `CStringT` Klasse verwendet. In der folgenden Tabelle sind die verschiedenen Typen aufgelistet:

|Name|Beschreibung|
|----------|-----------------|
|`XCHAR`|Ein einzelnes Zeichen (entweder **`wchar_t`** oder **`char`** ) mit dem gleichen Zeichentyp wie das- `CStringT` Objekt.|
|`YCHAR`|Ein einzelnes Zeichen (entweder **`wchar_t`** oder **`char`** ) mit dem umgekehrten Zeichentyp als `CStringT` Objekt.|
|`PXSTR`|Ein Zeiger auf eine Zeichenfolge (entweder **`wchar_t`** oder **`char`** ) mit dem gleichen Zeichentyp wie das- `CStringT` Objekt.|
|`PYSTR`|Ein Zeiger auf eine Zeichenfolge (entweder **`wchar_t`** oder **`char`** ) mit dem umgekehrten Zeichentyp als- `CStringT` Objekt.|
|`PCXSTR`|Ein Zeiger auf eine **`const`** Zeichenfolge (entweder **`wchar_t`** oder **`char`** ) mit dem gleichen Zeichentyp wie das- `CStringT` Objekt.|
|`PCYSTR`|Ein Zeiger auf eine **`const`** Zeichenfolge (entweder **`wchar_t`** oder **`char`** ) mit dem umgekehrten Zeichentyp als- `CStringT` Objekt.|

> [!NOTE]
> Code, der zuvor nicht dokumentierte Methoden von (z. b.) verwendet hat, `CString` `AssignCopy` muss durch Code ersetzt werden, der die folgenden dokumentierten Methoden von verwendet `CStringT` (z `GetBuffer` . b `ReleaseBuffer` . oder). Diese Methoden werden von geerbt `CSimpleStringT` .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>Requirements (Anforderungen)

|Header|Zweck|
|------------|-------------|
|CStringT. h|Nur-MFC-Zeichen folgen Objekte|
|atlstr. h|Nicht-MFC-Zeichen folgen Objekte|

## <a name="cstringtallocsysstring"></a><a name="allocsysstring"></a> CStringT:: Zuordnung

Ordnet eine Automation-kompatible Zeichenfolge vom Typ BSTR zu und kopiert den Inhalt des- `CStringT` Objekts hinein, einschließlich des abschließenden NULL-Zeichens.

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>Rückgabewert

Die neu zugeordnete Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

In MFC-Programmen wird eine [cmemoryexception-Klasse](../../mfc/reference/cmemoryexception-class.md) ausgelöst, wenn nicht genügend Arbeitsspeicher vorhanden ist. In ATL-Programmen wird eine ""- [Ausnahme](../../atl/reference/catlexception-class.md) ausgelöst. Diese Funktion wird normalerweise verwendet, um Zeichen folgen für die Automatisierung zurückzugeben.

Wenn diese Zeichenfolge im Allgemeinen als [in]-Parameter an eine com-Funktion übergeben wird, muss der Aufrufer die Zeichenfolge freigeben. Dies kann mithilfe von [sysfrestring](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)erfolgen, wie im Windows SDK beschrieben. Weitere Informationen finden Sie unter [zuordnen und Freigeben von Arbeitsspeicher für ein BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).

Weitere Informationen zu OLE-Zuordnungs Funktionen in Windows finden Sie unter [SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) in der Windows SDK.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CStringT::AllocSysString`.

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

## <a name="cstringtansitooem"></a><a name="ansitooem"></a> CStringT:: ansian OEM

Konvertiert alle Zeichen in diesem- `CStringT` Objekt aus dem ANSI-Zeichensatz in den OEM-Zeichensatz.

```cpp
void AnsiToOem();
```

### <a name="remarks"></a>Bemerkungen

Die-Funktion ist nicht verfügbar, wenn _UNICODE definiert ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

## <a name="cstringtappendformat"></a><a name="appendformat"></a> CStringT:: AppendFormat

Fügt formatierte Daten an ein vorhandenes- `CStringT` Objekt an.

```cpp
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>Parameter

*pszformat*<br/>
Eine Format Steuerelement Zeichenfolge.

*nformatid*<br/>
Der Zeichen folgen Ressourcen Bezeichner, der die Format Steuerelement-Zeichenfolge enthält.

*argument*<br/>
Optionale Argumente.

### <a name="remarks"></a>Bemerkungen

Diese Funktion formatiert und fügt eine Reihe von Zeichen und Werten in der ein `CStringT` . Jedes optionale Argument (sofern vorhanden) wird entsprechend der entsprechenden Format Spezifikation in *pszformat* oder der durch *nformatd*identifizierten Zeichen folgen Ressource konvertiert und angefügt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

## <a name="cstringtcollate"></a><a name="collate"></a> CStringT:: COLLATE

Vergleicht zwei Zeichen folgen mithilfe der Funktion "Generic-Text" `_tcscoll` .

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parameter

*PSZ*<br/>
Die andere Zeichenfolge, die für den Vergleich verwendet wird.

### <a name="return-value"></a>Rückgabewert

0 (null), wenn die Zeichen folgen identisch sind, < 0, wenn dieses `CStringT` Objekt kleiner als *PSZ*ist, oder > 0, wenn dieses `CStringT` Objekt größer als *PSZ*ist.

### <a name="remarks"></a>Bemerkungen

Die `_tcscoll` in Tchar definierte generische Textfunktion. H, wird entweder `strcoll` , `wcscoll` oder zugeordnet `_mbscoll` , abhängig vom Zeichensatz, der zur Kompilierzeit definiert ist. Jede Funktion führt einen Vergleich der Zeichen folgen nach Groß-und Kleinschreibung entsprechend der derzeit verwendeten Codepage durch. Weitere Informationen finden Sie unter "_mbscoll", "", "_strcoll_l", " [_wcscoll_l _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)".

## <a name="cstringtcollatenocase"></a><a name="collatenocase"></a> CStringT:: collatsocase

Vergleicht zwei Zeichen folgen mithilfe der Funktion "Generic-Text" `_tcscoll` .

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parameter

*PSZ*<br/>
Die andere Zeichenfolge, die für den Vergleich verwendet wird.

### <a name="return-value"></a>Rückgabewert

0 (null), wenn die Zeichen folgen identisch sind (die Groß-/Kleinschreibung wird ignoriert), < 0, wenn dieses `CStringT` Objekt kleiner als *PSZ* ist (wobei die Groß-/Kleinschreibung ignoriert wird), oder > 0, wenn dieses `CStringT` Objekt größer als *psz*

### <a name="remarks"></a>Bemerkungen

Die `_tcscoll` in Tchar definierte generische Textfunktion. H, wird entweder `stricoll` , `wcsicoll` oder zugeordnet `_mbsicoll` , abhängig vom Zeichensatz, der zur Kompilierzeit definiert ist. Jede Funktion führt entsprechend der derzeit verwendeten Codepage einen Vergleich der Zeichen folgen ohne Beachtung der Groß-und Kleinschreibung durch. Weitere Informationen finden Sie unter "_mbscoll", "", "_strcoll_l", " [_wcscoll_l _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)".

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

## <a name="cstringtcompare"></a><a name="compare"></a> CStringT:: Compare

Vergleicht zwei Zeichen folgen (Groß-/Kleinschreibung beachten)

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>Parameter

*PSZ*<br/>
Die andere Zeichenfolge, die für den Vergleich verwendet wird.

### <a name="return-value"></a>Rückgabewert

0 (null), wenn die Zeichen folgen identisch sind, < 0, wenn dieses `CStringT` Objekt kleiner als *PSZ*ist, oder > 0, wenn dieses `CStringT` Objekt größer als *PSZ*ist.

### <a name="remarks"></a>Bemerkungen

Die `_tcscmp` in Tchar definierte generische Textfunktion. H, wird entweder `strcmp` , `wcscmp` oder zugeordnet `_mbscmp` , abhängig vom Zeichensatz, der zur Kompilierzeit definiert ist. Jede Funktion führt einen Vergleich der Zeichen folgen unter Beachtung der Groß-und Kleinschreibung durch und ist nicht vom Gebiets Schema betroffen. Weitere Informationen finden Sie unter " [straucmp, wcscmp", "_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)".

Wenn die Zeichenfolge eingebettete Nullen enthält, wird die Zeichenfolge für den Vergleich beim ersten eingebetteten NULL-Zeichen als abgeschnitten betrachtet.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CStringT::Compare`.

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

## <a name="cstringtcomparenocase"></a><a name="comparenocase"></a> CStringT:: comparoocase

Vergleicht zwei Zeichen folgen (Groß-/Kleinschreibung nicht beachtet

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parameter

*PSZ*<br/>
Die andere Zeichenfolge, die für den Vergleich verwendet wird.

### <a name="return-value"></a>Rückgabewert

0 (null), wenn die Zeichen folgen identisch sind (die Groß-/Kleinschreibung wird ignoriert), <0, wenn dieses `CStringT` Objekt kleiner als *PSZ* ist (wobei die Groß-/Kleinschreibung ignoriert wird), oder >0, wenn dieses `CStringT` Objekt größer als *psz*

### <a name="remarks"></a>Bemerkungen

Die `_tcsicmp` in Tchar definierte generische Textfunktion. H, wird entweder oder zugeordnet, `_stricmp` `_wcsicmp` `_mbsicmp` abhängig vom Zeichensatz, der zum Zeitpunkt der Kompilierung definiert wird. Jede Funktion führt einen Vergleich der Zeichen folgen ohne Beachtung der Groß-und Kleinschreibung durch. Der Vergleich hängt vom LC_CTYPE Aspekt des Gebiets Schemas ab, aber nicht von LC_COLLATE. Weitere Informationen finden Sie unter [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

## <a name="cstringtcstringt"></a><a name="cstringt"></a> CStringT:: CStringT

Erstellt ein `CStringT`-Objekt.

```
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

*PCH*<br/>
Ein Zeiger auf ein Array von Zeichen der Länge *nlength*, nicht NULL-terminiert.

*nlength*<br/>
Gibt die Anzahl der Zeichen in *PCH*an.

*ch*<br/>
Ein einzelnes Zeichen.

*pszSrc*<br/>
Eine mit NULL endende Zeichenfolge, die in dieses-Objekt kopiert werden soll `CStringT` .

*pstringmgr*<br/>
Ein Zeiger auf den Speicher-Manager für das- `CStringT` Objekt. Weitere Informationen zur `IAtlStringMgr` -und-Speicherverwaltung für finden Sie unter `CStringT` [Speicherverwaltung mit CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

*"Straume"*<br/>
Ein vorhandenes- `CStringT` Objekt, das in dieses-Objekt kopiert werden soll `CStringT` . Weitere Informationen zu `CThisString` und `CThisSimpleString` finden Sie im Abschnitt "Hinweise".

*varSrc*<br/>
Ein Variant-Objekt, das in dieses-Objekt kopiert werden soll `CStringT` .

*BaseType*<br/>
Der Zeichentyp der Zeichen folgen Klasse. Dabei kann es sich um eine der folgenden Methoden handeln:

**`char`** (für ANSI-Zeichen folgen).

**`wchar_t`** (für Unicode-Zeichen folgen).

Tchar (für ANSI-und Unicode-Zeichen folgen).

*bmfcdll*<br/>
Ein boolescher Wert, der angibt, ob das Projekt eine MFC-DLL (true) oder nicht (false) ist.

*Systemstring*<br/>
Muss sein `System::String` , und das Projekt muss mit/CLR. kompiliert werden.

*pstring*<br/>
Ein Handle für ein- `CStringT` Objekt.

### <a name="remarks"></a>Bemerkungen

Da die-Konstruktoren die Eingabedaten in neuen zugeordneten Speicher kopieren, sollten Sie beachten, dass Arbeitsspeicher Ausnahmen entstehen können. Beachten Sie, dass einige dieser Konstruktoren als Konvertierungs Funktionen fungieren. Dadurch können Sie z. b. einen LPTSTR ersetzen, in dem ein- `CStringT` Objekt erwartet wird.

- `CStringT`( `LPCSTR` `lpsz` ): Erstellt einen Unicode `CStringT` aus einer ANSI-Zeichenfolge. Sie können diesen Konstruktor auch verwenden, um eine Zeichen folgen Ressource zu laden, wie im folgenden Beispiel gezeigt.

- `CStringT(``LPCWSTR` `lpsz` ): Erstellt einen `CStringT` aus einer Unicode-Zeichenfolge.

- `CStringT`( `const unsigned char*` `psz` ): Ermöglicht das Erstellen eines `CStringT` von einem Zeiger auf **`unsigned char`** .

> [!NOTE]
> Definieren Sie das _CSTRING_DISABLE_NARROW_WIDE_CONVERSION Makro, um die implizite Zeichen folgen Konvertierung zwischen ANSI-und Unicode-Zeichen folgen zu deaktivieren. Das-Makro schließt Kompilierungs Konstruktoren aus, die Konvertierungen unterstützen.

Beachten Sie, dass der " *Strauch* "-Parameter entweder ein-oder-Objekt sein kann `CStringT` `CThisSimpleString` . Verwenden Sie für eine `CStringT` der Standard Instanziierungen ( `CString` , `CStringA` oder `CStringW` ), und verwenden Sie für `CThisSimpleString` einen- **`this`** Zeiger. `CThisSimpleString` deklariert eine Instanz der [CSimpleStringT-Klasse](../../atl-mfc-shared/reference/csimplestringt-class.md), die eine kleinere Zeichen folgen Klasse mit weniger integrierter Funktionalität als die- `CStringT` Klasse ist.

Der Überladungs Operator erstellt `CSimpleStringT<>&()` ein- `CStringT` Objekt aus einer- `CSimpleStringT` Deklaration.

> [!NOTE]
> Obwohl es möglich ist, Instanzen zu erstellen, `CStringT` die eingebettete NULL-Zeichen enthalten, empfiehlt es sich, diese zu erstellen. Das Aufrufen von Methoden und Operatoren für `CStringT` Objekte, die eingebettete NULL-Zeichen enthalten, kann unbeabsichtigte Ergebnisse verursachen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

## <a name="cstringtcstringt"></a><a name="_dtorcstringt"></a> CStringT:: ~ CStringT

Zerstört das `CStringT`-Objekt.

```
~CStringT() throw();
```

### <a name="remarks"></a>Bemerkungen

Zerstört das `CStringT`-Objekt.

## <a name="cstringtdelete"></a><a name="delete"></a> CStringT::D Elete

Löscht ein Zeichen oder Zeichen aus einer Zeichenfolge, beginnend mit dem Zeichen am angegebenen Index.

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
Der null basierte Index des ersten Zeichens im `CStringT` zu löschenden-Objekt.

*nCount*<br/>
Die Anzahl der zu entfernenden Zeichen.

### <a name="return-value"></a>Rückgabewert

Die Länge der geänderten Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Wenn *nCount* länger als die Zeichenfolge ist, wird der Rest der Zeichenfolge entfernt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

## <a name="cstringtfind"></a><a name="find"></a> CStringT:: Find

Durchsucht diese Zeichenfolge nach der ersten Entsprechung eines Zeichens oder einer Teil Zeichenfolge.

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>Parameter

*pszsub*<br/>
Eine zu suchende Teil Zeichenfolge.

*iStart*<br/>
Der Index des Zeichens in der Zeichenfolge, mit dem mit der Suche begonnen werden soll, oder 0, um von Anfang an zu beginnen.

*ch*<br/>
Ein einzelnes Zeichen, nach dem gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Der null basierte Index des ersten Zeichens in diesem- `CStringT` Objekt, das mit der angeforderten Teil Zeichenfolge übereinstimmt, oder-1, wenn die Teil Zeichenfolge oder das Zeichen nicht gefunden wurde.

### <a name="remarks"></a>Bemerkungen

Die-Funktion ist überladen, sodass beide einzelnen Zeichen (ähnlich der Lauf Zeitfunktion `strchr` ) und Zeichen folgen (ähnlich wie) akzeptiert werden `strstr` .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

## <a name="cstringtfindoneof"></a><a name="findoneof"></a> CStringT:: findoneof

Durchsucht diese Zeichenfolge nach dem ersten Zeichen, das mit jedem in *pszcharset*enthaltenen Zeichen übereinstimmt.

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>Parameter

*pszcharset*<br/>
Zeichenfolge mit Zeichen für den Abgleich.

### <a name="return-value"></a>Rückgabewert

Der null basierte Index des ersten Zeichens in dieser Zeichenfolge, das auch in *pszcharset*ist. -1, wenn keine Entsprechung vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Sucht das erste Vorkommen der Zeichen in *pszcharset*.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

## <a name="cstringtformat"></a><a name="format"></a> CStringT:: Format

Schreibt formatierte Daten auf `CStringT` dieselbe Weise wie [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) Formatieren von Daten in ein Zeichen Array im C-Format.

```cpp
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>Parameter

*nformatid*<br/>
Der Zeichen folgen Ressourcen Bezeichner, der die Format Steuerelement-Zeichenfolge enthält.

*pszformat*<br/>
Eine Format Steuerelement Zeichenfolge.

*argument*<br/>
Optionale Argumente.

### <a name="remarks"></a>Bemerkungen

Diese Funktion formatiert und speichert eine Reihe von Zeichen und Werten im `CStringT` . Jedes optionale Argument (sofern vorhanden) wird entsprechend der entsprechenden Format Spezifikation in *pszformat* oder der durch *nformatd*identifizierten Zeichen folgen Ressource konvertiert und ausgegeben.

Der-Befehl schlägt fehl, wenn das Zeichen folgen Objekt selbst als Parameter für angeboten wird `Format` . Der folgende Code führt z. b. zu unvorhersehbaren Ergebnissen:

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

Weitere Informationen finden Sie unter [Format Specification Syntax: printf and wprintf Functions (Syntax der Formatangabe: printf- und wprintf-Funktionen)](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

## <a name="cstringtformatmessage"></a><a name="formatmessage"></a> CStringT:: FormatMessage

Formatiert eine Nachrichten Zeichenfolge.

```cpp
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>Parameter

*nformatid*<br/>
Der Zeichen folgen Ressourcen Bezeichner, der den unformatierten Meldungs Text enthält.

*pszformat*<br/>
Verweist auf die Format Steuerelement Zeichenfolge. Sie wird auf Einfügungen überprüft und entsprechend formatiert. Die Format Zeichenfolge ähnelt der Format Zeichenfolge im *printf*-Format der Lauf Zeitfunktion, mit dem Unterschied, dass die Parameter in beliebiger Reihenfolge eingefügt werden können.

*argument*<br/>
Optionale Argumente.

### <a name="remarks"></a>Bemerkungen

Die-Funktion erfordert eine Nachrichten Definition als Eingabe. Die Nachrichten Definition wird von *pszformat* oder von der durch *nformatd*identifizierten Zeichen folgen Ressource bestimmt. Die-Funktion kopiert den formatierten Meldungs Text in das- `CStringT` Objekt und verarbeitet alle eingebetteten INSERT-Sequenzen, wenn dies angefordert wird.

> [!NOTE]
> `FormatMessage` versucht, den Systemspeicher für die neu formatierte Zeichenfolge zuzuweisen. Wenn dieser Versuch fehlschlägt, wird automatisch eine Speicher Ausnahme ausgelöst.

Jede Einfügung muss über einen entsprechenden Parameter verfügen, der auf den *pszformat* *-oder nformatd* -Parameter folgt. Im Nachrichtentext werden mehrere Escapesequenzen für die dynamische Formatierung der Nachricht unterstützt. Weitere Informationen finden Sie unter der Windows- [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) -Funktion in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

## <a name="cstringtformatmessagev"></a><a name="formatmessagev"></a> CStringT:: formatmessagev

Formatiert eine Meldungs Zeichenfolge mithilfe einer Variablen Argumentliste.

```cpp
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>Parameter

*pszformat*<br/>
Verweist auf die Format Steuerelement Zeichenfolge. Sie wird auf Einfügungen überprüft und entsprechend formatiert. Die Format Zeichenfolge ähnelt Lauf Zeit Funktions `printf` Format-Zeichen folgen, mit dem Unterschied, dass die Parameter in beliebiger Reihenfolge eingefügt werden können.

*Liste mit Parametern*<br/>
Zeiger auf eine Liste von Argumenten.

### <a name="remarks"></a>Bemerkungen

Die-Funktion erfordert eine Nachrichten Definition als Eingabe, die durch *pszformat*bestimmt wird. Die-Funktion kopiert den formatierten Meldungs Text und eine Variablen Liste von Argumenten in das- `CStringT` Objekt und verarbeitet dabei alle eingebetteten INSERT-Sequenzen, wenn dies angefordert wird.

> [!NOTE]
> `FormatMessageV` Ruft [CStringT:: FormatMessage](#formatmessage)auf, das versucht, Systemspeicher für die neu formatierte Zeichenfolge zuzuweisen. Wenn dieser Versuch fehlschlägt, wird automatisch eine Speicher Ausnahme ausgelöst.

Weitere Informationen finden Sie unter der Windows- [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) -Funktion in der Windows SDK.

## <a name="cstringtformatv"></a><a name="formatv"></a> CStringT:: formatv

Formatiert eine Meldungs Zeichenfolge mithilfe einer Variablen Argumentliste.

```cpp
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>Parameter

*pszformat*<br/>
Verweist auf die Format Steuerelement Zeichenfolge. Sie wird auf Einfügungen überprüft und entsprechend formatiert. Die Format Zeichenfolge ähnelt Lauf Zeit Funktions `printf` Format-Zeichen folgen, mit dem Unterschied, dass die Parameter in beliebiger Reihenfolge eingefügt werden können.

*args*<br/>
Zeiger auf eine Liste von Argumenten.

### <a name="remarks"></a>Bemerkungen

Schreibt eine formatierte Zeichenfolge und eine Variablen Liste von Argumenten `CStringT` in eine Zeichenfolge auf die gleiche Weise wie `vsprintf_s` Daten in ein Zeichen Array im C-Format.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

## <a name="cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a> CStringT:: GetEnvironmentVariable

Legt die Zeichenfolge auf den Wert der angegebenen Umgebungsvariablen fest.

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>Parameter

*pszvar*<br/>
Zeiger auf eine mit NULL endenden Zeichenfolge, die die Umgebungsvariable angibt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Ruft den Wert der angegebenen Variablen aus dem Umgebungsblock des aufrufenden Prozesses ab. Der Wert wird in Form einer auf NULL endenden Zeichenfolge angezeigt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

## <a name="cstringtinsert"></a><a name="insert"></a> CStringT:: INSERT

Fügt ein einzelnes Zeichen oder eine Teil Zeichenfolge am angegebenen Index innerhalb der Zeichenfolge ein.

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
Der Index des Zeichens, vor dem die Einfügung stattfinden soll.

*PSZ*<br/>
Ein Zeiger auf die einzufügende Teil Zeichenfolge.

*ch*<br/>
Das einzufügende Zeichen.

### <a name="return-value"></a>Rückgabewert

Die Länge der geänderten Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Der *iIndex* -Parameter identifiziert das erste Zeichen, das verschoben wird, um Platz für das Zeichen oder die Teil Zeichenfolge zu schaffen. Wenn *nIndex* 0 (null) ist, wird die Einfügung vor der gesamten Zeichenfolge ausgeführt. Wenn *nIndex* höher als die Länge der Zeichenfolge ist, verkettet die Funktion die vorhandene Zeichenfolge und das neue Material, das entweder von *ch* oder *PSZ*bereitgestellt wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

## <a name="cstringtleft"></a><a name="left"></a> CStringT:: Left

Extrahiert die äußersten linken *nCount* -Zeichen aus diesem `CStringT` -Objekt und gibt eine Kopie der extrahierten Teil Zeichenfolge zurück.

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>Parameter

*nCount*<br/>
Die Anzahl der aus diesem `CStringT`-Objekt zu extrahierenden Zeichen.

### <a name="return-value"></a>Rückgabewert

Ein `CStringT`-Objekt, das eine Kopie des angegebenen Zeichenbereichs enthält. Das zurückgegebene `CStringT`-Objekt ist ggf. leer.

### <a name="remarks"></a>Bemerkungen

Wenn *nCount* die Zeichen folgen Länge überschreitet, wird die gesamte Zeichenfolge extrahiert. `Left` ähnelt der `Left`-Funktion von ///Visual Basic.

Bei Multibyte-Zeichensätzen (MBCS) behandelt *nCount* jede 8-Bit-Sequenz als Zeichen, sodass *nCount* die Anzahl von Multibytezeichen mit zwei multipliziert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

## <a name="cstringtloadstring"></a><a name="loadstring"></a> CStringT:: loadstring

Liest eine durch *NID*identifizierte Windows-Zeichen folgen Ressource in ein vorhandenes- `CStringT` Objekt.

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>Parameter

*hInstance*<br/>
Ein Handle für die Instanz des Moduls.

*nID*<br/>
Eine Windows-Zeichen folgen Ressourcen-ID.

*wlanguageid*<br/>
Die Sprache der Zeichen folgen Ressource.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn der Ressourcen Ladevorgang erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Lädt die Zeichen folgen Ressource (*NID*) aus dem angegebenen Modul (*HINSTANCE*) unter Verwendung der angegebenen Sprache (*wlanguage*).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

## <a name="cstringtmakelower"></a><a name="makelower"></a> CStringT:: makelower

Konvertiert das- `CStringT` Objekt in eine Zeichenfolge in Kleinbuchstaben.

```
CStringT& MakeLower();
```

### <a name="return-value"></a>Rückgabewert

Die resultierende Zeichenfolge in Kleinbuchstaben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

## <a name="cstringtmakereverse"></a><a name="makereverse"></a> CStringT:: makereverse

Kehrt die Reihenfolge der Zeichen im- `CStringT` Objekt um.

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>Rückgabewert

Die resultierende umgekehrte Zeichenfolge.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

## <a name="cstringtmakeupper"></a><a name="makeupper"></a> CStringT:: makeUpper

Konvertiert das- `CStringT` Objekt in eine Zeichenfolge in Großbuchstaben.

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>Rückgabewert

Die resultierende Zeichenfolge in Großbuchstaben.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

## <a name="cstringtmid"></a><a name="mid"></a> CStringT:: Mid

Extrahiert eine Teil Zeichenfolge der Länge *nCount* -Zeichen aus diesem- `CStringT` Objekt, beginnend an der Position *ifirst* (null basiert).

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>Parameter

*ifirst*<br/>
Der null basierte Index des ersten Zeichens in diesem- `CStringT` Objekt, das in die extrahierte Teil Zeichenfolge eingeschlossen werden soll.

*nCount*<br/>
Die Anzahl der aus diesem `CStringT`-Objekt zu extrahierenden Zeichen. Wenn dieser Parameter nicht angegeben wird, wird der Rest der Zeichenfolge extrahiert.

### <a name="return-value"></a>Rückgabewert

Ein `CStringT`-Objekt, das eine Kopie des angegebenen Zeichenbereichs enthält. Beachten Sie, dass das zurückgegebene `CStringT` Objekt möglicherweise leer ist.

### <a name="remarks"></a>Bemerkungen

Die-Funktion gibt eine Kopie der extrahierten Teil Zeichenfolge zurück. `Mid` ähnelt der grundlegenden Mid-Funktion (mit dem Unterschied, dass Indizes in Basic ein einbasiertes sind).

Bei Multibytezeichen-Zeichensätzen (MBCS) bezieht sich *nCount* auf jedes 8-Bit-Zeichen. Das heißt, dass ein Lead-und ein nachfolgendes Byte in einem Multibytezeichen als zwei Zeichen gezählt werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

## <a name="cstringtoemtoansi"></a><a name="oemtoansi"></a> CStringT:: oemto ANSI

Konvertiert alle Zeichen in diesem- `CStringT` Objekt aus dem OEM-Zeichensatz in den ANSI-Zeichensatz.

```cpp
void OemToAnsi();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist nicht verfügbar, wenn _UNICODE definiert ist.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CStringT:: ansian OEM](#ansitooem).

## <a name="cstringtoperator-"></a><a name="operator_eq"></a> CStringT:: Operator =

Weist der Zeichenfolge einen neuen Wert zu.

```
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

*"Straume"*<br/>
Ein `CStringT` , der dieser Zeichenfolge zugewiesen werden soll.

*SRT*<br/>
Ein Verweis auf ein `CThisSimpleString`-Objekt.

*bmfcdll*<br/>
Ein boolescher Wert, der angibt, ob es sich bei dem Projekt um eine MFC-DLL handelt.

*BaseType*<br/>
Der Zeichen folgen-Basistyp.

*var*<br/>
Ein Variant-Objekt, das dieser Zeichenfolge zugewiesen werden soll.

*ch*<br/>
Ein ANSI-oder Unicode-Zeichen, das der Zeichenfolge zugewiesen werden soll.

*pszSrc*<br/>
Ein Zeiger auf die Original Zeichenfolge, die zugewiesen wird.

### <a name="remarks"></a>Bemerkungen

Der Zuweisungs Operator akzeptiert ein anderes `CStringT` Objekt, einen Zeichen Zeiger oder ein einzelnes Zeichen. Beachten Sie, dass Speicher Ausnahmen immer auftreten können, wenn Sie diesen Operator verwenden, da neuer Speicher zugeordnet werden kann.

Weitere Informationen zu `CThisSimpleString` finden Sie im Abschnitt "Hinweise" unter [CStringT:: CStringT](#cstringt).

> [!NOTE]
> Obwohl es möglich ist, Instanzen zu erstellen, `CStringT` die eingebettete NULL-Zeichen enthalten, empfiehlt es sich, diese zu erstellen. Das Aufrufen von Methoden und Operatoren für `CStringT` Objekte, die eingebettete NULL-Zeichen enthalten, kann unbeabsichtigte Ergebnisse verursachen.

## <a name="cstringtoperator-"></a><a name="operator_add"></a> CStringT:: Operator +

Verkettet zwei Zeichen folgen oder ein Zeichen und eine Zeichenfolge.

```
friend CStringT operator+(const CStringT& str1, const CStringT& str2);
friend CStringT operator+(const CStringT& str1, PCXSTR psz2);
friend CStringT operator+(PCXSTR psz1, const CStringT& str2,);
friend CStringT operator+(char ch1, const CStringT& str2,);
friend CStringT operator+(const CStringT& str1, char ch2);
friend CStringT operator+(const CStringT& str1, wchar_t ch2);
friend CStringT operator+(wchar_t ch1, const CStringT& str2,);
```

### <a name="parameters"></a>Parameter

*ch1*<br/>
Ein ANSI-oder Unicode-Zeichen, das mit einer Zeichenfolge verkettet werden soll.

*CH2*<br/>
Ein ANSI-oder Unicode-Zeichen, das mit einer Zeichenfolge verkettet werden soll.

*str1*<br/>
Ein `CStringT` , der mit einer Zeichenfolge oder einem Zeichen verkettet werden soll.

*str2*<br/>
Ein `CStringT` , der mit einer Zeichenfolge oder einem Zeichen verkettet werden soll.

*psz1*<br/>
Ein Zeiger auf eine mit NULL endenden Zeichenfolge, die mit einer Zeichenfolge oder einem Zeichen verkettet werden soll.

*psz2*<br/>
Ein Zeiger auf eine Zeichenfolge, die mit einer Zeichenfolge oder einem Zeichen verkettet werden soll.

### <a name="remarks"></a>Bemerkungen

Es gibt sieben Überladungs Formen der `CStringT::operator+` Funktion. Die erste Version verkettet zwei vorhandene `CStringT` Objekte. Die nächsten beiden verketten ein `CStringT` -Objekt und eine mit NULL endenden Zeichenfolge. Die nächsten beiden verketten ein `CStringT` -Objekt und ein ANSI-Zeichen. Die letzten beiden verketten ein `CStringT` -Objekt und ein Unicode-Zeichen.

> [!NOTE]
> Obwohl es möglich ist, Instanzen zu erstellen, `CStringT` die eingebettete NULL-Zeichen enthalten, empfiehlt es sich, diese zu erstellen. Das Aufrufen von Methoden und Operatoren für `CStringT` Objekte, die eingebettete NULL-Zeichen enthalten, kann unbeabsichtigte Ergebnisse verursachen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_add_eq"></a> CStringT:: Operator + =

Verkettet Zeichen bis zum Ende der Zeichenfolge.

```
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

*SRT*<br/>
Ein Verweis auf ein `CThisSimpleString`-Objekt.

*bmfcdll*<br/>
Ein boolescher Wert, der angibt, ob es sich bei dem Projekt um eine MFC-DLL handelt.

*BaseType*<br/>
Der Zeichen folgen-Basistyp.

*var*<br/>
Ein Variant-Objekt, das mit dieser Zeichenfolge verkettet werden soll.

*ch*<br/>
Ein ANSI-oder Unicode-Zeichen, das mit einer Zeichenfolge verkettet werden soll.

*pszSrc*<br/>
Ein Zeiger auf die ursprüngliche zu verkettende Zeichenfolge.

*"Straume"*<br/>
Eine `CStringT` , die mit dieser Zeichenfolge verkettet werden soll.

### <a name="remarks"></a>Bemerkungen

Der Operator akzeptiert ein anderes `CStringT` Objekt, einen Zeichen Zeiger oder ein einzelnes Zeichen. Beachten Sie, dass Arbeitsspeicher Ausnahmen immer auftreten können, wenn Sie diesen Verkettungs Operator verwenden, da neuer Speicher für Zeichen zugeordnet werden kann, die diesem-Objekt hinzugefügt werden `CStringT` .

Weitere Informationen zu `CThisSimpleString` finden Sie im Abschnitt "Hinweise" unter [CStringT:: CStringT](#cstringt).

> [!NOTE]
> Obwohl es möglich ist, Instanzen zu erstellen, `CStringT` die eingebettete NULL-Zeichen enthalten, empfiehlt es sich, diese zu erstellen. Das Aufrufen von Methoden und Operatoren für `CStringT` Objekte, die eingebettete NULL-Zeichen enthalten, kann unbeabsichtigte Ergebnisse verursachen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_eq_eq"></a> CStringT:: Operator = =

Bestimmt, ob zwei Zeichen folgen logisch gleich sind.

```
friend bool operator==(const CStringT& str1, const CStringT& str2) throw();
friend bool operator==(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator==(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator==(const CStringT& str1, XCHAR ch2) throw();
friend bool operator==(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator==(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator==(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>Parameter

*ch1*<br/>
Ein ANSI-oder Unicode-Zeichen für den Vergleich.

*CH2*<br/>
Ein ANSI-oder Unicode-Zeichen für den Vergleich.

*str1*<br/>
Ein `CStringT` für den Vergleich.

*str2*<br/>
Ein `CStringT` für den Vergleich.

*psz1*<br/>
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

*psz2*<br/>
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

### <a name="remarks"></a>Bemerkungen

Testet, ob eine Zeichenfolge oder ein Zeichen auf der linken Seite gleich einer Zeichenfolge oder einem Zeichen auf der rechten Seite ist, und gibt entsprechend true oder false zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_neq"></a> CStringT:: Operator! =

Bestimmt, ob zwei Zeichen folgen logisch nicht gleich sind.

```
friend bool operator!=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator!=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator!=(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator!=(const CStringT& str1, XCHAR ch2) throw();
friend bool operator!=(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator!=(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator!=(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>Parameter

*ch1*<br/>
Ein ANSI-oder Unicode-Zeichen, das mit einer Zeichenfolge verkettet werden soll.

*CH2*<br/>
Ein ANSI-oder Unicode-Zeichen, das mit einer Zeichenfolge verkettet werden soll.

*str1*<br/>
Ein `CStringT` für den Vergleich.

*str2*<br/>
Ein `CStringT` für den Vergleich.

*psz1*<br/>
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

*psz2*<br/>
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

### <a name="remarks"></a>Bemerkungen

Testet, ob eine Zeichenfolge oder ein Zeichen auf der linken Seite gleich einer Zeichenfolge oder einem Zeichen auf der rechten Seite ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt"></a> CStringT:: Operator &lt;

Bestimmt, ob die Zeichenfolge links vom Operator kleiner als die Zeichenfolge auf der rechten Seite ist.

```
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Ein `CStringT` für den Vergleich.

*str2*<br/>
Ein `CStringT` für den Vergleich.

*psz1*<br/>
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

*psz2*<br/>
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

### <a name="remarks"></a>Bemerkungen

Ein lexikografischer Vergleich zwischen Zeichen folgen, Zeichen nach Zeichen bis:

- Er zwei korrespondierende ungleiche Zeichen findet, und deren Vergleich als Ergebnis des Vergleichs zweier Zeichenfolgen genommen wird.

- Er keine Ungleichheiten findet, aber eine Zeichenfolge mehr Zeichen hat als die andere und die kürzere Zeichenfolge als kleiner als die längere Zeichenfolge betrachtet wird.

- Er keine Ungleichheiten findet und feststellt, dass die Zeichenfolgen die gleiche Anzahl von Zeichen haben und daher gleich sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt"></a> CStringT:: Operator &gt;

Bestimmt, ob die Zeichenfolge links vom Operator größer als die Zeichenfolge auf der rechten Seite ist.

```
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Ein `CStringT` für den Vergleich.

*str2*<br/>
Ein `CStringT` für den Vergleich.

*psz1*<br/>
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

*psz2*<br/>
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

### <a name="remarks"></a>Bemerkungen

Ein lexikografischer Vergleich zwischen Zeichen folgen, Zeichen nach Zeichen bis:

- Er zwei korrespondierende ungleiche Zeichen findet, und deren Vergleich als Ergebnis des Vergleichs zweier Zeichenfolgen genommen wird.

- Er keine Ungleichheiten findet, aber eine Zeichenfolge mehr Zeichen hat als die andere und die kürzere Zeichenfolge als kleiner als die längere Zeichenfolge betrachtet wird.

- Er keine Ungleichheiten findet und feststellt, dass die Zeichenfolgen die gleiche Anzahl von Zeichen haben und daher gleich sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt_eq"></a> CStringT:: Operator &lt;=

Bestimmt, ob die Zeichenfolge links vom Operator kleiner als oder gleich der Zeichenfolge auf der rechten Seite ist.

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Ein `CStringT` für den Vergleich.

*str2*<br/>
Ein `CStringT` für den Vergleich.

*psz1*<br/>
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

*psz2*<br/>
Ein Zeiger auf eine NULL-terminierte Zeichenfolge für den Vergleich.

### <a name="remarks"></a>Bemerkungen

Ein lexikografischer Vergleich zwischen Zeichen folgen, Zeichen nach Zeichen bis:

- Er zwei korrespondierende ungleiche Zeichen findet, und deren Vergleich als Ergebnis des Vergleichs zweier Zeichenfolgen genommen wird.

- Er keine Ungleichheiten findet, aber eine Zeichenfolge mehr Zeichen hat als die andere und die kürzere Zeichenfolge als kleiner als die längere Zeichenfolge betrachtet wird.

- Er keine Ungleichheiten findet und feststellt, dass die Zeichenfolgen die gleiche Anzahl von Zeichen haben und daher gleich sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt_eq"></a> CStringT:: Operator &gt;=

Bestimmt, ob die Zeichenfolge links vom Operator größer oder gleich der Zeichenfolge auf der rechten Seite ist.

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Ein `CStringT` für den Vergleich.

*str2*<br/>
Ein `CStringT` für den Vergleich.

*psz1*<br/>
Ein Zeiger auf eine Zeichenfolge für den Vergleich.

*psz2*<br/>
Ein Zeiger auf eine Zeichenfolge für den Vergleich.

### <a name="remarks"></a>Bemerkungen

Ein lexikografischer Vergleich zwischen Zeichen folgen, Zeichen nach Zeichen bis:

- Er zwei korrespondierende ungleiche Zeichen findet, und deren Vergleich als Ergebnis des Vergleichs zweier Zeichenfolgen genommen wird.

- Er keine Ungleichheiten findet, aber eine Zeichenfolge mehr Zeichen hat als die andere und die kürzere Zeichenfolge als kleiner als die längere Zeichenfolge betrachtet wird.

- Er keine Ungleichheiten findet und feststellt, dass die Zeichenfolgen die gleiche Anzahl von Zeichen haben und daher gleich sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

## <a name="cstringtremove"></a><a name="remove"></a> CStringT:: Remove

Entfernt alle Instanzen des angegebenen Zeichens aus der Zeichenfolge.

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>Parameter

*chremove*<br/>
Das Zeichen, das aus einer Zeichenfolge entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Zeichen, die aus der Zeichenfolge entfernt wurden. NULL, wenn die Zeichenfolge nicht geändert wird.

### <a name="remarks"></a>Bemerkungen

Bei Vergleichen für das Zeichen wird Groß-/Kleinschreibung beachtet

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

## <a name="cstringtreplace"></a><a name="replace"></a> CStringT:: Replace

Es gibt zwei Versionen von `Replace` . Die erste Version ersetzt eine oder mehrere Kopien einer Teil Zeichenfolge durch eine andere Teil Zeichenfolge. Beide Teil Zeichenfolgen werden mit Null beendet. Die zweite Version ersetzt eine oder mehrere Kopien eines Zeichens durch ein anderes Zeichen. Beide Versionen arbeiten mit den Zeichendaten, die in gespeichert sind `CStringT` .

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>Parameter

*pszold*<br/>
Ein Zeiger auf eine mit NULL endende Zeichenfolge, die durch *psznew*ersetzt werden soll.

*psznew*<br/>
Ein Zeiger auf eine NULL-terminierte Zeichenfolge, die *pszold*ersetzt.

*chOld*<br/>
Das Zeichen, das durch *chnew*ersetzt werden soll.

*chnew*<br/>
Das Zeichen, das " *chOld*" ersetzt.

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der ersetzten Instanzen des Zeichens oder der Teil Zeichenfolge zurück, oder NULL, wenn die Zeichenfolge nicht geändert wird.

### <a name="remarks"></a>Bemerkungen

`Replace` kann die Zeichen folgen Länge ändern, da *psznew* und *pszold* nicht die gleiche Länge aufweisen müssen und mehrere Kopien der alten Teil Zeichenfolge in die neue geändert werden können. Bei der-Funktion wird die Groß-/Kleinschreibung beachtet.

Beispiele für `CStringT` -Instanzen sind `CString` , `CStringA` und `CStringW` .

Für `CStringA` `Replace` funktioniert mit ANSI-oder Multibytezeichen-Zeichen (MBCS). Für `CStringW` `Replace` funktioniert mit breit Zeichen.

Für `CString` wird der Zeichen Datentyp zur Kompilierzeit ausgewählt, je nachdem, ob die Konstanten in der folgenden Tabelle definiert sind.

|Definierte Konstante|Zeichen Datentyp|
|----------------------|-------------------------|
|_UNICODE|Breitzeichen|
|_MBCS|Mehr Byte Zeichen|
|Neither|Einzel Byte Zeichen|
|Beide|Nicht definiert|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

## <a name="cstringtreversefind"></a><a name="reversefind"></a> CStringT:: reverstellen suchen

Durchsucht dieses- `CStringT` Objekt nach der letzten Entsprechung eines Zeichens.

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>Parameter

*ch*<br/>
Das zu suchende Zeichen.

### <a name="return-value"></a>Rückgabewert

Der null basierte Index des letzten Zeichens in diesem- `CStringT` Objekt, das mit dem angeforderten Zeichen übereinstimmt, oder-1, wenn das Zeichen nicht gefunden wurde.

### <a name="remarks"></a>Bemerkungen

Die-Funktion ähnelt der-Lauf Zeitfunktion `strrchr` .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

## <a name="cstringtright"></a><a name="right"></a> CStringT:: Right

Extrahiert die letzten *nCount* -Zeichen (d. h. ganz rechts) aus diesem `CStringT` -Objekt und gibt eine Kopie der extrahierten Teil Zeichenfolge zurück.

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>Parameter

*nCount*<br/>
Die Anzahl der aus diesem `CStringT`-Objekt zu extrahierenden Zeichen.

### <a name="return-value"></a>Rückgabewert

Ein `CStringT`-Objekt, das eine Kopie des angegebenen Zeichenbereichs enthält. Beachten Sie, dass das zurückgegebene- `CStringT` Objekt leer sein kann.

### <a name="remarks"></a>Bemerkungen

Wenn *nCount* die Zeichen folgen Länge überschreitet, wird die gesamte Zeichenfolge extrahiert. `Right` ähnelt der Basic- `Right` Funktion (mit der Ausnahme, dass Indizes in Basic Null basiert).

Bei Multibytezeichen-Zeichensätzen (MBCS) bezieht sich *nCount* auf jedes 8-Bit-Zeichen. Das heißt, dass ein Lead-und ein nachfolgendes Byte in einem Multibytezeichen als zwei Zeichen gezählt werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

## <a name="cstringtsetsysstring"></a><a name="setsysstring"></a> CStringT:: SetSysString

Ordnet den BSTR, auf den von *pbstr* verwiesen wird, neu zu und kopiert den Inhalt des- `CStringT` Objekts in diesen, einschließlich des NULL-Zeichens.

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>Parameter

*pbstr*<br/>
Ein Zeiger auf eine Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Die neue Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Abhängig vom Inhalt des `CStringT` Objekts kann sich der Wert des BSTR, auf den *pbstr* verweist, ändern. Die Funktion löst eine aus, `CMemoryException` Wenn nicht genügend Arbeitsspeicher vorhanden ist.

Diese Funktion wird normalerweise verwendet, um den Wert von Zeichen folgen zu ändern, die als Verweis für die Automatisierung verwendet werden

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

## <a name="cstringtspanexcluding"></a><a name="spanexcluding"></a> CStringT:: Span Ausschluss

Extrahiert Zeichen aus der Zeichenfolge, beginnend mit dem ersten Zeichen, die nicht in dem von *pszcharset*identifizierten Zeichensatz enthalten sind.

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parameter

*pszcharset*<br/>
Eine Zeichenfolge, die als Zeichensatz interpretiert wird.

### <a name="return-value"></a>Rückgabewert

Eine Teil Zeichenfolge, die Zeichen in der Zeichenfolge enthält, die nicht in *pszcharset*enthalten sind, beginnend mit dem ersten Zeichen in der Zeichenfolge und mit dem ersten Zeichen in der Zeichenfolge, das auch in *pszcharset* enthalten ist (d. h. beginnend mit dem ersten Zeichen in der Zeichenfolge und bis zu dem ersten Zeichen in der Zeichenfolge, das als *p* Sie gibt die gesamte Zeichenfolge zurück, wenn kein Zeichen in *pszcharset* in der Zeichenfolge gefunden wird.

### <a name="remarks"></a>Bemerkungen

`SpanExcluding` extrahiert und gibt alle Zeichen zurück, die vor dem ersten Vorkommen eines Zeichens aus *pszcharset* stehen (d. h., das Zeichen aus *pszcharset* und alle Zeichen, die in der Zeichenfolge darauf folgen, werden nicht zurückgegeben). Wenn kein Zeichen aus *pszcharset* in der Zeichenfolge gefunden wird, wird `SpanExcluding` die gesamte Zeichenfolge zurückgegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

## <a name="cstringtspanincluding"></a><a name="spanincluding"></a> CStringT:: Span einschließen

Extrahiert Zeichen aus der Zeichenfolge, beginnend mit dem ersten Zeichen, das sich in dem von *pszcharset*identifizierten Zeichensatz befinden.

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parameter

*pszcharset*<br/>
Eine Zeichenfolge, die als Zeichensatz interpretiert wird.

### <a name="return-value"></a>Rückgabewert

Eine Teil Zeichenfolge, die Zeichen in der Zeichenfolge in *pszcharset*enthält, beginnend mit dem ersten Zeichen in der Zeichenfolge und dem Zeitpunkt, zu dem ein Zeichen in der Zeichenfolge gefunden wird, die nicht in *pszcharset*enthalten ist. `SpanIncluding` gibt eine leere Teil Zeichenfolge zurück, wenn das erste Zeichen in der Zeichenfolge nicht in der angegebenen Menge ist.

### <a name="remarks"></a>Bemerkungen

Wenn das erste Zeichen der Zeichenfolge nicht im Zeichensatz ist, wird `SpanIncluding` eine leere Zeichenfolge zurückgegeben. Andernfalls wird eine Sequenz von aufeinander folgenden Zeichen zurückgegeben, die in der Menge enthalten sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

## <a name="cstringttokenize"></a><a name="tokenize"></a> CStringT:: tokenize

Sucht das nächste Token in einer Ziel Zeichenfolge.

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>Parameter

*psztokens*<br/>
Eine Zeichenfolge, die Tokentrennzeichen enthält. Die Reihenfolge dieser Trennzeichen ist nicht wichtig.

*iStart*<br/>
Der null basierte Index, an dem mit der Suche begonnen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein- `CStringT` Objekt, das den aktuellen Tokenwert enthält.

### <a name="remarks"></a>Bemerkungen

Die- `Tokenize` Funktion sucht das nächste Token in der Ziel Zeichenfolge. Der Satz von Zeichen in *psztokens* gibt mögliche Trennzeichen des gefundenen Tokens an. Bei jedem Aufrufe `Tokenize` der-Funktion beginnt bei *iStart*, überspringt führende Trennzeichen und gibt ein- `CStringT` Objekt zurück, das das aktuelle Token enthält. Dies ist die Zeichenfolge bis zum nächsten Trennzeichen. Der Wert von *iStart* wird auf die Position des endtrennzeichens aktualisiert, oder-1, wenn das Ende der Zeichenfolge erreicht wurde. Weitere Token können aus dem Rest der Ziel Zeichenfolge durch eine Reihe von Aufrufen von getrennt werden `Tokenize` . dabei wird *iStart* verwendet, um nachzuverfolgen, wo in der Zeichenfolge das nächste Token gelesen werden soll. Wenn keine weiteren Token vorhanden sind, gibt die Funktion eine leere Zeichenfolge zurück, und *iStart* wird auf-1 festgelegt.

Im Unterschied zu den CRT-versehen-Funktionen wie [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l _mbstok_s](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md), _mbstok_s_l wird `Tokenize` die Ziel Zeichenfolge nicht geändert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>Bemerkungen

Die Ausgabe dieses Beispiels lautet wie folgt:

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

## <a name="cstringttrim"></a><a name="trim"></a> CStringT:: Trim

Entfernt führende und nachfolgende Zeichen aus der Zeichenfolge.

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>Parameter

*chtarget*<br/>
Das zu gekürzte Ziel Zeichen.

*pszTargets*<br/>
Ein Zeiger auf eine Zeichenfolge, die die zu gekürzten Ziel Zeichen enthält. Alle führenden und nachfolgenden Vorkommen von Zeichen in *psztarget* werden aus dem- `CStringT` Objekt abgeschnitten.

### <a name="return-value"></a>Rückgabewert

Gibt die gekürzte Zeichenfolge zurück.

### <a name="remarks"></a>Bemerkungen

Entfernt alle führenden und nachfolgenden Vorkommen einer der folgenden:

- Das von *chtarget*angegebene Zeichen.

- Alle Zeichen, die in der durch *pszTargets*angegebenen Zeichenfolge gefunden werden.

- Leerzeichen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>Bemerkungen

Die Ausgabe dieses Beispiels lautet wie folgt:

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

## <a name="cstringttrimleft"></a><a name="trimleft"></a> CStringT:: TrimLeft

Entfernt führende Zeichen aus der Zeichenfolge.

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>Parameter

*chtarget*<br/>
Das zu gekürzte Ziel Zeichen.

*pszTargets*<br/>
Ein Zeiger auf eine Zeichenfolge, die die zu gekürzten Ziel Zeichen enthält. Alle führenden Vorkommen von Zeichen in *psztarget* werden aus dem- `CStringT` Objekt abgeschnitten.

### <a name="return-value"></a>Rückgabewert

Die resultierende gekürzte Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Entfernt alle führenden und nachfolgenden Vorkommen einer der folgenden:

- Das von *chtarget*angegebene Zeichen.

- Alle Zeichen, die in der durch *pszTargets*angegebenen Zeichenfolge gefunden werden.

- Leerzeichen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

## <a name="cstringttrimright"></a><a name="trimright"></a> CStringT:: TrimRight

Entfernt nachfolgende Zeichen aus der Zeichenfolge.

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>Parameter

*chtarget*<br/>
Das zu gekürzte Ziel Zeichen.

*pszTargets*<br/>
Ein Zeiger auf eine Zeichenfolge, die die zu gekürzten Ziel Zeichen enthält. Alle nachfolgenden Vorkommen von Zeichen in *psztarget* werden aus dem- `CStringT` Objekt abgeschnitten.

### <a name="return-value"></a>Rückgabewert

Gibt das- `CStringT` Objekt zurück, das die gekürzte Zeichenfolge enthält.

### <a name="remarks"></a>Bemerkungen

Entfernt nachfolgende Vorkommen einer der folgenden:

- Das von *chtarget*angegebene Zeichen.

- Alle Zeichen, die in der durch *pszTargets*angegebenen Zeichenfolge gefunden werden.

- Leerzeichen.

Die `CStringT& TrimRight(XCHAR chTarget)` Version akzeptiert einen Zeichen Parameter und entfernt alle Kopien dieses Zeichens aus dem Ende der `CStringT` Zeichen folgen Daten. Sie beginnt am Ende der Zeichenfolge und funktioniert im Vordergrund. Sie wird beendet, wenn ein anderes Zeichen gefunden wird oder wenn `CSTringT` keine Zeichendaten mehr zur Anwendung kommt.

Die `CStringT& TrimRight(PCXSTR pszTargets)` Version akzeptiert eine NULL-terminierte Zeichenfolge, die alle unterschiedlichen Zeichen enthält, nach denen gesucht werden soll. Es entfernt alle Kopien dieser Zeichen im- `CStringT` Objekt. Sie beginnt am Ende der Zeichenfolge und funktioniert im Vordergrund. Sie wird beendet, wenn ein Zeichen gefunden wird, das sich nicht in der Ziel Zeichenfolge befindet, oder wenn nicht `CStringT` mehr Zeichendaten ausführt. Es wird nicht versucht, die gesamte Ziel Zeichenfolge mit einer Teil Zeichenfolge am Ende von abzugleichen `CStringT` .

Die `CStringT& TrimRight()` Version erfordert keine Parameter. Alle nachfolgenden Leerzeichen werden vom Ende der `CStringT` Zeichenfolge entfernt. Leerzeichen können Zeilenumbrüche, Leerzeichen oder Registerkarten sein.

-

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Gemeinsam genutzte ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[CSimpleStringT-Klasse](../../atl-mfc-shared/reference/csimplestringt-class.md)
