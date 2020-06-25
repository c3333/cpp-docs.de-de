---
title: /MANIFESTUAC (bettet UAC-Informationen in Manifest ein)
ms.date: 06/12/2020
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
ms.openlocfilehash: 96719c6f6f5359afb03b967524b1f65db6dc664a
ms.sourcegitcommit: 8645408c7929558b8162f781776d0908d790a41c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "85334938"
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC (bettet UAC-Informationen in Manifest ein)

Gibt an, ob Informationen zur Benutzerkontensteuerung (UAC) in das Programmmanifest eingebettet werden.

## <a name="syntax"></a>Syntax

> **`/MANIFESTUAC`**\
> **`/MANIFESTUAC:NO`**\
> **`/MANIFESTUAC:`**_`level`_\
> **`/MANIFESTUAC:`**_`uiAccess`_\
> **`/MANIFESTUAC:`**_`fragment`_

### <a name="parameters"></a>Parameter

**`NO`**<br/>
Der Linker bindet keine UAC-Informationen in das Programm Manifest ein.

*`level`*<br/>
**`level=`** gefolgt von einer von **`'asInvoker'`** , **`'highestAvailable'`** oder **`'requireAdministrator'`** . Der Standardwert ist **`'asInvoker'`** . Weitere Informationen finden Sie im Abschnitt [Hinweise](#remarks).

*`uiAccess`*<br/>
**`uiAccess='true'`** Wenn die Anwendung die Schutz Ebenen der Benutzeroberfläche umgehen und Eingaben in Fenster mit höheren Berechtigungen auf dem Desktop steuern soll, andernfalls **`uiAccess='false'`** . Der Standardwert ist **`uiAccess='false'`** . Legen Sie dieses Argument **`uiAccess='true'`** nur für Barrierefreiheits Anwendungen von Benutzeroberflächen fest.

*`fragment`*<br/>
Eine Zeichenfolge, die die *`level`* -und- *`uiAccess`* Werte enthält. Kann optional in doppelte Anführungszeichen eingeschlossen werden. Weitere Informationen finden Sie im Abschnitt [Hinweise](#remarks).

## <a name="remarks"></a>Hinweise

Wenn Sie mehrere **`/MANIFESTUAC`** Optionen in der Befehlszeile angeben, hat der letzte eingegebene Vorrang.

Folgende Optionen stehen zur Auswahl **`/MANIFESTUAC:`** _`level`_ :

- **`level='asInvoker'`**: Die Anwendung wird auf der gleichen Berechtigungsstufe wie der Prozess ausgeführt, der Sie gestartet hat. Sie können die Anwendung auf eine höhere Berechtigungsstufe erhöhen, indem Sie **als Administrator ausführen**auswählen.

- **`level='highestAvailable'`**: Die Anwendung wird mit der höchsten Berechtigungsstufe ausgeführt. Wenn der Benutzer, der die Anwendung startet, Mitglied der Gruppe "Administratoren" ist, ist diese Option identisch mit **`level='requireAdministrator'`** . Wenn die höchste verfügbare Berechtigungsebene höher als die Ebene des öffnenden Prozesses ist, fordert das System zur Eingabe von Anmelde Informationen auf.

- **`level='requireAdministrator'`**: Die Anwendung wird mit Administrator Berechtigungen ausgeführt. Der Benutzer, der die Anwendung startet, muss ein Mitglied der Gruppe "Administratoren" sein. Wenn der öffnende Prozess nicht mit Administrator Berechtigungen ausgeführt wird, fordert das System zur Eingabe von Anmelde Informationen auf.

Sie können den *`level`* -Wert und den- *`uiAccess`* Wert in einem Schritt mithilfe der- **`/MANIFESTUAC:`** _`fragment`_ Option angeben. Das Fragment muss das folgende Format aufweisen:

> **`/MANIFESTUAC:`** \[ **`"`** ] **`level=`** { **`'asInvoker'`** | **`'highestAvailable'`** | **`'requireAdministrator'`** } **`uiAccess=`** { **`'true'`** | **`'false'`** } \[ **`"`** ]

Zum Beispiel:

**`/MANIFESTUAC:"level='highestAvailable' uiAccess='true'"`**

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die Eigenschaften Seite der linkermanifestressourcendatei aus **Configuration Properties**  >  **Linker**  >  **Manifest File** .

1. Ändern Sie die Eigenschaften **Benutzerkontensteuerung (User Account Control, UAC)**, **UAC-Ausführungs Ebene**und **UAC-Umgehung der UI-Schutz** .

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

1. Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A> und <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)
