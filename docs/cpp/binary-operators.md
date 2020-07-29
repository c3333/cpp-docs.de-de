---
title: Binäre Operatoren
ms.date: 06/14/2018
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
ms.openlocfilehash: f44217b68f6700603218c6f4f3e846075b7e7d55
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229128"
---
# <a name="binary-operators"></a>Binäre Operatoren

Die folgende Tabelle zeigt eine Liste von Operatoren, die überladen werden können.

## <a name="redefinable-binary-operators"></a>Neu definierbare binäre Operatoren

|Operator|Name|
|--------------|----------|
|**,**|Komma|
|**!=**|Ungleichheit|
|**%**|Modulus|
|**%=**|Modulo/Zuweisung|
|**&**|Bitweises AND|
|**&&**|Logisches AND|
|**&=**|Bitweises AND/Zuweisung|
|**&#42;**|Multiplikation|
|**&#42;=**|Multiplikation/Zuweisung|
|**+**|Addition|
|**+=**|Addition/Zuweisung|
|**-**|Subtraktion|
|**-=**|Subtraktion/Zuweisung|
|**->**|Memberauswahl|
|**->&#42;**|Pointer-to-member-Auswahl|
|**/**|Division|
|**/=**|Division/Zuweisung|
|**<**|Kleiner als|
|**<<**|Nach links verschieben|
|**<<=**|Nach links verschieben/Zuweisung|
|**<=**|Kleiner als oder gleich|
|**=**|Zuweisung|
|**==**|Gleichheit|
|**>**|Größer als|
|**>=**|Größer als oder gleich|
|**>>**|Nach rechts verschieben|
|**>>=**|Nach rechts verschieben/Zuweisung|
|**^**|Exklusives OR|
|**^=**|Exklusives OR/Zuweisung|
|**&#124;**|Bitweises inklusives OR|
|**&#124;=**|Bitweises inklusives OR/Zuweisung|
|**&#124;&#124;**|Logisches OR|

Um eine binäre Operatorfunktion als nicht statischen Member zu deklarieren, muss sie im folgenden Format deklariert werden:

> *ret-Typ* **`operator`** *op* **(** *arg* **)**

Wenn der " *ret-Type* " der Rückgabetyp ist, ist " *op* " einer der in der obigen Tabelle aufgelisteten Operatoren, und " *arg* " ist ein Argument eines beliebigen Typs.

Um eine binäre Operatorfunktion als globale Funktion zu deklarieren, muss sie im folgenden Format deklariert werden:

> *ret-Typ* **`operator`** *op* **(** _arg1_**,** _arg2_ **)**

Dabei sind " *ret-Type* " und " *op* " wie für Member-Operator Funktionen beschrieben und *arg1* und *arg2* sind Argumente. Mindestens eines der Argumente muss ein Klassentyp sein.

> [!NOTE]
> Es gibt keine Einschränkung für die Rückgabetypen der binären Operatoren. Die meisten benutzerdefinierten binären Operatoren geben jedoch entweder einen Klassentyp oder einen Verweis auf einen Klassentyp zurück.

## <a name="see-also"></a>Siehe auch

[Operator Überladung](../cpp/operator-overloading.md)
