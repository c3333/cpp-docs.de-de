---
title: Steuerelementtypen für die Symbolleiste
ms.date: 11/04/2016
helpviewer_keywords:
- ToolBar control styles [MFC]
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
ms.openlocfilehash: eab4dbde68fcebdb0afd0d058b4678c464874c81
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837124"
---
# <a name="toolbar-control-styles"></a>Steuerelementtypen für die Symbolleiste

Die [cmfctoolbarbutton-Klasse](../../mfc/reference/cmfctoolbarbutton-class.md) verfügt über eine Reihe von stilflags, mit denen die Darstellung und das Verhalten der Schaltfläche bestimmt werden. Sie können eine Kombination dieser Flags festlegen, indem Sie [cmfctoolbarbutton:: SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)aufrufen. In diesem Thema werden die stilflagwerte und ihre Bedeutung aufgeführt.

## <a name="property-values"></a>Eigenschaftswerte

Die folgenden Werte bestimmen den Typ der Schaltfläche, die das-Steuerelement darstellt:

|Name|Beschreibung|
|-|-|
|TBBS_BUTTON|Standard-PUSHBUTTON (Standard).  |
|TBBS_CHECKBOX|Kontrollkästchen.  |
|TBBS_CHECKGROUP|Der Start einer Gruppe von Kontrollkästchen.  |
|TBBS_GROUP|Der Anfang einer Gruppe von Schaltflächen.  |
|TBBS_SEPARATOR|Trennzeichen.  |

Die folgenden Werte stellen den aktuellen Status des-Steuer Elements dar:

|Name|Beschreibung|
|-|-|
|TBBS_CHECKED|Das Kontrollkästchen ist aktiviert.  |
|TBBS_DISABLED|Das Steuerelement ist deaktiviert.  |
|TBBS_INDETERMINATE|Das Kontrollkästchen befindet sich in einem unbestimmten Zustand.  |
|TBBS_PRESSED|Die Schaltfläche wird gedrückt.  |

Der folgende Wert ändert das Layout der Schaltfläche auf der Symbolleiste:

|Name|Beschreibung|
|-|-|
|TBBS_BREAK|Platziert das Element in einer neuen Zeile oder in einer neuen Spalte, ohne Spalten zu trennen.  |

## <a name="remarks"></a>Bemerkungen

Der aktuelle Stil wird in [cmfctoolbarbutton:: m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle)gespeichert. Legen Sie einen neuen Wert nicht                 `m_nStyle` direkt fest, da einige abgeleitete Klassen beim Ausführen von zusätzliche Verarbeitungsvorgänge ausführen `SetStyles` .

Der visuelle Manager bestimmt die Darstellung der Schaltflächen in jedem Zustand. Weitere Informationen finden Sie unter [Visualisierungs-Manager](../../mfc/visualization-manager.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxtoolbarbutton. h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Cmfctoolbarbutton-Klasse](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Visualisierungs-Manager](../../mfc/visualization-manager.md)
