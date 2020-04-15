---
title: Reguläre Ausdrücke (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- regular expressions [C++]
ms.assetid: aafe202a-1d96-4b36-a270-d676dfd3c51c
ms.openlocfilehash: a6ff0fafce9f4b3e029be053d27ca68d096ec108
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368526"
---
# <a name="regular-expressions-c"></a>Reguläre Ausdrücke (C++)

Die C++-Standardbibliothek unterstützt mehrere Grammatiken für reguläre Ausdrücke. In diesem Thema werden die Grammatikvariationen erläutert, die bei der Verwendung regulärer Ausdrücke verfügbar sind.

## <a name="regular-expression-grammar"></a><a name="regexgrammar"></a> Grammatik für reguläre Ausdrücke

Die zu verwendende Grammatik des regulären Ausdrucks `std::regex_constants::syntax_option_type` wird durch die Verwendung eines der Enumerationswerte angegeben. Diese Grammatiken für reguläre Ausdrücke sind in std::regex_constants definiert:

- `ECMAScript`: Dies entspricht der Grammatik, die von JavaScript und den .NET-Sprachen verwendet wird.
- `basic`: PoSIX grundlegende reguläre Ausdrücke oder BRE.
- `extended`: Die POSIX erweiterte reguläre Ausdrücke oder ERE.
- `awk`: Dies ist `extended`, aber es hat zusätzliche Escapes für nicht druckende Zeichen.
- `grep`: Dies ist `basic`, aber es erlaubt auch Newline-Zeichen (''')-Zeichen, Umwechsel zu trennen.
- `egrep`: Dies ist `extended`, aber es ermöglicht auch Zeilenumleinen Zeichen, um Wechsel zu trennen.

Wenn keine Grammatik angegeben ist, `ECMAScript` wird standardmäßig angenommen. Es kann nur eine Grammatik angegeben werden.

Zusätzlich zur Grammatik können mehrere Flags angewendet werden:

- `icase`: Ignorieren Sie den Fall beim Abgleich.
- `nosubs`: Ignorieren Sie markierte Übereinstimmungen (d. h. Ausdrücke in Klammern); es werden keine Substitutionen gespeichert.
- `optimize`: Machen Sie das Matching schneller, auf kostendiesbelange Bauzeit.
- `collate`: Verwenden Sie gebietsschemasensitive Sortiersequenzen (z. B. Bereiche der Form "[a-z]").

Null oder mehr Flags können mit der Grammatik kombiniert werden, um das Verhalten des Moduls für reguläre Ausdrücke anzugeben. Wenn nur Flags `ECMAScript` angegeben werden, wird als Grammatik angenommen.

### <a name="element"></a>Element

Bei einem Element kann es sich um Folgendes handeln:

- Ein *normales Zeichen*, das dem gleichen Zeichen in der Zielsequenz entspricht.

- Ein *Platzhalterzeichen* „.“, das jedem Zeichen in der Zielsequenz außer einem Zeilenumbruch entspricht.

- Ein *Klammerausdruck* im Format "[`expr`]", das einem Zeichen oder einem Sortierreihenfolgenelement in der Zielsequenz entspricht, die ebenfalls in dem durch den Ausdruck `expr` definierten Satz enthalten ist, oder im Format "[^`expr`]", das einem Zeichen oder einem Sortierreihenfolgenelement in der Zielsequenz entspricht, die nicht in dem durch den Ausdruck `expr` definierten Satz enthalten ist.

   Der Ausdruck `expr` kann jede Kombination der folgenden Elemente enthalten:

  - Ein einzelnes Zeichen. Fügt das Zeichen dem Satz hinzu, der durch `expr` definiert wird.

  - Ein *Zeichenbereich* der`ch1`-`ch2`Form " . Fügt die Zeichen, die durch Werte im geschlossenen Bereich [`ch1`, `ch2`] dargestellt werden, dem Satz hinzu, der durch `expr` festgelegt ist.

  - Eine *Zeichenklasse* im Format "[:`name`:]". Fügt die Zeichen in der benannten Klasse dem Satz hinzu, der durch `expr` definiert wird.

  - Eine *Äkquivalenzklasse* im Format "[=`elt`=]". Fügt Sortierungselemente, die mit `elt` äquivalent sind, dem Satz hinzu, der durch `expr` definiert wird.

  - Ein *Sortierungssymbol* im Format "[.`elt`.]". Fügt das Sortierreihenfolgenelement `elt` dem Satz hinzu, der durch `expr` definiert wird.

- Ein *Anker*. Der Anker "^" entspricht dem Anfang der Zielsequenz, während der Anker "$ " mit dem Ende der Zielsequenz übereinstimmt.

Eine *Erfassungsgruppe* im Format "( *Teilausdruck* )" oder "\\( *Teilausdruck* \\)" in `basic` und `grep`, die der Reihenfolge der Zeichen in der Zielsequenz entspricht, die anhand des Musters zwischen den Trennzeichen verglichen wird.

- Eine *Identitätsescape* der\\`k`Form " `k` ", die dem Zeichen in der Zielsequenz entspricht.

Beispiele:

- "a" entspricht der Zielsequenz "a", stimmt jedoch nicht mit den Zielsequenzen "B", "b" oder "c" überein.

- "." entspricht allen Zielsequenzen "a", "B", "b" und "c".

- "[b-z]" entspricht den Zielsequenzen "b" und "c", stimmt jedoch nicht mit den Zielsequenzen "a" oder "B" überein.

- "[:lower:]" entspricht den Zielsequenzen "a", "b" und "c", stimmt jedoch nicht mit der Zielsequenz "B" überein.

- "(a)" entspricht der Zielsequenz "a" und ordnet die Erfassungsgruppe 1 der Untersequenz "a" zu, stimmt jedoch nicht mit den Zielsequenzen "B", "b" oder "c" überein.

In `ECMAScript` `basic`, `grep`und , kann ein Element auch ein\\`dd` *Rückverweis* des Formulars " sein, wobei `dd` ein Dezimalwert N darstellt, der mit einer Zeichenfolge in der Zielsequenz übereinstimmt, die mit der Zeichenfolge übereinstimmt, die von der Nth-Erfassungsgruppe abgeglichen wird. *capture group* "(a)\1" entspricht beispielsweise der Zielsequenz "aa", da die erste (und einzige) Erfassungsgruppe mit der ursprünglichen Sequenz "a" übereinstimmt und \1 dann der letzten Sequenz "a" entspricht.

In `ECMAScript` kann ein Element auch Folgendes sein:

- Eine *Nichterfassungsgruppe* des Formulars "(?: *Subexpression* )". Entspricht der Folge von Zeichen in der Zielsequenz, die anhand des Musters zwischen den Trennzeichen verglichen wird.

- Ein eingeschränktes *Dateiformat-Escapezeichen* im Format "\f", "\n", "\r", "\t" oder "\v". Diese Zeichen entsprechen einem Seitenvorschub, einem Zeilenumbruch, einem Wagenrücklauf, einem horizontalen bzw. einem vertikalen Tabulator in der Zielsequenz.

- Eine *positive Assertion* im Format "(= *Teilausdruck* )". Entspricht der Folge von Zeichen in der Zielsequenz, die anhand des Musters zwischen den Trennzeichen abgeglichen wird, jedoch die Abgleichungsposition in der Zielsequenz nicht ändert.

- Eine *negative Assertion* im Format "(! *Teilausdruck* )". Entspricht einer Folge von Zeichen in der Zielsequenz, die dem Muster zwischen den Trennzeichen nicht entspricht und mit der Abgleichungsposition in der Zielsequenz nicht übereinstimmt.

- Eine *hexadezimale Escapesequenz* im Format "\x`hh`". Entspricht einem Zeichen in der Zielsequenz, das durch die zwei Hexadezimalzeichen `hh` dargestellt wird.

- Eine *Unicode-Escapesequenz* im Format "\u`hhhh`". Entspricht einem Zeichen in der Zielsequenz, das durch die vier Hexadezimalzeichen `hhhh` dargestellt wird.

- Eine *Escapesequenz für Steuerzeichen* im Format "\c`k`". Entspricht dem Steuerzeichen, das durch das Zeichen `k` benannt wird.

- Eine *Wortgrenzenassertion* im Format "\b". Stimmt überein, wenn die aktuelle Position in der Zielsequenz unmittelbar hinter einer *Wortgrenze* liegt.

- Eine *negative Wortgrenzenassertion* im Format "\B". Stimmt überein, wenn die aktuelle Position in der Zielsequenz nicht unmittelbar hinter einer *Wortgrenze* liegt.

- Ein *DSW-Escapezeichen* im Format "\d", "\D", "\s", "\S", "\w", "\W". Gibt einen Kurznamen für eine Zeichenklasse an.

Beispiele:

- "(?:a)" entspricht der Zielsequenz "a", aber "(?:a)\1" ist ungültig, da es keine Erfassungsgruppe 1 gibt.

- "(?=a)a" entspricht der Zielsequenz "a". Die positive Assertion entspricht der ursprünglichen Sequenz "a" in der Zielsequenz, und der letzte Wert "a" im regulären Ausdruck entspricht der ursprünglichen Sequenz "a" in der Zielsequenz.

- "(?!a)a" entspricht nicht der Zielsequenz "a".

- "a\b." entspricht der Zielsequenz "a~", stimmt jedoch nicht mit der Zielsequenz "ab" überein.

- "a\B." entspricht der Zielsequenz "ab", stimmt jedoch nicht mit der Zielsequenz "ab~" überein.

In `awk` kann ein Element auch Folgendes sein:

- Ein *Dateiformat-Escape* der\\\\Form " ", "a", "-b", "-f", "-n", "-, " ", "-t" oder "-v". Diese Zeichen entsprechen einem umgekehrten Schrägstrich, einer Warnmeldung, einer Rücktaste, einem Seitenvorschub, einem Zeilenumbruch, einem Wagenrücklauf, einem horizontalen bzw. einem vertikalen Tabulator in der Zielsequenz.

- Eine *oktale Escape-Sequenz* \\`ooo`der Form " " . Entspricht einem Zeichen in der Zielsequenz, dessen Darstellung der Wert ist, der durch die ein, zwei oder drei oktalen Ziffern `ooo` dargestellt wird.

### <a name="repetition"></a>Wiederholen

Auf jedes Element außer einer *positiven Assertion*, einer *negativen Assertion* oder einem *Anker* kann eine Wiederholungsanzahl folgen. Die häufigste Art der Wiederholungsanzahl hat das Format "{`min`,`max`}" oder "\\{`min`,`max`\\}" in `basic` und `grep`. Ein Element, auf das dieses Format der Wiederholungsanzahl folgt, entspricht mindestens `min` aufeinander folgenden Vorkommen und nicht mehr als `max` aufeinander folgenden Vorkommen einer Sequenz, die mit dem Element übereinstimmt. Beispielsweise entspricht "a{2,3}" der Zielsequenz "aa" und der Zielsequenz "aaa", nicht aber der Zielsequenz "a" oder der Zielsequenz "aaaa".

Für eine Wiederholungsanzahl können auch folgende Formate verwendet werden:

- "{`min`,}" oder "\\{`min`\\}" in `basic` und `grep`. Entspricht "{`min`,`min`}".

- "{`min`,}" oder "\\{`min`,\\}" in `basic` und `grep`. Entspricht "{`min`,unbounded}".

- "\*". Entspricht "{0,unbounded}".

Beispiele:

- "a{2}" entspricht der Zielsequenz "aa", nicht aber der Zielsequenz "a" oder der Zielsequenz "aaa".

- "a{2,}" entspricht der Zielsequenz "aa", der Zielsequenz "aaa" usw., stimmt jedoch nicht mit der Zielsequenz "a" überein.

- "a\*" entspricht der Zielsequenz "", der Zielsequenz "a", der Zielsequenz "aa" usw.

Für alle Grammatiken außer `basic` und `grep` können für eine Wiederholungsanzahl folgende Formate verwendet werden:

- "?". Äquivalent zu{0,1}" ".

- "+". Entspricht "{1,unbounded}".

Beispiele:

- "a?" entspricht der Zielsequenz "" und der Zielsequenz "a", nicht aber der Zielsequenz "aa".

- "a+" entspricht der Zielsequenz "a", der Zielsequenz "aa" usw., jedoch nicht der Zielsequenz "".

In `ECMAScript`kann auf alle Formen der Wiederholungszahl der Charakter '?' folgen, der eine *nicht gierige Wiederholung*bezeichnet.

### <a name="concatenation"></a>Verkettung

Elemente des regulären Ausdrucks mit oder ohne *Wiederholungsanzahl* können verkettet werden, um längere reguläre Ausdrücke zu bilden. Der resultierende Ausdruck entspricht einer Zielsequenz, die eine Verkettung der Sequenzen ist, der die einzelnen Elemente entsprechen. Beispielsweise entspricht "a{2,3}b" der Zielsequenz "aab" und der Zielsequenz "aaab", entspricht jedoch nicht der Zielsequenz "ab" oder der Zielsequenz "aaaab".

### <a name="alternation"></a>Alternierung

In allen Grammatiken für reguläre Ausdrücke außer `basic` und `grep` kann ein Zeichen '&#124;' und ein anderer verketteter regulärer Ausdruck einem verketteten regulären Ausdruck folgen. Verkettete reguläre Ausdrücke können auf diese Weise in beliebiger Zahl kombiniert werden. Der resultierende Ausdruck entspricht jeder Zielsequenz, die mit mindestens einem verketteten regulären Ausdruck übereinstimmt.

Wenn mehrere der verketteten regulären Ausdrücke der Zielsequenz entsprechen, wählt `ECMAScript` den ersten verketteten regulären Ausdruck, der der Sequenz entspricht, als Übereinstimmung (*erste Übereinstimmung*) aus; die anderen Grammatiken für reguläre Ausdrücke wählen den Ausdruck aus, der die *längste Übereinstimmung* erzielt. Beispiel: "ab&#124;cd" entspricht der Zielsequenz "ab" und der Zielsequenz "cd", jedoch nicht der Zielsequenz "abd" oder der Zielsequenz "acd".

In `grep` und `egrep` kann ein Zeilenumbruchzeichen ("\n") verwendet werden, um Alternierungen zu trennen.

### <a name="subexpression"></a>Teilausdruck

In `basic` und `grep` ist ein Teilausdruck eine Verkettung. In den anderen Grammatiken für reguläre Ausdrücke ist ein Teilausdruck eine Alternierung.

## <a name="grammar-summary"></a><a name="grammarsummary"></a> Zusammenfassung der Grammatik

In der folgenden Tabelle sind die Funktionen zusammengefasst, die in verschiedenen Grammatiken für reguläre Ausdrücke verfügbar sind:

|Element|basic|Erweitert|ECMAScript|grep|egrep|awk|
|-------------|---------|---------|----------|----------|-----------|---------|
|Alternierung mit '&#124;'||+|+||+|+|
|Alternierung mit "\n"||||+|+||
|Anker|+|+|+|+|+|+|
|Rückverweis|+||+|+|||
|Klammerausdruck|+|+|+|+|+|+|
|Erfassungsgruppe, die "()" verwendet||+|+||+|+|
|Erfassungsgruppe, die "\\(\\)" verwendet|+|||+|||
|Escapesequenz für Steuerzeichen|||+||||
|DSW-Escapezeichen|||+||||
|Dateiformat-Escapezeichen|||+|||+|
|Hexadezimale Escapesequenz|||+||||
|Identitätsescapezeichen|+|+|+|+|+|+|
|Negative Assertion|||+||||
|Negative Wortgrenzenassertion|||+||||
|Nichterfassungsgruppe|||+||||
|Nicht gierige Wiederholung|||+||||
|Oktale Escapesequenz||||||+|
|Normales Zeichen|+|+|+|+|+|+|
|Positive Assertion|||+||||
|Wiederholung mit{}"||+|+||+|+|
|Wiederholung mit "\\{\\}"|+|||+|||
|Wiederholung mit\*' '|+|+|+|+|+|+|
|Wiederholung mit "?" und "+"||+|+||+|+|
|Unicode-Escapesequenz|||+||||
|Platzhalterzeichen|+|+|+|+|+|+|
|Wortgrenzenassertion|||+||||

## <a name="semantic-details"></a><a name="semanticdetails"></a> Semantische Details

### <a name="anchor"></a>Anker

Ein Anker entspricht einer Position in der Zielzeichenfolge, keinem Zeichen. Ein "^" entspricht dem Anfang der Zielzeichenfolge, und ein "$" entspricht dem Ende der Zielzeichenfolge.

### <a name="back-reference"></a>Rückverweis

Ein Rückverweis ist ein umgekehrter Schrägstrich, nach dem ein Dezimalwert n folgt. Er entspricht dem Inhalt der n-ten *Erfassungsgruppe*. Der Wert von N darf nicht mehr als die Anzahl von Erfassungsgruppen sein, die dem Rückverweis vorausgehen. In `basic` und `grep` wird der Wert N durch die Dezimalstelle bestimmt, die dem umgekehrten Schrägstrich folgt. In `ECMAScript` wird der Wert N von allen Dezimalstellen bestimmt, die dem umgekehrten Schrägstrich unmittelbar folgen. Daher überschreitet der Wert N in `basic` und `grep` nie den Wert 9, auch wenn der reguläre Ausdruck über mehr als neun Erfassungsgruppen verfügt. In `ECMAScript` ist der Wert N unbegrenzt.

Beispiele:

- "((a+)(b+))(c+)\3" entspricht der Zielsequenz "aabbbcbbb". Der Rückverweis "\3" entspricht dem Text in der dritten Erfassungsgruppe, d. h "(b+)". Er entspricht nicht der Zielsequenz "aabbbcbb".

- "(a)\2" ist nicht gültig.

- "(b(((((((((a))))))))))\10" hat verschiedene Bedeutungen in `basic` und `ECMAScript`. In `basic` ist der Rückverweis "\1". Der Rückverweis entspricht dem Inhalt der ersten Erfassungsgruppe (d. h. der Gruppe, die mit "(b" beginnt und mit dem letzten Zeichen ")" endet und vor dem Rückverweis steht). Die letzte "0" entspricht dem normalen Zeichen "0". In `ECMAScript` ist der Rückverweis "\10". Er entspricht der zehnten Erfassungsgruppe, d. h. der innersten.

### <a name="bracket-expression"></a>Klammerausdruck

Ein Klammerausdruck definiert einen Satz von Zeichen und *Sortierungselementen*. Wenn der Klammerausdruck mit dem Zeichen "^" beginnt, ist die Übereinstimmung erfolgreich, wenn keine Elemente im Satz dem aktuellen Zeichen in der Zielsequenz entsprechen. Andernfalls ist die Übereinstimmung erfolgreich, wenn eines der Elemente im Satz dem aktuellen Zeichen in der Zielsequenz entspricht.

Der Satz von Zeichen kann definiert werden, indem eine beliebige Kombination von *einzelnen Zeichen*, *Zeichenbereichen*, *Zeichenklassen*, *Äquivalenzklassen* und *Sortierungssymbolen* aufgelistet wird.

### <a name="capture-group"></a>Erfassungsgruppe

Eine Erfassungsgruppe markiert ihren Inhalt als einzelne Einheit in der Grammatik für reguläre Ausdrücke und versieht den Zieltext, der dem Inhalt entspricht, mit einer Bezeichnung. Die Bezeichnung, die den einzelnen Erfassungsgruppen zugeordnet ist, ist eine Zahl, die bestimmt wird, indem die öffnenden Klammern, die Erfassungsgruppen markieren, bis einschließlich der öffnenden Klammer, die die aktuelle Erfassungsgruppe markiert, gezählt werden. In dieser Implementierung ist die maximale Anzahl von Erfassungsgruppen 31.

Beispiele:

- "ab+" entspricht der Zielsequenz "abb", stimmt jedoch nicht mit der Zielsequenz "abab" überein.

- "(ab)+" entspricht nicht der Zielsequenz "abb", stimmt jedoch mit der Zielsequenz "abab" überein.

- "((a+)(b+))(c+)" entspricht der Zielsequenz "aabbbc" und ordnet die Erfassungsgruppe 1 der Untersequenz "aabbb", die Erfassungsgruppe 2 der Untersequenz "aa", die Erfassungsgruppe 3 der Untersequenz "bbb" und die Erfassungsgruppe 4 der Untersequenz "c" zu.

### <a name="character-class"></a>Zeichenklasse

Eine Zeichenklasse in einem Klammerausdruck fügt alle Zeichen in der benannten Klasse dem Zeichensatz hinzu, der durch den Klammerausdruck definiert wird. Um eine Zeichenklasse zu erstellen, verwenden Sie "[:" gefolgt vom Namen der Klasse, auf den ":]" folgt. Intern werden Namen von Zeichenklassen erkannt, indem `id = traits.lookup_classname` aufgerufen wird. Ein Zeichen `ch` gehört einer solchen Klasse an, wenn `traits.isctype(ch, id)` "true" zurückgibt. Die standardmäßige `regex_traits`-Vorlage unterstützt die Klassennamen in der folgenden Tabelle.

|Klassenname|BESCHREIBUNG|
|----------------|-----------------|
|"alnum"|Kleinbuchstaben, Großbuchstaben und Ziffern|
|"alpha"|Kleinbuchstaben und Großbuchstaben|
|"blank"|Leerzeichen oder Tabstopp|
|"STRG"|die *Dateiformat-Escapezeichen*|
|"digit"|Zahlen|
|"graph"|Kleinbuchstaben, Großbuchstaben, Ziffern und Interpunktion|
|"lower"|Kleinbuchstaben|
|"print"|Kleinbuchstaben, Großbuchstaben, Ziffern, Interpunktion und Leerzeichen|
|"punct"|Interpunktion|
|"space"|Leerzeichen|
|"upper"|Großbuchstaben|
|"xdigit"|Ziffern, "a", "b", "c", "d", "e", "f", "A", "B", "C", "D", "E", "F"|
|"d"|wie "digit"|
|"s"|wie "space"|
|"w"|wie "alnum"|

### <a name="character-range"></a>Zeichenbereich

Ein Zeichenbereich in einem Klammerausdruck fügt alle Zeichen in dem Bereich dem Zeichensatz hinzu, der durch den Klammerausdruck definiert wird. Um einen Zeichenbereich zu erstellen, platzieren Sie das Zeichen "-" zwischen das erste und letzte Zeichen im Bereich. Damit werden alle Zeichen in den Satz aufgenommen, die einen numerischen Wert haben, der größer oder gleich dem numerischen Wert des ersten Zeichens und kleiner oder gleich dem numerischen Wert des letzten Zeichen ist. Beachten Sie, dass dieser Satz von hinzugefügten Zeichen von der plattformspezifischen Darstellung der Zeichen abhängt. Wenn das Zeichen "-" am Anfang oder am Ende eines Klammerausdrucks oder als erstes oder letztes Zeichen des Zeichenbereichs auftritt, stellt es sich selbst dar.

Beispiele:

- "[0-7]" stellt den Satz von Zeichen dar {"0", "1", "2", "3", "4", "5", "6", "7"}. Der Ausdruck entspricht den Zielsequenzen "0", "1" usw., nicht jedoch "a".

- Auf Systemen, die die ASCII-Zeichencodierung verwenden, stellt "[h-k]" den Satz von Zeichen {"h", "i", "j", "k"} dar. Der Ausdruck entspricht den Zielsequenzen "h", "i" usw., jedoch nicht "\x8A" oder "0".

- Auf Systemen, die die EBCDIC-Zeichencodierung verwenden, stellt "[h-k]" den Satz von Zeichen { "h", "i", "\x8A", "\x8B", "\x8C", "\x8D", "\x8E", "\x8F", "\x90", "j", "k" } dar ("h" wird als 0x88 und "k" als 0x92 codiert). Der Ausdruck entspricht den Zielsequenzen "h", "i", "\x8A" usw., jedoch nicht "0".

- "[-0-24]" stellt den Satz von Zeichen {"-", "0", "1", "2", "3", "4"} dar.

- "[0-2-]" stellt den Satz von Zeichen {"0", "1", "2", "-"} dar.

- Auf Systemen, die die ASCII-Zeichencodierung verwenden, stellt "[+--]" den Satz von Zeichen {"+", ",", "-"} dar.

Wenn gebietsschemaabhängige Bereiche verwendet werden, werden die Zeichen in einem Bereich von den Sortierreihenfolgenregeln für das Gebietsschema bestimmt. Zeichen, die nach dem ersten Zeichen in der Definition des Bereichs und vor das letzte Zeichen der Definition des Bereichs sortiert werden, befinden sich im Satz. Die beiden Endzeichen befinden sich ebenfalls im Satz.

### <a name="collating-element"></a>Sortierungselement

Ein Sortierungselement ist eine Sequenz mit mehreren Zeichen, die als einzelnes Zeichen behandelt wird.

### <a name="collating-symbol"></a>Sortierungssymbol

Ein Sortierungssymbol in einem Klammerausdruck fügt dem Satz, der durch den Klammerausdruck definiert wird, ein *Sortierungselement* hinzu. Um ein Sortierungssymbol zu erstellen, verwenden Sie "[.", gefolgt vom Sortierungselement, gefolgt von ".]".

### <a name="control-escape-sequence"></a>Escapesequenz für Steuerzeichen

Eine Escapesequenz für Steuerzeichen ist ein umgekehrter Schrägstrich gefolgt vom Buchstaben "c", auf den einer der Buchstaben "a" bis "z" oder "A" bis "Z" folgt. Sie entspricht dem ASCII-Steuerzeichen, das von diesen Buchstaben benannt wird. Beispielsweise entspricht "\ci" der Zielsequenz "\x09", da \<STRG-i> den Wert 0x09 hat.

### <a name="dsw-character-escape"></a>DSW-Escapezeichen

Ein DSW-Escapezeichen ist ein Kurzname für eine Zeichenklasse, wie in der folgenden Tabelle dargestellt.

|Escapesequenz|Äquivalente benannte Klasse|Standardmäßige benannte Klasse|
|---------------------|----------------------------|-------------------------|
|"\d"|"[[:d:]]"|"[[:digit:]]"|
|"\D"|"[^[:d:]]"|"[^[:digit:]]"|
|"\s"|"[[:s:]]"|"[[:space:]]"|
|"\S"|"[^[:s:]]"|"[^[:space:]]"|
|"\w"|"[[:w:]]"|"[a-zA-Z0-9_]"\*|
|"\W"|"[^[:w:]]"|"[-a-zA-Z0-9_]"\*|

\*ASCII-Zeichensatz

### <a name="equivalence-class"></a>Äquivalenzklasse

Eine Äquivalenzklasse in einem Klammerausdruck fügt dem Satz, der durch den Klammerausdruck definiert wird, alle Zeichen und *Sortierungselemente* hinzu, die dem Sortierungselement in der Äquivalenzklassendefinition entsprechen. Um eine Äquivalenzklasse zu erstellen, verwenden Sie "[=" gefolgt von einem Sortierungselement, auf das "=]" folgt. Intern sind zwei Sortierungselemente `elt1` und `elt2` äquivalent, wenn `traits.transform_primary(elt1.begin(), elt1.end()) == traits.transform_primary(elt2.begin(), elt2.end())`.

### <a name="file-format-escape"></a>Dateiformat-Escapezeichen

Ein Dateiformat-Escapezeichen besteht aus den üblichen Escapezeichensequenzen der C-Programmiersprache "\\\\", "\a", "\b", "\f", "\n", "\r", "\t", "\v". Diese haben die üblichen Bedeutungen, d.h. umgekehrter Schrägstrich, Warnmeldung, Rücktaste, Seitenvorschub, Zeilenvorschub, Wagenrücklauf, horizontaler bzw. vertikaler Tabulator. In `ECMAScript` sind "\a" und "\b" nicht zulässig. ("\\\\" ist zulässig, es handelt sich jedoch um ein Identitätsescapezeichen, nicht um ein Dateiformat-Escapezeichen).

### <a name="hexadecimal-escape-sequence"></a>Hexadezimale Escapesequenz

Eine hexadezimale Escapesequenz ist ein umgekehrter Schrägstrich, gefolgt vom Buchstaben "x", auf den zwei hexadezimale Ziffern (0-9a-fA-F) folgen. Sie entspricht einem Zeichen in der Zielsequenz mit dem Wert, der durch die zwei Ziffern angegeben wird. Beispielsweise entspricht "\x41" der Zielsequenz "A", wenn die ASCII-Zeichencodierung verwendet wird.

### <a name="identity-escape"></a>Identitätsescapezeichen

Ein Identitätsescapezeichen ist ein umgekehrter Schrägstrich, auf den ein einzelnes Zeichen folgt. Es entspricht diesem Zeichen. Das Escapezeichen ist erforderlich, wenn das Zeichen eine besondere Bedeutung hat. Durch das Identitätsescapezeichen wird die besondere Bedeutung aufgehoben. Beispiel:

- "a\*" entspricht der Zielsequenz "aaa", stimmt aber\*nicht mit der Zielsequenz "a" überein.

- "a\\\*" stimmt nicht mit der Zielsequenz "aaa"\*überein, sondern mit der Zielsequenz "a".

Der Satz von Zeichen, die in einem Identitätsescapezeichen zulässig sind, hängt von der Grammatik für die regulären Ausdrücke ab, wie in der folgenden Tabelle dargestellt.

|Grammatik|Zulässige Identitätsescapezeichen|
|-------------|----------------------------------------|
|`basic`, `grep`|{ '(', ')', '{', '}', '.', '[', '\\', '\*', '^', '$' }|
|`extended`, `egrep`|" '(', ')', ''', '',',\\'[', '' ' ' ' '\*' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '+', '+', '?', '&#124;'|
|`awk`|`extended` plus { '"', '/' }|
|`ECMAScript`|Alle Zeichen außer denjenigen, die Bestandteil eines Bezeichners sein können. In der Regel umfasst dies Buchstaben,\_Ziffern, ''', ' ' ' und Unicode-Escape-Sequenzen. Weitere Informationen finden Sie in der ECMAScript-Sprachspezifikation.|

### <a name="individual-character"></a>Einzelnes Zeichen

Ein einzelnes Zeichen in einem Klammerausdruck fügt dieses Zeichen dem Zeichensatz hinzu, der durch den Klammerausdruck definiert wird. Überall in einem Klammerausdruck, außer zu Beginn, stellt sicher ein "^" selbst dar.

Beispiele:

- "[abc]" entspricht den Zielsequenzen "a", "b" und "c", nicht jedoch der Sequenz "d".

- "[^abc]" entspricht der Zielsequenz "d", jedoch nicht den Zielsequenzen "a", "b" oder "c".

- "[a^bc]" entspricht den Zielsequenzen "a", "b", "c" und "^", jedoch nicht der Zielsequenz "d".

In allen Grammatiken für reguläre Ausdrücke außer `ECMAScript` gilt: Wenn "]" das erste Zeichen ist, das der öffnenden Klammer "[" folgt, oder das erste Zeichen, das einem anfänglichen Zeichen "^" folgt, stellt es sich selbst dar.

Beispiele:

- "[]a" ist ungültig, da es kein "]" gibt, um den Klammerausdruck zu beenden.

- "[]abc]" entspricht den Zielsequenzen "a", "b", "c" und "]", jedoch nicht der Zielsequenz "d".

- "[^]abc]" entspricht der Zielsequenz "d", jedoch nicht den Zielsequenzen "a", "b", "c" oder "]".

In `ECMAScript` verwenden Sie " \\]", um das Zeichen "]" in einem Klammerausdruck darzustellen.

Beispiele:

- "[]a" entspricht der Zielsequenz "a", da der Klammerausdruck leer ist.

- "[\\]abc]" entspricht den Zielsequenzen "a", "b", "c" und "]", jedoch nicht der Zielsequenz "d".

### <a name="negative-assert"></a>Negative Assertion

Eine negative Assertion entspricht allem, außer ihrem Inhalt. Sie verarbeitet keine Zeichen in der Zielsequenz. Beispielsweise entspricht "(!aa)(a\*)" der Zielsequenz "a" und ordnet Erfassungsgruppe 1 mit der Untersequenz "a" zu. Die Sequenz entspricht nicht der Zielsequenz "aa" oder der Zielsequenz "aaa".

### <a name="negative-word-boundary-assert"></a>Negative Wortgrenzenassertion

Eine negative Wortgrenzenassertion stimmt überein, wenn die aktuelle Position in der Zielzeichenfolge nicht unmittelbar hinter einer *Wortgrenze* liegt.

### <a name="non-capture-group"></a>Nichterfassungsgruppe

Eine Nichterfassungsgruppe markiert ihren Inhalt als einzelne Einheit in der Grammatik für reguläre Ausdrücke, versieht den Zieltext jedoch nicht mit einer Bezeichnung. Beispielsweise entspricht "(a)(?:b)\*(c)" dem Zieltext "abbc" und ordnet Erfassungsgruppe 1 mit der Untersequenz "a" und Erfassungsgruppe 2 mit der Untersequenz "c" zu.

### <a name="non-greedy-repetition"></a>Nicht gierige Wiederholung

Eine nicht gierige Wiederholung nutzt die kürzeste Untersequenz der Zielsequenz, die dem Muster entspricht. Eine gierige Wiederholung verwendet die längste Untersequenz. Beispielsweise entspricht "(a+)(a\*b)" der Zielsequenz "aaab". Wenn eine nicht gierige Wiederholung verwendet wird, wird die Erfassungsgruppe 1 der Untersequenz "a" am Anfang der Zielsequenz und die Erfassungsgruppe 2 der Untersequenz "aab" am Ende der Zielsequenz zugeordnet. Wenn eine gierige Übereinstimmung verwendet wird, wird die Erfassungsgruppe 1 der Untersequenz "aaa" und die Erfassungsgruppe 2 der Untersequenz "b" zugeordnet.

### <a name="octal-escape-sequence"></a>Oktale Escapesequenz

Eine oktale Escapesequenz ist ein umgekehrter Schrägstrich, gefolgt von einer, zwei oder drei Oktalziffern (0-7). Sie entspricht einem Zeichen in der Zielsequenz mit dem Wert, der durch diese Ziffern angegeben wird. Wenn alle Ziffern "0 " sind, ist die Sequenz ungültig. Beispielsweise entspricht "\101" der Zielsequenz "A", wenn die ASCII-Zeichencodierung verwendet wird.

### <a name="ordinary-character"></a>Normales Zeichen

Ein normales Zeichen ist ein beliebiges gültiges Zeichen, das in der aktuellen Grammatik keine besondere Bedeutung hat.

In `ECMAScript` haben die folgenden Zeichen eine besondere Bedeutung:

- ^  $  \  .  \*+  ?  ( \[ ) ] . . . &#124; . . . . . . . . . . . . . .

In `basic` und `grep` haben die folgenden Zeichen eine besondere Bedeutung:

- .   \[   \

In `basic` und `grep` verfügen die folgenden Zeichen außerdem über eine besondere Bedeutung, wenn sie in einem bestimmten Kontext verwendet werden:

- '\*' hat in allen Fällen eine besondere Bedeutung, außer wenn es sich um das erste Zeichen in einem regulären Ausdruck oder das erste Zeichen handelt, das auf ein anfängliches ''' in einem regulären Ausdruck folgt, oder wenn es sich um das erste Zeichen einer Erfassungsgruppe oder das erste Zeichen handelt, das auf ein anfängliches ''' in einer Erfassungsgruppe folgt.

- "^" hat eine besondere Bedeutung, wenn es das erste Zeichen eines regulären Ausdrucks ist.

- "$" hat eine besondere Bedeutung, wenn es das letzte Zeichen eines regulären Ausdrucks ist.

In `extended`, `egrep` und `awk` haben die folgenden Zeichen eine besondere Bedeutung:

- .   \[\   (   \*   +   ?   • &#124;

In `extended`, `egrep` und `awk` verfügen die folgenden Zeichen außerdem über eine besondere Bedeutung, wenn sie in einem bestimmten Kontext verwendet werden:

- ')' hat eine besondere Bedeutung, wenn es einem vorhergehenden '(' entspricht.

- "^" hat eine besondere Bedeutung, wenn es das erste Zeichen eines regulären Ausdrucks ist.

- "$" hat eine besondere Bedeutung, wenn es das letzte Zeichen eines regulären Ausdrucks ist.

Ein normales Zeichen entspricht dem gleichen Zeichen in der Zielsequenz. Standardmäßig heißt das, dass die Übereinstimmung erfolgreich ist, wenn die beiden Zeichen durch den gleichen Wert dargestellt werden. In einer Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung stimmen zwei Zeichen `ch0` und `ch1` überein, wenn `traits.translate_nocase(ch0) == traits.translate_nocase(ch1)`. In einer Übereinstimmung unter Beachtung des Gebietsschemas stimmen zwei Zeichen `ch0` und `ch1` überein, wenn `traits.translate(ch0) == traits.translate(ch1)`.

### <a name="positive-assert"></a>Positive Assertion

Eine positive Assertion entspricht ihrem Inhalt, verwendet jedoch keine Zeichen in der Zielsequenz.

Beispiele:

- "(=aa)(a\*)" entspricht der Zielsequenz "aaaa" und ordnet die Erfassungsgruppe 1 mit der Untersequenz "aaaa" zu.

- "(aa)(a)"\*entspricht der Zielsequenz "aaaa" und ordnet Dieerfassungsgruppe 1 mit der Untersequenz "aa" am Anfang der Zielsequenz und der Erfassungsgruppe 2 mit der Folge "aa" am Ende der Zielsequenz zu.

- "(=aa)(a)&#124;(a)" entspricht der Zielsequenz "a" und ordnet die Erfassungsgruppe 1 einer leeren Sequenz (aufgrund eines Fehlers bei der positiven Assertion) und die Erfassungsgruppe 2 der Untersequenz "a" zu. Außerdem entspricht die Zielsequenz "aa" und ordnet die Erfassungsgruppe 1 der Untersequenz "aa" und die Erfassungsgruppe 2 einer leeren Sequenz zu.

### <a name="unicode-escape-sequence"></a>Unicode-Escapesequenz

Eine Unicode-Escapesequenz ist ein umgekehrter Schrägstrich, gefolgt vom Buchstaben "u", auf den vier hexadezimale Ziffern (0-9a-fA-F) folgen. Sie entspricht einem Zeichen in der Zielsequenz mit dem Wert, der durch die vier Ziffern angegeben wird. Beispielsweise entspricht "\u0041" der Zielsequenz "A", wenn die ASCII-Zeichencodierung verwendet wird.

### <a name="wildcard-character"></a>Platzhalterzeichen

Ein Platzhalterzeichen entspricht jedem Zeichen im Zielausdruck außer einem Zeilenumbruch.

### <a name="word-boundary"></a>Wortgrenze

Eine Wortgrenze tritt in den folgenden Fällen auf:

- Das aktuelle Zeichen befindet sich am Anfang der Zielsequenz und ist eines der Wortzeichen `A-Za-z0-9_.`

- Die aktuelle Zeichenposition liegt hinter dem Ende der Zielsequenz und das letzte Zeichen der Zielsequenz ist eines der Wortzeichen.

- Das aktuelle Zeichen ist eines der Wortzeichen und das vorherige Zeichen nicht.

- Das aktuelle Zeichen ist keines der Wortzeichen und das vorherige Zeichen ist ein Wortzeichen.

### <a name="word-boundary-assert"></a>Wortgrenzenassertion

Eine Wortgrenzenassertion stimmt überein, wenn die aktuelle Position in der Zielzeichenfolge nicht unmittelbar hinter einer *Wortgrenze* liegt.

## <a name="matching-and-searching"></a><a name="matchingandsearching"></a> Zuordnen und Suchen

Damit ein regulärer Ausdruck einer Zielsequenz entspricht, muss der gesamte reguläre Ausdruck mit der gesamten Zielsequenz übereinstimmen. Beispielsweise entspricht der reguläre Ausdruck "bcd" der Zielsequenz "bcd", stimmt jedoch weder mit der Zielsequenz "abcd" noch mit der Zielsequenz "bcde" überein.

Damit eine Suche mit regulärem Ausdruck erfolgt, muss eine Untersequenz in der Zielsequenz vorhanden sein, die dem regulären Ausdruck entspricht. Die Suche ergibt in der Regel die äußerst linke entsprechende Untersequenz.

Beispiele:

- Eine Suche nach dem regulären Ausdruck "bcd" in der Zielsequenz "bcd" ist erfolgreich und entspricht der gesamten Sequenz. Die gleiche Suche in der Zielsequenz "abcd" ist auch erfolgreich und stimmt mit den letzten drei Zeichen überein. Die gleiche Suche in der Zielsequenz "bcde" ist auch erfolgreich und stimmt mit den ersten drei Zeichen überein.

- Eine Suche nach dem regulären Ausdruck "bcd" in der Zielsequenz "bcdbcd" ist erfolgreich und stimmt mit den ersten drei Zeichen überein.

Wenn es mehr als eine Untersequenz gibt, die mit einer Position in der Zielsequenz übereinstimmt, gibt es zwei Möglichkeiten, das entsprechende Muster auszuwählen. Die *erste Übereinstimmung* wählt die Untersequenz aus, die zuerst gefunden wurde, wenn der reguläre Ausdruck übereinstimmt. Die *längste Übereinstimmung* wählt die längste Untersequenz aus den Sequenzen aus, die an dieser Position übereinstimmen. Wenn es mehr als eine Untersequenz gibt, die die maximale Länge hat, wird mit der längsten Übereinstimmung diejenige ausgewählt, die zuerst gefunden wurde. Wenn die erste Übereinstimmung verwendet wird, ergibt eine Suche nach dem regulären Ausdruck "b&#124;bc" in der Zielsequenz "abcd" die Untersequenz "b", da der linke Alternierungsausdruck dieser Untersequenz entspricht. Daher berücksichtigt diese Methode den rechten Alternierungsausdruck nicht. Wenn die längste Übereinstimmung verwendet wird, ergibt die gleiche Suche "bc", da "bc" länger als "b" ist.

Eine partielle Übereinstimmung ist erfolgreich, wenn die Übereinstimmung das Ende der Zielsequenz ohne Fehler erreicht, auch wenn sie das Ende des regulären Ausdruck nicht erreicht hat. Nachdem eine partielle Übereinstimmung erfolgreich ist, kann das Anhängen von Zeichen an die Zielsequenz daher dazu führen, dass bei einer späteren partiellen Übereinstimmung ein Fehler auftritt. Nachdem ein Fehler bei einer partiellen Übereinstimmung aufgetreten ist, kann das Anhängen von Zeichen an die Zielsequenz nicht dazu führen, dass eine spätere partielle Übereinstimmung erfolgreich ist. Beispielsweise entspricht "ab" bei einer partiellen Übereinstimmung der Zielsequenz "a", jedoch nicht "ac".

## <a name="format-flags"></a><a name="formatflags"></a> Formatflags

|ECMAScript-Formatierungsregeln|sed-Formatierungsregeln|Ersetzungstext|
|-----------------------------|----------------------|----------------------|
|"$&"|"&"|Die Zeichensequenz, die dem gesamten regulären Ausdruck entspricht (`[match[0].first, match[0].second)`)|
|"$$"||"$"|
||"\\&"|"&"|
|"-\`(Dollarzeichen gefolgt von Back-Zitat)|| Die Zeichensequenz, die der Untersequenz vorangeht, die dem regulären Ausdruck entspricht (`[match.prefix().first, match.prefix().second)`)|
|"$ '" (Dollarzeichen gefolgt vom Vorwärtsanführungszeichen)||Die Zeichensequenz, die der Untersequenz folgt, die dem regulären Ausdruck entspricht (`[match.suffix().first, match.suffix().second)`)|
|"$n"|"\n"|Die Zeichensequenz, die der `n`Erfassungsgruppe an der Position entspricht, wobei `n` eine Zahl zwischen 0 und 9 (`[match[n].first, match[n].second)`) liegt.|
||"\\\n"|"\n"|
|"$nn"||Die Zeichensequenz, die der `nn`Erfassungsgruppe an der Position entspricht, wobei `nn` eine Zahl zwischen 10 und 99 (`[match[nn].first, match[nn].second)`) liegt.|

## <a name="see-also"></a>Siehe auch

[Übersicht über die C++-Standardbibliothek](../standard-library/cpp-standard-library-overview.md)
