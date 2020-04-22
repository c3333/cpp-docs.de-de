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
ms.openlocfilehash: 8fcce4c426cd99785d34dc080f238cc78cdfee36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746707"
---
# <a name="cstringt-class"></a>CStringT-Klasse

Diese Klasse `CStringT` stellt ein Objekt dar.

## <a name="syntax"></a>Syntax

```
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>Parameter

*BaseType*<br/>
Der Zeichentyp der Zeichenfolgenklasse. Dabei kann es sich um eine der folgenden Methoden handeln:

- **char** (für ANSI-Zeichenfolgen).

- **wchar_t** (für Unicode-Zeichenfolgen).

- TCHAR (für ANSI- und Unicode-Zeichenfolgen).

*StringTraits*<br/>
Bestimmt, ob die Zeichenfolgenklasse C Run-Time (CRT)-Bibliotheksunterstützung benötigt und wo sich Zeichenfolgenressourcen befinden. Dabei kann es sich um eine der folgenden Methoden handeln:

- **StrTraitATL< wchar_t** &#124; wchar_t &#124; **TCHAR, ChTraitsCRT< wchar_t &#124;** **char** &#124; **TCHAR > >** **char**

   Die Klasse benötigt CRT-Unterstützung und sucht nach `m_hInstResource` Ressourcenzeichenfolgen im Modul, das von (einem Member der Modulklasse der Anwendung) angegeben wird.

- **StrTraitATL< wchar_t &#124;** **char** &#124; **TCHAR, ChTraitsOS< wchar_t** &#124; wchar_t **wchar_t &#124;** **TCHAR > >**

   Die Klasse benötigt keine CRT-Unterstützung und sucht nach `m_hInstResource` Ressourcenzeichenfolgen im Modul, das von (einem Member der Modulklasse der Anwendung) angegeben wird.

- **StrTraitMFC< wchar_t &#124;** **char** &#124; **TCHAR, ChTraitsCRT< wchar_t** &#124; **char** &#124; **TCHAR > >**

   Die Klasse benötigt CRT-Unterstützung und sucht mithilfe des Standardmäßigen MFC-Suchalgorithmus nach Ressourcenzeichenfolgen.

- **StrTraitMFC< wchar_t** &#124; &#124; **tCHAR, ChTraitsOS< wchar_t &#124;** &#124; &#124; **&#124;** ** > >** > >**char**

   Die Klasse benötigt keine CRT-Unterstützung und sucht mithilfe des standardmäßigen MFC-Suchalgorithmus nach Ressourcenzeichenfolgen.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStringT::CStringT](#cstringt)|Erstellt ein `CStringT` Objekt auf verschiedene Weise.|
|[CStringT::-CStringT](#_dtorcstringt)|Zerstört ein `CStringT` -Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStringT::AllocSysString](#allocsysstring)|Ordnet einen BSTR `CStringT` aus Daten zu.|
|[CStringT::AnsiToOem](#ansitooem)|Führt eine ortsnahe Konvertierung aus dem ANSI-Zeichensatz in den OEM-Zeichensatz durch.|
|[CStringT::AppendFormat](#appendformat)|Fügt formatierte Daten an `CStringT` ein vorhandenes Objekt an.|
|[CStringT::Collate](#collate)|Vergleicht zwei Zeichenfolgen (groß ist die Groß-/Kleinschreibung, verwendet gebietsschemaspezifische Informationen).|
|[CStringT::CollateNoCase](#collatenocase)|Vergleicht zwei Zeichenfolgen (bei Nichtberücksichtigte verwendet gebietsschemaspezifische Informationen).|
|[CStringT::Vergleichen](#compare)|Vergleicht zwei Zeichenfolgen (Groß-/Kleinschreibung).|
|[CStringT::CompareNoCase](#comparenocase)|Vergleicht zwei Zeichenfolgen (inderinsensitive Groß-/Kleinschreibung).|
|[CStringT::Delete](#delete)|Löscht ein Zeichen oder Zeichen aus einer Zeichenfolge.|
|[CStringT::Suchen](#find)|Sucht ein Zeichen oder eine Teilzeichenfolge innerhalb einer größeren Zeichenfolge.|
|[CstringT::FindOneVon](#findoneof)|Sucht das erste übereinstimmende Zeichen aus einem Satz.|
|[CStringT::Format](#format)|Formatiert die `sprintf` Zeichenfolge wie möglich.|
|[CStringT::FormatMessage](#formatmessage)|Formatiert eine Nachrichtenzeichenfolge.|
|[CStringT::FormatMessageV](#formatmessagev)|Formatiert eine Nachrichtenzeichenfolge mithilfe einer Variablenargumentliste.|
|[CStringT::FormatV](#formatv)|Formatiert die Zeichenfolge mithilfe einer Variablenliste von Argumenten.|
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|Legt die Zeichenfolge auf den Wert der angegebenen Umgebungsvariablen fest.|
|[CStringT::Einfügen](#insert)|Fügt ein einzelnes Zeichen oder eine Teilzeichenfolge am angegebenen Index innerhalb der Zeichenfolge ein.|
|[CStringT::Links](#left)|Extrahiert den linken Teil einer Zeichenfolge.|
|[CStringT::LoadString](#loadstring)|Lädt ein `CStringT` vorhandenes Objekt aus einer Windows-Ressource.|
|[CStringT::MakeLower](#makelower)|Konvertiert alle Zeichen in dieser Zeichenfolge in Kleinbuchstaben.|
|[CStringT::MakeReverse](#makereverse)|Kehrt die Zeichenfolge um.|
|[CStringT::MakeUpper](#makeupper)|Konvertiert alle Zeichen in dieser Zeichenfolge in Großbuchstaben.|
|[CStringT::Mitte](#mid)|Extrahiert den mittleren Teil einer Zeichenfolge.|
|[CStringT::OemToAnsi](#oemtoansi)|Führt eine ortsnahe Konvertierung aus dem OEM-Zeichensatz in den ANSI-Zeichensatz durch.|
|[CStringT::Entfernen](#remove)|Entfernt angezeigte Zeichen aus einer Zeichenfolge.|
|[CStringT::Ersetzen](#replace)|Ersetzt angezeigte Zeichen durch andere Zeichen.|
|[CStringT::ReverseFind](#reversefind)|Sucht ein Zeichen innerhalb einer größeren Zeichenfolge; beginnt am Ende.|
|[CStringT::Rechts](#right)|Extrahiert den rechten Teil einer Zeichenfolge.|
|[CStringT::SetSysString](#setsysstring)|Legt ein vorhandenes BSTR-Objekt mit Daten aus einem `CStringT` Objekt fest.|
|[CStringT::SpanExcluding](#spanexcluding)|Extrahiert Zeichen aus der Zeichenfolge, beginnend mit dem ersten Zeichen, die `pszCharSet`nicht in dem Satz von Zeichen enthalten sind, die durch identifiziert werden.|
|[CStringT::Spanincluding](#spanincluding)|Extrahiert eine Teilzeichenfolge, die nur die Zeichen in einem Satz enthält.|
|[CStringT::Tokenize](#tokenize)|Extrahiert angegebene Token in einer Zielzeichenfolge.|
|[CStringT::Trim](#trim)|Trimmt alle führenden und nachfolgenden Leerzeichen aus der Zeichenfolge.|
|[CStringT::TrimLeft](#trimleft)|Trimmt führende Leerzeichen aus der Zeichenfolge.|
|[CStringT::TrimRight](#trimright)|Trimmt nachgestellte Leerzeichen aus der Zeichenfolge.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[CStringT::operator =](#operator_eq)|Weist einem `CStringT` Objekt einen neuen Wert zu.|
|[CStringT::Operator +](#operator_add)|Vergibt zwei Zeichenfolgen oder ein Zeichen und eine Zeichenfolge.|
|[CStringT::Operator +=](#operator_add_eq)|Verkettet eine neue Zeichenfolge am Ende einer vorhandenen Zeichenfolge.|
|[CStringT::operator ==](#operator_eq_eq)|Bestimmt, ob zwei Zeichenfolgen logisch gleich sind.|
|[CStringT::operator !=](#operator_neq)|Bestimmt, ob zwei Zeichenfolgen logisch nicht gleich sind.|
|[CStringT::Operator&lt;](#operator_lt)|Legt fest, ob die Zeichenfolge auf der linken Seite des Operators kleiner als die Zeichenfolge auf der rechten Seite ist.|
|[CStringT::Operator&gt;](#operator_gt)|Legt fest, ob die Zeichenfolge auf der linken Seite des Operators größer als die Zeichenfolge auf der rechten Seite ist.|
|[CStringT::Operator&lt;=](#operator_lt_eq)|Legt fest, ob die Zeichenfolge auf der linken Seite des Operators kleiner oder gleich der Zeichenfolge auf der rechten Seite ist.|
|[CStringT::Operator&gt;=](#operator_gt_eq)|Legt fest, ob die Zeichenfolge auf der linken Seite des Operators größer oder gleich der Zeichenfolge auf der rechten Seite ist.|

## <a name="remarks"></a>Bemerkungen

`CStringT`erbt von der [CSimpleStringT-Klasse](../../atl-mfc-shared/reference/csimplestringt-class.md). Erweiterte Funktionen wie Zeichenmanipulation, Sortierung und Suche `CStringT`werden von implementiert.

> [!NOTE]
> `CStringT`Objekte sind in der Lage, Ausnahmen auszulösen. Dies tritt `CStringT` auf, wenn einem Objekt aus irgendeinem Grund der Arbeitsspeicher ausgeht.

Ein `CStringT` Objekt besteht aus einer Zeichenfolge mit variabler Länge. `CStringT`stellt Funktionen und Operatoren bereit, die eine Syntax verwenden, die der von Basic ähnelt. Verkettungs- und Vergleichsoperatoren sowie `CStringT` eine vereinfachte Speicherverwaltung erleichtern die Verwendung von Objekten als gewöhnliche Zeichenarrays.

> [!NOTE]
> Obwohl es möglich `CStringT` ist, Instanzen zu erstellen, die eingebettete Nullzeichen enthalten, wird empfohlen. Aufrufen von Methoden `CStringT` und Operatoren für Objekte, die eingebettete Nullzeichen enthalten, können unbeabsichtigte Ergebnisse erzeugen.

Durch die Verwendung verschiedener Kombinationen der `BaseType` und `StringTraits` Parameter können `CStringT` Objekte in den folgenden Typen stammen, die von den ATL-Bibliotheken vordefiniert wurden.

Bei Verwendung in einer ATL-Anwendung:

`CString`, `CStringA`und `CStringW` werden aus der MFC-DLL (MFC90. DLL), niemals aus Benutzer-DLLs. Dies geschieht, `CStringT` um zu verhindern, dass die Multiplikation definiert wird.

> [!NOTE]
> Wenn Ihr Code die Problemumgehung für Linkerfehler enthält, die unter [Exportieren von Zeichenfolgenklassen mit CStringT](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md)beschrieben wird, sollten Sie diesen Code entfernen. Es wird nicht mehr benötigt.

Die folgenden Zeichenfolgentypen sind in MFC-basierten Anwendungen verfügbar:

|CStringT-Typ|Deklaration|
|-------------------|-----------------|
|`CStringA`|Eine ANSI-Zeichentypzeichenfolge mit CRT-Unterstützung.|
|`CStringW`|Eine Unicode-Zeichentypzeichenfolge mit CRT-Unterstützung.|
|`CString`|Sowohl ANSI- als auch Unicode-Zeichentypen mit CRT-Unterstützung.|

Die folgenden Zeichenfolgentypen sind in Projekten verfügbar, in denen ATL_CSTRING_NO_CRT definiert ist:

|CStringT-Typ|Deklaration|
|-------------------|-----------------|
|`CAtlStringA`|Eine ANSI-Zeichentypzeichenfolge ohne CRT-Unterstützung.|
|`CAtlStringW`|Eine Unicode-Zeichentypzeichenfolge ohne CRT-Unterstützung.|
|`CAtlString`|Sowohl ANSI- als auch Unicode-Zeichentypen ohne CRT-Unterstützung.|

Die folgenden Zeichenfolgentypen sind in Projekten verfügbar, in denen ATL_CSTRING_NO_CRT nicht definiert ist:

|CStringT-Typ|Deklaration|
|-------------------|-----------------|
|`CAtlStringA`|Eine ANSI-Zeichentypzeichenfolge mit CRT-Unterstützung.|
|`CAtlStringW`|Eine Unicode-Zeichentypzeichenfolge mit CRT-Unterstützung.|
|`CAtlString`|Sowohl ANSI- als auch Unicode-Zeichentypen mit CRT-Unterstützung.|

`CString`Objekte haben außerdem die folgenden Eigenschaften:

- `CStringT`Objekte können durch Verkettungsvorgänge wachsen.

- `CStringT`Objekte folgen "Wertsemantik". Stellen Sie `CStringT` sich ein Objekt als tatsächliche Zeichenfolge vor, nicht als Zeiger auf eine Zeichenfolge.

- Sie können `CStringT` Objekte `PCXSTR` frei durch Funktionsargumente ersetzen.

- Benutzerdefinierte Speicherverwaltung für Zeichenfolgenpuffer. Weitere Informationen finden Sie unter [Speicherverwaltung und CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringt-predefined-types"></a>CStringT Vordefinierte Typen

Da `CStringT` ein Vorlagenargument verwendet wird, um den unterstützten Zeichentyp (entweder [wchar_t](../../c-runtime-library/standard-types.md) oder [char](../../c-runtime-library/standard-types.md)) zu definieren, können Methodenparametertypen manchmal kompliziert sein. Um dieses Problem zu vereinfachen, wird ein Satz `CStringT` vordefinierter Typen definiert und in der gesamten Klasse verwendet. In der folgenden Tabelle sind die verschiedenen Typen aufgeführt:

|Name|BESCHREIBUNG|
|----------|-----------------|
|`XCHAR`|Ein einzelnes Zeichen (entweder **wchar_t** oder **char** `CStringT` ) mit demselben Zeichentyp wie das Objekt.|
|`YCHAR`|Ein einzelnes Zeichen (entweder **wchar_t** oder **char** `CStringT` ) mit dem entgegengesetzten Zeichentyp als Objekt.|
|`PXSTR`|Ein Zeiger auf eine Zeichenkette (entweder **wchar_t** oder **char** `CStringT` ) mit demselben Zeichentyp wie das Objekt.|
|`PYSTR`|Ein Zeiger auf eine Zeichenkette (entweder **wchar_t** oder **char** `CStringT` ) mit dem entgegengesetzten Zeichentyp als Objekt.|
|`PCXSTR`|Ein Zeiger auf eine **const-Zeichenfolge** (entweder **wchar_t** oder **char** `CStringT` ) mit demselben Zeichentyp wie das Objekt.|
|`PCYSTR`|Ein Zeiger auf eine **const-Zeichenzeichenfolge** (entweder **wchar_t** oder **char**) mit dem entgegengesetzten Zeichentyp als `CStringT` Objekt.|

> [!NOTE]
> Code, der zuvor nicht `CString` dokumentierte `AssignCopy`Methoden von (z. B. ) verwendet `CStringT` hat, `GetBuffer` `ReleaseBuffer`muss durch Code ersetzt werden, der die folgenden dokumentierten Methoden von (z. B. oder ) verwendet. Diese Methoden werden `CSimpleStringT`von geerbt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>Requirements (Anforderungen)

|Header|Zweck|
|------------|-------------|
|cstringt.h|Nur MFC-Zeichenfolgenobjekte|
|atlstr.h|Nicht-MFC-Zeichenfolgenobjekte|

## <a name="cstringtallocsysstring"></a><a name="allocsysstring"></a>CStringT::AllocSysString

Ordnet eine Automation-kompatible Zeichenfolge vom Typ BSTR zu `CStringT` und kopiert den Inhalt des Objekts darin, einschließlich des beendenden Nullzeichens.

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>Rückgabewert

Die neu zugewiesene Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

In MFC-Programmen wird eine [CMemoryException-Klasse](../../mfc/reference/cmemoryexception-class.md) ausgelöst, wenn nicht genügend Arbeitsspeicher vorhanden ist. In ATL-Programmen wird eine [CAtlException](../../atl/reference/catlexception-class.md) ausgelöst. Diese Funktion wird normalerweise verwendet, um Zeichenfolgen für Automation zurückzugeben.

Wenn diese Zeichenfolge häufig als [in]-Parameter an eine COM-Funktion übergeben wird, muss der Aufrufer die Zeichenfolge freimachen. Dies kann mithilfe von [SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)erfolgen, wie im Windows SDK beschrieben. Weitere Informationen finden Sie unter [Zuweisen und Freigeben von Speicher für einen BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).

Weitere Informationen zu OLE-Zuweisungsfunktionen in Windows finden Sie unter [SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) im Windows SDK.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CStringT::AllocSysString`.

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

## <a name="cstringtansitooem"></a><a name="ansitooem"></a>CStringT::AnsiToOem

Konvertiert alle Zeichen in `CStringT` diesem Objekt aus dem ANSI-Zeichensatz in den OEM-Zeichensatz.

```cpp
void AnsiToOem();
```

### <a name="remarks"></a>Bemerkungen

Die Funktion ist nicht verfügbar, wenn _UNICODE definiert ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

## <a name="cstringtappendformat"></a><a name="appendformat"></a>CStringT::AppendFormat

Fügt formatierte Daten an `CStringT` ein vorhandenes Objekt an.

```cpp
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>Parameter

*pszFormat*<br/>
Eine Formatsteuerungszeichenfolge.

*nFormatID*<br/>
Der Zeichenfolgenressourcenbezeichner, der die Formatsteuerungszeichenfolge enthält.

*Argument*<br/>
Optionale Argumente.

### <a name="remarks"></a>Bemerkungen

Diese Funktion formatiert und fügt eine Reihe `CStringT`von Zeichen und Werten im an. Jedes optionale Argument (falls vorhanden) wird entsprechend der entsprechenden Formatspezifikation in *pszFormat* oder aus der zeichenfolgen Ressource konvertiert und angehängt, die von *nFormatID*identifiziert wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

## <a name="cstringtcollate"></a><a name="collate"></a>CStringT::Collate

Vergleicht zwei Zeichenfolgen mit `_tcscoll`der Generic-Text-Funktion .

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parameter

*Psz*<br/>
Die andere Zeichenfolge, die zum Vergleich verwendet wird.

### <a name="return-value"></a>Rückgabewert

Null, wenn die Zeichenfolgen identisch `CStringT` sind, < 0, wenn dieses `CStringT` Objekt kleiner als *psz*ist, oder > 0, wenn dieses Objekt größer als *psz*ist.

### <a name="remarks"></a>Bemerkungen

Die generische Textfunktion `_tcscoll`, die in TCHAR definiert ist. H, ordnet `strcoll`entweder `wcscoll`, `_mbscoll`oder , in Abhängigkeit von dem Zeichensatz, der zur Kompilierungszeit definiert wird. Jede Funktion führt einen Groß-/Kleinschreibungsvergleich der Zeichenfolgen gemäß der derzeit verwendenden Codepage durch. Weitere Informationen finden Sie unter [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

## <a name="cstringtcollatenocase"></a><a name="collatenocase"></a>CStringT::CollateNoCase

Vergleicht zwei Zeichenfolgen mit `_tcscoll`der Generic-Text-Funktion .

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parameter

*Psz*<br/>
Die andere Zeichenfolge, die zum Vergleich verwendet wird.

### <a name="return-value"></a>Rückgabewert

Null, wenn die Zeichenfolgen identisch sind `CStringT` (Ignorieren der Groß-/Kleinschreibung), < 0, wenn dieses Objekt kleiner als *psz* ist (Ignorieren der Fall) oder > 0, wenn dieses `CStringT` Objekt größer als *psz* ist (Fall ignorieren).

### <a name="remarks"></a>Bemerkungen

Die generische Textfunktion `_tcscoll`, die in TCHAR definiert ist. H, ordnet `stricoll`entweder `wcsicoll`, `_mbsicoll`oder , in Abhängigkeit von dem Zeichensatz, der zur Kompilierungszeit definiert wird. Jede Funktion führt einen Vergleich der Zeichenfolgen nach Groß-/Kleinschreibung gemäß der derzeit in Verwendung befindlichen Codepage durch. Weitere Informationen finden Sie unter [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

## <a name="cstringtcompare"></a><a name="compare"></a>CStringT::Vergleichen

Vergleicht zwei Zeichenfolgen (Groß-/Kleinschreibung).

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>Parameter

*Psz*<br/>
Die andere Zeichenfolge, die zum Vergleich verwendet wird.

### <a name="return-value"></a>Rückgabewert

Null, wenn die Zeichenfolgen identisch `CStringT` sind, < 0, wenn dieses `CStringT` Objekt kleiner als *psz*ist, oder > 0, wenn dieses Objekt größer als *psz*ist.

### <a name="remarks"></a>Bemerkungen

Die generische Textfunktion `_tcscmp`, die in TCHAR definiert ist. H, ordnet `strcmp`entweder `wcscmp`, `_mbscmp`oder , in Abhängigkeit von dem Zeichensatz, der zur Kompilierungszeit definiert wird. Jede Funktion führt einen Groß-/Kleinschreibungsvergleich der Zeichenfolgen durch und ist nicht vom Gebietsschema betroffen. Weitere Informationen finden Sie unter [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md).

Wenn die Zeichenfolge eingebettete NULLs enthält, wird die Zeichenfolge zum Vergleich beim ersten eingebetteten Nullzeichen als abgeschnitten betrachtet.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CStringT::Compare`.

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

## <a name="cstringtcomparenocase"></a><a name="comparenocase"></a>CStringT::CompareNoCase

Vergleicht zwei Zeichenfolgen (inderinsensitive Groß-/Kleinschreibung).

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parameter

*Psz*<br/>
Die andere Zeichenfolge, die zum Vergleich verwendet wird.

### <a name="return-value"></a>Rückgabewert

Null, wenn die Zeichenfolgen identisch sind `CStringT` (Fall ignorieren), <0, wenn dieses `CStringT` Objekt kleiner als *psz* ist (Fall ignorieren) oder >0, wenn dieses Objekt größer als *psz* ist (Fall ignorieren).

### <a name="remarks"></a>Bemerkungen

Die generische Textfunktion `_tcsicmp`, die in TCHAR definiert ist. H, ordnet `_stricmp`entweder `_wcsicmp` `_mbsicmp`zu , oder , abhängig von dem Zeichensatz, der zur Kompilierungszeit definiert wird. Jede Funktion führt einen Vergleich der Zeichenfolgen durch, bei dem die Groß-/Kleinschreibung nicht berücksichtigt wird. Der Vergleich hängt vom LC_CTYPE Aspekt des Gebietsschemas ab, aber nicht vom LC_COLLATE. Weitere Informationen finden Sie unter [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

## <a name="cstringtcstringt"></a><a name="cstringt"></a>CStringT::CStringT

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

*Pch*<br/>
Ein Zeiger auf ein Array von Zeichen der Länge *nLength*, nicht null-beendet.

*nLänge*<br/>
Eine Anzahl der Zeichen in *pch*.

*Ch*<br/>
Ein einzelnes Zeichen.

*pszSrc*<br/>
Eine null-terminierte Zeichenfolge, die `CStringT` in dieses Objekt kopiert werden soll.

*pStringMgr*<br/>
Ein Zeiger auf den Speicher-Manager für das `CStringT` Objekt. Weitere Informationen `IAtlStringMgr` zu und `CStringT`Speicherverwaltung für finden Sie unter [Speicherverwaltung mit CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

*strSrc*<br/>
Ein `CStringT` vorhandenes Objekt, `CStringT` das in dieses Objekt kopiert werden soll. Weitere Informationen `CThisString` zu `CThisSimpleString`und finden Sie im Abschnitt "Bemerkungen".

*varSrc*<br/>
Ein Variantenobjekt, das `CStringT` in dieses Objekt kopiert werden soll.

*BaseType*<br/>
Der Zeichentyp der Zeichenfolgenklasse. Dabei kann es sich um eine der folgenden Methoden handeln:

**char** (für ANSI-Zeichenfolgen).

**wchar_t** (für Unicode-Zeichenfolgen).

TCHAR (für ANSI- und Unicode-Zeichenfolgen).

*bMFCDLL*<br/>
Boolesche, die angibt, ob es sich bei dem Projekt um eine MFC-DLL (TRUE) handelt oder nicht (FALSE).

*SystemString*<br/>
Muss `System::String`sein, und das Projekt muss mit /clr kompiliert werden.

*pString*<br/>
Ein Handle `CStringT` für ein Objekt.

### <a name="remarks"></a>Bemerkungen

Da die Konstruktoren die Eingabedaten in neuen zugewiesenen Speicher kopieren, sollten Sie sich bewusst sein, dass Speicherausnahmen auftreten können. Beachten Sie, dass einige dieser Konstruktoren als Konvertierungsfunktionen fungieren. Auf diese Weise können Sie z. B. `CStringT` einen LPTSTR ersetzen, bei dem ein Objekt erwartet wird.

- `CStringT`( `LPCSTR` `lpsz` ): Erstellt einen `CStringT` Unicode aus einer ANSI-Zeichenfolge. Sie können diesen Konstruktor auch verwenden, um eine Zeichenfolgenressource zu laden, wie im folgenden Beispiel gezeigt.

- `CStringT(`): Erstellt `CStringT` a aus einer Unicode-Zeichenfolge. `LPCWSTR` `lpsz`

- `CStringT`( `const unsigned char*` `psz` ): Ermöglicht das `CStringT` Erstellen eines von einem Zeiger auf **nicht signiertes Zeichen**.

> [!NOTE]
> Definieren Sie das _CSTRING_DISABLE_NARROW_WIDE_CONVERSION Makros, um die implizite Zeichenfolgenkonvertierung zwischen ANSI- und Unicode-Zeichenfolgen zu deaktivieren. Das Makro schließt kompilierungskonstruktoren aus, die die Konvertierung unterstützen.

Beachten Sie, dass der *strSrc-Parameter* entweder ein `CStringT` oder `CThisSimpleString` ein Objekt sein kann. Verwenden `CStringT`Sie für eine der Standardinstanziierungen (`CString`, `CStringA`, oder `CStringW`); verwenden `CThisSimpleString`Sie für einen **dieser** Zeiger. `CThisSimpleString`deklariert eine Instanz der [CSimpleStringT-Klasse](../../atl-mfc-shared/reference/csimplestringt-class.md), die eine kleinere Zeichenfolgenklasse mit weniger integrierter Funktionalität als die `CStringT` Klasse ist.

Der Überladungsoperator `CSimpleStringT<>&()` `CStringT` erstellt ein `CSimpleStringT` Objekt aus einer Deklaration.

> [!NOTE]
> Obwohl es möglich `CStringT` ist, Instanzen zu erstellen, die eingebettete Nullzeichen enthalten, wird empfohlen. Aufrufen von Methoden `CStringT` und Operatoren für Objekte, die eingebettete Nullzeichen enthalten, können unbeabsichtigte Ergebnisse erzeugen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

## <a name="cstringtcstringt"></a><a name="_dtorcstringt"></a>CStringT::-CStringT

Zerstört das `CStringT`-Objekt.

```
~CStringT() throw();
```

### <a name="remarks"></a>Bemerkungen

Zerstört das `CStringT`-Objekt.

## <a name="cstringtdelete"></a><a name="delete"></a>CStringT::Delete

Löscht ein Zeichen oder Zeichen aus einer Zeichenfolge, die mit dem Zeichen am angegebenen Index beginnt.

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
Der nullbasierte Index des ersten `CStringT` zu löschenden Zeichens im zu löschenden Objekt.

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

## <a name="cstringtfind"></a><a name="find"></a>CStringT::Suchen

Durchsucht diese Zeichenfolge nach der ersten Übereinstimmung eines Zeichens oder einer Teilzeichenfolge.

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>Parameter

*pszSub*<br/>
Eine Teilzeichenfolge, nach der gesucht werden soll.

*iStart*<br/>
Der Index des Zeichens in der Zeichenfolge, mit dem die Suche beginnen soll, oder 0, um von Anfang an zu beginnen.

*Ch*<br/>
Ein einzelnes Zeichen, nach dem gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index des ersten `CStringT` Zeichens in diesem Objekt, das mit der angeforderten Teilzeichenfolge oder den angeforderten Zeichen übereinstimmt; -1, wenn die Teilzeichenfolge oder das Zeichen nicht gefunden wird.

### <a name="remarks"></a>Bemerkungen

Die Funktion ist überladen, um sowohl einzelne Zeichen `strchr`(ähnlich der Laufzeitfunktion) als auch Zeichenfolgen (ähnlich `strstr`) zu akzeptieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

## <a name="cstringtfindoneof"></a><a name="findoneof"></a>CstringT::FindOneVon

Durchsucht diese Zeichenfolge nach dem ersten Zeichen, das mit einem beliebigen Zeichen übereinstimmt, das in *pszCharSet*enthalten ist.

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>Parameter

*pszCharSet*<br/>
Zeichenfolge, die Zeichen zum Abgleichen enthält.

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index des ersten Zeichens in dieser Zeichenfolge, die sich ebenfalls in *pszCharSet*befindet; -1, wenn keine Übereinstimmung vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Sucht das erste Vorkommen eines der Zeichen in *pszCharSet*.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

## <a name="cstringtformat"></a><a name="format"></a>CStringT::Format

Schreibt formatierte Daten `CStringT` auf die gleiche Weise, wie [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) Daten in ein Zeichenarray im C-Stil formatiert.

```cpp
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>Parameter

*nFormatID*<br/>
Der Zeichenfolgenressourcenbezeichner, der die Formatsteuerungszeichenfolge enthält.

*pszFormat*<br/>
Eine Formatsteuerungszeichenfolge.

*Argument*<br/>
Optionale Argumente.

### <a name="remarks"></a>Bemerkungen

Diese Funktion formatiert und speichert eine `CStringT`Reihe von Zeichen und Werten im . Jedes optionale Argument (falls vorhanden) wird entsprechend der entsprechenden Formatspezifikation in *pszFormat* oder aus der zeichenfolgen Ressource, die von *nFormatID*identifiziert wird, konvertiert und ausgegeben.

Der Aufruf schlägt fehl, wenn das Zeichenfolgenobjekt selbst als Parameter für `Format`angeboten wird. Der folgende Code führt z. B. zu unvorhersehbaren Ergebnissen:

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

Weitere Informationen finden Sie unter [Format Specification Syntax: printf and wprintf Functions (Syntax der Formatangabe: printf- und wprintf-Funktionen)](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

## <a name="cstringtformatmessage"></a><a name="formatmessage"></a>CStringT::FormatMessage

Formatiert eine Nachrichtenzeichenfolge.

```cpp
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>Parameter

*nFormatID*<br/>
Der Zeichenfolgenressourcenbezeichner, der den unformatierten Nachrichtentext enthält.

*pszFormat*<br/>
Zeigt auf die Formatsteuerungszeichenfolge. Es wird auf Einfügungen gescannt und entsprechend formatiert. Die Formatzeichenfolge ähnelt der Laufzeitfunktion printf-style-Formatzeichenfolgen, außer sie ermöglicht das Einfügen der Parameter in beliebiger Reihenfolge. *printf*

*Argument*<br/>
Optionale Argumente.

### <a name="remarks"></a>Bemerkungen

Die Funktion erfordert eine Nachrichtendefinition als Eingabe. Die Nachrichtendefinition wird durch *pszFormat* oder aus der Zeichenfolgenressource bestimmt, die von *nFormatID*identifiziert wird. Die Funktion kopiert den formatierten `CStringT` Nachrichtentext in das Objekt und verarbeitet auf Wunsch alle eingebetteten Einfügesequenzen.

> [!NOTE]
> `FormatMessage`versucht, systemspeicher für die neu formatierte Zeichenfolge zuzuweisen. Wenn dieser Versuch fehlschlägt, wird automatisch eine Speicherausnahme ausgelöst.

Jede Einfügung muss über einen entsprechenden Parameter verfügen, der dem Parameter *pszFormat* oder *nFormatID* folgt. Innerhalb des Nachrichtentextes werden mehrere Escapesequenzen unterstützt, um die Nachricht dynamisch zu formatieren. Weitere Informationen finden Sie unter die Windows [FormatMessage-Funktion](/windows/win32/api/winbase/nf-winbase-formatmessage) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

## <a name="cstringtformatmessagev"></a><a name="formatmessagev"></a>CStringT::FormatMessageV

Formatiert eine Nachrichtenzeichenfolge mithilfe einer Variablenargumentliste.

```cpp
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>Parameter

*pszFormat*<br/>
Zeigt auf die Formatsteuerungszeichenfolge. Es wird auf Einfügungen gescannt und entsprechend formatiert. Die Formatzeichenfolge ähnelt Laufzeitfunktion `printf`-style-Formatzeichenfolgen, außer sie ermöglicht das Einfügen der Parameter in beliebiger Reihenfolge.

*pArgList*<br/>
Zeiger auf eine Liste von Argumenten.

### <a name="remarks"></a>Bemerkungen

Die Funktion erfordert eine Nachrichtendefinition als Eingabe, die von *pszFormat*bestimmt wird. Die Funktion kopiert den formatierten Nachrichtentext und `CStringT` eine Variablenliste von Argumenten in das Objekt und verarbeitet auf Wunsch alle eingebetteten Einfügesequenzen.

> [!NOTE]
> `FormatMessageV`ruft [CStringT::FormatMessage](#formatmessage)auf, das versucht, Systemspeicher für die neu formatierte Zeichenfolge zuzuweisen. Wenn dieser Versuch fehlschlägt, wird automatisch eine Speicherausnahme ausgelöst.

Weitere Informationen finden Sie unter die Windows [FormatMessage-Funktion](/windows/win32/api/winbase/nf-winbase-formatmessage) im Windows SDK.

## <a name="cstringtformatv"></a><a name="formatv"></a>CStringT::FormatV

Formatiert eine Nachrichtenzeichenfolge mithilfe einer Variablenargumentliste.

```cpp
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>Parameter

*pszFormat*<br/>
Zeigt auf die Formatsteuerungszeichenfolge. Es wird auf Einfügungen gescannt und entsprechend formatiert. Die Formatzeichenfolge ähnelt Laufzeitfunktion `printf`-style-Formatzeichenfolgen, außer sie ermöglicht das Einfügen der Parameter in beliebiger Reihenfolge.

*args*<br/>
Zeiger auf eine Liste von Argumenten.

### <a name="remarks"></a>Bemerkungen

Schreibt eine formatierte Zeichenfolge und eine `CStringT` Variablenliste von Argumenten in eine Zeichenfolge auf die gleiche Weise, wie `vsprintf_s` Daten in ein Zeichenarray im C-Stil formatiert werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

## <a name="cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a>CStringT::GetEnvironmentVariable

Legt die Zeichenfolge auf den Wert der angegebenen Umgebungsvariablen fest.

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>Parameter

*pszVar*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die die Umgebungsvariable angibt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Ruft den Wert der angegebenen Variablen aus dem Umgebungsblock des aufrufenden Prozesses ab. Der Wert hat die Form einer null-terminierten Zeichenfolge.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

## <a name="cstringtinsert"></a><a name="insert"></a>CStringT::Einfügen

Fügt ein einzelnes Zeichen oder eine Teilzeichenfolge am angegebenen Index innerhalb der Zeichenfolge ein.

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
Der Index des Zeichens, vor dem die Einfügung stattfindet.

*Psz*<br/>
Ein Zeiger auf die Teilzeichenfolge, die eingefügt werden soll.

*Ch*<br/>
Das einzufügende Zeichen.

### <a name="return-value"></a>Rückgabewert

Die Länge der geänderten Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Der *iIndex-Parameter* identifiziert das erste Zeichen, das verschoben wird, um Platz für das Zeichen oder die Teilzeichenfolge zu schaffen. Wenn *nIndex* Null ist, erfolgt die Einfügung vor der gesamten Zeichenfolge. Wenn *nIndex* höher als die Länge der Zeichenfolge ist, verkettet die Funktion die aktuelle Zeichenfolge und das neue Material, das von *ch* oder *psz*bereitgestellt wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

## <a name="cstringtleft"></a><a name="left"></a>CStringT::Links

Extrahiert die linkshöchsten *nCount-Zeichen* aus diesem `CStringT` Objekt und gibt eine Kopie der extrahierten Teilzeichenfolge zurück.

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>Parameter

*nCount*<br/>
Die Anzahl der aus diesem `CStringT`-Objekt zu extrahierenden Zeichen.

### <a name="return-value"></a>Rückgabewert

Ein `CStringT`-Objekt, das eine Kopie des angegebenen Zeichenbereichs enthält. Das zurückgegebene `CStringT`-Objekt ist ggf. leer.

### <a name="remarks"></a>Bemerkungen

Wenn *nCount* die Zeichenfolgenlänge überschreitet, wird die gesamte Zeichenfolge extrahiert. `Left` ähnelt der `Left`-Funktion von ///Visual Basic.

Bei Multi-Byte-Zeichensätzen (MBCS) behandelt *nCount* jede 8-Bit-Sequenz als Zeichen, sodass *nCount* die Anzahl der Multi-Byte-Zeichen multipliziert mit zwei zurückgibt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

## <a name="cstringtloadstring"></a><a name="loadstring"></a>CStringT::LoadString

Liest eine Windows-Zeichenfolgenressource, die durch `CStringT` *nID*identifiziert wird, in ein vorhandenes Objekt.

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>Parameter

*hInstance*<br/>
Ein Handle für die Instanz des Moduls.

*nID*<br/>
Eine Windows-Zeichenfolgenressourcen-ID.

*wLanguageID*<br/>
Die Sprache der Zeichenfolgenressource.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Ressourcenlast erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Lädt die Zeichenfolgenressource (*nID*) aus dem angegebenen Modul (*hInstance*) mit der angegebenen Sprache (*wLanguage*).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

## <a name="cstringtmakelower"></a><a name="makelower"></a>CStringT::MakeLower

Konvertiert das `CStringT` Objekt in eine Zeichenfolge in Kleinbuchstaben.

```
CStringT& MakeLower();
```

### <a name="return-value"></a>Rückgabewert

Die resultierende Kleinbuchstabenzeichenfolge.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

## <a name="cstringtmakereverse"></a><a name="makereverse"></a>CStringT::MakeReverse

Kehrt die Reihenfolge der Zeichen `CStringT` im Objekt um.

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>Rückgabewert

Die resultierende umgekehrte Zeichenfolge.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

## <a name="cstringtmakeupper"></a><a name="makeupper"></a>CStringT::MakeUpper

Konvertiert das `CStringT` Objekt in eine Großbuchstabenzeichenfolge.

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>Rückgabewert

Die resultierende Großbuchstabenzeichenfolge.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

## <a name="cstringtmid"></a><a name="mid"></a>CStringT::Mitte

Extrahiert eine Teilzeichenfolge mit *nCount-Zeichen* der Länge aus diesem `CStringT` Objekt, beginnend an position *iFirst* (nullbasiert).

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>Parameter

*iFirst*<br/>
Der nullbasierte Index des ersten `CStringT` Zeichens in diesem Objekt, das in die extrahierte Teilzeichenfolge aufgenommen werden soll.

*nCount*<br/>
Die Anzahl der aus diesem `CStringT`-Objekt zu extrahierenden Zeichen. Wenn dieser Parameter nicht angegeben wird, wird der Rest der Zeichenfolge extrahiert.

### <a name="return-value"></a>Rückgabewert

Ein `CStringT`-Objekt, das eine Kopie des angegebenen Zeichenbereichs enthält. Beachten Sie, `CStringT` dass das zurückgegebene Objekt möglicherweise leer ist.

### <a name="remarks"></a>Bemerkungen

Die Funktion gibt eine Kopie der extrahierten Teilzeichenfolge zurück. `Mid`ist ähnlich wie die Basic Mid-Funktion (mit der Ausnahme, dass Indizes in Basic einbasiert sind).

Bei Multibyte-Zeichensätzen (MBCS) bezieht sich *nCount* auf jedes 8-Bit-Zeichen. Das heißt, ein Lead- und Trailbyte in einem Multibyte-Zeichen werden als zwei Zeichen gezählt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

## <a name="cstringtoemtoansi"></a><a name="oemtoansi"></a>CStringT::OemToAnsi

Konvertiert alle Zeichen in `CStringT` diesem Objekt aus dem OEM-Zeichensatz in den ANSI-Zeichensatz.

```cpp
void OemToAnsi();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist nicht verfügbar, wenn _UNICODE definiert ist.

### <a name="example"></a>Beispiel

Siehe beispielfür [CStringT::AnsiToOem](#ansitooem).

## <a name="cstringtoperator-"></a><a name="operator_eq"></a>CStringT::operator =

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

*strSrc*<br/>
A, `CStringT` das dieser Zeichenfolge zugewiesen werden soll.

*Str*<br/>
Ein Verweis auf ein `CThisSimpleString`-Objekt.

*bMFCDLL*<br/>
Ein boolescher Wert, der angibt, ob es sich bei dem Projekt um eine MFC-DLL handelt oder nicht.

*BaseType*<br/>
Der Zeichenfolgenbasistyp.

*var*<br/>
Ein Variantenobjekt, das dieser Zeichenfolge zugewiesen werden soll.

*Ch*<br/>
Ein ANSI- oder Unicode-Zeichen, das der Zeichenfolge zugewiesen werden soll.

*pszSrc*<br/>
Ein Zeiger auf die ursprüngliche Zeichenfolge, die zugewiesen wird.

### <a name="remarks"></a>Bemerkungen

Der Zuweisungsoperator `CStringT` akzeptiert ein anderes Objekt, einen Zeichenzeiger oder ein einzelnes Zeichen. Sie sollten sich bewusst sein, dass Speicherausnahmen auftreten können, wenn Sie diesen Operator verwenden, da neuer Speicher zugewiesen werden kann.

Weitere Informationen `CThisSimpleString`finden Sie im Abschnitt "Hinweise" von [CStringT::CStringT](#cstringt).

> [!NOTE]
> Obwohl es möglich `CStringT` ist, Instanzen zu erstellen, die eingebettete Nullzeichen enthalten, wird empfohlen. Aufrufen von Methoden `CStringT` und Operatoren für Objekte, die eingebettete Nullzeichen enthalten, können unbeabsichtigte Ergebnisse erzeugen.

## <a name="cstringtoperator-"></a><a name="operator_add"></a>CStringT::Operator +

Vergibt zwei Zeichenfolgen oder ein Zeichen und eine Zeichenfolge.

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
Ein ANSI- oder Unicode-Zeichen, das mit einer Zeichenfolge verkettet werden soll.

*ch2*<br/>
Ein ANSI- oder Unicode-Zeichen, das mit einer Zeichenfolge verkettet werden soll.

*str1*<br/>
A, `CStringT` um sie mit einer Zeichenfolge oder einem Zeichen zu verketten.

*str2*<br/>
A, `CStringT` um sie mit einer Zeichenfolge oder einem Zeichen zu verketten.

*psz1*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge, die mit einer Zeichenfolge oder einem Zeichen verkettet werden soll.

*psz2*<br/>
Ein Zeiger auf eine Zeichenfolge, die mit einer Zeichenfolge oder einem Zeichen verkettet werden soll.

### <a name="remarks"></a>Bemerkungen

Es gibt sieben Überlastformen der `CStringT::operator+` Funktion. Die erste Version verkettet `CStringT` zwei vorhandene Objekte. Die nächsten beiden verketten ein `CStringT` Objekt und eine null-terminierte Zeichenfolge. Die nächsten beiden verketten ein `CStringT` Objekt und ein ANSI-Zeichen. Die letzten beiden verketten ein `CStringT` Objekt und ein Unicode-Zeichen.

> [!NOTE]
> Obwohl es möglich `CStringT` ist, Instanzen zu erstellen, die eingebettete Nullzeichen enthalten, wird empfohlen. Aufrufen von Methoden `CStringT` und Operatoren für Objekte, die eingebettete Nullzeichen enthalten, können unbeabsichtigte Ergebnisse erzeugen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_add_eq"></a>CStringT::Operator +=

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

*Str*<br/>
Ein Verweis auf ein `CThisSimpleString`-Objekt.

*bMFCDLL*<br/>
Ein boolescher Wert, der angibt, ob es sich bei dem Projekt um eine MFC-DLL handelt oder nicht.

*BaseType*<br/>
Der Zeichenfolgenbasistyp.

*var*<br/>
Ein Variantenobjekt, das mit dieser Zeichenfolge verkettet werden soll.

*Ch*<br/>
Ein ANSI- oder Unicode-Zeichen, das mit einer Zeichenfolge verkettet werden soll.

*pszSrc*<br/>
Ein Zeiger auf die ursprüngliche Zeichenfolge, die verkettet wird.

*strSrc*<br/>
A, `CStringT` um diese Zeichenfolge zu verketten.

### <a name="remarks"></a>Bemerkungen

Der Operator `CStringT` akzeptiert ein anderes Objekt, einen Zeichenzeiger oder ein einzelnes Zeichen. Sie sollten sich bewusst sein, dass Speicherausnahmen auftreten können, wenn Sie diesen Verkettungsoperator verwenden, da neuer Speicher für Zeichen zugewiesen werden kann, die diesem `CStringT` Objekt hinzugefügt wurden.

Weitere Informationen `CThisSimpleString`finden Sie im Abschnitt "Hinweise" von [CStringT::CStringT](#cstringt).

> [!NOTE]
> Obwohl es möglich `CStringT` ist, Instanzen zu erstellen, die eingebettete Nullzeichen enthalten, wird empfohlen. Aufrufen von Methoden `CStringT` und Operatoren für Objekte, die eingebettete Nullzeichen enthalten, können unbeabsichtigte Ergebnisse erzeugen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_eq_eq"></a>CStringT::operator ==

Bestimmt, ob zwei Zeichenfolgen logisch gleich sind.

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
Ein ANSI- oder Unicode-Zeichen zum Vergleich.

*ch2*<br/>
Ein ANSI- oder Unicode-Zeichen zum Vergleich.

*str1*<br/>
Ein `CStringT` Vergleich.

*str2*<br/>
Ein `CStringT` Vergleich.

*psz1*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge zum Vergleich.

*psz2*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge zum Vergleich.

### <a name="remarks"></a>Bemerkungen

Testet, ob eine Zeichenfolge oder ein Zeichen auf der linken Seite einer Zeichenfolge oder einem Zeichen auf der rechten Seite entspricht, und gibt TRUE oder FALSE entsprechend zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_neq"></a>CStringT::operator !=

Bestimmt, ob zwei Zeichenfolgen logisch nicht gleich sind.

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
Ein ANSI- oder Unicode-Zeichen, das mit einer Zeichenfolge verkettet werden soll.

*ch2*<br/>
Ein ANSI- oder Unicode-Zeichen, das mit einer Zeichenfolge verkettet werden soll.

*str1*<br/>
Ein `CStringT` Vergleich.

*str2*<br/>
Ein `CStringT` Vergleich.

*psz1*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge zum Vergleich.

*psz2*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge zum Vergleich.

### <a name="remarks"></a>Bemerkungen

Testet, ob eine Zeichenfolge oder ein Zeichen auf der linken Seite nicht gleich einer Zeichenfolge oder einem Zeichen auf der rechten Seite ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt"></a>CStringT::Operator&lt;

Bestimmt, ob die Zeichenfolge auf der linken Seite des Operators kleiner als die Zeichenfolge auf der rechten Seite ist.

```
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Ein `CStringT` Vergleich.

*str2*<br/>
Ein `CStringT` Vergleich.

*psz1*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge zum Vergleich.

*psz2*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge zum Vergleich.

### <a name="remarks"></a>Bemerkungen

Ein lexikographischer Vergleich zwischen Zeichenfolgen, Zeichen für Zeichen bis:

- Er zwei korrespondierende ungleiche Zeichen findet, und deren Vergleich als Ergebnis des Vergleichs zweier Zeichenfolgen genommen wird.

- Er keine Ungleichheiten findet, aber eine Zeichenfolge mehr Zeichen hat als die andere und die kürzere Zeichenfolge als kleiner als die längere Zeichenfolge betrachtet wird.

- Er keine Ungleichheiten findet und feststellt, dass die Zeichenfolgen die gleiche Anzahl von Zeichen haben und daher gleich sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt"></a>CStringT::Operator&gt;

Bestimmt, ob die Zeichenfolge auf der linken Seite des Operators größer als die Zeichenfolge auf der rechten Seite ist.

```
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Ein `CStringT` Vergleich.

*str2*<br/>
Ein `CStringT` Vergleich.

*psz1*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge zum Vergleich.

*psz2*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge zum Vergleich.

### <a name="remarks"></a>Bemerkungen

Ein lexikographischer Vergleich zwischen Zeichenfolgen, Zeichen für Zeichen bis:

- Er zwei korrespondierende ungleiche Zeichen findet, und deren Vergleich als Ergebnis des Vergleichs zweier Zeichenfolgen genommen wird.

- Er keine Ungleichheiten findet, aber eine Zeichenfolge mehr Zeichen hat als die andere und die kürzere Zeichenfolge als kleiner als die längere Zeichenfolge betrachtet wird.

- Er keine Ungleichheiten findet und feststellt, dass die Zeichenfolgen die gleiche Anzahl von Zeichen haben und daher gleich sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt_eq"></a>CStringT::Operator&lt;=

Bestimmt, ob die Zeichenfolge auf der linken Seite des Operators kleiner oder gleich der Zeichenfolge auf der rechten Seite ist.

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Ein `CStringT` Vergleich.

*str2*<br/>
Ein `CStringT` Vergleich.

*psz1*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge zum Vergleich.

*psz2*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge zum Vergleich.

### <a name="remarks"></a>Bemerkungen

Ein lexikographischer Vergleich zwischen Zeichenfolgen, Zeichen für Zeichen bis:

- Er zwei korrespondierende ungleiche Zeichen findet, und deren Vergleich als Ergebnis des Vergleichs zweier Zeichenfolgen genommen wird.

- Er keine Ungleichheiten findet, aber eine Zeichenfolge mehr Zeichen hat als die andere und die kürzere Zeichenfolge als kleiner als die längere Zeichenfolge betrachtet wird.

- Er keine Ungleichheiten findet und feststellt, dass die Zeichenfolgen die gleiche Anzahl von Zeichen haben und daher gleich sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt_eq"></a>CStringT::Operator&gt;=

Bestimmt, ob die Zeichenfolge auf der linken Seite des Operators größer oder gleich der Zeichenfolge auf der rechten Seite ist.

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Ein `CStringT` Vergleich.

*str2*<br/>
Ein `CStringT` Vergleich.

*psz1*<br/>
Ein Zeiger auf eine Zeichenfolge zum Vergleich.

*psz2*<br/>
Ein Zeiger auf eine Zeichenfolge zum Vergleich.

### <a name="remarks"></a>Bemerkungen

Ein lexikographischer Vergleich zwischen Zeichenfolgen, Zeichen für Zeichen bis:

- Er zwei korrespondierende ungleiche Zeichen findet, und deren Vergleich als Ergebnis des Vergleichs zweier Zeichenfolgen genommen wird.

- Er keine Ungleichheiten findet, aber eine Zeichenfolge mehr Zeichen hat als die andere und die kürzere Zeichenfolge als kleiner als die längere Zeichenfolge betrachtet wird.

- Er keine Ungleichheiten findet und feststellt, dass die Zeichenfolgen die gleiche Anzahl von Zeichen haben und daher gleich sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

## <a name="cstringtremove"></a><a name="remove"></a>CStringT::Entfernen

Entfernt alle Instanzen des angegebenen Zeichens aus der Zeichenfolge.

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>Parameter

*chRemove*<br/>
Das Zeichen, das aus einer Zeichenfolge entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeichen, die aus der Zeichenfolge entfernt wurden. Null, wenn die Zeichenfolge nicht geändert wird.

### <a name="remarks"></a>Bemerkungen

Bei Vergleichen für das Zeichen wird die Groß-/Kleinschreibung beachtet.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

## <a name="cstringtreplace"></a><a name="replace"></a>CStringT::Ersetzen

Es gibt zwei `Replace`Versionen von . Die erste Version ersetzt eine oder mehrere Kopien einer Teilzeichenfolge durch eine andere Teilzeichenfolge. Beide Teilzeichenfolgen sind null-beendet. Die zweite Version ersetzt eine oder mehrere Kopien eines Zeichens durch die Verwendung eines anderen Zeichens. Beide Versionen arbeiten mit den `CStringT`in gespeicherten Zeichendaten.

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>Parameter

*pszOld*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge, die durch *pszNew*ersetzt werden soll.

*pszNeu*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge, die *pszOld*ersetzt.

*chOld*<br/>
Das Zeichen, das durch *chNew*ersetzt werden soll.

*chNeue*<br/>
Das Zeichen ersetzt *chOld*.

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der ersetzten Instanzen des Zeichens oder der Teilzeichenfolge oder Null zurück, wenn die Zeichenfolge nicht geändert wird.

### <a name="remarks"></a>Bemerkungen

`Replace`kann die Zeichenfolgenlänge ändern, da *pszNew* und *pszOld* nicht die gleiche Länge haben müssen und mehrere Kopien der alten Teilzeichenfolge in die neue geändert werden können. Die Funktion führt eine Übereinstimmung mit großstder Groß-/Kleinschreibung durch.

Beispiele `CStringT` für `CString`Instanzen sind , `CStringA`und `CStringW`.

Für `CStringA` `Replace` funktioniert mit ANSI- oder Multibyte-Zeichen (MBCS). Für `CStringW` `Replace` funktioniert mit breiten Zeichen.

Für `CString`wird der Zeichendatentyp zur Kompilierungszeit ausgewählt, je nachdem, ob die Konstanten in der folgenden Tabelle definiert sind.

|Definierte Konstante|Zeichendatentyp|
|----------------------|-------------------------|
|_UNICODE|Breitzeichen|
|_MBCS|Multibyte-Zeichen|
|Neither|Single-Byte-Zeichen|
|Beide|Nicht definiert|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

## <a name="cstringtreversefind"></a><a name="reversefind"></a>CStringT::ReverseFind

Durchsucht dieses `CStringT` Objekt nach der letzten Übereinstimmung eines Zeichens.

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>Parameter

*Ch*<br/>
Das Zu suchende Zeichen.

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index des letzten `CStringT` Zeichens in diesem Objekt, das mit dem angeforderten Zeichen übereinstimmt, oder -1, wenn das Zeichen nicht gefunden wird.

### <a name="remarks"></a>Bemerkungen

Die Funktion ähnelt der Laufzeitfunktion `strrchr`.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

## <a name="cstringtright"></a><a name="right"></a>CStringT::Rechts

Extrahiert die letzten (d. h. ganz rechts) *nCount-Zeichen* aus diesem `CStringT` Objekt und gibt eine Kopie der extrahierten Teilzeichenfolge zurück.

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>Parameter

*nCount*<br/>
Die Anzahl der aus diesem `CStringT`-Objekt zu extrahierenden Zeichen.

### <a name="return-value"></a>Rückgabewert

Ein `CStringT`-Objekt, das eine Kopie des angegebenen Zeichenbereichs enthält. Beachten Sie, `CStringT` dass das zurückgegebene Objekt leer sein kann.

### <a name="remarks"></a>Bemerkungen

Wenn *nCount* die Zeichenfolgenlänge überschreitet, wird die gesamte Zeichenfolge extrahiert. `Right`ist ähnlich wie `Right` die Basic-Funktion (mit der Ausnahme, dass Indizes in Basic nullbasiert sind).

Bei Multibyte-Zeichensätzen (MBCS) bezieht sich *nCount* auf jedes 8-Bit-Zeichen. Das heißt, ein Lead- und Trailbyte in einem Multibyte-Zeichen werden als zwei Zeichen gezählt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

## <a name="cstringtsetsysstring"></a><a name="setsysstring"></a>CStringT::SetSysString

Ordnet den Von *pbstr* darauf gezeigten BSTR `CStringT` neu zu und kopiert den Inhalt des Objekts in das Objekt, einschließlich des Zeichens NULL.

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>Parameter

*pbstr*<br/>
Ein Zeiger auf eine Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Die neue Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Je nach Inhalt `CStringT` des Objekts kann sich der Wert des Von *pbstr* referenzierten BSTR ändern. Die Funktion `CMemoryException` löst eine aus, wenn nicht genügend Arbeitsspeicher vorhanden ist.

Diese Funktion wird normalerweise verwendet, um den Wert von Zeichenfolgen zu ändern, die als Verweis für Automation übergeben werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

## <a name="cstringtspanexcluding"></a><a name="spanexcluding"></a>CStringT::SpanExcluding

Extrahiert Zeichen aus der Zeichenfolge, beginnend mit dem ersten Zeichen, die nicht in dem Satz von Zeichen sind, die von *pszCharSet*identifiziert werden.

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parameter

*pszCharSet*<br/>
Eine Zeichenfolge, die als zeichensatz interpretiert wird.

### <a name="return-value"></a>Rückgabewert

Eine Teilzeichenfolge, die Zeichen in der Zeichenfolge enthält, die nicht in *pszCharSet*enthalten sind, beginnend mit dem ersten Zeichen in der Zeichenfolge und endet mit dem ersten Zeichen in der Zeichenfolge, das sich ebenfalls in *pszCharSet* befindet (d. h. beginnend mit dem ersten Zeichen in der Zeichenfolge und bis zum ersten Zeichen in der Zeichenfolge, die *pszCharSet*gefunden wird). Es gibt die gesamte Zeichenfolge zurück, wenn kein Zeichen in *pszCharSet* in der Zeichenfolge gefunden wird.

### <a name="remarks"></a>Bemerkungen

`SpanExcluding`extrahiert und gibt alle Zeichen zurück, die dem ersten Vorkommen eines Zeichens aus *pszCharSet* vorangehen (d. h. das Zeichen aus *pszCharSet* und alle Zeichen, die ihm in der Zeichenfolge folgen, werden nicht zurückgegeben). Wenn kein Zeichen aus *pszCharSet* in `SpanExcluding` der Zeichenfolge gefunden wird, gibt die gesamte Zeichenfolge zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

## <a name="cstringtspanincluding"></a><a name="spanincluding"></a>CStringT::Spanincluding

Extrahiert Zeichen aus der Zeichenfolge, beginnend mit dem ersten Zeichen, die sich in dem Satz von Zeichen befinden, die von *pszCharSet*identifiziert werden.

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parameter

*pszCharSet*<br/>
Eine Zeichenfolge, die als zeichensatz interpretiert wird.

### <a name="return-value"></a>Rückgabewert

Eine Teilzeichenfolge, die Zeichen in der Zeichenfolge in *pszCharSet*enthält, beginnend mit dem ersten Zeichen in der Zeichenfolge und endend, wenn ein Zeichen in der Zeichenfolge gefunden wird, die nicht in *pszCharSet*ist. `SpanIncluding`gibt eine leere Teilzeichenfolge zurück, wenn sich das erste Zeichen in der Zeichenfolge nicht im angegebenen Satz befindet.

### <a name="remarks"></a>Bemerkungen

Wenn sich das erste Zeichen der Zeichenfolge nicht `SpanIncluding` im Zeichensatz befindet, wird eine leere Zeichenfolge zurückgegeben. Andernfalls wird eine Folge aufeinander folgender Zeichen zurückgegeben, die sich in der Gruppe befinden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

## <a name="cstringttokenize"></a><a name="tokenize"></a>CStringT::Tokenize

Sucht das nächste Token in einer Zielzeichenfolge

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>Parameter

*pszTokens*<br/>
Eine Zeichenfolge, die Tokentrennzeichen enthält. Die Reihenfolge dieser Trennzeichen ist nicht wichtig.

*iStart*<br/>
Der nullbasierte Index, um die Suche zu starten.

### <a name="return-value"></a>Rückgabewert

Ein `CStringT` Objekt, das den aktuellen Tokenwert enthält.

### <a name="remarks"></a>Bemerkungen

Die `Tokenize` Funktion findet das nächste Token in der Zielzeichenfolge. Der Satz von Zeichen in *pszTokens* gibt mögliche Trennzeichen des zu findenden Tokens an. Bei jedem `Tokenize` Aufruf der Funktion beginnt bei *iStart*, überspringt `CStringT` führende Trennzeichen und gibt ein Objekt zurück, das das aktuelle Token enthält, d. h. die Zeichenfolge bis zum nächsten Trennzeichen. Der Wert von *iStart* wird so aktualisiert, dass er die Position nach dem Endtrennzeichen ist, oder -1, wenn das Ende der Zeichenfolge erreicht wurde. Weitere Token können aus dem Rest der Zielzeichenfolge durch eine `Tokenize`Reihe von Aufrufen von gebrochen werden, wobei *iStart* verwendet wird, um nachzuverfolgen, wo in der Zeichenfolge das nächste Token gelesen werden soll. Wenn keine Token mehr vorhanden sind, gibt die Funktion eine leere Zeichenfolge zurück und *iStart* wird auf -1 gesetzt.

Im Gegensatz zu CRT-Tokenfunktionen wie [strtok_s, ändert _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md) `Tokenize` die Zielzeichenfolge nicht.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>Bemerkungen

Die Ausgabe aus diesem Beispiel ist wie folgt:

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

## <a name="cstringttrim"></a><a name="trim"></a>CStringT::Trim

Trimmt führende und nachfolgende Zeichen aus der Zeichenfolge.

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>Parameter

*chTarget*<br/>
Das zu trimmende Zielzeichen.

*pszTargets*<br/>
Ein Zeiger auf eine Zeichenfolge, die die zu trimmenden Zielzeichen enthält. Alle führenden und nachgestellten Vorkommen von Zeichen in *pszTarget* werden aus dem `CStringT` Objekt abgeschnitten.

### <a name="return-value"></a>Rückgabewert

Gibt die getrimmte Zeichenfolge zurück.

### <a name="remarks"></a>Bemerkungen

Entfernt alle führenden und nachgestellten Vorkommen eines der folgenden Punkte:

- Das von *chTarget*angegebene Zeichen .

- Alle Zeichen in der von *pszTargets*angegebenen Zeichenfolge .

- Leerzeichen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>Bemerkungen

Die Ausgabe aus diesem Beispiel ist wie folgt:

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

## <a name="cstringttrimleft"></a><a name="trimleft"></a>CStringT::TrimLeft

Trimmt führende Zeichen aus der Zeichenfolge.

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>Parameter

*chTarget*<br/>
Das zu trimmende Zielzeichen.

*pszTargets*<br/>
Ein Zeiger auf eine Zeichenfolge, die die zu trimmenden Zielzeichen enthält. Alle führenden Vorkommen von Zeichen in *pszTarget* `CStringT` werden aus dem Objekt abgeschnitten.

### <a name="return-value"></a>Rückgabewert

Die resultierende getrimmte Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Entfernt alle führenden und nachgestellten Vorkommen eines der folgenden Punkte:

- Das von *chTarget*angegebene Zeichen .

- Alle Zeichen in der von *pszTargets*angegebenen Zeichenfolge .

- Leerzeichen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

## <a name="cstringttrimright"></a><a name="trimright"></a>CStringT::TrimRight

Trimmt nachfolgende Zeichen aus der Zeichenfolge.

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>Parameter

*chTarget*<br/>
Das zu trimmende Zielzeichen.

*pszTargets*<br/>
Ein Zeiger auf eine Zeichenfolge, die die zu trimmenden Zielzeichen enthält. Alle nachfolgenden Vorkommen von Zeichen in *pszTarget* `CStringT` werden aus dem Objekt abgeschnitten.

### <a name="return-value"></a>Rückgabewert

Gibt `CStringT` das Objekt zurück, das die getrimmte Zeichenfolge enthält.

### <a name="remarks"></a>Bemerkungen

Entfernt nachfolgende Vorkommen eines der folgenden Punkte:

- Das von *chTarget*angegebene Zeichen .

- Alle Zeichen in der von *pszTargets*angegebenen Zeichenfolge .

- Leerzeichen.

Die `CStringT& TrimRight(XCHAR chTarget)` Version akzeptiert einen Zeichenparameter und entfernt alle Kopien `CStringT` dieses Zeichens vom Ende der Zeichenfolgendaten. Es beginnt am Ende der Saite und arbeitet nach vorne. Es stoppt, wenn ein anderes `CSTringT` Zeichen gefunden wird oder wenn keine Zeichendaten mehr enthalten sind.

Die `CStringT& TrimRight(PCXSTR pszTargets)` Version akzeptiert eine null-terminierte Zeichenfolge, die alle verschiedenen Zeichen enthält, nach denen gesucht werden soll. Es werden alle Kopien dieser `CStringT` Zeichen im Objekt entfernt. Es beginnt am Ende der Saite und arbeitet nach vorne. Es wird beendet, wenn ein Zeichen gefunden wird, `CStringT` das sich nicht in der Zielzeichenfolge befindet, oder wenn keine Zeichendaten mehr zur Seite stehen. Es wird nicht versucht, die gesamte Zielzeichenfolge mit `CStringT`einer Teilzeichenfolge am Ende von abzugleichen.

Die `CStringT& TrimRight()` Version erfordert keine Parameter. Es schneidet alle nachfolgenden Leerzeichen vom `CStringT` Ende der Zeichenfolge. Leerzeichen können Zeilenumbrüche, Leerzeichen oder Tabstopps sein.

-

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[FREIGEGEBENe ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[CSimpleStringT-Klasse](../../atl-mfc-shared/reference/csimplestringt-class.md)
