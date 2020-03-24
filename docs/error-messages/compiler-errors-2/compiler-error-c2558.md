---
title: Compilerfehler C2558
ms.date: 11/04/2016
f1_keywords:
- C2558
helpviewer_keywords:
- C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
ms.openlocfilehash: 93b6e414f26c56702a1c7ac12863cbcd5063b570
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177494"
---
# <a name="compiler-error-c2558"></a>Compilerfehler C2558

'Bezeichner': Kein Kopierkonstruktor verfügbar, oder der Kopierkonstruktor ist als 'explicit' deklariert

Durch einen Kopierkonstruktor wird ein Objekt von einem anderen Objekt desselben Typs initialisiert. (Es wird eine Kopie des-Objekts erstellt.) Der Compiler generiert einen Standardkopierkonstruktor, wenn Sie keine Konstruktoren definieren.

### <a name="to-fix-this-error"></a>So beheben Sie diesen Fehler

1. Das Problem kann auftreten bei dem Versuch, eine Klasse zu kopieren, deren Kopierkonstruktor als `private` deklariert ist. In den meisten Fällen sollte eine Klasse mit einem als `private` deklarierten Kopierkonstruktor nicht kopiert werden. Mithilfe allgemeiner Programmierpraktiken wurde ein Kopierkonstruktor als `private` deklariert, um die direkte Verwendung einer Klasse zu verhindern. Die Klasse ist möglicherweise nutzlos oder benötigt eine andere Klasse, um ordnungsgemäß zu funktionieren.

   Wenn es Ihnen sicher erscheint, eine Klasse mit einem `private`-Kopierkonstruktor zu verwenden, leiten Sie von der Klasse eine neue Klasse mit einem `private`-Konstruktor ab und stellen Sie in der neuen Klasse einen `public`-Kopierkonstruktor oder einen `protected`-Kopierkonstruktor bereit. Verwenden Sie die abgeleitete Klasse anstelle des Originals.

1. Das Problem kann auftreten bei dem Versuch, eine Klasse zu kopieren, deren Kopierkonstruktor als explicit deklariert ist. Das Deklarieren eines Kopierkonstruktors als `explicit` verhindert die Übergabe/Rückgabe von Objekten einer Klasse an/von Funktionen. Weitere Informationen zu expliziten Konstruktoren finden Sie unter [benutzerdefinierte Typkonvertierungen](../../cpp/user-defined-type-conversions-cpp.md).

1. Das Problem kann auftreten bei dem Versuch, eine Klasseninstanz zu kopieren, die als `const` deklariert ist, und ein Kopierkonstruktor verwendet wird, der keinen `const` Verweisparameter akzeptiert. Deklarieren Sie den Kopierkonstruktor mit einem Verweis vom Typ `const` und nicht mit einem nicht konstanten Verweis.
