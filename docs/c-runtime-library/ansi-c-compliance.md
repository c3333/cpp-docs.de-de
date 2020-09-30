---
title: ANSI C-Kompatibilität
description: Eine Übersicht über die Benennungs Konventionen der Microsoft C-Laufzeit für die ANSI C-Konformität.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Ansi
helpviewer_keywords:
- underscores, leading
- compatibility [C++], ANSI C
- compliance with ANSI C
- conventions [C++], Microsoft extensions
- underscores
- naming conventions [C++], Microsoft library
- ANSI [C++], C standard
- Microsoft extensions naming conventions
ms.assetid: 6be271bf-eecf-491a-a928-0ee2dd60e3b9
ms.openlocfilehash: 39a3f9299be7dbef4783faa8e6d08fe6ad8461f5
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590302"
---
# <a name="ansi-c-compliance"></a>ANSI C-Kompatibilität

Die Namenskonvention für alle Microsoft-spezifischen Bezeichner im Laufzeitsystem (z.B. Funktionen, Makros, Konstanten, Variablen und Typdefinitionen) ist ANSI-kompatibel. In dieser Dokumentation wird jede Laufzeitfunktion, die den Standards ANSI/ISO C entspricht, als ANSI-kompatibel aufgeführt. ANSI-kompatible Anwendungen sollten nur diese ANSI-kompatiblen Funktionen verwenden.

Die Namen der Microsoft-spezifischen Funktionen und globalen Variablen beginnen mit einem einzelnen Unterstrich. Diese Namen können nur lokal innerhalb des Bereichs Ihres Codes überschrieben werden. Wenn Sie z.B. die Microsoft-Laufzeitheaderdateien einbeziehen, können Sie weiterhin die Microsoft-spezifische Funktion `_open` lokal überschreiben, indem Sie eine lokale Variable mit demselben Namen deklarieren. Allerdings können Sie diesen Namen nicht für Ihre eigene globale Funktion oder globale Variable verwenden.

Die Namen von Microsoft-spezifischen Makros und Manifestkonstanten beginnen mit zwei Unterstrichen oder einem einzelnen vorangestellten Unterstrich, direkt gefolgt von einem Großbuchstaben. Der Bereich dieser Bezeichner ist absolut. Sie können aus diesem Grund beispielsweise nicht den Microsoft-spezifischen Bezeichner **_UPPER** verwenden.

## <a name="see-also"></a>Weitere Informationen

[Kompatibilität](../c-runtime-library/compatibility.md)
