---
title: regex_constants-Klasse
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_constants
- regex/std::regex_constants::error_collate
- regex/std::regex_constants::error_ctype
- regex/std::regex_constants::error_escape
- regex/std::regex_constants::error_backref
- regex/std::regex_constants::error_brack
- regex/std::regex_constants::error_paren
- regex/std::regex_constants::error_brace
- regex/std::regex_constants::error_badbrace
- regex/std::regex_constants::error_range
- regex/std::regex_constants::error_space
- regex/std::regex_constants::error_badrepeat
- regex/std::regex_constants::error_complexity
- regex/std::regex_constants::error_stack
- regex/std::regex_constants::error_parse
- regex/std::regex_constants::error_syntax
- regex/std::regex_constants::match_default
- regex/std::regex_constants::match_not_bol
- regex/std::regex_constants::match_not_eol
- regex/std::regex_constants::match_not_bow
- regex/std::regex_constants::match_not_eow
- regex/std::regex_constants::match_any
- regex/std::regex_constants::match_not_null
- regex/std::regex_constants::match_continuous
- regex/std::regex_constants::match_prev_avail
- regex/std::regex_constants::format_default
- regex/std::regex_constants::format_sed
- regex/std::regex_constants::format_no_copy
- regex/std::regex_constants::format_first_only
- regex/std::regex_constants::ECMAScript
- regex/std::regex_constants::basic
- regex/std::regex_constants::extended
- regex/std::regex_constants::awk
- regex/std::regex_constants::grep
- regex/std::regex_constants::egrep
- regex/std::regex_constants::icase
- regex/std::regex_constants::nosubs
- regex/std::regex_constants::optimize
- regex/std::regex_constants::collate
helpviewer_keywords:
- std::regex_constants [C++]
- std::regex_constants [C++], error_collate
- std::regex_constants [C++], error_ctype
- std::regex_constants [C++], error_escape
- std::regex_constants [C++], error_backref
- std::regex_constants [C++], error_brack
- std::regex_constants [C++], error_paren
- std::regex_constants [C++], error_brace
- std::regex_constants [C++], error_badbrace
- std::regex_constants [C++], error_range
- std::regex_constants [C++], error_space
- std::regex_constants [C++], error_badrepeat
- std::regex_constants [C++], error_complexity
- std::regex_constants [C++], error_stack
- std::regex_constants [C++], error_parse
- std::regex_constants [C++], error_syntax
- std::regex_constants [C++], match_default
- std::regex_constants [C++], match_not_bol
- std::regex_constants [C++], match_not_eol
- std::regex_constants [C++], match_not_bow
- std::regex_constants [C++], match_not_eow
- std::regex_constants [C++], match_any
- std::regex_constants [C++], match_not_null
- std::regex_constants [C++], match_continuous
- std::regex_constants [C++], match_prev_avail
- std::regex_constants [C++], format_default
- std::regex_constants [C++], format_sed
- std::regex_constants [C++], format_no_copy
- std::regex_constants [C++], format_first_only
- std::regex_constants [C++], ECMAScript
- std::regex_constants [C++], basic
- std::regex_constants [C++], extended
- std::regex_constants [C++], awk
- std::regex_constants [C++], grep
- std::regex_constants [C++], egrep
- std::regex_constants [C++], icase
- std::regex_constants [C++], nosubs
- std::regex_constants [C++], optimize
- std::regex_constants [C++], collate
ms.assetid: 4a69c0ba-c46d-46e4-bd29-6f4efb805f26
ms.openlocfilehash: c8abca8109db9c781d63721b795feb01161fdb40
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425232"
---
# <a name="regex_constants-namespace"></a>regex_constants-Namespace

Namespace für Flags für reguläre Ausdrücke.

## <a name="syntax"></a>Syntax

```cpp
namespace regex_constants {
    enum syntax_option_type;
    enum match_flag_type;
    enum error_type;
}
```

## <a name="remarks"></a>Hinweise

Der Namespace `regex_constants` kapselt mehrere Flagtypen und ihre zugeordneten Flagwerte.

|||
|-|-|
|[error_type](#error_type)|Flags für die Berichterstellung bei Syntaxfehlern für reguläre Ausdrücke.|
|[match_flag_type](#match_flag_type)|Flags für Optionen zum Vergleichen regulärer Ausdrücke.|
|[syntax_option_type](#syntax_option_type)|Flags zum Auswählen von Syntaxoptionen.|

## <a name="requirements"></a>Voraussetzungen

**Header:** \<Regex >

**Namespace:** std

## <a name="error_type"></a> regex_constants::error_type

Flags für die Berichterstellung bei Syntaxfehlern für reguläre Ausdrücke.

```cpp
enum error_type
    {    // identify error
    error_collate,
    error_ctype,
    error_escape,
    error_backref,
    error_brack,
    error_paren,
    error_brace,
    error_badbrace,
    error_range,
    error_space,
    error_badrepeat,
    error_complexity,
    error_stack,
    error_parse,
    error_syntax
    };
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein enumerierter Typ, der ein Objekt beschreibt, das Fehlerflags aufnehmen kann. Die unterschiedlichen Flagwerte sind:

`error_backref`: Der Ausdruck enthielt einen ungültigen Rückverweis.

`error_badbrace`: Der Ausdruck enthielt eine ungültige Anzahl in einem {}-Ausdruck.

`error_badrepeat`: Einem Wiederholungsausdruck (in den meisten Kontexten einer von „*“, „“, „+“, „{“) wurde kein Ausdruck vorangestellt.

`error_brace`: Der Ausdruck enthielt eine nicht übereinstimmende Anzahl von „{' or '}“.

`error_brack`: Der Ausdruck enthielt eine nicht übereinstimmende Anzahl von „[' or ']“.

`error_collate`: Der Ausdruck enthielt einen ungültigen Sortierungselementnamen.

`error_complexity`: Bei einem versuchten Vergleich ist ein Fehler aufgetreten, da dieser zu komplex war.

`error_ctype`: Der Ausdruck enthielt einen ungültigen Zeichenklassennamen.

`error_escape`: Der Ausdruck enthielt eine ungültige Escapesequenz.

`error_paren`: Der Ausdruck enthielt eine nicht übereinstimmende Anzahl von „(' or ')“.

`error_parse`: Der Ausdruck konnte nicht analysiert werden.

`error_range`: Der Ausdruck enthielt einen ungültigen Zeichenbereichsbezeichner.

`error_space`: Beim Analysieren eines regulären Ausdrucks ist ein Fehler aufgetreten, da nicht ausreichend Ressourcen verfügbar waren.

`error_stack`: Bei einem versuchten Vergleich ist ein Fehler aufgetreten, da nicht ausreichend Arbeitsspeicher verfügbar war.

`error_syntax`: Beim Analysieren eines Syntaxfehler ist ein Fehler aufgetreten.

`error_backref`: Der Ausdruck enthielt einen ungültigen Rückverweis.

## <a name="match_flag_type"></a> regex_constants::match_flag_type

Flags für Optionen zum Vergleichen regulärer Ausdrücke.

```cpp
enum match_flag_type
    {    // specify matching and formatting rules
    match_default = 0x0000,
    match_not_bol = 0x0001,
    match_not_eol = 0x0002,
    match_not_bow = 0x0004,
    match_not_eow = 0x0008,
    match_any = 0x0010,
    match_not_null = 0x0020,
    match_continuous = 0x0040,
    match_prev_avail = 0x0100,
    format_default = 0x0000,
    format_sed = 0x0400,
    format_no_copy = 0x0800,
    format_first_only = 0x1000,
    _Match_not_null = 0x2000
    };
```

### <a name="remarks"></a>Hinweise

Der Typ ist eine „Bitmaske“, die Optionen für den Vergleich einer Textsequenz mit einem regulären Ausdruck und Formatflags beschreibt, die beim Ersetzen von Text verwendet werden. Optionen können mit `|`kombiniert werden.

Vergleichsoptionen:

`match_default`

`match_not_bol`: Die erste Position in der Zielsequenz nicht als Zeilenanfang behandeln.

`match_not_eol`: Die „past-the-end“-Position in der Zielsequenz nicht als Zeilenende behandeln.

`match_not_bow`: Die erste Position in der Zielsequenz nicht als Wortanfang behandeln.

`match_not_eow`: Die „past-the-end“-Position in der Zielsequenz nicht als Wortende behandeln.

`match_any`: Wenn mehr als eine Übereinstimmung möglich ist, kann jede Übereinstimmung akzeptiert werden.

`match_not_null`: Eine leere Untersequenz nicht als Übereinstimmung behandeln.

`match_continuous`: Nur am Anfang der Zielsequenz nach Übereinstimmungen suchen.

`match_prev_avail` -- `--first` ist ein gültiger Iterator. Ignorieren Sie `match_not_bol` und `match_not_bow`, falls diese festgelegt sind.

Formatflags:

`format_default`: ECMAScript-Formatierungsregeln verwenden

`format_sed`: „sed“-Formatierungsregeln verwenden

`format_no_copy`: keinen Text kopieren, der nicht mit dem regulären Ausdruck übereinstimmt

`format_first_only`: nach der ersten Übereinstimmung nicht nach weiteren Übereinstimmungen suchen

## <a name="syntax_option_type"></a> regex_constants::syntax_option_type

Flags zum Auswählen von Syntaxoptionen.

```cpp
enum syntax_option_type
    {    // specify RE syntax rules
    ECMAScript = 0x01,
    basic = 0x02,
    extended = 0x04,
    awk = 0x08,
    grep = 0x10,
    egrep = 0x20,
    _Gmask = 0x3F,

    icase = 0x0100,
    nosubs = 0x0200,
    optimize = 0x0400,
    collate = 0x0800
    };
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein Bitmaskentyp, der Sprachenspezifizierer und Syntaxmodifikatoren beschreibt, die beim Kompilieren eines regulären Ausdrucks verwendet werden sollen. Optionen können mit `|`kombiniert werden. Es darf immer nur jeweils ein Sprachenspezifizierer verwendet werden.

Es gibt folgende Sprachenspezifizierer:

`ECMAScript`: als ECMAScript kompilieren

`basic`: als BRE kompilieren

`extended`: als ERE kompilieren

`awk`: als awk kompilieren

`grep`: als grep kompilieren

`egrep`: als egrep kompilieren

Es gibt folgende Syntaxmodifikatoren:

`icase`: Beachtung der Groß-/Kleinschreibung für Übereinstimmungen aufheben

`nosubs`: die Implementierung muss die Inhalte von Erfassungsgruppen nicht nachverfolgen

`optimize`:die Implementierung muss mehr Wert auf die Geschwindigkeit der Übereinstimmung anstatt die Geschwindigkeit der Kompilierung regulärer Ausdrücke legen

`collate`: für Übereinstimmungen soll Gebietsschema beachtet werden

## <a name="see-also"></a>Siehe auch

[\<regex>](../standard-library/regex.md)\
[regex_error-Klasse](../standard-library/regex-error-class.md)\
[\<Regex-> Funktionen](../standard-library/regex-functions.md)\
[regex_iterator-Klasse](../standard-library/regex-iterator-class.md)\
[\<Regex-> Operatoren](../standard-library/regex-operators.md)\
[regex_token_iterator-Klasse](../standard-library/regex-token-iterator-class.md)\
[regex_traits-Klasse](../standard-library/regex-traits-class.md)\
[\<regex>-Typdefinitionen](../standard-library/regex-typedefs.md)
