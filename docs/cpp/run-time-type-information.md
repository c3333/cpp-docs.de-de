---
title: Laufzeit-Typinformationen
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
ms.openlocfilehash: b6d3652539572f094d0e7139e6672402341c956d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232234"
---
# <a name="run-time-type-information"></a>Laufzeit-Typinformationen

Laufzeittypinformationen (Run-Time Type Information, RTTI) sind ein Mechanismus, mit dem der Typ eines Objekts während der Programmausführung bestimmt werden kann. Laufzeittypinformationen wurden zur Programmiersprache C++ hinzugefügt, da viele Anbieter von Klassenbibliotheken diese Funktion selbst implementiert haben. Dies verursachte Inkompatibilitäten zwischen Bibliotheken. Deshalb wurde es offensichtlich, dass eine Unterstützung der Laufzeittypinformationen auf Sprachebene erforderlich war.

Aus Gründen der Übersichtlichkeit wird die Erläuterung der Laufzeittypinformationen nahezu ausschließlich auf Zeiger beschränkt. Jedoch gelten die erläuterten Konzepte auch für Verweise.

Es gibt drei primäre Sprachelemente von C++ zur Ausführung von Laufzeittypinformationen:

- Der [dynamic_cast](../cpp/dynamic-cast-operator.md) -Operator.

   Wird zur Konvertierung von polymorphen Typen verwendet.

- Der [typeid](../cpp/typeid-operator.md) -Operator.

   Wird zum Kennzeichnen des genauen Typ eines Objekts verwendet.

- Die [Type_info](../cpp/type-info-class.md) -Klasse.

   Wird zum Speichern der vom Operator zurückgegebenen Typinformationen verwendet **`typeid`** .

## <a name="see-also"></a>Weitere Informationen

[Umwandlung](../cpp/casting.md)
