---
title: Schwerwiegender Fehler C1010
ms.date: 09/03/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 40a2828ce6b21384ec49c371f23e506d816f1284
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204788"
---
# <a name="fatal-error-c1010"></a>Schwerwiegender Fehler C1010

> Unerwartetes Dateiende während der Suche nach dem vorkompilierten Header. Haben Sie vergessen, der Quelle "#include *Name*" hinzuzufügen?

## <a name="remarks"></a>Bemerkungen

Eine Includedatei, die von [/Yu](../../build/reference/yu-use-precompiled-header-file.md) angegeben wird, ist nicht in der Quelldatei aufgeführt. Diese Option ist in vielen Visual Studio C++ -Projekttypen standardmäßig aktiviert. Die standardmäßige Includedatei, die von dieser Option angegeben wird, ist " *PCH. h*" oder " *stdafx. h* " in Visual Studio 2017 und früher.

Verwenden Sie in der Visual Studio-Umgebung eine der folgenden Methoden, um diesen Fehler zu beheben:

- Stellen Sie sicher, dass Sie die *PCH. h* -Header Datei oder die *PCH. cpp* -Quelldatei nicht versehentlich aus dem aktuellen Projekt gelöscht, umbenannt oder entfernt haben. (In älteren Projekten haben diese Dateien möglicherweise den Namen " *stdafx. h* " und " *stdafx. cpp*".)

- Stellen Sie sicher, dass die Header Datei " *PCH. h* " oder " *stdafx. h* " vor allen anderen Code-oder Präprozessoranweisungen in den Quelldateien enthalten ist. (In Visual Studio wird diese Header Datei durch die **Vorkompilierte Header Datei** -Projekt Eigenschaft angegeben.)

- Sie können die Verwendung des vorkompilierten Headers deaktivieren. Wenn Sie vorkompilierte Header deaktivieren, kann sich dies erheblich auf die Buildleistung auswirken.

### <a name="to-turn-off-precompiled-headers"></a>So deaktivieren Sie vorkompilierte Header

Um die Verwendung des vorkompilierten Headers in einem Projekt zu deaktivieren, führen Sie die folgenden Schritte aus:

1. Klicken Sie im **Projektmappen-Explorer** Fenster mit der rechten Maustaste auf den Projektnamen, und wählen Sie dann Eigenschaften aus, um das Dialogfeld **Eigenschaften** **Seiten** für das Projekt zu öffnen.

1. Wählen Sie **Configuration** in der Dropdown-Konfiguration **alle Konfigurationen**aus.

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften** > **C++ C/**  > **Vorkompilierte Header** aus.

1. Wählen Sie in der Liste Eigenschaft die Dropdown Liste für die Eigenschaft **vorkompilierter Header** aus, und wählen Sie dann **keine vorkompilierten Header**aus. Klicken Sie auf **OK**, um die Änderungen zu speichern.

1. Klicken Sie im **Projektmappen-Explorer** Fenster mit der rechten Maustaste auf die *PCH. cpp* -Quelldatei in Ihrem Projekt. (In älteren Projekten kann die Datei " *stdafx. cpp*" genannt werden.) Wählen Sie **aus Projekt ausschließen aus** , um es aus dem Build zu entfernen.

1. Verwenden Sie den Menübefehl **Build** > **Clean Solution** für jede Konfiguration, die Sie erstellen, um alle *PROJECT_NAME PCH* -Dateien in ihren zwischenbuildverzeichnissen zu löschen.

## <a name="see-also"></a>Weitere Informationen

[Vorkompilierte Header Dateien](../../build/creating-precompiled-header-files.md)\
[/Yc (Vorkompilierte Header Datei erstellen)](../../build/reference/yc-create-precompiled-header-file.md)\
[/Yu (Vorkompilierte Header Datei verwenden)](../../build/reference/yu-use-precompiled-header-file.md)
