---
title: Typsicherer Zugriff auf Steuerelemente mit Code-Assistenten
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: bfbc27dbcdeeb38c40f5d989bacd65a23198d4f5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213969"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Typsicherer Zugriff auf Steuerelemente mit Code-Assistenten

Wenn Sie mit DDX-Funktionen vertraut sind, können Sie die Control-Eigenschaft im [Assistenten zum Hinzufügen](../ide/add-member-variable-wizard.md) von Element Variablen verwenden, um typsicheren Zugriff zu erstellen. Diese Vorgehensweise ist einfacher als das Erstellen von Steuerelementen ohne Code-Assistenten.

Wenn Sie einfach auf den Wert eines Steuer Elements zugreifen möchten, stellt DDX es bereit. Wenn Sie mehr als auf den Wert eines Steuer Elements zugreifen möchten, verwenden Sie den Assistenten zum Hinzufügen von Element Variablen, um der Dialogfeld Klasse eine Member-Variable der entsprechenden Klasse hinzuzufügen. Fügen Sie diese Element Variable an die Steuerelement Eigenschaft an.

Element Variablen können eine Steuerelement Eigenschaft anstelle einer Value-Eigenschaft aufweisen. Die Value-Eigenschaft bezieht sich auf den Datentyp, der vom Steuerelement zurückgegeben wird, z `CString` **`int`** . b. oder. Die Control-Eigenschaft ermöglicht den direkten Zugriff auf das Steuerelement über einen Datenmember, dessen Typ eine der Steuerelement Klassen in MFC ist, z `CButton` `CEdit` . b. oder.

> [!NOTE]
> Für ein bestimmtes Steuerelement können Sie, wenn gewünscht, über mehrere Element Variablen mit der Value-Eigenschaft und höchstens eine Element Variable mit der Control-Eigenschaft verfügen. Einem Steuerelement kann nur ein MFC-Objekt zugeordnet werden, da mehrere Objekte, die an ein Steuerelement angefügt sind, oder ein beliebiges anderes Fenster in der Meldungs Zuordnung zu einer Mehrdeutigkeit führen würde.

Mit diesem Objekt können Sie beliebige Element Funktionen für das Steuerelement Objekt aufzurufen. Solche Aufrufe wirken sich auf das Steuerelement im Dialogfeld aus. Wenn beispielsweise ein Kontrollkästchen-Steuerelement, das durch eine Variable *m_Checkbox*dargestellt wird, vom Typ `CButton` ist, können Sie Folgendes aufzurufen:

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

Hier erfüllt die Element Variable *m_Checkbox* den gleichen Zweck wie die Member `GetMyCheckbox` -Funktion, die unter [typsicherer Zugriff auf Steuerelemente ohne Code-Assistenten](../mfc/type-safe-access-to-controls-without-code-wizards.md)angezeigt wird. Wenn es sich bei dem Kontrollkästchen nicht um ein automatisches Kontrollkästchen handelt, benötigen Sie in der Dialogfeld Klasse weiterhin einen Handler für die BN_CLICKED Steuerelement-Benachrichtigungs Meldung, wenn auf die Schaltfläche geklickt wird.

Weitere Informationen zu-Steuerelementen finden Sie unter Steuer [Elemente](../mfc/controls-mfc.md).

## <a name="see-also"></a>Weitere Informationen

[Typsicherer Zugriff auf Steuerelemente in einem Dialog Feld](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Arbeiten mit Dialogfeldern in MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Typsicherer Zugriff auf Steuerelemente ohne Code-Assistenten](../mfc/type-safe-access-to-controls-without-code-wizards.md)
