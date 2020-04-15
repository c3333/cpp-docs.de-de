---
title: Zeichenfolgenkonvertierungsmakros
ms.date: 11/04/2016
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
ms.openlocfilehash: 8df496b78334d26e7d3664642b2e9d93d6149843
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325852"
---
# <a name="string-conversion-macros"></a>Zeichenfolgenkonvertierungsmakros

Diese Makros bieten Zeichenfolgenkonvertierungsfunktionen.

## <a name="atl-and-mfc-string-conversion-macros"></a><a name="atl_and_mfc_string_conversion_macros"></a>ATL- und MFC-Zeichenfolgenkonvertierungsmakros

Die hier besprochenen Zeichenfolgenkonvertierungsmakros sind sowohl für ATL als auch für MFC gültig. Weitere Informationen zur MFC-Zeichenfolgenkonvertierung finden Sie unter [TN059: Verwenden von MFC MBCS/Unicode Conversion Macros](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) und [MFC Macros and Globals](../../mfc/reference/mfc-macros-and-globals.md).

## <a name="devmode-and-textmetric-string-conversion-macros"></a><a name="devmode_and_textmetric_string_conversion_macros"></a>DEVMODE- und TEXTMETRIC-Zeichenfolgenkonvertierungsmakros

Diese Makros erstellen eine Kopie einer [DEVMODE-](/windows/win32/api/wingdi/ns-wingdi-devmodea) oder [TEXTMETRIC-Struktur](/windows/win32/api/wingdi/ns-wingdi-textmetricw) und konvertieren die Zeichenfolgen innerhalb der neuen Struktur in einen neuen Zeichenfolgentyp. Die Makros weisen Speicher auf dem Stapel für die neue Struktur zu und geben einen Zeiger auf die neue Struktur zurück.

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>Bemerkungen

Beispiel:

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

und:

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

In den Makronamen befindet sich der Zeichenfolgentyp in der Quellstruktur auf der linken Seite (z. B. **A**) und der Zeichenfolgentyp in der Zielstruktur auf der rechten Seite (z. B. **W**). **A** steht für LPSTR, **OLE** steht für LPOLESTR, **T** für LPTSTR und **W** für LPWSTR.

Daher kopiert DEVMODEA2W `DEVMODE` eine Struktur mit `DEVMODE` LPSTR-Zeichenfolgen in eine Struktur mit `TEXTMETRIC` LPWSTR-Zeichenfolgen, `TEXTMETRIC` TEXTMETRICOLE2T kopiert eine Struktur mit LPOLESTR-Zeichenfolgen in eine Struktur mit LPTSTR-Zeichenfolgen usw.

Die beiden in `DEVMODE` der Struktur konvertierten`dmDeviceName`Zeichenfolgen sind`dmFormName`der Gerätename ( ) und der Formularname ( ). Die `DEVMODE` Zeichenfolgenkonvertierungsmakros aktualisieren`dmSize`auch die Strukturgröße ( ).

Die vier in `TEXTMETRIC` der Struktur konvertierten`tmFirstChar`Zeichenfolgen sind`tmLastChar`das erste`tmDefaultChar`Zeichen ( ),`tmBreakChar`das letzte Zeichen ( ), das Standardzeichen ( ), und das Unterbrechungszeichen ( ).

Das Verhalten `DEVMODE` der `TEXTMETRIC` und String-Konvertierungsmakros hängt ggf. von der jeweiligen Compilerdirektive ab. Wenn die Quell- und Zieltypen gleich sind, findet keine Konvertierung statt. Compilerdirektiven ändern **T** und **OLE** wie folgt:

|Geltende Compiler-Anweisung|T wird zu|OLE wird zu|
|----------------------------------|---------------|-----------------|
|Keine|**A**|**W**|
|**\_Unicode**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|UNICODE und **OLE2ANSI** ** \_**|**W**|**A**|

In der folgenden `DEVMODE` `TEXTMETRIC` Tabelle sind die und String-Konvertierungsmakros aufgeführt.

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
