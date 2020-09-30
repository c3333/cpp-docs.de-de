---
title: Codepages
description: Eine Beschreibung der Code Page Unterstützung in der Microsoft C-Laufzeit.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
ms.openlocfilehash: 1f9d311ec714d2043e072cbbfbac505d3f804294
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590068"
---
# <a name="code-pages"></a>Codepages

Eine *Codepage* ist ein Zeichensatz, der Zahlen, Interpunktionszeichen und andere Glyphen enthalten kann. Von unterschiedlichen Sprachen und Gebietsschemas werden möglicherweise unterschiedliche Codepages verwendet. Die ANSI-Codepage 1252 wird z.B. für Englisch und die meisten europäischen Sprachen verwendet, während die OEM-Codepage 932 für das japanische Kanji eingesetzt wird.

Eine Codepage kann in einer Tabelle als Zuordnung von Zeichen zu Einzel Byte-oder multibytewerten dargestellt werden. Viele Codepages verwenden den ASCII-Zeichensatz für Zeichen im Bereich von 0x00 bis 0x7F.

Die Microsoft-Lauf Zeit Bibliothek verwendet die folgenden Typen von Codepages:

- Standard-ANSI-Codepage des Systems. Standardmäßig wird beim Start vom Laufzeitsystem automatisch die Multibytezeichen-Codepage auf die Standard-ANSI-Codepage des Systems festgelegt, die vom Betriebssystem abgerufen wird. Der Aufruf

    ```C
    setlocale ( LC_ALL, "" );
    ```

   legt auch das Gebietsschema auf die Standard-ANSI-Codepage des Systems fest.

- Gebietsschema-Codepage. Das Verhalten einiger Laufzeitroutinen ist abhängig von der aktuellen Einstellung des Gebietsschemas, das die Gebietsschema-Codepage enthält. (Weitere Informationen finden Sie unter Gebiets Schema [abhängige Routinen](../c-runtime-library/locale.md).) Standardmäßig verwenden alle vom Gebiets Schema abhängigen Routinen in der Microsoft-Lauf Zeit Bibliothek die Codepage, die dem Gebiets Schema "C" entspricht. Zur Laufzeit können Sie die verwendete Gebiets Schema-Codepage mit einem Aufruf von [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)ändern oder Abfragen.

- Multibyte-Codepage. Das Verhalten der meisten Multibytezeichenroutinen in der Laufzeitbibliothek hängt von der aktuellen Einstellung der Multibyte-Codepage ab. In der Standardeinstellung verwenden diese Routinen die Standard-ANSI-Codepage des Systems. Zur Laufzeit können Sie die Multibyte-Codepage mit [_getmbcp](../c-runtime-library/reference/getmbcp.md) oder [_setmbcp](../c-runtime-library/reference/setmbcp.md) abfragen bzw. ändern.

- Das Gebietsschema „C“ wird von ANSI so definiert, das es dem Gebietsschema entspricht, in dem C-Programme bisher ausgeführt wurden. Die Codepage für das Gebietsschema „C“ („C“-Codepage) entspricht dem ASCII-Zeichensatz. Zum Beispiel gibt **islower** im Gebietsschema „C“ nur für die Werte 0x61 bis 0x7A TRUE zurück. In einem anderen Gebiets Schema kann **IsLower** `true` für diese und andere Werte zurückgeben, wie von diesem Gebiets Schema definiert.

## <a name="see-also"></a>Weitere Informationen

[Internationalisierung](../c-runtime-library/internationalization.md)\
[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)
