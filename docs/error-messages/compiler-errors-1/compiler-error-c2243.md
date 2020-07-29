---
title: Compilerfehler C2243
ms.date: 11/04/2016
f1_keywords:
- C2243
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
ms.openlocfilehash: ab0dbe8c5595c18a01f78c22056803dce91a3f31
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212838"
---
# <a name="compiler-error-c2243"></a>Compilerfehler C2243

'Konvertierungstyp'-Konvertierung von 'Typ1' zu 'Typ2' ist vorhaden, jedoch kann darauf nicht zugegriffen werden

Der Zugriffsschutz ( **`protected`** oder **`private`** ) hat die Konvertierung von einem Zeiger auf eine abgeleitete Klasse in einen Zeiger auf die Basisklasse verhindert.

Das folgende Beispiel generiert C2243:

```cpp
// C2243.cpp
// compile with: /c
class B {};
class D : private B {};
class E : public B {};

D d;
B *p = &d;   // C2243

E e;
B *p2 = &e;
```

Auf Basisklassen mit- **`protected`** oder- **`private`** Zugriff kann für Clients der abgeleiteten Klasse nicht zugegriffen werden. Diese Ebenen der Zugriffssteuerung werden verwendet, um anzugeben, dass die Basisklasse ein Implementierungsdetail ist, das für Clients nicht sichtbar sein sollte. Verwenden Sie die öffentliche Ableitung, wenn Sie möchten, dass Clients der abgeleiteten Klasse Zugriff auf die implizite Konvertierung eines abgeleiteten Klassenzeigers auf einen Zeiger auf die Basisklasse haben sollen.
