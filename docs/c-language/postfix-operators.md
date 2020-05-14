---
title: Postfix-Operatoren
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
ms.openlocfilehash: a86ede25feeaee3a9fb1c6b146cf9667b85c0c2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232246"
---
# <a name="postfix-operators"></a>Postfix-Operatoren

Die Postfix-Operatoren weisen den höchsten Rang (die festeste Bindung) in der Ausdrucksauswertung auf.

## <a name="syntax"></a>Syntax

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-Ausdruck*  **[**  *Ausdruck*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-Ausdruck*  **(**  *argument-Ausdrucksliste*<sub>opt</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-Ausdruck*  **.**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-Ausdruck*  **->**  *Bezeichner*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-Ausdruck*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-Ausdruck*  **--**

Operatoren in dieser Rangfolgenebene sind die Arrayfeldindizes, Funktionsaufrufe, die Struktur- und Union-Member sowie Postfix-Operatoren für Inkrement und Dekrement.

## <a name="see-also"></a>Siehe auch

[C-Operatoren](../c-language/c-operators.md)
