---
title: Typsicherer Zugriff auf Steuerelemente mit Code-Assistenten
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: b49c1b6f21dfe5270e40649241812320303ad411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370918"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Typsicherer Zugriff auf Steuerelemente mit Code-Assistenten

Wenn Sie mit DDX-Features vertraut sind, können Sie die Control-Eigenschaft im Assistenten zum Hinzufügen von [Mitgliedsvariablen](../ide/add-member-variable-wizard.md) verwenden, um typsicheren Zugriff zu erstellen. Dieser Ansatz ist einfacher als das Erstellen von Steuerelementen ohne Code-Assistenten.

Wenn Sie einfach nur auf den Wert eines Steuerelements zugreifen möchten, stellt DDX ihn bereit. Wenn Sie mehr als nur auf den Wert eines Steuerelements zugreifen möchten, verwenden Sie den Assistenten zum Hinzufügen von Membervariablen, um Ihrer Dialogklasse eine Membervariable der entsprechenden Klasse hinzuzufügen. Fügen Sie diese Membervariable an die Control-Eigenschaft an.

Membervariablen können eine Control-Eigenschaft anstelle einer Value-Eigenschaft haben. Die Value-Eigenschaft bezieht sich auf den Typ `CString` der vom Steuerelement zurückgegebenen Daten, z. B. oder **int**. Die Control-Eigenschaft ermöglicht den direkten Zugriff auf das Steuerelement über einen Datenmember, `CButton` `CEdit`dessen Typ eine der Steuerelementklassen in MFC ist, z. B. oder .

> [!NOTE]
> Für ein bestimmtes Steuerelement können Sie, wenn Sie möchten, mehrere Membervariablen mit der Value-Eigenschaft und höchstens eine Membervariable mit der Control-Eigenschaft haben. Sie können nur ein MFC-Objekt einem Steuerelement zugeordnet haben, da mehrere Objekte, die an ein Steuerelement oder ein anderes Fenster angefügt sind, zu einer Mehrdeutigkeit in der Nachrichtenzuordnung führen würden.

Sie können dieses Objekt verwenden, um beliebige Memberfunktionen für das Steuerelementobjekt aufzurufen. Solche Aufrufe wirken sich auf das Steuerelement im Dialogfeld aus. Für ein Kontrollkästchen-Steuerelement, das durch eine Variable `CButton`m_Checkbox *dargestellt*wird, können Sie z. B. folgende Aufrufen anfordern:

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

Hier dient die Membervariable *m_Checkbox* dem `GetMyCheckbox` gleichen Zweck wie die Memberfunktion, die unter [Typsicherer Zugriff auf Steuerelemente ohne Code-Assistenten](../mfc/type-safe-access-to-controls-without-code-wizards.md)angezeigt wird. Wenn es sich bei dem Kontrollkästchen nicht um ein automatisches Kontrollkästchen handelt, benötigen Sie weiterhin einen Handler in der Dialogklasse für die BN_CLICKED-Steuerbenachrichtigungsmeldung, wenn auf die Schaltfläche geklickt wird.

Weitere Informationen zu Steuerelementen finden Sie unter [Steuerelemente](../mfc/controls-mfc.md).

## <a name="see-also"></a>Siehe auch

[Typsicherer Zugriff auf die Steuerelemente in einem Dialogfeld](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Arbeiten mit Dialogfeldern in MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Typsicherer Zugriff auf Steuerelemente ohne Code-Assistenten](../mfc/type-safe-access-to-controls-without-code-wizards.md)
