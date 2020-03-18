---
title: /SUBSYSTEM
ms.date: 11/04/2016
f1_keywords:
- /subsystem_editbin
helpviewer_keywords:
- /SUBSYSTEM editbin option
- -SUBSYSTEM editbin option
- SUBSYSTEM editbin option
ms.assetid: 515e4cdf-3cc4-4659-8764-1f2757b49215
ms.openlocfilehash: 708bfcce3e6d6616116bcc08441f374b46914c82
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438863"
---
# <a name="subsystem"></a>/SUBSYSTEM

Gibt die vom ausführbaren Image benötigte Ausführungsumgebung an.

```
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|
        EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|
        NATIVE|POSIX|WINDOWS|WINDOWSCE}[,major[.minor]]
```

## <a name="remarks"></a>Bemerkungen

Mit dieser Option wird das Image so bearbeitet, dass erkennbar ist, welches Subsystem vom Betriebssystem zur Ausführung aufgerufen werden muss.

Sie können jedes der folgenden Subsysteme angeben:

**BOOT_APPLICATION**<br/>
Eine in der Windows-Startumgebung ausgeführte Anwendung. Weitere Informationen zu Start Anwendungen finden Sie unter [Informationen zum BCD-WMI-Anbieter](/previous-versions/windows/desktop/bcd/about-bcd).

**TS**<br/>
Eine Windows-Zeichenmodusanwendung. Im Betriebssystem wird eine Konsole für Konsolenanwendungen zur Verfügung gestellt.

**EFI_APPLICATION**<br/>
**EFI_BOOT_SERVICE_DRIVER**<br/>
**EFI_ROM**<br/>
**EFI_RUNTIME_DRIVER**<br/>
Extensible Firmware Interface (EFI)-Image

Die EFI-Subsystemoptionen beschreiben ausführbare Images, die in die Extensible Firmware Interface-Umgebung ausgeführt werden. Diese Umgebung wird in der Regel mit der Hardware bereitgestellt und ausgeführt, bevor das Betriebssystem geladen wird. Die Hauptunterschiede zwischen EFI-Imagetypen sind die Speicheradresse, in die das Image geladen wird und die Aktionen, die ausgeführt wird, wenn der Aufruf zum Image zurückgegeben wird. Ein EFI_APPLICATIONS-Image wird entladen, wenn die Steuerung zurückgegeben wird. Ein EFI_BOOT_SERVICE_DRIVER oder ein EFI_RUNTIME_DRIVER wird entladen, wenn die Steuerung mit einem Fehlercode zurückgegeben wird. Ein EFI_ROM-Image wird vom ROM ausgeführt. Weitere Informationen finden Sie in den Spezifikationen auf der [Unified EFI-Forums](https://www.uefi.org/) Website.

**Einheimischen**<br/>
Code, der ohne eine Subsystemumgebung ausgeführt wird – z. B. Gerätetreiber im Kernelmodus und systemeigene Systemprozesse. Diese Option ist üblicherweise für Windows-Systemfunktionen reserviert.

**POSIX**<br/>
Eine App, die im POSIX-Subsystem in Windows ausgeführt wird.

**Windows**<br/>
Eine App, die in der grafischen Umgebung von Windows ausgeführt wird. Dies gilt sowohl für Desktop-Apps als auch für universelle Windows-Plattform-Apps (UWP).

**WindowsCE**<br/>
Das WINDOWSCE-Subsystem gibt an, dass die App dafür vorgesehen ist, auf einem Gerät mit einer Version von Windows CE-Kernels ausgeführt zu werden. Kernelversionen schließen PocketPC, Windows Mobile, Windows Phone 7, Windows CE V1.0-6.0R3 und Windows Embedded Compact 7 ein.

Mit den optionalen `major` und `minor`-Werten werden die Mindestanforderungen in Bezug auf die Version des angegebenen Subsystems festgelegt:

- Der Ganzzahlenbereich der Versionsnummer (der Abschnitt links vom Dezimalpunkt) wird durch `major` wiedergegeben.

- Der Nachkommabereich der Versionsnummer (der Abschnitt rechts vom Dezimalpunkt) wird durch `minor` wiedergegeben.

- Die Werte für `major` und `minor` müssen in einem Bereich von 0 bis 65.535 liegen.

Die Wahl des Subsystems wirkt sich auf die Standardstartadresse des Programms aus. Weitere Informationen finden Sie unter [/Entry (Einstiegspunkt Symbol)](entry-entry-point-symbol.md), der Linker/Entry:*Function* -Option.

Weitere Informationen, einschließlich der Mindest-und Standardwerte für die Haupt-und neben Versionsnummern der einzelnen Subsysteme, finden Sie unter der [/Subsystem](subsystem-specify-subsystem.md) -Linkeroption.

## <a name="see-also"></a>Weitere Informationen

[EDITBIN-Optionen](editbin-options.md)
