---
title: Zeiger (C++)
ms.date: 11/19/2019
description: Informationen zu unformatierten Zeigern und intelligenten Zeigern in Microsoft C++.
helpviewer_keywords:
- pointers (C++)
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
ms.openlocfilehash: 485cee667fa288bff76fdeac7c9f229355c276d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371920"
---
# <a name="pointers-c"></a>Zeiger (C++)

Ein Zeiger ist eine Variable, die die Speicheradresse eines Objekts speichert. Zeiger werden sowohl in C als auch in C++ für drei Hauptzwecke ausgiebig verwendet:

- um neue Objekte auf dem Heap zuzuweisen,
- So übergeben Sie Funktionen an andere Funktionen
- , um Elemente in Arrays oder anderen Datenstrukturen zu iterieren.

In der C-Programmierung werden für all diese Szenarien *unformatierte Zeiger* verwendet. Rohzeiger sind jedoch die Ursache für viele schwerwiegende Programmierfehler. Daher wird von ihrer Verwendung dringend abgeraten, es sei denn, sie bieten einen erheblichen Leistungsvorteil und es gibt keine Unklarheit darüber, welcher Zeiger der *eigene Zeiger* ist, der für das Löschen des Objekts verantwortlich ist. Modernes C++ bietet *intelligente Zeiger* zum Zuweisen von Objekten, *Iteratoren* zum Durchlaufen von Datenstrukturen und *Lambdaausdrücke* zum Übergeben von Funktionen. Durch die Verwendung dieser Sprach- und Bibliotheksfunktionen anstelle von rohen Zeigern machen Sie Ihr Programm sicherer, einfacher zu debuggen und einfacher zu verstehen und zu verwalten. Weitere Informationen finden Sie unter [Smart Pointers](smart-pointers-modern-cpp.md), [Iterators](../standard-library/iterators.md)und [Lambda-Ausdrücke.](lambda-expressions-in-cpp.md)

## <a name="in-this-section"></a>In diesem Abschnitt

- [Rohzeiger](raw-pointers.md)
- [Const und flüchtige Zeiger](const-and-volatile-pointers.md)
- [Neue und löschen operatoren](new-and-delete-operators.md)
- [Intelligente Zeiger](smart-pointers-modern-cpp.md)
- [Gewusst wie: Erstellen und Verwenden unique_ptr-Instanzen](how-to-create-and-use-unique-ptr-instances.md)
- [Gewusst wie: Erstellen und Verwenden shared_ptr-Instanzen](how-to-create-and-use-shared-ptr-instances.md)
- [Gewusst wie: Erstellen und Verwenden weak_ptr-Instanzen](how-to-create-and-use-weak-ptr-instances.md)
- [Gewusst wie: Erstellen und Verwenden von CComPtr- und CComQIPtr-Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)

## <a name="see-also"></a>Siehe auch

[Iterators](../standard-library/iterators.md)</br>
[Lambda-Ausdrücke](lambda-expressions-in-cpp.md)
