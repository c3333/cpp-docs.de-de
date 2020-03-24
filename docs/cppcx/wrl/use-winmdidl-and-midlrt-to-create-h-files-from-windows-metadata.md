---
title: 'Gewusst wie: Verwenden von winmdidl.exe und midlrt.exe zum Erstellen von .h-Dateien aus Windows-Metadaten'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4be8ba11-c223-44ad-9256-7e1edae9a7bc
ms.openlocfilehash: bceb4aff22f6ebba9c8705b3b5a55d0478f244c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213537"
---
# <a name="how-to-use-winmdidlexe-and-midlrtexe-to-create-h-files-from-windows-metadata"></a>Gewusst wie: Verwenden von winmdidl.exe und midlrt.exe zum Erstellen von .h-Dateien aus Windows-Metadaten

"Winmdidl.exe" und "midlrt.exe" aktivieren Interaktionen auf COM-Ebene zwischen systemeigenem C++-Code und Komponenten für Windows-Runtime. "Winmdidl.exe" verwendet als Eingabe eine WINMD-Datei, die Metadaten für eine Komponente für Windows-Runtime enthält, und gibt eine IDL-Datei aus. "Midlrt.exe" konvertiert diese IDL-Datei in Headerdateien, die der C++-Code verarbeiten kann. Beide Tools werden an der Befehlszeile ausgeführt.

Sie verwenden diese Tools in zwei Hauptszenarien:

- Erstellen von benutzerdefinierten IDL-Dateien und Headerdateien, sodass eine C++-App, die mithilfe der Vorlagenbibliothek für Windows-Runtime geschrieben wurde, eine benutzerdefinierte Komponente für Windows-Runtime verarbeiten kann

- Generieren von Proxy- und Stub-Dateien für benutzerdefinierte Ereignistypen in einer Komponente für Windows-Runtime Weitere Informationen finden Sie unter [benutzerdefinierte Ereignisse und Ereignisaccessoren in Windows-Runtime-Komponenten](/windows/uwp/winrt-components/custom-events-and-event-accessors-in-windows-runtime-components).

Diese Tools sind nur für das Analysieren von benutzerdefinierten WINMD-Dateien erforderlich. Die IDL- und H-Dateien für Komponenten des Windows-Betriebssystems sind bereits für Sie generiert. Standardmäßig befinden sich diese in Windows 8.1 in \Programme (x86) \Windows kits\8.1\include\winrt\\.

## <a name="location-of-the-tools"></a>Speicherort der Tools

Windows 8.1 Standardmäßig befinden sich die Datei "winmdidl. exe" und die Datei ". exe" im Verzeichnis "c:\Programme (x86) \Windows kits\8.1\\". Versionen der Tools sind auch in den Ordnern "\bin\x86\" und "\bin\x64\" verfügbar.

## <a name="winmdidl-command-line-arguments"></a>Winmdidl-Befehlszeilenargumente

```
Winmdidl.exe [/nologo] [/suppressversioncheck] [/time] [/outdir:dir] [/banner:file] [/utf8] Winmdfile
```

**/nologo**<br/>
Verhindert die Anzeige der winmdidl-Copyrightmeldung und -Versionsnummer auf der Konsole.

**/suppressversioncheck**<br/>
Wird nicht verwendet.

**/Time**<br/>
Zeigt die gesamte Ausführungszeit in der Konsolenausgabe an.

**/OutDir:** <em>dir</em><br/>
Gibt ein Ausgabeverzeichnis an. Wenn der Pfad Leerzeichen enthält, verwenden Sie Anführungszeichen. Das Standardausgabe Verzeichnis ist *\<Laufwerk >* : \Users\\ *\<username >* \AppData\Local\VirtualStore\Program Files (x86) \Microsoft Visual Studio 12,0\\.

**/Banner:** <em>Datei</em><br/>
Gibt eine Datei an, die benutzerdefinierten Text enthält, der am Anfang der generierten IDL-Datei der standardmäßigen Copyrightmeldung und winmdidl-Versionsnummer vorangestellt wird. Wenn der Pfad Leerzeichen enthält, verwenden Sie Anführungszeichen.

**/utf8**<br/>
Bewirkt, dass die Datei als UTF-8 formatiert wird.

*Winmdfile*<br/>
Der Dateiname der zu analysierenden WINMD-Datei. Wenn der Pfad Leerzeichen enthält, verwenden Sie Anführungszeichen.

## <a name="midlrt-command-line-arguments"></a>Midlrt-Befehlszeilenargumente

Weitere Informationen finden Sie unter [mittlere und Windows-Runtime Komponenten](/windows/win32/Midl/midlrt-and-windows-runtime-components).

## <a name="examples"></a>Beispiele

Das folgende Beispiel zeigt einen winmdidl-Befehl an einer Visual Studio-x86-Eingabeaufforderung. Es wird ein Ausgabeverzeichnis und eine Datei angegeben, die speziellen Bannertext enthält, der der generierten IDL-Datei hinzugefügt wird.

`C:\Program Files (x86)\Microsoft Visual Studio 12.0>winmdidl /nologo /outdir:c:\users\giraffe\documents\ /banner:c:\users\giraffe\documents\banner.txt "C:\Users\giraffe\Documents\Visual Studio 2013\Projects\Test_for_winmdidl\Debug\Test_for_winmdidl\test_for_winmdidl.winmd"`

Im folgenden Beispiel wird die Konsolenanzeige von "winmdidl" gezeigt, die angibt, dass der Vorgang erfolgreich war.

**C:\users\giraffe\documents\\\ Test_for_winmdidl. idl wird erzeugt.**

Anschließend wird "midlrt" auf der generierten IDL-Datei ausgeführt. Beachten Sie, dass das **metadata_dir** -Argument nach dem Namen der IDL-Datei angegeben wird. Der Pfad von "\WinMetadata\" ist erforderlich – es ist der Speicherort für "windows.winmd".

`C:\Program Files (x86)\Microsoft Visual Studio 12.0> midlrt "c:\users\username\documents\test_for_winmdidl.idl" /metadata_dir "C:\Windows\System32\WinMetadata"`

## <a name="remarks"></a>Bemerkungen

Die Ausgabedatei eines winmdidl-Vorgangs weist denselben Namen wie die Eingabedatei auf, hat aber die Dateierweiterung IDL.

Wenn Sie eine Komponente für Windows-Runtime entwickeln, auf die von WRL zugegriffen wird, können Sie "winmdidl.exe" und "midlrt.exe" angeben, um als Postbuildschritte ausgeführt zu werden, sodass die IDL- und H-Dateien für jedes Build erzeugt werden. Ein Beispiel finden Sie unter [Ereignis erbenden Ereignisse in Windows-Runtime-Komponenten](/windows/uwp/winrt-components/raising-events-in-windows-runtime-components).
