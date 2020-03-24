---
title: Versionsinformationen-EditorC++()
ms.date: 02/14/2019
f1_keywords:
- vc.editors.version.F1
- vc.editors.version
helpviewer_keywords:
- Version Information editor [C++], about Version Information editor
- editors, Version Information
- resource editors [C++], Version Information editor
- version information resources [C++]
- resources [C++], editing version information
- languages, version information
- New Version Info Block
- blocks, adding
- resources [C++], adding version information
- version information, adding for languages
- blocks, deleting
- version information, deleting blocks
- resources [C++], deleting version information
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
ms.openlocfilehash: b083ed27b6b1f471dbec9b96e7be7a6165f8d125
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214369"
---
# <a name="version-information-editor-c"></a>Versionsinformationen-EditorC++()

Versionsinformationen bestehen aus einer Firmen- und einer Produkt-ID, einer Produktseriennummer und Copyright- und Markenbestimmungen. Mit dem **Versionsinformationen-Editor**erstellen und verwalten Sie diese Daten, die in der Versions Informations Ressource gespeichert sind. Die Versions Informations Ressource ist für eine Anwendung nicht erforderlich, aber Sie ist ein nützlicher Ort, um Informationen zu sammeln, die die Anwendung identifizieren. Versionsinformationen werden auch von Setup-APIs verwendet.

> [!NOTE]
> Der Windows-Standard sieht nur eine Versionsressource mit dem Namen VS_VERSION_INFO vor.

Eine Versionsinformationsressource weist einen oberen Block und mindestens einen unteren Block auf: ein einzelner Block mit unveränderlichen Informationen oben und mindestens ein weiterer Versionsinformationsblock darunter (für andere Sprachen und/oder Zeichensätze). Der obere Block weist sowohl editierbare Zahlenfelder als auch auswählbare Dropdownlisten auf. Die unteren Blöcke weisen nur editierbare Textfelder auf.

> [!NOTE]
> Wenn Sie den **Versionsinformationen-Editor**verwenden, können Sie in vielen Fällen mit der rechten Maustaste klicken, um ein Kontextmenü mit Ressourcen spezifischen Befehlen anzuzeigen. Wenn Sie z. b. auswählen, während Sie auf einen Block Header Eintrag zeigen, zeigt das Kontextmenü die Befehle " **neue Versions Block Informationen** " und " **Versions Block Informationen löschen** " an.

## <a name="how-to"></a>Vorgehensweise

Der **Versions Informations-Editor** ermöglicht Ihnen Folgendes:

### <a name="to-edit-a-string-in-a-version-information-resource"></a>So bearbeiten Sie eine Zeichenfolge in einer Versionsinformationsressource

Wählen Sie das Element einmal aus, um es auszuwählen, und klicken Sie dann erneut, um es zu bearbeiten. Nehmen Sie Änderungen direkt in der **Versions Informations** Tabelle oder im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)vor. Die vorgenommenen Änderungen werden an beiden Orten berücksichtigt.

Beachten Sie beim Bearbeiten des `FILEFLAGS` Schlüssels im **Versionsinformationen-Editor**, dass Sie die Eigenschaften **Debug**, **private Build**oder **Special Build** im **Eigenschaften** Fenster für RC-Dateien nicht festlegen können:

- Der **Versions Informations-Editor** legt die **Debug** -Eigenschaft mit einem `#ifdef` im Ressourcen Skript fest, basierend auf dem `_DEBUG` Build-Flag.

- Wenn für den `Private Build`-Schlüssel ein **Wert** in der **Versions Informations** Tabelle festgelegt ist, ist die entsprechende **private Build** -Eigenschaft im **Eigenschaften** Fenster für die `FILEFLAGS` Taste **true**. Wenn **value** leer ist, ist die Eigenschaft **false**. Ebenso ist der **spezielle** buildschlüssel in der **Versions Informations** Tabelle an die **spezielle** Buildeigenschaft für den `FILEFLAGS` Schlüssel gebunden.

Sie können die Informations Sequenz des Zeichen folgen Blocks sortieren, indem Sie entweder die Spaltenüberschriften **Key** oder **value** auswählen. Mithilfe dieser Überschriften können die Informationen automatisch in der ausgewählten Reihenfolge neu angeordnet werden.

### <a name="to-add-version-information-for-another-language-new-version-info-block"></a>So fügen Sie Versionsinformationen für eine andere Sprache hinzu (neuer Versions Informationsblock)

1. Öffnen Sie eine Versionsinformationsressource, indem Sie in der [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)darauf doppelklicken.

1. Klicken Sie mit der rechten Maustaste in der Versions Informations Tabelle, und wählen Sie **neuer Versions Informations Block**aus.

   Dieser Befehl fügt der aktuellen Versionsinformationsressource einen zusätzlichen Informationsblock hinzu und öffnet dessen entsprechende Eigenschaften im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window).

1. Wählen Sie im **Eigenschaftenfenster** die Sprache und den Zeichensatz für den neuen Block aus.

### <a name="to-delete-a-version-information-block"></a>So löschen Sie einen Versionsinformationsblock

1. Öffnen Sie die Versionsinformationsressource, indem Sie in der [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)auf ihr Symbol doppelklicken.

1. Klicken Sie mit der rechten Maustaste auf den Block Header, den Sie löschen möchten, und wählen Sie **Versions Informationsblock löschen**.

   Mit diesem Befehl wird der ausgewählte Header gelöscht, und die restlichen Versionsinformationen bleiben intakt. Die Aktion kann nicht rückgängig gemacht werden.

### <a name="to-access-version-information-from-within-your-program"></a>So greifen Sie aus Ihrem Programm auf Versionsinformationen zu

Wenn Sie aus ihrem Programm auf die Versionsinformationen zugreifen möchten, verwenden Sie die Funktion [GetFileVersionInfo](/windows/win32/api/winver/nf-winver-getfileversioninfow) und die Funktion [VerQueryValue](/windows/win32/api/winver/nf-winver-verqueryvaluew) .

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Ressourcen-Editor](../windows/resource-editors.md)<br/>
[Menüs und weitere Ressourcen](/windows/win32/menurc/resources)<br/>
[Versionsinformationen (Windows)](/windows/win32/menurc/version-information)
