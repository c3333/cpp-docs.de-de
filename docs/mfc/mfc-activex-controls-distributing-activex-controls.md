---
title: 'MFC-ActiveX-Steuerelemente: Weitergabe von ActiveX-Steuerelementen'
ms.date: 09/12/2018
f1_keywords:
- GetWindowsDirectory
- GetSystemDirectory
helpviewer_keywords:
- MFC ActiveX controls [MFC], ANSI or Unicode versions
- RegSvr32.exe
- MFC ActiveX controls [MFC], distributing
- distributing MFC ActiveX controls
- redistributable files, MFC ActiveX controls
- GetSystemDirectory method [MFC]
- registering ActiveX controls
- MSVCRT40.dll
- registry [MFC], registering controls
- LoadLibrary method, registering ActiveX controls
- MFC40U.DLL
- MFC40.DLL
- GetWindowsDirectory method [MFC]
- installing ActiveX controls
- GetProcAddress method, registering ActiveX controls
- MFC ActiveX controls [MFC], installing
- MFC ActiveX controls [MFC], registering
- registering controls
- OLEPRO32.DLL
ms.assetid: cd70ac9b-f613-4879-9e81-6381fdfda2a1
ms.openlocfilehash: 11d647922a4f8097e03e112c0c93c833524c2c4e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618207"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>MFC-ActiveX-Steuerelemente: Weitergabe von ActiveX-Steuerelementen

In diesem Artikel werden mehrere Probleme im Zusammenhang mit der Verteilung von ActiveX-Steuerelementen erläutert

- [ANSI-oder Unicode-Steuerelement Versionen](#_core_ansi_or_unicode_control_versions)

- [Installieren von ActiveX-Steuerelementen und verteilbaren DLLs](#_core_installing_activex_controls_and_redistributable_dlls)

- [Registrieren von Steuerelementen](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

## <a name="ansi-or-unicode-control-versions"></a><a name="_core_ansi_or_unicode_control_versions"></a>ANSI-oder Unicode-Steuerelement Versionen

Sie müssen entscheiden, ob eine ANSI-oder Unicode-Version des Steuer Elements oder beides ausgeliefert werden soll. Diese Entscheidung basiert auf Portabilitäts Faktoren, die in ANSI-und Unicode-Zeichensätzen enthalten sind.

ANSI-Steuerelemente, die für alle Win32-Betriebssysteme funktionieren, ermöglichen eine maximale Portabilität zwischen den verschiedenen Win32-Betriebssystemen. Unicode-Steuerelemente funktionieren nur unter Windows NT (Version 3,51 oder höher), jedoch nicht unter Windows 95 oder Windows 98. Wenn die Portabilität Ihr Hauptanliegen ist, senden Sie ANSI-Steuerelemente. Wenn Ihre Steuerelemente nur unter Windows NT ausgeführt werden, können Sie Unicode-Steuerelemente liefern. Sie können auch auswählen, ob beide ausgeliefert werden und dass Ihre Anwendung die für das Betriebssystem des Benutzers am besten geeignete Version installiert.

## <a name="installing-activex-controls-and-redistributable-dlls"></a><a name="_core_installing_activex_controls_and_redistributable_dlls"></a>Installieren von ActiveX-Steuerelementen und verteilbaren DLLs

Das Setup Programm, das Sie mit ihren ActiveX-Steuerelementen bereitstellen, sollte ein spezielles Unterverzeichnis des Windows-Verzeichnisses erstellen und die Steuerelemente installieren. Ocx-Dateien darin.

> [!NOTE]
> Verwenden Sie die Windows- `GetWindowsDirectory` API in Ihrem Setup Programm, um den Namen des Windows-Verzeichnisses abzurufen. Möglicherweise möchten Sie den Namen des Unterverzeichnisses aus dem Namen Ihres Unternehmens oder Produkts ableiten.

Das Setup Programm muss die erforderlichen verteilbaren dll-Dateien im Windows-System Verzeichnis installieren. Wenn eine der DLLs bereits auf dem Computer des Benutzers vorhanden ist, sollte das Setup Programm Ihre Versionen mit den Versionen vergleichen, die Sie installieren. Installieren Sie eine Datei nur dann neu, wenn die Versionsnummer höher ist als die Datei, die bereits installiert ist.

Da ActiveX-Steuerelemente nur in OLE-Container Anwendungen verwendet werden können, ist es nicht erforderlich, den vollständigen Satz von OLE-DLLs mit den Steuerelementen zu verteilen. Sie können davon ausgehen, dass für die enthaltende Anwendung (oder das Betriebssystem) die standardmäßigen OLE-DLLs installiert sind.

## <a name="registering-controls"></a><a name="_core_registering_controls"></a>Registrieren von Steuerelementen

Damit ein Steuerelement verwendet werden kann, müssen entsprechende Einträge in der Windows-Registrierungsdatenbank erstellt werden. Einige ActiveX-Steuerelement Container stellen ein Menü Element bereit, mit dem Benutzer neue Steuerelemente registrieren können. diese Funktion ist jedoch möglicherweise nicht in allen Containern verfügbar. Daher kann es sein, dass das Setup Programm die Steuerelemente bei Ihrer Installation registrieren soll.

Wenn Sie möchten, können Sie das Setup Programm so schreiben, dass das Steuerelement direkt registriert wird.

Verwenden `LoadLibrary` Sie die Windows-API zum Laden der Steuerelement-DLL. Verwenden Sie als nächstes `GetProcAddress` zum Abrufen der Adresse der Funktion "DllRegisterServer". Zum Schluss wird die- `DllRegisterServer` Funktion aufgerufen. Das folgende Codebeispiel veranschaulicht eine mögliche Methode, wobei `hLib` das Handle der Steuerelement Bibliothek speichert und `lpDllEntryPoint` die Adresse der Funktion "DllRegisterServer" speichert.

[!code-cpp[NVC_MFC_AxCont#16](codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

Der Vorteil der direkten Registrierung des Steuer Elements besteht darin, dass Sie keinen separaten Prozess (nämlich regsvr32) aufrufen und laden müssen, um die Installationszeit zu verkürzen. Da die Registrierung ein interner Prozess ist, kann das Setup Programm außerdem Fehler und unvorhergesehene Situationen verarbeiten, die besser als ein externer Prozess möglich sind.

> [!NOTE]
> Vor der Installation eines ActiveX-Steuer Elements durch das Setup Programm sollte aufgerufen werden `OleInitialize` . Wenn das Setup Programm abgeschlossen ist, wird aufgerufen `OleUnitialize` . Dadurch wird sichergestellt, dass die OLE-System-DLLs den richtigen Zustand zum Registrieren eines ActiveX-Steuer Elements aufweisen.

Sie sollten MFCx0. dll registrieren.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)
