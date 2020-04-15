---
title: Verteilen der MFC-Bibliothek
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
ms.openlocfilehash: e1434bee6d134d4c02b2c06125d340a68a6c305d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359902"
---
# <a name="redistributing-the-mfc-library"></a>Verteilen der MFC-Bibliothek

Wenn Sie Ihre Anwendung dynamisch mit der MFC-Bibliothek verknüpfen, müssen Sie die entsprechende MFC-DLL verteilen. Wenn Ihre MFC-App beispielsweise mithilfe der Version von MFC erstellt wurde, die in Visual Studio 2015 enthalten ist, müssen Sie je nachdem, ob Ihre App für schmale Zeichen oder Unicode-Unterstützung kompiliert wird, „mfc140.dll“ oder „mfc140u.dll“ verteilen.

> [!NOTE]
> Die Datei „mfc140.dll“ ist nicht im Verzeichnis für verteilbare Dateien in Visual Studio 2015 RTM enthalten. Sie können stattdessen die Versionen verwenden, die von Visual Studio 2015 in den Verzeichnissen Windows\system32 and Windows\syswow64 installiert wurden.

Da alle MFC-DLLs die freigegebene Version der C-Laufzeitbibliothek (CRT) verwenden, müssen Sie diese möglicherweise ebenfalls verteilen. Die Version von MFC, die in Visual Studio 2015 enthalten ist, verwendet die universelle CRT-Bibliothek, die in Windows 10 enthalten ist. Sie müssen die universelle CRT verteilen, um eine MFC-Anwendung auszuführen, die mithilfe von Visual Studio 2015 auf früheren Versionen von Windows erstellt wurde. Weitere Informationen zum Verteilen der universellen CRT als Betriebssystemkomponente oder durch lokale Bereitstellung finden Sie unter [Introducing the Universal CRT (Einführung der universellen CRT)](https://devblogs.microsoft.com/cppblog/introducing-the-universal-crt/). Informationen zum Herunterladen der universellen CRT für die zentrale Bereitstellung auf unterstützten Windows-Versionen finden Sie unter [Windows 10 Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=48234). Verteilbare architekturspezifische Versionen von „ucrtbase.dll“ für die lokale Bereitstellung finden Sie im Windows SDK. Standardmäßig installiert Visual Studio diese unter C:\Programme (x86)\Windows Kits\10\Redist\ucrt\DLLs\ in einem architekturspezifischen Unterverzeichnis.

Wenn Ihre App erstellt wird, indem Sie eine frühere Version der MFC-Bibliothek verwenden, müssen Sie die entsprechende CRT-DLL aus dem Verzeichnis für verteilbare Dateien verteilen. Wenn Ihre MFC-Anwendung beispielsweise mithilfe des Visual Studio 2013-Toolsets (vc120) erstellt wurde, müssen Sie die Datei „msvcr120.dll“ verteilen. Sie müssen ebenfalls die entsprechende Datei „mfc`<version>`u.dll“ oder „mfc`<version>`.dll“ verteilen.

Wenn Sie die Anwendung statisch mit MFC verknüpfen, (das heißt, wenn Sie im Dialogfeld **Eigenschaften** auf der Registerkarte **Allgemein** die Option **MFC in einer statischen Bibliothek verwenden** angeben), müssen Sie keine MFC-DLL verteilen. Obwohl die statische Verknüpfung möglicherweise bei Tests und internen Bereitstellungen von Anwendungen funktioniert, sollte dieses Verfahren nicht zur Neuverteilung von MFC verwendet werden. Weitere Informationen zu den empfohlenen Vorgehensweisen zum Bereitstellen von Visual C++-Bibliotheken finden Sie unter [Choosing a Deployment Method (Auswählen einer Bereitstellungsmethode)](choosing-a-deployment-method.md).

Wenn die Anwendung die MFC-Klassen verwendet, die das WebBrowser-Steuerelement implementieren (z.B. [CHtmlView Class](../mfc/reference/chtmlview-class.md) oder [CHtmlEditView Class](../mfc/reference/chtmleditview-class.md)), sollte auch die aktuellste Version von Microsoft Internet Explorer installiert werden, damit auf dem Zielcomputer die aktuellen allgemeinen Steuerungsdateien vorhanden sind. (Mindestens ist Internet Explorer 4.0 erforderlich.) Informationen zum Installieren von Internet Explorer-Komponenten finden Sie unter "Artikel 185375: Erstellen einer einzelnen EXE-Installation von Internet Explorer" auf der Microsoft Support-Website.

Wenn in der Anwendung die MFC-Datenbankklassen (z.B. [CRecordset Class](../mfc/reference/crecordset-class.md) und [CRecordView Class](../mfc/reference/crecordview-class.md)) verwendet werden, müssen Sie ODBC und alle in der Anwendung verwendeten ODBC-Treiber verteilen.

Wenn die MFC-Anwendung Windows Forms-Steuerelemente verwendet, müssen Sie mfcmifc80.dll mit der Anwendung verteilen. Diese DLL ist eine mit einem starken Namen signierte .NET-Assembly, die mit einer Anwendung in deren lokalem Ordner oder durch Bereitstellung im globalen Assemblycache (GAC) mit [Gacutil.exe (Tool für globale Assemblycaches)](/dotnet/framework/tools/gacutil-exe-gac-tool) verteilt werden kann.

Wenn Sie eine MFC-DLL weiterverteilen, achten Sie darauf, nicht die Debugversion, sondern die Verkaufsversion weiterzuverteilen. Debugversionen der DLLs können nicht weiterverteilt werden. Die Namen von Debugversionen der MFC-DLLs enden auf „d“, z.B. „Mfc140d.dll“.

Sie können MFC entweder mit VCRedist_*architecture*.exe, Mergemodulen, die zusammen mit Visual Studio installiert werden, oder durch Bereitstellung der MFC-DLL im gleichen Ordner wie die Anwendung verteilen. Weitere Informationen zum Verteilen von MFC finden Sie unter [Redistributing Visual C++ Files (Verteilen von Visual C++-Dateien)](redistributing-visual-cpp-files.md).

## <a name="installation-of-localized-mfc-components"></a>Installation lokalisierter MFC-Komponenten

Wenn Sie die Anwendung durch Installieren einer MFC-Lokalisierungs-DLL lokalisieren möchten, müssen Sie die verteilbaren Mergedateien (MSM-Datei) verwenden. Wenn Sie zum Beispiel die Anwendung auf einem x86-Computer lokalisieren möchten, müssen Sie „Microsoft_VC`<version>`_MFCLOC_x86.msm“ im Installationspaket für einen x86-Computer zusammenführen.

Die weiterverteilbaren MSM-Dateien enthalten die DLLs, die für die Lokalisierung verwendet werden. Es gibt eine DLL für jede unterstützte Sprache. Beim Installationsvorgang werden diese DLLs im Ordner "%WINDIR%\system32\" auf dem Zielcomputer installiert.

Weitere Informationen zum Lokalisieren von MFC-Anwendungen finden Sie unter [TN057: Lokalisierung von MFC-Komponenten](../mfc/tn057-localization-of-mfc-components.md).

Sie können MFC-Lokalisierungs-DLLs verteilen, indem Sie die MFC-DLL im lokalen Anwendungsordner bereitstellen. Weitere Informationen zum Verteilen von Visual C++-Bibliotheken finden Sie unter [Redistributing Visual C++ Files (Verteilen von Visual C++-Dateien)](redistributing-visual-cpp-files.md).

## <a name="see-also"></a>Siehe auch

[Verteilen von Visual C++-Dateien](redistributing-visual-cpp-files.md)
