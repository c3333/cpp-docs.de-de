---
title: Variant-Parametertypkonstanten
ms.date: 11/04/2016
f1_keywords:
- VTS_YPOS_HIMETRIC
- VTS_PICTURE
- VTS_FONT
- VTS_XPOS_HIMETRIC
- VTS_XPOS_PIXELS
- VTS_XSIZE_HIMETRIC
- VTS_YPOS_PIXELS
- VTS_TRISTATE
- VTS_HANDLE
- VTS_YSIZE_HIMETRIC
- VTS_COLOR
- VTS_OPTEXCLUSIVE
- VTS_YSIZE_PIXELS
- VTS_XSIZE_PIXELS
helpviewer_keywords:
- VTS_XPOS_HIMETRIC constant [MFC]
- VTS_FONT constant [MFC]
- VTS_XPOS_PIXELS constant [MFC]
- VTS_COLOR constant [MFC]
- Variants [MFC]
- VTS_YPOS_PIXELS constant [MFC]
- VTS_YSIZE_HIMETRIC constant [MFC]
- VTS_YPOS_HIMETRIC constant [MFC]
- Variants, parameter type constants
- Variant data constants [MFC]
- VTS_PICTURE constant [MFC]
- VTS_TRISTATE constant [MFC]
- VTS_XSIZE_HIMETRIC constant [MFC]
- VTS_HANDLE constant [MFC]
- VTS_XSIZE_PIXELS constant [MFC]
- VTS_OPTEXCLUSIVE constant [MFC]
- VTS_YSIZE_PIXELS constant [MFC]
ms.assetid: de99c7a9-7aae-4dc4-b723-40c6380543ab
ms.openlocfilehash: f73c72830216679f8a91d0037d48c1e1b8e400c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372863"
---
# <a name="variant-parameter-type-constants"></a>Variant-Parametertypkonstanten

In diesem Thema werden neue Konstanten aufgeführt, die Variantenparametertypen angeben, die für die Verwendung mit den OLE-Steuerelementklassen der Microsoft Foundation-Klassenbibliothek entwickelt wurden.

Im Folgenden finden Sie eine Liste von Klassenkonstanten:

## <a name="variant-data-constants"></a><a name="_mfc_variant_data_constants"></a>Variantendatenkonstanten

- VTS_COLOR Eine 32-Bit-Ganzzahl, die zur Darstellung eines RGB-Farbwerts verwendet wird.

- VTS_FONT Ein Zeiger `IFontDisp` auf die Schnittstelle eines OLE-Schriftartobjekts.

- VTS_HANDLE Ein Windows-Handlewert.

- VTS_PICTURE Ein Zeiger `IPictureDisp` auf die Schnittstelle eines OLE-Bildobjekts.

- VTS_OPTEXCLUSIVE Ein 16-Bit-Wert, der für ein Steuerelement verwendet wird, das in einer Gruppe von Steuerelementen verwendet werden soll, z. B. Optionsfelder. Dieser Typ teilt dem Container mit, dass alle anderen Personen FALSE sein müssen, wenn ein Steuerelement in einer Gruppe einen TRUE-Wert hat.

- VTS_TRISTATE Eine 16-Bit-signierte Ganzzahl, die für Eigenschaften verwendet wird, die einen von drei möglichen Werten aufweisen können (ausgewählt, deaktiviert, nicht verfügbar), z. B. ein Kontrollkästchen.

- VTS_XPOS_HIMETRIC Eine 32-Bit-Ganzzahl ohne Vorzeichen, die verwendet wird, um eine Position entlang der x-Achse in HIMETRIC-Einheiten darzustellen.

- VTS_YPOS_HIMETRIC Eine 32-Bit-Ganzzahl ohne Vorzeichen, die verwendet wird, um eine Position entlang der y-Achse in HIMETRIC-Einheiten darzustellen.

- VTS_XPOS_PIXELS Eine 32-Bit-Ganzzahl ohne Vorzeichen, die verwendet wird, um eine Position entlang der x-Achse in Pixel darzustellen.

- VTS_YPOS_PIXELS Eine 32-Bit-Ganzzahl ohne Vorzeichen, die verwendet wird, um eine Position entlang der y-Achse in Pixel darzustellen.

- VTS_XSIZE_PIXELS Eine 32-Bit-Ganzzahl ohne Vorzeichen, die verwendet wird, um die Breite eines Bildschirmobjekts in Pixel darzustellen.

- VTS_YSIZE_PIXELS Eine 32-Bit-Ganzzahl ohne Vorzeichen, die verwendet wird, um die Höhe eines Bildschirmobjekts in Pixel n. Chr. darzustellen.

- VTS_XSIZE_HIMETRIC Eine 32-Bit-Ganzzahl ohne Vorzeichen, die zur Darstellung der Breite eines Bildschirmobjekts in HIMETRIC-Einheiten verwendet wird.

- VTS_YSIZE_HIMETRIC Eine 32-Bit-Ganzzahl ohne Vorzeichen, die zur Darstellung der Höhe eines Bildschirmobjekts in HIMETRIC-Einheiten verwendet wird.

    > [!NOTE]
    >  Für alle Variantentypen wurden zusätzliche Variantenkonstanten definiert, mit Ausnahme von VTS_FONT und VTS_PICTURE, die einen Zeiger auf die Variantendatenkonstante liefern. Diese Konstanten werden mithilfe`constantname` der VTS_P-Konvention benannt. VTS_PCOLOR ist z. B. ein Zeiger auf eine VTS_COLOR Konstante.

## <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
