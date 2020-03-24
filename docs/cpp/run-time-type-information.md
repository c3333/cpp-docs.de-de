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
ms.openlocfilehash: 195274d7bcef0ff4d82383a8ec828ca9267573b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178937"
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

   Wird zum Speichern der Typinformationen verwendet, die vom **typeid** -Operator zurückgegeben werden.

## <a name="see-also"></a>Weitere Informationen

[Umwandlung](../cpp/casting.md)
