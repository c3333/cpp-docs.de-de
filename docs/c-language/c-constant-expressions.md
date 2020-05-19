---
title: Konstante Ausdrücke in C
ms.date: 06/14/2018
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
ms.openlocfilehash: f6984c47ef8acde462a8e92e01b72ef26a61eddc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325740"
---
# <a name="c-constant-expressions"></a>Konstante Ausdrücke in C

Ein konstanter Ausdruck wird nicht zur Laufzeit, sondern zur Kompilierzeit ausgewertet, Er kann überall dort eingesetzt werden, wo auch eine Konstante verwendet werden kann. Ergebnis des konstanten Ausdrucks muss eine Konstante sein, deren Wert für den betreffenden Typ darstellbar sein muss. Die Operanden eines konstanten Ausdrucks können ganzzahlige Konstanten, Zeichenkonstanten, Gleitkommakonstanten, Enumerationskonstanten, Typumwandlungen, **sizeof**-Ausdrücke oder sonstige konstante Ausdrücke sein.

## <a name="syntax"></a>Syntax

*constant-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*

*conditional-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logischer-OR-Ausdruck* **?** *Ausdruck* **:** *bedingter-Ausdruck*

*expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Ausdruck* **,** *Zuweisungsausdruck*

*assignment-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unärer-Ausdruck* *Zuweisungsoperator* *Zuweisungsausdruck*

*assignment-operator*: eines der folgenden Zeichen:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **=** **&#42;=** **/=** **%=** **+=** **-=** **\<\<=** **>>=** **&=** **^=** **&#124;=**

Die Non-Terminals für den Strukturdeklarator, den Enumerator, den direkten Deklarator, den direkt-abstrakten Deklarator und die Anweisung mit Bezeichnung enthalten das Non-Terminal *constant-expression*.

Ein ganzzahliger konstanter Ausdruck muss verwendet werden, um die Größe eines Bitfeldmembers einer Struktur, den Wert einer Enumerationskonstanten, die Größe eines Arrays oder den Wert einer **case**-Konstanten anzugeben.

Konstante Ausdrücke, die in Präprozessoranweisungen verwendet werden, unterliegen zusätzlichen Einschränkungen. Daher werden sie als „eingeschränkte konstante Ausdrücke“ bezeichnet. Ein eingeschränkter konstanter Ausdruck darf keine **sizeof**-Ausdrücke, Enumerationskonstanten, Typumwandlungen in beliebige Typen oder Gleitkommakonstanten enthalten. Dagegen kann der spezielle konstante Ausdruck **defined (** _Bezeichner_ **)** enthalten sein.

## <a name="see-also"></a>Siehe auch

- [Operanden und Ausdrücke](../c-language/operands-and-expressions.md)
