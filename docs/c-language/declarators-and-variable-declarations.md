---
title: Deklaratoren und Variablendeklarationen
ms.date: 11/04/2016
helpviewer_keywords:
- declaring variables, declarators
- declarators, definition
- declaring variables, declaration statements
ms.assetid: 5fd67a6a-3a6a-4ec9-b257-3f7390a48d40
ms.openlocfilehash: 928de4b1724577a9fdb282f5109b4b5d0b31c4e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234524"
---
# <a name="declarators-and-variable-declarations"></a>Deklaratoren und Variablendeklarationen

Im folgenden Abschnitt wird die Form und Bedeutung von Deklarationen für die Variablentypen in dieser Liste beschrieben. Insbesondere wird in den übrigen Abschnitten erklärt, wie Sie Folgendes deklarieren:

|Variablentyp|Beschreibung|
|----------------------|-----------------|
|[Einfache Variablen](../c-language/simple-variable-declarations.md)|Einzelwertvariablen vom Typ "Ganzzahl" oder "Gleitkomma"|
|[Arrays](../c-language/array-declarations.md)|Variablen, die aus einer Auflistung von Elementen mit demselben Typ bestehen|
|[Zeiger](../c-language/pointer-declarations.md)|Variablen, die auf andere Variablen zeigen und die Speicherorte anderer Variablen (in Form von Adressen) anstelle von Werten enthalten|
|[Enumerationsvariablen](../c-language/c-enumeration-declarations.md)|Einfache Variablen mit ganzzahligem Typ, die einen Wert aus einem Satz benannter ganzzahliger Konstanten enthalten|
|[Strukturen](../c-language/structure-declarations.md)|Variablen, die aus einer Auflistung von Werten bestehen, die unterschiedliche Typen aufweisen können|
|[Unions](../c-language/union-declarations.md)|Variablen, die aus mehreren Werten unterschiedlichen Typs bestehen, die denselben Speicherplatz belegen|

Ein Deklarator ist der Teil einer Deklaration, der den Namen angibt, der im Programm eingefügt werden soll. Dies kann Modifizierer wie <strong>\*</strong> (pointer-to) sowie jegliche Microsoft-Schlüsselwörter für die Aufrufkonvention einschließen.

**Microsoft-spezifisch**

Im Deklarator

```C
__declspec(thread) char *var;
```

ist `char` der Typspezifizierer, `__declspec(thread)` und `*` sind die Modifizierer und `var` ist der Name des Bezeichners.

**Ende Microsoft-spezifisch**

Sie verwenden Deklaratoren, um Wertarrays, Zeiger auf Werte und Funktionen, die Werte eines angegebenen Typs zurückgeben, zu deklarieren. Deklaratoren kommen in den Array- und Zeigerdeklarationen vor, die weiter unten in diesem Abschnitt beschrieben werden.

## <a name="syntax"></a>Syntax

*declarator*:<br/>
&nbsp;&nbsp;*Zeiger*<sub>opt</sub> *direkter-Deklarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(**  *Deklarator*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direkter-Deklarator*  **[**  *konstanter-Ausdruck*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direkter-Deklarator*  **(**  *Parametertypliste*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direkter-Deklarator*  **(**  *Bezeichnerliste*<sub>opt</sub> **)**

*pointer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Typqualifiziererliste*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Typqualifiziererliste*<sub>opt</sub> *Zeiger*

*type-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier-list type-qualifier*

> [!NOTE]
> Informationen zur Syntax für *declaration* finden Sie in der [Übersicht über Deklarationen](../c-language/overview-of-declarations.md). Informationen zur Syntax, die auf einen *declarator* verweist, finden Sie unter [Zusammenfassung der C-Sprachsyntax](../c-language/c-language-syntax-summary.md).

Wenn ein Deklarator aus einem unveränderten Bezeichner besteht, hat das deklarierte Element einen Basistyp. Wenn ein Sternchen (<strong>\*</strong>) auf der linken Seite eines Bezeichners steht, wird der Typ in einen Zeigertyp geändert. Wenn auf den Bezeichner eckige Klammern ( **[ ]** ) folgen, wird der Typ in einen Arraytyp geändert. Wenn auf den Bezeichner Klammern folgen, wird der Typ in einen Funktionstyp geändert. Weitere Informationen zum Interpretieren der Rangfolge in den Deklarationen finden Sie unter [Interpretieren von komplexeren Deklaratoren](../c-language/interpreting-more-complex-declarators.md).

Jeder Deklarator deklariert mindestens einen Bezeichner. Ein Deklarator muss einen Typspezifizierer enthalten, um eine vollständige Deklaration zu sein. Der Typspezifizierer gibt den Typ der Elemente eines Arraytyps, den Typ des von einem Zeigertyp angesprochenen Objekts oder den Rückgabetyp einer Funktion an.

[Array](../c-language/array-declarations.md)- und [Zeiger](../c-language/pointer-declarations.md)-Deklarationen werden weiter unten in diesem Abschnitt ausführlicher beschrieben. Die folgenden Beispiele veranschaulichen ein paar einfache Formen von Deklaratoren:

```C
int list[20]; // Declares an array of 20 int values named list
char *cp;     // Declares a pointer to a char value
double func( void ); // Declares a function named func, with no
                     // arguments, that returns a double value
int *aptr[10] // Declares an array of 10 pointers
```

**Microsoft-spezifisch**

Der Microsoft C-Compiler lässt eine unbeschränkte Anzahl von Deklaratoren zu, die einen arithmetischen, Struktur- oder Union-Typ ändern können. Die Anzahl wird nur durch den verfügbaren Speicher beschränkt.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Deklarationen und Typen](../c-language/declarations-and-types.md)
