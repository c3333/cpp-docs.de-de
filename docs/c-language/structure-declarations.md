---
title: Strukturdeklarationen
ms.date: 11/04/2016
helpviewer_keywords:
- structure declarations
- anonymous structures
- types [C], declarations
- structure members
- embedded structures
ms.assetid: 5be3be77-a236-4153-b574-7aa77675df7f
ms.openlocfilehash: 3b9aa30cfeecbd60fda61e6a484043c82c9a3b28
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217050"
---
# <a name="structure-declarations"></a>Strukturdeklarationen

Eine "Strukturdeklaration" benennt einen Typ und gibt eine Sequenz von Variablenwerten an (so genannte "Member" oder "Felder" der Struktur), die unterschiedliche Typen aufweisen können. Ein optionaler Bezeichner, "Tag" genannt, gibt den Namen des Strukturtyps an und kann in nachfolgenden Verweisen für den Strukturtyp verwendet werden. Eine Variable des Strukturtyps enthält die gesamte Sequenz, die durch diesen Typ definiert ist. Strukturen in C ähneln den Typen, die als "Datensätze" in anderen Sprachen bekannt sind.

## <a name="syntax"></a>Syntax

*struct-or-union-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktur-oder-Union* *Bezeichner*<sub>opt</sub> **{** *Strukturdeklarationsliste* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktur-oder-Union* *Bezeichner*

*struct-or-union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`struct`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`union`**

*struct-declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Strukturdeklarationsliste* *Strukturdeklaration*

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Spezifizierer-/Qualifiziererliste* *Strukturdeklaratorliste* **;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typspezifizierer* *Spezifizierer-/Qualifiziererliste*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typqualifizierer* *Spezifizierer-/Qualifiziererliste*<sub>opt</sub>

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Strukturdeklarator* *Strukturdeklaratorliste* **,** *Strukturdeklarator*

*struct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typspezifizierer* *Deklarator*<sub>opt</sub> **:** *konstanter-Ausdruck*

Die Deklaration eines Strukturtyps hält keinen Platz für eine Struktur bereit. Es ist nur eine Vorlage für spätere Deklarationen von Strukturvariablen.

Ein zuvor definierter *Identifier* (Tag) kann verwendet werden, um auf einen Strukturtyp zu verweisen, der an anderer Stelle definiert ist. In diesem Fall kann *struct-declaration-list* nicht wiederholt werden, solange die Definition sichtbar ist. Deklarationen von Zeigern auf Strukturen und Typedefs für Strukturtypen können das Strukturtag verwenden, bevor der Strukturtyp definiert ist. Allerdings muss die Strukturdefinition vor jeder tatsächlichen Verwendung der Größe der Felder gefunden werden. Dies ist eine unvollständige Definition des Typs und des Typ-Tags. Damit diese Definition abgeschlossen werden kann, muss eine Typdefinition später im gleichen Bereich angezeigt werden.

Mit *struct-declaration-list* werden die Typen und Namen der Strukturmember angegeben. Ein *struct-declaration-list*-Argument enthält mindestens eine Variable oder Bitfelddeklaration.

Jede Variable, die in der *struct-declaration-list* deklariert wurde, wird als Member des Strukturtyps definiert. Variablendeklarationen in *struct-declaration-list* verfügen über das gleiche Format wie andere Variablendeklarationen, die in diesem Abschnitt erläutert werden, mit der Ausnahme, dass die Deklarationen keine Speicherklassenspezifizierer oder -initialisierer enthalten dürfen. Die Strukturmember können alle Variablentypen mit Ausnahme von **`void`** , einen unvollständigen Typ oder einen Funktionstyp aufweisen.

Ein Member kann nicht mit dem Typ oder der Struktur deklariert werden, in dem/der er enthalten ist. Allerdings kann ein Member als Zeiger auf den Strukturtyp deklariert werden, in dem er angezeigt wird, solange der Strukturtyp über einen Tag verfügt. Dadurch können Sie verknüpfte Listen von Strukturen erstellen.

Für Strukturen gilt derselbe Gültigkeitsbereich wie für andere Bezeichner. Strukturbezeichner müssen sich von anderen Struktur-, Union- und Enumerations-Tags derselben Sichtbarkeit unterscheiden.

Jede *struct-declaration* in einer *struct-declaration-list* muss in der Liste eindeutig sein. Allerdings müssen sich Bezeichnernamen in einer *struct-declaration-list* nicht von gewöhnlichen Variablennamen oder Bezeichnern in anderen Strukturdeklarationslisten unterscheiden.

Auf geschachtelte Strukturen kann auch so zugegriffen werden, als wären sie auf der Dateibereichsebene deklariert wurden. Beispielsweise bei dieser Deklaration:

```C
struct a
{
    int x;
    struct b
    {
      int y;
    } var2;
} var1;
```

diese Deklarationen sind beide gültig:

```C
struct a var3;
struct b var4;
```

## <a name="examples"></a>Beispiele

Diese Beispiele veranschaulichen Strukturdeklarationen:

```C
struct employee   /* Defines a structure variable named temp */
{
    char name[20];
    int id;
    long class;
} temp;
```

Die `employee`-Struktur hat drei Member: `name`, `id` und `class`. Der `name`-Member ist ein Array mit 20 Elementen, und `id` und `class` sind einfache Member vom Typ **`int`** bzw. **`long`** . Der Bezeichner `employee` ist der Strukturbezeichner.

```C
struct employee student, faculty, staff;
```

Dieses Beispiel definiert drei Strukturvariablen: `student`, `faculty` und `staff`. Jede Struktur verfügt über die gleiche Liste von drei Membern. Member müssen den Strukturtyp `employee` im vorherigen Beispiel definiert haben.

```C
struct           /* Defines an anonymous struct and a */
{                /* structure variable named complex  */
    float x, y;
} complex;
```

Die `complex`-Struktur verfügt über zwei Member vom Typ **`float`** : `x` und `y`. Der Strukturtyp hat kein Tag und ist somit unbenannt oder anonym.

```C
struct sample   /* Defines a structure named x */
{
    char c;
    float *pf;
    struct sample *next;
} x;
```

Die ersten beiden Member der Struktur sind eine **`char`** -Variable und ein Zeiger auf einen **`float`** -Wert. Der dritte Member, `next`, wird als Zeiger auf den definierten Strukturtyp deklariert (`sample`).

Anonyme Strukturen können nützlich sein, wenn der angegebene Tag nicht benötigt wird. Dies ist der Fall, wenn eine Deklaration alle Strukturinstanzen definiert. Zum Beispiel:

```C
struct
{
    int x;
    int y;
} mystruct;
```

Eingebettete Strukturen sind häufig anonym.

```C
struct somestruct
{
    struct    /* Anonymous structure */
    {
        int x, y;
    } point;
    int type;
} w;
```

**Microsoft-spezifisch**

Der Compiler lässt ein Array ohne Größenangabe oder ein Array der Größe 0 (null) als letzten Member einer Struktur zu. Dies kann hilfreich sein, wenn sich die Größe eines konstanten Arrays in verschiedenen Situationen unterscheidet. Die Deklaration einer solchen Struktur sieht wie folgt aus:

**`struct`** *Bezeichner* **{** *mehrere-Deklarationen* *Type* <em>Arrayname</em> **\[]; };**

Arrays ohne Größenangabe können nur als letzter Member einer Struktur angegeben werden. Die Strukturen, die Arraydeklarationen ohne Größenangabe enthalten, können in andere Strukturen geschachtelt werden, solange keine weiteren Member in anderen einschließenden Strukturen deklariert werden. Arrays von solchen Strukturen sind nicht zulässig. Der **`sizeof`** -Operator nimmt bei Anwendung auf eine Variable dieses Typs oder auf den Typ selbst 0 für die Größe des Arrays an.

Strukturdeklarationen können auch ohne Deklaration angegeben werden, wenn diese Member einer anderen Struktur oder Union sind. Die Feldnamen werden in die einschließende Struktur hochgestuft. Eine namenlose Struktur sieht beispielsweise wie folgt aus:

```C
struct s
{
    float y;
    struct
    {
        int a, b, c;
    };
    char str[10];
} *p_s;
.
.
.
p_s->b = 100;  /* A reference to a field in the s structure */
```

Weitere Informationen zu Strukturverweisen erhalten Sie unter [Struktur- und Unionmember](../c-language/structure-and-union-members.md).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Deklaratoren und Variablendeklarationen](../c-language/declarators-and-variable-declarations.md)
