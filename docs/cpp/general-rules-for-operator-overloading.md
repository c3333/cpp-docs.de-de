---
title: Allgemeine Regeln für die Überladung von Operatoren
ms.date: 11/04/2016
helpviewer_keywords:
- operator overloading [C++], rules
ms.assetid: eb2b3754-35f7-4832-b1da-c502893dc0c7
ms.openlocfilehash: 0c8cbea3411acd50be376ae0853a143af57458f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188593"
---
# <a name="general-rules-for-operator-overloading"></a>Allgemeine Regeln für die Überladung von Operatoren

Die folgenden Regeln schränken die Art und Weise ein, wie überladene Operatoren implementiert werden. Allerdings gelten Sie nicht für die [New](../cpp/new-operator-cpp.md) -und [Delete](../cpp/delete-operator-cpp.md) -Operatoren, die separat abgedeckt werden.

- Sie können keine neuen Operatoren definieren, wie z **. b..**

- Sie können die Bedeutung von Operatoren nicht neu definieren, wenn sie auf integrierte Datentypen angewendet werden.

- Überladene Operatoren müssen entweder eine nicht statische Klassenmemberfunktion oder eine globale Funktion sein. Eine globale Funktion, die auf private oder geschützte Klassenmember zugreifen muss, muss als Friend dieser Klasse deklariert sein. Eine globale Funktion muss mindestens ein Argument annehmen, das vom Klassen- oder Aufzählungstyp ist, oder das ein Verweis auf einen Klassen- oder Aufzählungstyp ist. Beispiel:

    ```cpp
    // rules_for_operator_overloading.cpp
    class Point
    {
    public:
        Point operator<( Point & );  // Declare a member operator
                                     //  overload.
        // Declare addition operators.
        friend Point operator+( Point&, int );
        friend Point operator+( int, Point& );
    };

    int main()
    {
    }
    ```

   Das vorhergehende Codebeispiel deklariert den Less Than-Operator als Memberfunktion. Allerdings werden die Additionsoperatoren als globale Funktionen deklariert, die Friend-Zugriff haben. Beachten Sie, dass mehr als eine Implementierung für einen angegebenen Operator bereitgestellt werden kann. Im Fall des vorhergehenden Additionsoperators werden die beiden Implementierungen bereitgestellt, um Kommutativität zu ermöglichen. Es ist ebenso wahrscheinlich, dass Operatoren, die einer `Point`eine `Point` hinzufügen, **int** zu einem `Point`usw., möglicherweise implementiert werden.

- Operatoren unterliegen der Priorität, Gruppierung und Anzahl von Operanden, die durch ihre typische Verwendung mit integrierten Typen vorgegeben werden. Daher gibt es keine Möglichkeit, das Konzept "Hinzufügen von 2 und 3 zu einem Objekt vom Typ" `Point`"auszudrücken, wobei erwartet wird, dass 2 der *x* -Koordinate hinzugefügt wird und 3 der *y* -Koordinate hinzugefügt wird.

- Unäre Operatoren, die als Memberfunktionen deklariert werden, akzeptieren keine Argumente. Wenn sie als globale Funktionen deklariert werden, nehmen sie ein Argument an.

- Binäre Operatoren, die als Memberfunktionen deklariert werden, akzeptieren ein Argument. Wenn sie als globale Funktionen deklariert werden, nehmen sie zwei Argumente an.

- Wenn ein Operator entweder als unärer oder als binärer Operator ( __&__ , __*__ , __+__ und __-__ ) verwendet werden kann, können Sie jede Verwendung separat überladen.

- Überladene Operatoren können keine Standardargumente haben.

- Alle überladenen Operatoren außer Zuweisung (**Operator =** ) werden von abgeleiteten Klassen geerbt.

- Das erste Argument für mit Memberfunktionen überladene Operatoren weist immer den Klassentyp des Objekts auf, für das der Operator aufgerufen wird (die Klasse, in der der Operator deklariert ist, oder eine Klasse, die von dieser Klasse abgeleitet ist). Es werden keine Konvertierungen für das erste Argument bereitgestellt.

Beachten Sie, dass die Bedeutung aller Operatoren vollständig geändert werden kann. Dies schließt die Bedeutung der Address-of ( **&** )-, Zuweisungs-( **=** ) und Funktions aufrufoperatoren ein. Auch Identitäten, auf denen integrierte Typen basieren können, können mithilfe der Operatorüberladung geändert werden. Beispielsweise sind die folgenden vier Anweisungen normalerweise gleichwertig, wenn sie vollständig ausgewertet werden:

```cpp
var = var + 1;
var += 1;
var++;
++var;
```

Klassentypen, die Operatoren überladen, können nicht auf dieser Identität basieren. Darüber hinaus sind einige der Anforderungen, die für die Verwendung dieser Operatoren für grundlegende Typen gelten, für überladene Operatoren weniger strikt. Der Additions-/Zuweisungs Operator ( **+=** ) erfordert beispielsweise, dass der linke Operand ein l-Wert ist, wenn er auf grundlegende Typen angewendet wird. eine solche Anforderung ist nicht erforderlich, wenn der Operator überladen wird.

> [!NOTE]
> Aus Gründen der Konsistenz ist es oft am besten, beim Definieren überladener Operatoren das Modell der integrierten Typen zu befolgen. Wenn sich die Semantik eines überladenen Operators deutlich von seiner Bedeutung in anderen Kontexten unterscheidet, kann das eher verwirrend als nützlich sein.

## <a name="see-also"></a>Weitere Informationen

[Operatorüberladung](../cpp/operator-overloading.md)
