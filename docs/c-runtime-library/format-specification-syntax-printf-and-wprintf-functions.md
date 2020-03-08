---
title: 'Syntax der Formatangabe: printf- und wprintf-Funktionen'
ms.date: 10/21/2019
helpviewer_keywords:
- format specification fields for printf function
- printf function format specification fields
- flag directives, printf function
- type fields, printf function
- width fields, printf function
- precision fields, printf function
ms.assetid: 664b1717-2760-4c61-bd9c-22eee618d825
ms.openlocfilehash: 024e757f57e62ba2b30048c783798180b4da2b9a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865493"
---
# <a name="format-specification-syntax-printf-and-wprintf-functions"></a>Syntax der Formatangabe: printf- und wprintf-Funktionen

Die verschiedenen `printf`- und `wprintf`-Funktionen nehmen eine Formatzeichenfolge sowie optionale Argumente an und generieren eine formatierte Zeichenfolgensequenz für die Ausgabe. Die Formatzeichenfolge enthält 0 oder mehr *Anweisungen*, die entweder literale Zeichen für die Ausgabe oder codierte *Konvertierungsangaben* sind, die beschreiben, wie ein Argument in der Ausgabe formatiert wird. Dieser Artikel beschreibt die Syntax, die zum Codieren von Konvertierungsangaben in der Formatzeichenfolge verwendet wird. Eine Auflistung dieser Funktionen finden Sie unter [Stream E/A](../c-runtime-library/stream-i-o.md). 

Eine Konvertierungsangabe besteht aus optionalen Feldern und Pflichtfeldern in folgender Form:

**%** [[*flags*](#flags)][[*width*](#width)][.[*precision*](#precision)][[*size*](#size)][*type*](#type)

Jedes Feld der Konvertierungsangabe ist entweder ein Zeichen oder eine Zahl, das bzw. die eine bestimmte Formatoption oder Konvertierungsspezifizierer darstellt. Das erforderliche *Typ*feld gibt die Art der Konvertierung an, die an einem Argument vorgenommen wird. Die optionalen Felder *flags*, *width* und *precision* steuern zusätzliche Formataspekte, z.B. Leerzeichen oder Nullen, Ausrichtung und dargestellte Genauigkeit. Das Feld *size* gibt die Größe des verwendeten und konvertierten Arguments an.

Eine grundlegende Formatspezifikation enthält nur das Prozentzeichen und ein *Typ*zeichen. `%s` gibt z.B. eine Zeichenfolgenkonvertierung an. Um ein Prozentzeichen zu drucken, verwenden Sie `%%`. Es wird ein ungültiger Parameterhandler aufgerufen, wenn einem Prozentzeichen ein Zeichen folgt, das keine Bedeutung für ein Formatfeld hat. Weitere Informationen finden Sie unter [Parametervalidierung](../c-runtime-library/parameter-validation.md).

> [!IMPORTANT]
> Überprüfen Sie aus Sicherheits- und Stabilitätsgründen, dass die Zeichenfolgen der Konvertierungsangabe nicht benutzerdefiniert sind. Beispiel: Ein Programm, das den Benutzer zur Eingabe eines Namens auffordert und die Eingabe in einer Zeichenfolgevariablen namens `user_name` speichert. Führen Sie zum Drucken von `user_name` nicht diesen Schritt aus:
>
> `printf( user_name ); /* Danger!  If user_name contains "%s", program will crash */`
>
> Sondern gehen Sie stattdessen so vor:
>
> `printf( "%s", user_name );`

<a name="type"></a>

> [!NOTE] 
> In Visual Studio 2015 wurden die `printf`-und `scanf`-Funktions Familie als **Inline** deklariert und in die Header `<stdio.h>` und `<conio.h>` verschoben. Wenn Sie älteren Code migrieren, kann *LNK2019* in Verbindung mit diesen Funktionen angezeigt werden. Weitere Informationen finden Sie unter [visueller C++ Änderungs Verlauf 2003-2015](../porting/visual-cpp-change-history-2003-2015.md#stdio_and_conio).

## <a name="type-conversion-specifier"></a>Typkonvertierungsspezifizierer

Das *Typ*-Konvertierungsspezifiziererzeichen gibt an, ob das entsprechende Argument als Zeichen, Zeichenfolge, Zeiger, ganze Zahl oder Gleitkommazahl interpretiert werden soll. Das *Typ*zeichen ist das einzige erforderliche Konvertierungsangabenfeld und erscheint nach allen optionalen Feldern.

Die Argumente, die der Formatzeichenfolge folgen, werden nach dem entsprechenden *Typ*zeichen und dem optionalen [Größen](#size)präfix interpretiert. Konvertierungen für die Zeichentypen `char` und `wchar_t` werden durch **c** oder **C** angegeben, und Einzelbyte- und Multibyte- oder Breitzeichen-Zeichenfolgen werden je nach benötigter Formatierungsfunktion durch **s** oder **S** angegeben. Zeichen und Zeichenfolgenargumente, die durch **c** und **s** angegeben werden, werden von den `char`-Familienfunktionen als `char*` und `printf` oder von den `wchar_t`-Familienfunktionen als `wchar_t*` und `wprintf` interpretiert. Zeichen und Zeichenfolgenargumente, die durch **C** und **S** angegeben werden, werden von den `wchar_t`-Familienfunktionen als `wchar_t*` und `printf` oder von den `char`-Familienfunktionen als `char*` und `wprintf` interpretiert. Dieses Verhalten ist Microsoft-spezifisch.

Ganzzahlige Typen wie `short`, `int`, `long`, `long long`und deren `unsigned` Varianten werden mithilfe von **d**, **i**, **o**, **u**, **x**und **x**angegeben. Gleit Komma Typen wie `float`, `double`und `long double`**werden mithilfe von**, **a**, **e**, **e**, **f**, **f**, **g**und **g**angegeben. Wenn Sie nicht durch ein *Größen* Präfix geändert werden, werden ganzzahlige Argumente standardmäßig in `int` Typ umgewandelt, und Gleit Komma Argumente werden in `double`umgewandelt. Bei 64-Bit-Systemen ist `int` ein 32-Bit-Wert. Daher werden ganze 64-Bit-Zahlen verkürzt, wenn sie für Ausgabe formatiert werden, sofern nicht ein *Größen*präfix von **ll** oder **I64** verwendet wird. Durch **p** angegebene Zeigertypen verwenden die Standardzeigergröße für die Plattform.

> [!NOTE]
> **Microsoft-spezifisch:** Das **Z** -Typzeichen und das Verhalten der **c**-, **c**-, **s**-und **s** -Typzeichen, wenn Sie mit den Funktionen `printf` und `wprintf` verwendet werden, sind Microsoft-Erweiterungen. Der ISO C-Standard verwendet konsistent **c** und **s** für schmale Zeichen und Zeichenfolgen sowie **C** und **S** für Breitzeichen und Zeichenfolgen in allen Formatierungsfunktionen.

### <a name="type-field-characters"></a>Typenfeldzeichen

|Typzeichen|Argument|Ausgabeformat|
|--------------------|--------------|-------------------|
|**c**|Zeichen|Gibt bei Verwendung mit `printf`-Funktionen ein Einzelbytezeichen und bei Verwendung mit `wprintf`-Funktionen ein Breitzeichen an.|
|**C**|Zeichen|Gibt bei Verwendung mit `printf`-Funktionen ein Breitzeichen und bei Verwendung mit `wprintf`-Funktionen ein Einzelbytezeichen an.|
|**d**|Integer|Ganze Dezimalzahl mit Vorzeichen|
|**i**|Integer|Ganze Dezimalzahl mit Vorzeichen|
|**o**|Integer|Oktale ganze Zahl ohne Vorzeichen|
|**u**|Integer|Ganze Dezimalzahl ohne Vorzeichen|
|**x**|Integer|Ganze Hexadezimalzahl ohne Vorzeichen; verwendet „abcdef“.|
|**X**|Integer|Ganze Hexadezimalzahl ohne Vorzeichen; verwendet „ABCDEF“.|
|**e**|Gleitkomma|Ein Wert mit Vorzeichen im Format [-]*d.dddd*__e±__*dd*\[*d*], wobei *d* eine Dezimalzahl ist, *dddd* eine oder mehrere Dezimalstellen sind, je nach angegebener Präzision, oder standardmäßig sechs. *dd*\[*d*] stellt zwei oder drei Dezimalstellen dar, je nach [Ausgabeformat](../c-runtime-library/set-output-format.md) und Exponentengröße.|
|**E**|Gleitkomma|Identisch mit dem **e**-Format mit der Ausnahme, dass **E** anstelle von **e** den Exponenten einführt.|
|**f**|Gleitkomma|Ein Wert mit Vorzeichen im Format [–]*dddd* __.__ *dddd*, wobei *dddd* eine oder mehrere Dezimalstellen sind. Die Anzahl der Ziffern vor dem Dezimaltrennzeichen ist abhängig von der Größe der Zahl, und die Anzahl der Ziffern nach dem Dezimaltrennzeichen ist abhängig von der angeforderten Genauigkeit oder standardmäßig sechs.|
|**F**|Gleitkomma|Identisch mit dem Format **f**, außer dass die infinity- und die NaN-Ausgabe groß geschrieben werden.|
|**g**|Gleitkomma|Werte mit Vorzeichen werden im **f**- oder **e**-Format angezeigt, je nachdem, was für den angegebenen Wert und die Genauigkeit kompakter ist. Das **e**-Format wird nur verwendet, wenn der Exponent des Werts kleiner als -4 oder größer als oder gleich dem *precision*-Argument ist. Nachfolgende Nullen werden abgeschnitten, und das Dezimaltrennzeichen wird nur angezeigt, wenn eine oder mehrere Ziffern darauf folgen.|
|**G**|Gleitkomma|Identisch mit dem **g**-Format mit der Ausnahme, dass **E** anstelle von **e** den Exponenten einführt (falls zutreffend).|
|**a**|Gleitkomma|Ein hexadezimaler Gleitkommawert mit Vorzeichen mit doppelter Genauigkeit in der Form [−]0x*h.hhhh*__p±__*dd*, wobei *h.hhhh* die hexadezimalen Ziffern (aus Kleinbuchstaben) der Mantisse sind und *dd* eine oder mehrere Ziffern für den Exponenten darstellt. Die Genauigkeit gibt die Anzahl der Ziffern nach dem Punkt an.|
|**A**|Gleitkomma|Ein hexadezimaler Gleitkommawert mit Vorzeichen mit doppelter Genauigkeit mit der Form [−]0X*h.hhhh*__P±__*dd*, wobei *h.hhhh* die hexadezimalen Ziffern (aus Großbuchstaben) der Mantisse sind und *dd* eine oder mehrere Ziffern für den Exponenten darstellt. Die Genauigkeit gibt die Anzahl der Ziffern nach dem Punkt an.|
|**n**|Zeiger auf eine ganze Zahl|Anzahl der Zeichen, die bisher erfolgreich in den Stream oder Puffer geschrieben wurden. Dieser Wert wird in der ganzen Zahl gespeichert, deren Adresse als Argument angegeben ist. Die Größe des Integers, auf den gezeigt wird, kann durch ein Präfix mit Argumentengrößenangabe gesteuert werden. Der **n**-Bezeichner ist standardmäßig deaktiviert. Weitere Informationen finden Sie im wichtigen Sicherheitshinweis.|
|**p**|Zeigertyp|Zeigt das Argument als Adresse in Hexadezimalziffern an.|
|**s**|String|Gibt bei Verwendung mit `printf`-Funktionen eine Einzelbyte- oder Multibyte-Zeichenfolge und bei Verwendung mit `wprintf`-Funktionen eine Breitzeichenfolge an. Zeichen werden bis zum ersten NULL-Zeichen oder bis zum *precision*-Wert angezeigt.|
|**S**|String|Gibt bei Verwendung mit `printf`-Funktionen eine Breitzeichenfolge und bei Verwendung mit `wprintf`-Funktionen eine Einzelbyte- oder Multibyte-Zeichenfolge an. Zeichen werden bis zum ersten NULL-Zeichen oder bis zum *precision*-Wert angezeigt.|
|**Z**|`ANSI_STRING`- oder `UNICODE_STRING`-Struktur|Wenn die Adresse einer [ANSI_STRING](/windows/win32/api/ntdef/ns-ntdef-string)- oder [UNICODE_STRING](/windows/win32/api/ntdef/ns-ntdef-_unicode_string)-Struktur als Argument übergeben wird, wird die Zeichenfolge, die im Puffer angezeigt wird und auf die vom `Buffer`-Feld der Struktur gezeigt wird, übergeben. Verwenden Sie ein *size*-Längenpräfix von **w**, um ein `UNICODE_STRING`-Argument anzugeben, z.B. `%wZ`. Das `Length`-Feld der Struktur muss auf die Länge der Zeichenfolge in Bytes festgelegt sein. Das `MaximumLength`-Feld der Struktur muss auf die Länge des Puffers in Bytes festgelegt sein.<br /><br /> In der Regel wird das **Z**-Typzeichen nur in Treiberdebugfunktionen mit einer Formatangabe verwendet, z.B. `dbgPrint` und `kdPrint`.|

Ab Visual Studio 2015 entspricht die formatierte Ausgabe dem C99-Standard, wenn das Argument, das einem Gleitkomma-Konvertierungsspezifizierer (**a**, **A**, **e**, **E**, **f**, **F**, **g**, **G**) entspricht, unendlich, unbestimmt oder NaN ist. In dieser Tabelle ist die formatierte Ausgabe aufgeführt:

|value|Output|
|-----------|------------|
|infinity|`inf`|
|Stiller NaN|`nan`|
|Signalisierender NaN|`nan(snan)`|
|Unbestimmter NaN|`nan(ind)`|

All diesen Werten kann ein Vorzeichen vorangestellt werden. Wenn ein Gleitkomma-Konvertierungsspezifizierer*typ* ein Großbuchstabe ist,dann wird die Ausgabe auch in Großbuchstaben formatiert. Wenn der Formatbezeichner beispielsweise `%F` statt `%f` ist, wird infinity als `INF` statt `inf` formatiert. Die `scanf`-Funktionen können diese Zeichenfolgen auch analysieren, damit diese Werte einen Roundtrip für `printf`- und `scanf`-Funktionen durchführen können.

Vor Visual Studio 2015 verwendete die CRT ein anderes, Nicht-Standard-Format für die Ausgabe von unendlichen, unbestimmten oder NaN-Werten:

|value|Output|
|-----------|------------|
|+unendlich|`1.#INF` von *Zufalls Ziffern*|
|- infinity|`-1.#INF` von *Zufalls Ziffern*|
|unbestimmt (mit stillem NaN identisch)|*Ziffern* `.#IND` *Zufalls Ziffern*|
|NaN|*Ziffern* `.#NAN` *Zufalls Ziffern*|

Allen diesen Werte konnte ein Vorzeichen vorangestellt werden und sie wurden möglicherweise je nach Feldbreite und Genauigkeit unterschiedlich formatiert, z.B. mit ungewöhnlichen Effekten. Die Funktion `printf("%.2f\n", INFINITY)` hat `1.#J` ausgegeben, da #INF auf zwei Stellen gerundet wird.

> [!NOTE]
> Wenn das Argument, das `%s` oder `%S` oder dem `Buffer`-Feld des Arguments entspricht, das `%Z` entspricht, ein NULL-Zeiger „(NULL)“ ist, wird es angezeigt.

> [!NOTE]
> In allen Exponentialformaten beträgt die Anzahl der Ziffern des Exponenten, der angezeigt wird, zwei. Es werden nur wenn nötig drei verwendet. Mithilfe der [_set_output_format](../c-runtime-library/set-output-format.md)-Funktion können Sie die Anzahl der angezeigten Ziffern auf drei für die Abwärtskompatibilität mit Code für Visual Studio 2013 und davor festlegen.

> [!IMPORTANT]
> Da das `%n`-Format grundsätzlich unsicher ist, ist es standardmäßig deaktiviert. Wenn `%n` in einer Formatzeichenfolge festgestellt wird, wird der ungültige Parameterhandler wie in [Parametervalidierung](../c-runtime-library/parameter-validation.md) beschrieben aufgerufen. Informationen zum Aktivieren der `%n`-Unterstützung finden Sie unter [_set_printf_count_output](../c-runtime-library/reference/set-printf-count-output.md).

<a name="flags"></a>

## <a name="flag-directives"></a>Flag-Direktiven

Das erste optionale Feld in einer Konvertierungsangabe enthält *Flag-Anweisungen*, 0 oder mehr Flag-Zeichen, die die Ausgaberechtfertigung angeben und die Ausgabe von Zeichen steuern: Leerzeichen, führende Nullen, Dezimalstellen sowie oktale und hexadezimale Präfixe. In einer Konvertierungsangabe können mehr als eine Flag-Anweisung erscheinen, und die Flag-Zeichen können in beliebiger Reihenfolge dargestellt werden.

### <a name="flag-characters"></a>Flag-Zeichen

|Flag|Bedeutung|Standard|
|----------|-------------|-------------|
|**-**|Das Ergebnis mit der angegebenen Feldweite ist linksbündig.|Rechtsbündig.|
|**+**|Verwenden Sie ein Zeichen (+ der -), um dem Ausgabewert ein Präfix hinzuzufügen, wenn dieser einem signed-Typ entspricht.|Das Vorzeichen taucht nur für negative Werte mit Vorzeichen (-) auf.|
|**0**|Wenn *width* das Vorzeichen **0** hat, werden führende Nullen hinzugefügt, bis die minimale Breite erreicht ist. Wenn **0** und **-** jeweils erscheinen, wird **0** ignoriert. Wenn **0** für ein Integerformat angegeben wird (**i**, **u**, **x**, **X**, **o**, **d**) und auch eine Genauigkeitsangabe vorhanden ist, z.B. `%04.d`, wird **0** ignoriert. Wird **0** für das Gleitkommaformat **a** oder **A** angegeben, werden führende Nullen der Mantisse nach dem Präfix `0x` oder `0X` vorangestellt.|Keine Auffüllung.|
|**Leerzeichen** („ “)|Verwenden Sie ein Leerzeichen, um dem Ausgabewert ein Präfix hinzuzufügen, wenn er signiert und positiv ist. Das Leerzeichen wird ignoriert, wenn jeweils das Leerzeichen- und das „+“-Flag erscheinen.|Es wird kein Leerzeichen angezeigt.|
|**#**|Bei Verwendung mit dem Format **o**, **x** oder **X** verwendet das Flag **#** jeweils 0, 0x oder 0X, um jeden Ausgabewert ungleich null ein Präfix hinzuzufügen.|Es wird kein Leerzeichen angezeigt.|
||Bei Verwendung mit dem Format **e**, **E**, **f**, **F**, **a** oder **A**, zwingt das Flag **#** den Ausgabewert dazu, ein Dezimaltrennzeichen zu enthalten.|Dezimaltrennzeichen werden nur dann angezeigt, wenn Ziffern darauf folgen.|
||Bei Verwendung mit dem Format **g** oder **G**, zwingt das Flag **#** den Ausgabewert, ein Dezimaltrennzeichen zu enthalten und verhindert das Abschneiden von Nachkommanullen.<br /><br /> Bei Verwendung mit **c**, **d**, **i**, **u** oder **s** wird dies ignoriert.|Dezimaltrennzeichen werden nur dann angezeigt, wenn Ziffern darauf folgen. Nachfolgende Nullen werden abgeschnitten.|

<a name="width"></a>

## <a name="width-specification"></a>Breitenangabe

In einer Konvertierungsangabe, erscheint das optionale Feld für die Breitenangabe nach jedem *flags*-Zeichen. Das Argument *width* ist eine nicht-negative ganze Dezimalzahl, die die minimale Anzahl von Zeichen steuert, die ausgegeben werden. Wenn die Anzahl der Zeichen im Ausgabewert kleiner als die angegebene Breite ist, werden Leerzeichen links oder rechts neben den Werten hinzugefügt – je nachdem, ob das Flag der Linksausrichtung ( **-** ) angegeben ist – bis die Mindestbreite erreicht ist. Wenn *width* das Vorzeichen 0 hat, werden dem Integer oder den Gleitkommakonvertierungen Nullen hinzugefügt, bis die minimale Breite erreicht ist. Eine Ausnahme ist, wenn die Konvertierung auf infinity oder NaN festgelegt ist.

Die Breitenangabe sorgt nie dafür, dass ein Wert abgeschnitten wird. Wenn die Anzahl der Zeichen im Ausgabewert größer als die angegebene Breite ist oder wenn *width* nicht angegeben ist, werden alle Zeichen des Werts ausgegeben, unterliegen aber der Spezifikation *precision*.

Wenn die Genauigkeitsangabe ein Sternchen (`*`) ist, stellt ein `int`-Argument aus der Argumentliste den Wert bereit. In der Argumentliste muss das *width*-Argument vor dem Wert stehen, der formatiert wird, wie im folgenden Beispiel gezeigt:

`printf("%0*d", 5, 3);  /* 00003 is output */`

Ein fehlender oder kleiner Wert *width* sorgt in einer Konvertierungsangabe nicht dafür, dass ein Ausgabewert abgeschnitten wird. Wenn das Ergebnis einer Konvertierung breiter als der Wert *width* ist, wird das Feld erweitert, damit es das Konvertierungsergebnis aufnehmen kann.

<a name="precision"></a>

## <a name="precision-specification"></a>Genauigkeitsangabe

In einer Konvertierungsangabe gibt das dritte optionale Feld die Genauigkeit an. Es besteht aus einem Punkt (.), gefolgt von einer nicht-negativen, ganzen Dezimalzahl, die je nach Konvertierungstyp die Anzahl der Zeichenfolge, die Anzahl der Dezimalstellen oder die Anzahl von signifikanten ausgegebenen Stellen angibt.

Im Gegensatz zu den Breitenangabe kann die Genauigkeitsangabe den Ausgabewert abschneiden oder auf einen Gleitkommawert aufrunden. Wenn *precision* als 0 angegeben wird und der zu konvertierende Wert 0 beträgt, ist das Ergebnis keine Zeichenausgabe, wie im folgenden Beispiel gezeigt:

`printf( "%.0d", 0 );      /* No characters output */`

Wenn die Genauigkeitsangabe ein Sternchen (\*) ist, stellt ein `int`-Argument aus der Argumentliste den Wert bereit. In der Argumentliste muss das *precision*-Argument vor dem Wert stehen, der formatiert wird, wie im folgenden Beispiel gezeigt:

`printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`

Das *Typ*zeichen bestimmt entweder die Interpretation von *precision* oder die Standardgenauigkeit, wenn *precision* weggelassen wird, wie in der folgenden Tabelle dargestellt.

### <a name="how-precision-values-affect-type"></a>Wie sich Genauigkeitswerte auf den Typ auswirken

|type|Bedeutung|Standard|
|----------|-------------|-------------|
|**a**, **A**|Die Genauigkeit gibt die Anzahl der Ziffern nach dem Punkt an.|Die Standardgenauigkeit beträgt 13. Wenn die Genauigkeit 0 beträgt, wird kein Dezimaltrennzeichen gedruckt, es sei denn, das **#** -Flag wird verwendet.|
|**c**, **C**|Die Genauigkeit hat keine Auswirkung.|Zeichen wird gedruckt.|
|**d**, **i**, **o**, **u**, **x**, **X**|Die Genauigkeit gibt die minimale Anzahl der zu druckenden Ziffern an. Wenn die Anzahl der Ziffern im Argument kleiner als *precision* ist, wird der Ausgabewert auf der linken Seite mit Nullen aufgefüllt. Der Wert wird nicht abgeschnitten, wenn die Anzahl der Ziffern *precision* überschreitet.|Die Standardgenauigkeit beträgt 1.|
|**e**, **E**|Die Genauigkeit gibt die Anzahl der zu druckenden Ziffern nach dem Dezimaltrennzeichen an. Die letzte gedruckte Ziffer ist gerundet.|Die Standardgenauigkeit beträgt 6. Wenn *precision* 0 ist oder der Punkt (.) angezeigt wird, ohne dass eine Zahl folgt, wird kein Dezimaltrennzeichen gedruckt.|
|**f**, **F**|Der Genauigkeitswert gibt die Anzahl der Ziffern nach dem Dezimaltrennzeichen an. Wenn ein Dezimaltrennzeichen angezeigt wird, wird mindestens eine Ziffer davor angezeigt. Der Wert wird auf die entsprechende Anzahl an Stellen gerundet.|Die Standardgenauigkeit beträgt 6. Wenn *precision* 0 beträgt, oder wenn der Punkt (.) ohne eine ihm nachfolgende Zahl angezeigt wird, wird kein Dezimaltrennzeichen gedruckt.|
|**g**, **G**|Die Genauigkeit gibt die maximale Anzahl an gedruckten signifikanten Stellen an.|Sechs signifikante Stellen werden gedruckt, und nachfolgende Nullen werden abgeschnitten.|
|**s**, **S**|Die Genauigkeit gibt die maximale Anzahl der zu druckenden Zeichen an. Es werden nicht mehr als *precision* Zeichen gedruckt.|Zeichen werden gedruckt, bis ein Null-Zeichen gefunden wird.|

<a name="size"></a>

## <a name="argument-size-specification"></a>Angabe der Argumentgröße

In einer Konvertierungsangabe ist das *size*-Feld ein Argumentlängenmodifizierer für den Konvertierungsspezifizierer*typ*. Das *size*-Feld fungiert als Präfix für das *Typ*feld; **hh**, **h**, **j**, **l** (L als Kleinbuchstabe), **L**, **ll**, **t**, **w**, **z**, **I** (i als Großbuchstabe), **I32** und **I64** geben je nach dem Konvertierungsspezifizierer, den sie ändern, die „Größe“ des entsprechenden Arguments an: lang oder kurz, 32 Bit oder 64 Bit, Einzelbytezeichen oder Breitzeichen. Diese Größenpräfixe werden zusammen mit *Typ*zeichen in den Familien `printf` und `wprintf` der Funktionen verwendet, um der Interpretation von Argumentlängen gemäß der Darstellung in der folgenden Tabelle anzugeben. Das *size*-Feld ist für einige Argumenttypen optional. Wenn kein Größenpräfix angegeben ist, konsumiert das Formatierungsprogramm ganzzahlige Argumente, z.B. `char`, `short`, `int`, `long` mit oder ohne Vorzeichen und Aufzählungstypen, wie etwa 32-Bit `int`-Typen und `float`, `double` sowie `long double`, während Gleitkommaargumente als 64-Bit-`double`-Typen konsumiert werden. Dieses Verhalten stimmt mit den standardmäßigen Typerweiterungsregeln für Listen von Variablenargumenten überein. Weitere Informationen zur Typerweiterung bei Argumenten finden Sie unter „Ellipsen und Standardargumente“ in [Postfixausdrücke](../cpp/postfix-expressions.md). Sowohl auf 32-Bit als auch auf 64-Bit-Systemen muss die Konvertierungsangabe eines ganzzahligen 64-Bit-Arguments das Größenpräfix **ll** oder **I64** beinhalten. Andernfalls ist das Verhalten des Formatierungsprogramms nicht definiert.

Einige Typen weisen in 32-Bit- und 64-Bit-Code verschiedene Größen auf. Beispielsweise ist `size_t` in für x86-Systeme kompiliertem Code 32 Bit lang, bei Code für X64-Systeme jedoch 64 Bit lang. Zum Erstellen von plattformunabhängigem Formatierungscode für Typen mit variabler Breite können Sie einen Argumentgrößenmodifizierer mit variabler Breite verwenden. Verwenden Sie alternativ einen Argumentgrößenmodifizierer mit 64-Bit, und stufen Sie den Argumenttyp mit variabler Breite explizit auf 64 Bit herauf. Der Microsoft-spezifische Argumentgrößenmodifizierer **I** (i als Großbuchstabe) verarbeitet Integerargumente mit variabler Breite. Es empfiehlt sich jedoch, die typspezifischen Modifizierer **j**, **t** und **z** für Portabilität zu verwenden.

### <a name="size-prefixes-for-printf-and-wprintf-format-type-specifiers"></a>Größenpräfix für die Formattypspezifizierer printf und wprintf

|Angabe von|Präfix|Mit Typspezifizierer|
|----------------|----------------|-------------------------|
|`char`<br />`unsigned char`|**hh**|**d**, **i**, **o**, **u**, **x** oder **X**|
|`short int`<br />`short unsigned int`|**h**|**d**, **i**, **o**, **u**, **x** oder **X**|
|`__int32`<br />`unsigned __int32`|**I32**|**d**, **i**, **o**, **u**, **x** oder **X**|
|`__int64`<br />`unsigned __int64`|**I64**|**d**, **i**, **o**, **u**, **x** oder **X**|
|`intmax_t`<br />`uintmax_t`|**j** oder **I64**|**d**, **i**, **o**, **u**, **x** oder **X**|
|`long double`|**l** (L als Kleinbuchstabe) oder **L**|**a**, **A**, **e**, **E**, **f**, **F**, **g** oder **G**|
|`long int`<br />`long unsigned int`|**l** (L als Kleinbuchstabe)|**d**, **i**, **o**, **u**, **x** oder **X**|
|`long long int`<br />`unsigned long long int`|**ll** (LL in Kleinbuchstaben)|**d**, **i**, **o**, **u**, **x** oder **X**|
|`ptrdiff_t`|**t** oder **I** (i als Großbuchstabe)|**d**, **i**, **o**, **u**, **x** oder **X**|
|`size_t`|**z** oder **I** (i als Großbuchstabe)|**d**, **i**, **o**, **u**, **x** oder **X**|
|Einzelbytezeichen|**h**|**c** oder **C**|
|Breitzeichen|**l** (L als Kleinbuchstabe) oder **w**|**c** oder **C**|
|Einzelbytezeichenfolge|**h**|**s**, **S** oder **Z**|
|Breitzeichenfolge|**l** (L als Kleinbuchstabe) oder **w**|**s**, **S** oder **Z**|

Die Typen `ptrdiff_t` und `size_t` sind `__int32` oder `unsigned __int32` auf 32-Bit-Plattformen und `__int64` oder `unsigned __int64` auf 64-Bit-Plattformen. Die Größenpräfixe **I** (i als Großbuchstabe), **j**, **t** und **z** übernehmen die richtige Argumentbreite für die Plattform.

Obwohl `long double` in Visual C++ ein gesonderter Typ ist, hat er die gleiche interne Darstellung wie `double`.

Ein **hc**- oder **hC**-Typspezifizierer ist mit **c** in `printf`-Funktionen und mit **C** in `wprintf`-Funktionen synonym. Ein **lc**-, **lC**-, **wc**- oder **wC**-Typspezifizierer ist mit **C** in `printf`-Funktionen und mit **c** in `wprintf`-Funktionen synonym. Ein **hs**- oder **hS**-Typspezifizierer ist mit **s** in `printf`-Funktionen und mit **S** in `wprintf`-Funktionen synonym. Ein **ls**-, **lS**-, **ws**- oder **wS**-Typspezifizierer ist mit **S** in `printf`-Funktionen und mit **s** in `wprintf`-Funktionen synonym.

> [!NOTE]
> **Microsoft-spezifisch:** Die Präfixe " **i** " (Großbuchstabe i), " **i32**", " **I64**" und " **w** Argument size Modifizierer" sind Microsoft-Erweiterungen und sind nicht ISO-kompatibel. Das **h**-Präfix, wenn es mit Daten des Typs `char` und das **I**-Präfix (Kleinbuchstabe „l“), wenn es mit Daten des Typs `double` verwendet wird, sind Microsoft-Erweiterungen.

## <a name="see-also"></a>Weitere Informationen

[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[printf_p Positional Parameters (printf_p-Positionsparameter)](../c-runtime-library/printf-p-positional-parameters.md)
