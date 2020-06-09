---
title: Dialogleisten
ms.date: 11/19/2018
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
ms.openlocfilehash: 052e0b8a085c052f73d3c6540521f57fdfbb9c51
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624896"
---
# <a name="dialog-bars"></a>Dialogleisten

Eine Dialog Leiste ist eine Symbolleiste, eine [Steuerleiste](control-bars.md) , die eine beliebige Art von Steuerelement enthalten kann. Da es die Eigenschaften eines nicht modalem Dialog Felds hat, bietet ein [CDialogBar](reference/cdialogbar-class.md) -Objekt eine leistungsfähigere Symbolleiste.

Es gibt mehrere wichtige Unterschiede zwischen einer Symbolleiste und einem- `CDialogBar` Objekt. Ein `CDialogBar` -Objekt wird aus einer Dialogfeld Vorlagen-Ressource erstellt, die Sie mit dem Dialogfeld-Editor für Visual C++ erstellen können, das beliebige Arten von Windows-Steuerelementen enthalten kann. Der Benutzer kann von Steuerelement zu Steuerelement Tab. Und Sie können einen Ausrichtungs Stil angeben, um die Dialog Leiste mit einem beliebigen Teil des übergeordneten Rahmen Fensters auszurichten, oder sogar, wenn die Größe des übergeordneten Elements geändert wird. Die folgende Abbildung zeigt eine Dialog Leiste mit einer Reihe von Steuerelementen.

![VC-Dialogleiste](../mfc/media/vc378t1.gif "VC-Dialogleiste") <br/>
Eine Dialog Leiste

Anders als bei einem-Objekt ist die Arbeit mit einem nicht modalem `CDialogBar` Dialogfeld identisch. Verwenden Sie den Dialog-Editor zum Entwerfen und Erstellen der Dialogfeld Ressource.

Eine der Vorzüge von Dialog leisten ist, dass Sie andere Steuerelemente enthalten können als Schaltflächen.

Obwohl es normal ist, eigene Dialog Klassen von abzuleiten `CDialog` , leiten Sie in der Regel nicht Ihre eigene Klasse für eine Dialog Leiste ab. Dialog leisten sind Erweiterungen für ein Hauptfenster, und alle Dialog leisten-Benachrichtigungs Meldungen, wie **BN_CLICKED** oder **EN_CHANGE**, werden an das übergeordnete Element der Dialog Leiste, das Hauptfenster, gesendet.

## <a name="see-also"></a>Siehe auch

[Elemente der Benutzeroberfläche](user-interface-elements-mfc.md)<br/>
[Beispiel](../overview/visual-cpp-samples.md)
