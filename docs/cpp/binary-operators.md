---
title: Binäre Operatoren
ms.date: 06/14/2018
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
ms.openlocfilehash: 030ae71fec7a0d1572804f30d09f6f9b2749e436
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181303"
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

> *ret-Type-* **Operator** *op* **(** *arg* **)**

Wenn der " *ret-Type* " der Rückgabetyp ist, ist " *op* " einer der in der obigen Tabelle aufgelisteten Operatoren, und " *arg* " ist ein Argument eines beliebigen Typs.

Um eine binäre Operatorfunktion als globale Funktion zu deklarieren, muss sie im folgenden Format deklariert werden:

> *ret-Type-* **Operator** *op* **(** _arg1_ **,** _arg2_ **)**

Dabei sind " *ret-Type* " und " *op* " wie für Member-Operator Funktionen beschrieben und *arg1* und *arg2* sind Argumente. Mindestens eines der Argumente muss ein Klassentyp sein.

> [!NOTE]
> Es gibt keine Einschränkung für die Rückgabetypen der binären Operatoren. Die meisten benutzerdefinierten binären Operatoren geben jedoch entweder einen Klassentyp oder einen Verweis auf einen Klassentyp zurück.

## <a name="see-also"></a>Weitere Informationen

[Operatorüberladung](../cpp/operator-overloading.md)
