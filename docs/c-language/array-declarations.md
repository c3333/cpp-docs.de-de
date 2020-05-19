---
title: Arraydeklarationen
ms.date: 11/04/2016
helpviewer_keywords:
- multidimensional arrays
- declaring arrays
- arrays [C++], declaring
ms.assetid: 5f958b97-cef0-4058-bbc6-37c460aaed9b
ms.openlocfilehash: 4bc75e86601da77758490544cc5b02c485dcee46
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313544"
---
# <a name="array-declarations"></a>Arraydeklarationen

Eine "Arraydeklaration" benennt das Array und gibt den Typ der Elemente an. Hiermit kann auch die Anzahl von Elementen im Array definiert werden. Eine Variable mit Arraytyp wird als Zeiger auf den Typ der Arrayelemente betrachtet.

## <a name="syntax"></a>Syntax

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarationsspezifizierer* *Initialisierungsdeklaratorliste*<sub>opt</sub> **;**

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Initialisierungsdeklaratorliste*  **,**  *Initialisierungsdeklarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator* **=** *Initialisierer*

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Zeiger*<sub>opt</sub> *direkter-Deklarator*

*direct-declarator*:/\* Ein Funktionsdeklarator \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direkter-Deklarator*  **[**  *konstanter-Ausdruck*<sub>opt</sub> **]**

Da *constant-expression* optional ist, hat die Syntax zwei Formen:

- Die erste Form definiert eine Arrayvariable. Das *constant-expression*-Argument innerhalb der Klammern gibt die Anzahl von Elementen im Array an. *constant-expression*, falls vorhanden, muss einen ganzzahligen Typ und einen Wert aufweisen, der größer als null ist. Jedes Element weist den Typ auf, der von *type-specifier* angegeben ist, der ein beliebiger Typ außer `void` sein kann. Ein Arrayelement darf kein Funktionstyp sein.

- Die zweite Form deklariert eine Variable, die an einer anderen Stelle definiert wurde. Sie lässt das *constant-expression*-Argument in Klammern weg, aber nicht die Klammern. Sie können diese Form nur dann verwenden, wenn Sie das Array zuvor initialisiert und als Parameter oder als Verweis auf ein Array deklariert haben, das explizit an anderer Stelle im Programm definiert ist.

Bei beiden Formen vergibt *direct-declarator* den Namen der Variable und kann den Typ der Variable ändern. Die Klammern ( **[ ]** ) nach *direct-declarator* ändern den Deklarator in einen Arraytyp.

Typqualifizierer können in der Deklaration eines Objekts des Arraytyps enthalten sein, die Qualifizierer gelten jedoch für die Elemente und nicht für das Array selbst.

Sie können ein Array von Arrays (ein "mehrdimensionales" Array) deklarieren, indem Sie der Arraydeklaration eine Liste konstanter Ausdrücke in Klammern in dieser Form nachstellen:

> *Typspezifizierer* *Deklarator* **[** *konstanter-Ausdruck* **]** **[** *konstanter-Ausdruck* **]** ...

Jeder *constant-expression* in Klammern definiert die Anzahl von Elementen in der angegebenen Dimension: zweidimensionale Arrays haben zwei Ausdrücke in Klammern, dreidimensionale Arrays haben drei usw. Sie können den ersten konstanten Ausdruck weglassen, wenn Sie das Array initialisiert und es als Parameter oder als Verweis auf ein Array deklariert haben, das explizit an anderer Stelle im Programm definiert ist.

Sie können Arrays von Zeigern auf verschiedene Objekttypen definieren, indem Sie komplexe Deklaratoren verwenden, wie unter [Interpretieren von komplexeren Deklaratoren](../c-language/interpreting-more-complex-declarators.md) beschrieben.

Arrays werden zeilenweise gespeichert. Zum Beispiel besteht das nächste Array aus zwei Zeilen mit jeweils drei Spalten:

```C
char A[2][3];
```

Die drei Spalten der ersten Zeile werden zuerst gespeichert, danach folgen die drei Spalten der zweiten Zeile. Dies bedeutet, dass sich der letzte Feldindex am schnellsten unterscheidet.

Um auf ein einzelnes Element eines Arrays zu verweisen, verwenden Sie einen Subscriptausdruck, wie unter [Postfix-Operatoren](../c-language/postfix-operators.md) beschrieben.

## <a name="examples"></a>Beispiele

Diese Beispiele veranschaulichen Arraydeklarationen:

```C
float matrix[10][15];
```

Das zweidimensionale Array namens `matrix` verfügt über 150 Elemente, von denen jedes den Typ **float** aufweist.

```C
struct {
    float x, y;
} complex[100];
```

Dies ist eine Deklaration eines Arrays von Strukturen. Dieses Array weist 100 Elemente auf. Jedes Element ist eine Struktur, die zwei Member enthält.

```C
extern char *name[];
```

Diese Anweisung deklariert den Typ und den Namen eines Arrays von Zeigern auf `char`. Die tatsächliche Definition von `name` ist an anderer Stelle zu finden.

**Microsoft-spezifisch**

Der Typ einer ganzen Zahl, die zum Speichern der maximalen Größe eines Arrays erforderlich ist, d.h. die Größe von **size_t**. **size_t** ist in der Headerdatei STDDEF.H definiert und repräsentiert eine `unsigned int` (ganze Zahl ohne Vorzeichen) aus dem Bereich 0x00000000 bis 0x7CFFFFFF.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Deklaratoren und Variablendeklarationen](../c-language/declarators-and-variable-declarations.md)
