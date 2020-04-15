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
ms.openlocfilehash: 1ada1c801b2d9d62f1cc4cd5bf72a2995225b3de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364624"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>MFC-ActiveX-Steuerelemente: Weitergabe von ActiveX-Steuerelementen

In diesem Artikel werden mehrere Probleme im Zusammenhang mit der Neuverteilung von ActiveX-Steuerelementen behandelt:

- [ANSI- oder Unicode-Steuerungsversionen](#_core_ansi_or_unicode_control_versions)

- [Installieren von ActiveX-Steuerelementen und rediszivernen DLLs](#_core_installing_activex_controls_and_redistributable_dlls)

- [Registrieren von Steuerelementen](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

## <a name="ansi-or-unicode-control-versions"></a><a name="_core_ansi_or_unicode_control_versions"></a>ANSI- oder Unicode-Steuerungsversionen

Sie müssen entscheiden, ob Sie eine ANSI- oder Unicode-Version des Steuerelements oder beides versenden möchten. Diese Entscheidung basiert auf Portabilitätsfaktoren, die ANSI- und Unicode-Zeichensätzen innewohnen.

ANSI-Steuerelemente, die auf allen Win32-Betriebssystemen funktionieren, ermöglichen eine maximale Portabilität zwischen den verschiedenen Win32-Betriebssystemen. Unicode-Steuerelemente funktionieren nur unter Windows NT (Version 3.51 oder höher), jedoch nicht unter Windows 95 oder Windows 98. Wenn die Portabilität Ihr Hauptanliegen ist, versenden Sie ANSI-Steuerelemente. Wenn Ihre Steuerelemente nur unter Windows NT ausgeführt werden, können Sie Unicode-Steuerelemente versenden. Sie können auch beide versenden und Ihre Anwendung die Version installieren lassen, die für das Betriebssystem des Benutzers am besten geeignet ist.

## <a name="installing-activex-controls-and-redistributable-dlls"></a><a name="_core_installing_activex_controls_and_redistributable_dlls"></a>Installieren von ActiveX-Steuerelementen und rediszivernen DLLs

Das Setupprogramm, das Sie mit Ihren ActiveX-Steuerelementen bereitstellen, sollte ein spezielles Unterverzeichnis des Windows-Verzeichnisses erstellen und die Steuerelemente installieren' . OCX-Dateien darin.

> [!NOTE]
> Verwenden Sie `GetWindowsDirectory` die Windows-API in Ihrem Setupprogramm, um den Namen des Windows-Verzeichnisses zu erhalten. Sie können den Namen des Unterverzeichnisses vom Namen Ihres Unternehmens oder Produkts ableiten.

Das Setupprogramm muss die erforderlichen verteilbaren DLL-Dateien im Windows-Systemverzeichnis installieren. Wenn eine der DLLs bereits auf dem Computer des Benutzers vorhanden ist, sollte das Setupprogramm ihre Versionen mit den Versionen vergleichen, die Sie installieren. Installieren Sie eine Datei nur dann neu, wenn ihre Versionsnummer höher ist als die bereits installierte Datei.

Da ActiveX-Steuerelemente nur in OLE-Containeranwendungen verwendet werden können, ist es nicht erforderlich, den vollständigen Satz von OLE-DLLs mit Ihren Steuerelementen zu verteilen. Sie können davon ausgehen, dass in der enthaltenden Anwendung (oder dem Betriebssystem selbst) die Standard-OLE-DLLs installiert sind.

## <a name="registering-controls"></a><a name="_core_registering_controls"></a>Registrieren von Steuerelementen

Bevor ein Steuerelement verwendet werden kann, müssen entsprechende Einträge für dieses Steuerelement in der Windows-Registrierungsdatenbank erstellt werden. Einige ActiveX-Steuerelementcontainer stellen ein Menüelement für Benutzer zum Registrieren neuer Steuerelemente bereit, aber diese Funktion ist möglicherweise nicht in allen Containern verfügbar. Daher können Sie möchten, dass Ihr Setupprogramm die Steuerelemente registriert, wenn sie installiert sind.

Wenn Sie möchten, können Sie Ihr Setup-Programm schreiben, um das Steuerelement direkt zu registrieren.

Verwenden `LoadLibrary` Sie die Windows-API, um die Steuer-DLL zu laden. Als Nächstes `GetProcAddress` verwenden Sie, um die Adresse der Funktion "DllRegisterServer" abzurufen. Rufen Sie `DllRegisterServer` schließlich die Funktion auf. Das folgende Codebeispiel veranschaulicht eine `hLib` mögliche Methode, bei der `lpDllEntryPoint` das Handle der Steuerelementbibliothek gespeichert und die Adresse der Funktion "DllRegisterServer" gespeichert wird.

[!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

Der Vorteil der direkten Registrierung des Steuerelements besteht darin, dass Sie keinen separaten Prozess aufrufen und laden müssen (nämlich REGSVR32), wodurch die Installationszeit reduziert wird. Da es sich bei der Registrierung um einen internen Prozess handelt, kann das Setupprogramm Fehler und unvorhergesehene Situationen besser behandeln als ein externer Prozess.

> [!NOTE]
> Bevor Ihr Setupprogramm ein ActiveX-Steuerelement `OleInitialize`installiert, sollte es aufrufen. Wenn Ihr Setupprogramm abgeschlossen `OleUnitialize`ist, rufen Sie an. Dadurch wird sichergestellt, dass sich die OLE-System-DLLs im ordnungsgemäßen Zustand für die Registrierung eines ActiveX-Steuerelements befinden.

Sie sollten MFCx0.DLL registrieren.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)
