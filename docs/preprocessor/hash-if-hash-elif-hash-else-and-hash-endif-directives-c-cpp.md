---
title: '##if-, #elif-, #else- und #endif-Anweisungen (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#else'
- '#endif'
- '#if'
- '#elif'
- defined
- __has_include
helpviewer_keywords:
- '#elif directive'
- conditional compilation, directives
- endif directive (#endif)
- preprocessor, directives
- '#else directive'
- '#endif directive'
- if directive (#if)
- else directive (#else)
- '#if directive'
- elif directive (#elif)
- defined directive
ms.assetid: c77a175f-6ca8-47d4-8df9-7bac5943d01b
ms.openlocfilehash: acbc54a80573bbbf29ad5cf67e7e5fd9351eeaa3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231597"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>#if-, #elif-, #else-und #endif-Direktiven (C/C++)

Die **#if** -Direktive steuert die Kompilierung von Teilen einer Quelldatei durch die Anweisungen **#elif**, **#else**und **#EndIf** . Wenn der Ausdruck, den Sie schreiben (nach dem **#if**) einen Wert ungleich 0 (null) aufweist, wird die Zeilen Gruppe, die unmittelbar auf die **#if** Direktive folgt, in der Übersetzungseinheit beibehalten.

## <a name="grammar"></a>Grammatik

*bedingt* : \
&nbsp;&nbsp;&nbsp;&nbsp;*if-Part elif-Parts*<sub>opt</sub> *else-Part*<sub>opt</sub> *EndIf-Line*

*if-Part* : \
&nbsp;&nbsp;&nbsp;&nbsp;*If-Line-Text*

*if-Line* : \
&nbsp;&nbsp;&nbsp;&nbsp;**#if** *konstanter Ausdruck*\
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef** *Bezeichner*\
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef** *Bezeichner*

*elif-Parts* : \
&nbsp;&nbsp;&nbsp;&nbsp;*Elif-Zeilen Text*\
&nbsp;&nbsp;&nbsp;&nbsp;*Elif-Parts elif-Line-Text*

*elif-Line* : \
&nbsp;&nbsp;&nbsp;&nbsp;**#elif**  *konstanter Ausdruck*

*else-Part* : \
&nbsp;&nbsp;&nbsp;&nbsp;*Else-Zeilen Text*

*else-Zeile* : \
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*EndIf-Zeile* : \
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

## <a name="remarks"></a>Bemerkungen

Jeder **#if** Direktive in einer Quelldatei muss eine schließende **#EndIf** Direktive zugeordnet werden. Es kann eine beliebige Anzahl von **#elif** Direktiven zwischen den **#if** -und **#EndIf** Direktiven angezeigt werden, es ist jedoch höchstens eine **#else** Direktive zulässig. Die **#else** -Direktive muss, falls vorhanden, die letzte Direktive vor **#EndIf**sein.

Die **#if**-, **#elif**-, **#else**-und **#EndIf** -Direktiven können in den *Text* Teilen anderer **#if** Direktiven geschachtelt werden. Jede **Gesch#else**-, **#elif**-oder **#EndIf** -Direktive gehört der nächstgelegenen vorangehenden **#if** -Direktive an.

Alle bedingten Kompilierungs Direktiven, wie z. b. **#if** und **#ifdef**, müssen eine schließende **#EndIf** Direktive vor dem Dateiende erfüllen. Andernfalls wird eine Fehlermeldung generiert. Wenn Includedateien bedingte Kompilierungsanweisungen enthalten, müssen sie die gleichen Bedingungen erfüllen: Am Ende der Includedatei dürfen sich keine bedingten Kompilierungsanweisungen ohne Entsprechung befinden.

Die Makro Ersetzung erfolgt innerhalb des Teils der Zeile, der auf einen **#elif** Befehl folgt, sodass ein Makro *-Ausdruck in Constant-Expression*verwendet werden kann.

Der Präprozessor wählt eine der angegebenen Vorkommen von *Text* zur weiteren Verarbeitung aus. Ein in *Text* angegebener Block kann eine beliebige Text Sequenz sein. Er kann mehr als eine Zeile umfassen. Normalerweise ist *Text* Programmtext, der für den Compiler oder den Präprozessor eine Bedeutung hat.

Der Präprozessor verarbeitet den ausgewählten *Text* und übergibt ihn an den Compiler. Wenn der *Text* Präprozessordirektiven enthält, führt der Präprozessor diese Anweisungen aus. Nur Textblöcke, die vom Präprozessor ausgewählt werden, werden kompiliert.

Der Präprozessor wählt ein einzelnes *Text* Element aus, indem er den konstanten Ausdruck nach jeder **#if** oder **#elif** Direktive auswertet, bis er einen konstanten Ausdruck (ungleich null) findet. Er wählt den gesamten Text (einschließlich anderer Präprozessordirektiven, die mit beginnen **#** ) bis zu dem zugeordneten **#elif**, **#else**oder **#EndIf**aus.

Wenn alle Vorkommen von *Constant-Expression* "false" sind oder wenn keine **#elif** Direktiven angezeigt werden, wählt der Präprozessor den TextBlock nach der **#else** -Klausel aus. Wenn keine **#else** -Klausel vorhanden ist und alle Instanzen von *Constant-Expression* im **#if** -Block false sind, wird kein TextBlock ausgewählt.

*Constant-Expression* ist ein ganzzahliger konstanter Ausdruck mit diesen zusätzlichen Einschränkungen:

- Ausdrücke müssen einen ganzzahligen Typ aufweisen und können nur ganzzahlige Konstanten, Zeichen Konstanten und den **definierten** Operator enthalten.

- Der Ausdruck kann nicht **`sizeof`** oder einen Typumwandlungs Operator verwenden.

- Die Zielumgebung kann möglicherweise nicht alle Bereiche von ganzen Zahlen darstellen.

- Die Übersetzung repräsentiert **`int`** den Typ auf die gleiche Weise wie der Typ **`long`** und **`unsigned int`** die gleiche Art wie **`unsigned long`** .

- Das Konvertierungsprogramm kann Zeichenkonstanten in einen Satz von Codewerten übersetzen, die sich vom Satz für die Zielumgebung unterscheiden. Um die Eigenschaften der Zielumgebung zu bestimmen, verwenden Sie eine APP, die für diese Umgebung erstellt wurde, um die Werte der Grenzwerte zu überprüfen *. H* -Makros.

- Der Ausdruck darf die Umgebung nicht Abfragen und muss von den Implementierungsdetails auf dem Bereitstellungs Zielcomputer isoliert bleiben.

## <a name="preprocessor-operators"></a>Präprozessor-Operatoren

### <a name="defined"></a>definiert

Der **definierte** Präprozessoroperator kann in speziellen konstanten Ausdrücken verwendet werden, wie in der folgenden Syntax gezeigt:

> **definiert (** *Bezeichner* **)**\
> **definierter** *Bezeichner*

Dieser Konstante Ausdruck gilt als true (ungleich null), wenn der *Bezeichner* aktuell definiert ist. Andernfalls ist die Bedingung "false" (0). Ein Bezeichner, der als leerer Text definiert wird, wird als definiert betrachtet. Der **definierte** Operator kann in einem **#if** und einer **#elif** -Anweisung verwendet werden, aber nirgendwo sonst.

Im folgenden Beispiel steuern die **#if** -und **#EndIf** Direktiven die Kompilierung von einem von drei Funktionsaufrufen:

```C
#if defined(CREDIT)
    credit();
#elif defined(DEBIT)
    debit();
#else
    printerror();
#endif
```

Der Funktionsaufruf an `credit` wird kompiliert, wenn der Bezeichner `CREDIT` definiert ist. Wenn der Bezeichner `DEBIT` definiert ist, wird der Funktionsaufruf an `debit` kompiliert. Wenn keiner der Bezeichner definiert ist, wird der Aufruf an `printerror` kompiliert. `CREDIT`Und `credit` sind unterschiedliche Bezeichner in C und C++, da sich ihre Fälle unterscheiden.

Die Anweisungen für die bedingte Kompilierung im folgenden Beispiel gehen von einer zuvor definierten symbolischen Konstante aus, die `DLEVEL` heißt.

```C
#if DLEVEL > 5
    #define SIGNAL  1
    #if STACKUSE == 1
        #define STACK   200
    #else
        #define STACK   100
    #endif
#else
    #define SIGNAL  0
    #if STACKUSE == 1
        #define STACK   100
    #else
        #define STACK   50
    #endif
#endif
#if DLEVEL == 0
    #define STACK 0
#elif DLEVEL == 1
    #define STACK 100
#elif DLEVEL > 5
    display( debugptr );
#else
    #define STACK 200
#endif
```

Der erste **#if** -Block zeigt zwei Sätze von **#if**-, **#else**-und **#EndIf** -Direktiven an. Der erste Satz von Direktiven wird nur verarbeitet, wenn `DLEVEL > 5` "true" ist. Andernfalls werden die Anweisungen nach der **#else** verarbeitet.

Die Anweisungen **#elif** und **#else** im zweiten Beispiel werden verwendet, um eine von vier Optionen basierend auf dem Wert von zu erstellen `DLEVEL` . Die Konstante `STACK` ist auf 0, 100 oder 200 festgelegt, abhängig von der Definition von `DLEVEL`. Wenn `DLEVEL` größer als 5 ist, wird die Anweisung

```C
#elif DLEVEL > 5
display(debugptr);
```

wird kompiliert und ist `STACK` nicht definiert.

Eine übliche Verwendung für die bedingte Kompilierung besteht darin, mehrere Inklusionen derselben Headerdatei zu verhindern. In C++, in denen Klassen häufig in Header Dateien definiert werden, können Konstrukte wie diese verwendet werden, um mehrere Definitionen zu verhindern:

```cpp
/*  EXAMPLE.H - Example header file  */
#if !defined( EXAMPLE_H )
#define EXAMPLE_H

class Example
{
    //...
};

#endif // !defined( EXAMPLE_H )
```

Der vorangehende Code überprüft, ob die symbolische Konstante `EXAMPLE_H` definiert ist. Wenn dies der Fall ist, wurde die Datei bereits eingeschlossen und muss nicht erneut verarbeitet werden. Wenn dies nicht der Fall ist, wird die Konstante `EXAMPLE_H` definiert, um EXAMPLE.H als bereits verarbeitet zu markieren.

### <a name="__has_include"></a>__has_include

**Visual Studio 2017 Version 15,3 und**höher: bestimmt, ob ein Bibliotheks Header zum einschließen verfügbar ist:

```cpp
#ifdef __has_include
#  if __has_include(<filesystem>)
#    include <filesystem>
#    define have_filesystem 1
#  elif __has_include(<experimental/filesystem>)
#    include <experimental/filesystem>
#    define have_filesystem 1
#    define experimental_filesystem
#  else
#    define have_filesystem 0
#  endif
#endif
```

## <a name="see-also"></a>Weitere Informationen

[Präprozessoranweisungen](../preprocessor/preprocessor-directives.md)
