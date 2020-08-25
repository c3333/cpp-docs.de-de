---
title: Zeichen folgen Konvertierungs Makros
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
ms.openlocfilehash: 60cccebf4e1db8369ea5a88f04a37b96838ff49f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835154"
---
# <a name="string-conversion-macros"></a>Zeichen folgen Konvertierungs Makros

Diese Makros Stellen Zeichen folgen Konvertierungs Funktionen bereit.

## <a name="atl-and-mfc-string-conversion-macros"></a><a name="atl_and_mfc_string_conversion_macros"></a> ATL-und MFC-Zeichen folgen Konvertierungs Makros

Die hier besprochenen Zeichenfolgenkonvertierungsmakros sind sowohl für ATL als auch für MFC gültig. Weitere Informationen zur MFC-Zeichen folgen Konvertierung finden [Sie unter TN059: Verwenden von MFC MBCS/Unicode-Konvertierungs Makros](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) und [MFC-Makros und Globals](../../mfc/reference/mfc-macros-and-globals.md).

## <a name="devmode-and-textmetric-string-conversion-macros"></a><a name="devmode_and_textmetric_string_conversion_macros"></a> Zeichen folgen Konvertierungs Makros für DEVMODE und TextMetric

Diese Makros erstellen eine Kopie einer [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) -oder [TextMetric](/windows/win32/api/wingdi/ns-wingdi-textmetricw) -Struktur und konvertieren die Zeichen folgen innerhalb der neuen-Struktur in einen neuen Zeichen Folgentyp. Die Makros weisen dem Stapel Speicher für die neue-Struktur zu und geben einen Zeiger auf die neue-Struktur zurück.

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>Bemerkungen

Beispiel:

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

und:

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

In den Makronamen befindet sich der Zeichen folgenyp in der Quell Struktur auf der linken Seite (z. b. **A**), und der Zeichen Folgentyp in der Zielstruktur befindet sich auf der rechten Seite (z. b. **W**). **A** steht für LPStr, **OLE** steht für lpolestr, **T** für LPTSTR und **W** für LPWSTR.

Daher kopiert DEVMODEA2W eine `DEVMODE` Struktur mit LPStr-Zeichen folgen in eine `DEVMODE` Struktur mit LPWSTR-Zeichen folgen, TEXTMETRICOLE2T kopiert eine `TEXTMETRIC` Struktur mit lpolestr-Zeichen folgen in eine `TEXTMETRIC` Struktur mit LPTSTR-Zeichen folgen usw.

Die beiden Zeichen folgen, die in der- `DEVMODE` Struktur konvertiert werden, sind der Gerätename ( `dmDeviceName` ) und der Formular Name ( `dmFormName` ). Die `DEVMODE` Makros für die Zeichen folgen Konvertierung aktualisieren ebenfalls die Struktur Größe ( `dmSize` ).

Die vier Zeichen folgen, die in der- `TEXTMETRIC` Struktur konvertiert werden, sind das erste Zeichen ( `tmFirstChar` ), das letzte Zeichen ( `tmLastChar` ), das Standard Zeichen ( `tmDefaultChar` ) und das Break-Zeichen ( `tmBreakChar` ).

Das Verhalten der `DEVMODE` -und- `TEXTMETRIC` Zeichen folgen Konvertierungs Makros hängt von der entsprechenden Compilerdirektive ab, sofern vorhanden. Wenn die Quell- und Zieltypen gleich sind, findet keine Konvertierung statt. Die Compilerdirektiven ändern **T** und **OLE** wie folgt:

|Geltende Compiler-Anweisung|T wird zu|OLE wird zu|
|----------------------------------|---------------|-----------------|
|Keine|**A**|**W**|
|**\_UNICODE**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|** \_ Unicode** und **OLE2ANSI**|**W**|**A**|

In der folgenden Tabelle sind die `DEVMODE` -und `TEXTMETRIC` Zeichen folgen Konvertierungs Makros aufgeführt.

|`DEVMODE` Hilfen|`TEXTMETRIC` Hilfen|
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>Weitere Informationen

[Makros](../../atl/reference/atl-macros.md)
