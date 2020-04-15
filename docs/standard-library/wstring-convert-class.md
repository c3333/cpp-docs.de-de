---
title: wstring_convert-Klasse
ms.date: 11/04/2016
f1_keywords:
- wstring/stdext::cvt::wstring_convert
- locale/std::wstring_convert::byte_string
- locale/std::wstring_convert::wide_string
- locale/std::wstring_convert::state_type
- locale/std::wstring_convert::int_type
- locale/std::wstring_convert::from_bytes
- locale/std::wstring_convert::to_bytes
- locale/std::wstring_convert::converted
- locale/std::wstring_convert::state
helpviewer_keywords:
- stdext::cvt [C++], wstring_convert
- std::wstring_convert [C++], byte_string
- std::wstring_convert [C++], wide_string
- std::wstring_convert [C++], state_type
- std::wstring_convert [C++], int_type
- std::wstring_convert [C++], from_bytes
- std::wstring_convert [C++], to_bytes
- std::wstring_convert [C++], converted
- std::wstring_convert [C++], state
ms.assetid: e34f5b65-d572-4bdc-ac69-20778712e376
ms.openlocfilehash: f09f12d9100e9faad849de608a9124f457da23df
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366367"
---
# <a name="wstring_convert-class"></a>wstring_convert-Klasse

Die Klassenvorlage `wstring_convert` führt Konvertierungen zwischen einer breiten Zeichenfolge und einer Bytezeichenfolge durch.

## <a name="syntax"></a>Syntax

```cpp
template <class Codecvt, class Elem = wchar_t>
class wstring_convert
```

### <a name="parameters"></a>Parameter

*Codecvt*\
Das Facet [locale](../standard-library/locale-class.md), das das Konvertierungsobjekt darstellt.

*Elem*\
Der Breitzeichen-Elementtyp.

## <a name="remarks"></a>Bemerkungen

Die Klassenvorlage beschreibt ein Objekt, das Konvertierungen `std::basic_string<Elem>` zwischen breiten Zeichenfolgenobjekten der Klasse und Bytezeichenfolgenobjekten der Klasse `std::basic_string<char>` (auch bekannt als `std::string`) steuert. Die Klassenvorlage definiert `wide_string` die `byte_string` Typen und als Synonyme für diese beiden Typen. Konvertierung zwischen einer Sequenz von `Elem`-Werten (in einem `wide_string`-Objekt gespeichert) und Multibytesequenzen (in einem `byte_string`-Objekt gespeichert) erfolgt durch ein Objekt der Klasse `Codecvt<Elem, char, std::mbstate_t>`, das die Anforderungen des Facets `std::codecvt<Elem, char, std::mbstate_t>` für die Standardcodekonvertierung erfüllt.

Ein Objekt dieser Klassenvorlage wird gespeichert:

- Eine bei Fehlern anzuzeigende Bytezeichenfolge

- Eine bei Fehlern anzuzeigende breite Zeichenfolge

- Ein Zeiger auf das zugeordnete Konvertierungsobjekt (das freigegeben wird, wenn das wbuffer_convert-Objekt zerstört wird)

- Ein Konvertierungsstatusobjekt vom Typ [state_type](#state_type)

- Eine Konvertierungsanzahl

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[wstring_convert](#wstring_convert)|Konstruiert ein Objekt vom Typ `wstring_convert`.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[byte_string](#byte_string)|Ein Typ, der eine Bytezeichenfolge darstellt.|
|[wide_string](#wide_string)|Ein Typ, der eine breite Zeichenfolge darstellt.|
|[state_type](#state_type)|Ein Typ, der den Konvertierungszustand darstellt.|
|[int_type](#int_type)|Ein Typ, der eine ganze Zahl darstellt.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[from_bytes](#from_bytes)|Konvertiert eine Bytezeichenfolge in eine breite Zeichenfolge.|
|[to_bytes](#to_bytes)|Konvertiert eine breite Zeichenfolge in eine Bytezeichenfolge.|
|[converted](#converted)|Gibt die Anzahl der erfolgreichen Konvertierungen zurück.|
|[Staat](#state)|Gibt ein Objekt zurück, das den Zustand für die Konvertierung darstellt.|

## <a name="requirements"></a>Anforderungen

**Header:** \<locale>

**Namespace:** std

## <a name="wstring_convertbyte_string"></a><a name="byte_string"></a>wstring_convert::byte_string

Ein Typ, der eine Bytezeichenfolge darstellt.

```cpp
typedef std::basic_string<char> byte_string;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `std::basic_string<char>`.

## <a name="wstring_convertconverted"></a><a name="converted"></a>wstring_convert::konvertiert

Gibt die Anzahl der erfolgreichen Konvertierungen zurück.

```cpp
size_t converted() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der erfolgreichen Konvertierungen.

### <a name="remarks"></a>Bemerkungen

Die Anzahl der erfolgreichen Konvertierungen wird im Konvertierungsanzahlobjekt gespeichert.

## <a name="wstring_convertfrom_bytes"></a><a name="from_bytes"></a>wstring_convert::from_bytes

Konvertiert eine Bytezeichenfolge in eine breite Zeichenfolge.

```cpp
wide_string from_bytes(char Byte);
wide_string from_bytes(const char* ptr);
wide_string from_bytes(const byte_string& Bstr);
wide_string from_bytes(const char* first, const char* last);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*Byte*|Die zu konvertierende Einzelelement-Bytesequenz.|
|*Ptr*|Die auf NULL endende Zeichenfolge im C-Stil der zu konvertierenden Zeichen.|
|*Bstr*|Der zu konvertierende [byte_string](#byte_string).|
|*first*|Das erste Zeichen in einem Bereich von zu konvertierenden Zeichen.|
|*last*|Das letzte Zeichen in einem Bereich von zu konvertierenden Zeichen.|

### <a name="return-value"></a>Rückgabewert

Ein breites Zeichenfolgenobjekt, das sich aus der Konvertierung ergibt.

### <a name="remarks"></a>Bemerkungen

Wenn das [Konvertierungsstatusobjekt](../standard-library/wstring-convert-class.md) *nicht* mit einem expliziten Wert erstellt wurde, wird es vor Beginn der Konvertierung auf den Standardwert (den ursprünglichen Konvertierungsstatus) festgelegt. Andernfalls bleibt es unverändert.

Die Anzahl der erfolgreich konvertierten Eingabeelemente wird im Konvertierungsanzahlobjekt gespeichert. Wenn kein Konvertierungsfehler auftritt, gibt die Memberfunktion die konvertierte breite Zeichenfolge zurück. Wenn das Objekt mit einem Initialisierer für die Breitzeichen-Fehlermeldung erstellt wurde, gibt die Memberfunktion das Breitzeichen-Fehlermeldungsobjekt zurück. Andernfalls gibt die Memberfunktion ein Objekt der Klasse [range_error](../standard-library/range-error-class.md) aus.

## <a name="wstring_convertint_type"></a><a name="int_type"></a>wstring_convert::int_type

Ein Typ, der eine ganze Zahl darstellt.

```cpp
typedef typename wide_string::traits_type::int_type int_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `wide_string::traits_type::int_type`.

## <a name="wstring_convertstate"></a><a name="state"></a>wstring_convert::Zustand

Gibt ein Objekt zurück, das den Zustand für die Konvertierung darstellt.

```cpp
state_type state() const;
```

### <a name="return-value"></a>Rückgabewert

Das [Konvertierungsstatusobjekt](../standard-library/wstring-convert-class.md), das den Status der Konvertierung darstellt.

### <a name="remarks"></a>Bemerkungen

## <a name="wstring_convertstate_type"></a><a name="state_type"></a>wstring_convert::state_type

Ein Typ, der den Konvertierungszustand darstellt.

```cpp
typedef typename Codecvt::state_type state_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt, das einen Konvertierungszustand repräsentieren kann. Der Typ ist ein Synonym für `Codecvt::state_type`.

## <a name="wstring_convertto_bytes"></a><a name="to_bytes"></a>wstring_convert::to_bytes

Konvertiert eine breite Zeichenfolge in eine Bytezeichenfolge.

```cpp
byte_string to_bytes(Elem Char);
byte_string to_bytes(const Elem* Wptr);
byte_string to_bytes(const wide_string& Wstr);
byte_string to_bytes(const Elem* first, const Elem* last);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Char*|Die zu konvertierenden Breitzeichenfolgen.|
|*Wptr*|Die auf NULL endende Sequenz im C-Stil, die bei `wptr`beginnt und konvertiert werden soll.|
|*Wstr*|Die zu konvertierende Zeichenfolge vom Typ [wide_string](#wide_string).|
|*first*|Das erste Element in dem zu konvertierenden Elementbereich.|
|*last*|Das letzte Element in dem zu konvertierenden Elementbereich.|

### <a name="remarks"></a>Bemerkungen

Wenn das [Konvertierungsstatusobjekt](../standard-library/wstring-convert-class.md) *nicht* mit einem expliziten Wert erstellt wurde, wird es vor Beginn der Konvertierung auf den Standardwert (den ursprünglichen Konvertierungsstatus) festgelegt. Andernfalls bleibt es unverändert.

Die Anzahl der erfolgreich konvertierten Eingabeelemente wird im Konvertierungsanzahlobjekt gespeichert. Wenn kein Konvertierungsfehler auftritt, gibt die Memberfunktion die konvertierte Bytezeichenfolge zurück. Wenn das Objekt mit einem Initialisierer für die Bytezeichen-Fehlermeldung erstellt wurde, gibt die Memberfunktion das Bytezeichen-Fehlermeldungsobjekt zurück. Andernfalls gibt die Memberfunktion ein Objekt der Klasse [range_error](../standard-library/range-error-class.md) aus.

## <a name="wstring_convertwide_string"></a><a name="wide_string"></a>wstring_convert::wide_string

Ein Typ, der eine breite Zeichenfolge darstellt.

```cpp
typedef std::basic_string<Elem> wide_string;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `std::basic_string<Elem>`.

## <a name="wstring_convertwstring_convert"></a><a name="wstring_convert"></a>wstring_convert::wstring_convert

Konstruiert ein Objekt vom Typ `wstring_convert`.

```cpp
wstring_convert(Codecvt *Pcvt = new Codecvt);
wstring_convert(Codecvt *Pcvt, state_type _State);
wstring_convert(const byte_string& _Berr, const wide_string& Werr = wide_string());
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*\*Pcvt*|Das Objekt des `Codecvt`-Typs zum Durchführen der Konvertierung.|
|*_state*|Das Objekt vom Typ [state_type](#state_type), das den Konvertierungsstatus darstellt.|
|*_Berr*|Die bei Fehlern anzuzeigende [byte_string](#byte_string).|
|*Werr*|Die bei Fehlern anzuzeigende [wide_string](#wide_string).|

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor speichert *Pcvt_arg* im [Konvertierungsobjekt](../standard-library/wstring-convert-class.md).
