---
title: Vererbungsschlüsselwörter
ms.date: 11/04/2016
f1_keywords:
- __multiple_inheritance
- __single_inheritance_cpp
- __virtual_inheritance_cpp
- __virtual_inheritance
- __multiple_inheritance_cpp
- __single_inheritance
helpviewer_keywords:
- __single_inheritance keyword [C++]
- declaring derived classes [C++]
- keywords [C++], inheritance keywords
- __multiple_inheritance keyword [C++]
- __virtual_inheritance keyword [C++]
- inheritance, declaring derived classes
- derived classes [C++], declaring
- inheritance, keywords
ms.assetid: bb810f56-7720-4fea-b8b6-9499edd141df
ms.openlocfilehash: bc9afdcb7971c478c1cad9185cece57ea6326a48
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233729"
---
# <a name="inheritance-keywords"></a>Vererbungsschlüsselwörter

**Microsoft-spezifisch**

```
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;
```

Dabei gilt:

*Klassenname*<br/>
Der Name der zu deklarierenden Klasse.

C++ ermöglicht es Ihnen, vor der Definition der Klasse einen Zeiger auf einen Klassenmember zu deklarieren. Beispiel:

```cpp
class S;
int S::*p;
```

Im obigen Code `p` wird als Zeiger auf einen ganzzahligen Member der Klasse S deklariert. Wurde jedoch `class S` noch nicht in diesem Code definiert. es wurde nur deklariert. Wenn der Compiler einen solchen Zeiger erkennt, muss er eine allgemeine Darstellung des Zeigers erzeugen. Die Größe der Darstellung ist vom angegebenen Vererbungsmodell abhängig. Es gibt vier Möglichkeiten, ein Vererbungsmodell für den Compiler anzugeben:

- In der IDE unter **Zeiger-zu-Member-Darstellung**

- In der Befehlszeile mithilfe des [/VMG](../build/reference/vmb-vmg-representation-method.md) -Schalters

- Verwenden des [pointers_to_members](../preprocessor/pointers-to-members.md) -Pragmas

- Mithilfe der Vererbungs Schlüsselwörter **`__single_inheritance`** , **`__multiple_inheritance`** und **`__virtual_inheritance`** . Dieses Verfahren steuert das Vererbungsmodell auf Basis einer einzelnen Klasse.

    > [!NOTE]
    >  Wenn Sie stets einen Zeiger auf einen Member einer Klasse deklarieren, nachdem Sie die Klasse definiert haben, ist es nicht erforderlich, eine dieser Optionen zu verwenden.

Das Deklarieren eines Zeigers auf einen Member einer Klasse vor der Klassendefinition wirkt sich auf die Größe und die Geschwindigkeit der erstellten ausführbaren Datei aus. Je komplexer die von einer Klasse genutzte Vererbung ist, desto größer sind die Byteanzahl, die für die Darstellung eines Zeigers auf einen Member der Klasse erforderlich ist, und der für die Interpretation des Zeigers erforderliche Code. Die einfache Vererbung ist am wenigsten komplex und die virtuelle Vererbung ist die komplexeste Vererbung.

Wenn das obige Beispiel so geändert wird:

```cpp
class __single_inheritance S;
int S::*p;
```

Unabhängig von Befehlszeilenoptionen oder Pragmas verwenden Zeiger auf Member von `class S` die kleinstmögliche Darstellung.

> [!NOTE]
> Dieselbe Vorwärtsdeklaration einer pointer-to-member-Klassendarstellung sollte in jeder Übersetzungseinheit auftreten, die Zeiger auf Member dieser Klasse deklariert. Die Deklaration sollte vor der pointer-to-member-Deklaration erfolgen.

Aus Kompatibilitätsgründen mit früheren Versionen sind **_single_inheritance**, **_multiple_inheritance**und **_virtual_inheritance** Synonyme für **`__single_inheritance`** , und, **`__multiple_inheritance`** **`__virtual_inheritance`** es sei denn, die Compileroption [/Za \( Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)
