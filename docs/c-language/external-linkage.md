---
title: Externe Verknüpfung
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
ms.openlocfilehash: 35b0fda1f501755640123f5181454a5c36b7e986
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233736"
---
# <a name="external-linkage"></a>Externe Verknüpfung

Wenn die erste Deklaration auf Dateigültigkeitsebene für einen Bezeichner nicht den **static**-Speicherklassenspezifizierer verwendet, verfügt das Objekt über eine externe Bindung.

Wenn die Deklaration eines Bezeichners für eine Funktion über keinen *Speicherklassenspezifizierer* verfügt, wird seine Bindung genauso bestimmt, als ob sie mit dem *Speicherklassenspezifizierer* `extern` deklariert worden wäre. Wenn die Deklaration eines Bezeichners für ein Objekt dateiweit gilt und keinen *storage-class-specifier* enthält, ist die Bindung extern.

Der Name eines Bezeichners mit externer Bindung legt dieselbe Funktion oder dasselbe Datenobjekt fest wie jede andere Deklaration für denselben Namen mit externer Bindung. Die beiden Deklarationen können sich in derselben Übersetzungseinheit oder in verschiedenen Übersetzungseinheiten befinden. Wenn das Objekt oder die Funktion auch eine globale Lebensdauer besitzt, ist das Objekt oder die Funktion im gesamten Programm verfügbar.

## <a name="see-also"></a>Siehe auch

[Verwenden von "extern" zur Angabe der Verknüpfung](../cpp/using-extern-to-specify-linkage.md)
