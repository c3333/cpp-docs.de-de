---
title: Namespaces
ms.date: 11/04/2016
helpviewer_keywords:
- union keyword [C], tags
- enumeration tags
- structure tags
- names [C++], declared elements
- name spaces [C++]
- tags, structure tags
- union keyword [C]
ms.assetid: b4bda1d1-cb5e-4f60-ac2b-29af93d8a9a2
ms.openlocfilehash: 76ad9b797a4f192e8f22f8c040f5a308371a461b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325766"
---
# <a name="name-spaces"></a>Namespaces

Der Compiler richtet "Namespaces" ein, um zwischen den Bezeichnern zu unterscheiden, die für verschiedene Arten von Elementen verwendet werden. Die Namen innerhalb eines Namespace müssen einmalig sein, um Konflikte zu vermeiden, aber ein identischer Name kann in mehreren Namespaces vorhanden sein. Dies bedeutet, dass Sie den gleichen Bezeichner für zwei oder mehr unterschiedliche Elemente verwenden können, vorausgesetzt, dass sich die Elemente in unterschiedlichen Namespaces befinden. Der Compiler kann Verweise auf Grundlage des syntaktischen Kontexts des Bezeichners im Programm auflösen.

> [!NOTE]
> Verwechseln Sie den eingeschränkten C-Begriff eines Namespace nicht mit der Funktion „Namespace“ von C++. Weitere Informationen erhalten Sie unter [Namespaces](../cpp/namespaces-cpp.md) in der C++-Sprachreferenz.

Diese Liste beschreibt die Namespaces, die in C verwendet werden.

Anweisungsbezeichnungen: Benannte Anweisungsbezeichnungen sind ein Bestandteil von Anweisungen. Hinter den Definitionen von Anweisungsbezeichnungen steht immer ein Doppelpunkt; sie sind jedoch nicht Teil der **case**-Bezeichnungen. Die Verwendungen der Anweisungsbezeichnungen folgen immer direkt auf das Schlüsselwort **goto**. Anweisungsbezeichnungen müssen sich nicht von anderen Namen oder Bezeichnungsnamen in anderen Funktionen unterscheiden.

Struktur-, Union- und Enumerationstags: Diese Tags sind Teil der Struktur-, Union- und Enumerationstypbezeichner und folgen immer unmittelbar auf die reservierten Wörtern **struct**, **union** oder **enum**, sofern vorhanden. Die Tagnamen müssen sich von allen anderen Struktur-, Enumerations- und Union-Tags mit derselben Sichtbarkeit unterscheiden.

Member von Strukturen oder Unions: Membernamen werden in Namespaces zugewiesen, die jedem Struktur- und Union-Typ zugeordnet sind. Das heißt, derselbe Bezeichner kann gleichzeitig ein Komponentenname in einer beliebigen Struktur- oder Union-Anzahl sein. Definitionen von Komponentennamen treten immer innerhalb der Struktur- oder Union-Typspezifizierer auf. Verwendungen des Komponentennamens folgen immer unmittelbar auf die Memberauswahloperatoren ( **->** und **.** ). Der Name eines Members muss innerhalb der Struktur oder Union einmalig sein, doch er kann anderen Namen im Programm gleichen. Das können die Membernamen in unterschiedlichen Strukturen und Unions oder der Strukturname selbst sein.

Gewöhnliche Bezeichner: Alle anderen Namen sind in einem Namespace enthalten, der die Variablen, Funktionen (einschließlich der formalen Parameter und lokaler Variablen) und Enumerationskonstanten enthält. Die Sichtbarkeit von Bezeichnernamen ist geschachtelt, sie können also innerhalb der Blöcke neu definiert werden.

Typedef-Namen: Typedef-Namen können nicht als Bezeichner in demselben Gültigkeitsbereich verwendet werden.

Da zum Beispiel Strukturtags, Strukturmember und Variablennamen in drei verschiedenen Namespaces sind, verursachen die drei Elemente mit Namen `student` in diesem Beispiel keinen Konflikt. Der Kontext des jeweiligen Elements ermöglicht die richtige Auslegung jedes Vorkommens von `student` im Programm. (Weitere Informationen zu Strukturen finden Sie unter [Strukturdeklarationen](../c-language/structure-declarations.md).)

```C
struct student {
   char student[20];
   int class;
   int id;
   } student;
```

Wenn `student` nach dem **struct**-Schlüsselwort angegeben wird, wird es vom Compiler als Strukturtag erkannt. Wenn `student` nach einem Memberauswahloperator ( **->** oder **.** ) vorhanden ist, bezeichnet der Name den Strukturmember. In anderen Kontexten bezieht sich `student` auf die Strukturvariable. Allerdings wird das Überladen des Tagnamespaces nicht empfohlen, weil dadurch die Bedeutung unklar wird.

## <a name="see-also"></a>Siehe auch

[Programmstruktur](../c-language/program-structure.md)
