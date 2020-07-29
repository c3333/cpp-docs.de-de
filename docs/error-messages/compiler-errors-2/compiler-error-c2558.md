---
title: Compilerfehler C2558
ms.date: 11/04/2016
f1_keywords:
- C2558
helpviewer_keywords:
- C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
ms.openlocfilehash: 2504b42f49ccb040f676f0aead8f243d33c7dd1a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207744"
---
# <a name="compiler-error-c2558"></a>Compilerfehler C2558

'Bezeichner': Kein Kopierkonstruktor verfügbar, oder der Kopierkonstruktor ist als 'explicit' deklariert

Durch einen Kopierkonstruktor wird ein Objekt von einem anderen Objekt desselben Typs initialisiert. (Es wird eine Kopie des-Objekts erstellt.) Der Compiler generiert einen Standardkopierkonstruktor, wenn Sie keine Konstruktoren definieren.

### <a name="to-fix-this-error"></a>So beheben Sie diesen Fehler

1. Das Problem kann auftreten, wenn versucht wird, eine Klasse zu kopieren, deren Kopierkonstruktor ist **`private`** . In den meisten Fällen sollte eine Klasse, die über einen **`private`** Kopierkonstruktor verfügt, nicht kopiert werden. Ein gängiges Programmierverfahren deklariert einen **`private`** Kopierkonstruktor, um die direkte Verwendung einer Klasse zu verhindern. Die Klasse ist möglicherweise nutzlos oder benötigt eine andere Klasse, um ordnungsgemäß zu funktionieren.

   Wenn Sie feststellen, dass die Verwendung einer Klasse, die über einen **`private`** Kopierkonstruktor verfügt, sicher ist, leiten Sie eine neue Klasse von der Klasse ab, die über den **`private`** Konstruktor verfügt, und erstellen Sie einen- **`public`** oder- **`protected`** Kopierkonstruktor in der neuen Klasse. Verwenden Sie die abgeleitete Klasse anstelle des Originals.

1. Das Problem kann auftreten bei dem Versuch, eine Klasse zu kopieren, deren Kopierkonstruktor explizit ist. Durch das Deklarieren eines Kopierkonstruktors als wird **`explicit`** verhindert, dass-Objekte einer Klasse an/von-Funktionen übergeben werden. Weitere Informationen zu expliziten Konstruktoren finden Sie unter [benutzerdefinierte Typkonvertierungen](../../cpp/user-defined-type-conversions-cpp.md).

1. Das Problem kann auftreten, wenn versucht wird, eine Klasseninstanz zu kopieren, die **`const`** mithilfe eines Kopierkonstruktors deklariert wurde, der keinen **`const`** Verweis Parameter übernimmt. Deklarieren Sie den Kopierkonstruktor mit einem **`const`** Typverweis anstelle eines nicht konstanten Typverweises.
