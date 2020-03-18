---
title: EDITBIN-Optionen
description: Referenzhandbuch zu den Befehlszeilenoptionen für das Microsoft-EDITBIN-Hilfsprogramm.
ms.date: 02/09/2020
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: 9fd4170e5ee020780963d83936f1a9fd08d2be11
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439974"
---
# <a name="editbin-options"></a>EDITBIN-Optionen

Sie können EDITBIN zum Ändern von Objektdateien, ausführbaren Dateien und Dynamic Link Libraries (DLLs) verwenden. Optionen geben die Änderungen an, die EDITBIN vornimmt.

Eine Option besteht aus einem optionsspezifizierer, bei dem es sich entweder um einen Bindestrich (`-`) oder einen Schrägstrich (`/`) handelt, gefolgt vom Namen der Option. Optionsnamen können nicht abgekürzt werden. Einige Optionen akzeptieren Argumente, die nach einem Doppelpunkt (`:`) angegeben werden. Innerhalb einer Optionsangabe sind keine Leerzeichen oder Tabstopps zulässig. Verwenden Sie eines oder mehrere Leerzeichen bzw. Tabstopps, um Optionsangaben in der Befehlszeile voneinander zu trennen. Bei Optionsnamen und Schlüsselwort Argumenten oder Dateinamen Argumenten wird die Groß-/Kleinschreibung nicht beachtet. Beispielsweise haben `-bind` und `/BIND` denselben Wert.

EDITBIN verfügt über die folgenden Optionen:

|Option|Zweck|
|------------|-------------|
|[/ALLOWBIND](allowbind.md)|Gibt an, ob eine DLL gebunden werden kann.|
|[/ALLOWISOLATION](allowisolation.md)|Gibt das Suchverhalten von dll-oder ausführbaren Datei Manifesten an.|
|[/APPCONTAINER](appcontainer.md)|Gibt an, ob die app in einem appcontainer ausgeführt werden muss, z. –. eine UWP-app.|
|[/BIND](bind.md)|Legt die Adressen für die Einstiegspunkte in den angegebenen-Objekten fest, um die Ladezeit zu beschleunigen.|
|[/DYNAMICBASE](dynamicbase.md)|Gibt an, ob die dll oder das ausführbare Image mithilfe der Address Space Layout Anordnung (ASLR) nach dem Zufallsprinzip zur Ladezeit neu erstellt werden kann.|
|[/ERRORREPORT](errorreport-editbin-exe.md)| Veraltet. Die Fehlerberichterstattung wird durch [Windows-Fehlerberichterstattung (wer)](/windows/win32/wer/windows-error-reporting) -Einstellungen gesteuert. |
|[/HEAP](heap.md)|Legt die Größe des Heap des ausführbaren Bilds in Bytes fest.|
|[/HIGHENTROPYVA](highentropyva.md)|Gibt an, ob die dll oder das ausführbare Image High Entropie (64-Bit) Address Space Layout Anordnung (ASLR) unterstützt.|
|[/INTEGRITYCHECK](integritycheck.md)|Gibt an, ob die digitale Signatur zur Ladezeit überprüft werden soll.|
|[/LARGEADDRESSAWARE](largeaddressaware.md)|Gibt an, ob das Objektadressen unterstützt, die größer als zwei Gigabytes sind.|
|[/NOLOGO](nologo-editbin.md)|Unterdrückt das EDITBIN-Start Banner.|
|[/NXCOMPAT](nxcompat.md)|Gibt an, ob das ausführbare Image mit der Windows-Daten Ausführungs Verhinderung kompatibel ist.|
|[/REBASE](rebase.md)|Legt die Basisadressen für die angegebenen Objekte fest.|
|[/RELEASE](release.md)|Legt die Prüfsumme im Header fest.|
|[/SECTION](section-editbin.md)|Überschreibt die Attribute eines Abschnitts.|
|[/STACK](stack.md)|Legt die Größe des Stapels des ausführbaren Bilds in Bytes fest.|
|[/SUBSYSTEM](subsystem.md)|Gibt die Ausführungsumgebung an.|
|[/SWAPRUN](swaprun.md)|Gibt an, dass das ausführbare Image in die Auslagerungs Datei kopiert und dann von dort aus ausgeführt wird.|
|[/TSAWARE](tsaware.md)|Gibt an, dass die app in einer Umgebung mit mehreren Benutzern ausgeführt werden soll.|
|[/VERSION](version.md)|Legt die Versionsnummer in der Kopfzeile fest.|

## <a name="see-also"></a>Weitere Informationen

[Zusätzliche MSVC-Buildtools](c-cpp-build-tools.md)\
[EDITBIN-Referenz](editbin-reference.md)
