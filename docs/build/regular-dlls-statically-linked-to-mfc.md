---
title: Reguläre, statisch mit MFC verknüpfte MFC-DLLs
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
ms.openlocfilehash: 1f05b5e3c268935cf3161fb7184e04b3e3ea1446
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314779"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>Reguläre, statisch mit MFC verknüpfte MFC-DLLs

Eine reguläre, statisch mit MFC verknüpfte DLL verwendet MFC intern, und die exportierten Funktionen in der DLL können entweder von ausführbaren MFC- oder Nicht-MFC-Dateien aufgerufen werden. Wie der Name schon sagt, wird diese Art von DLL mithilfe der statischen Verknüpfungsbibliotheksversion von MFC erstellt. Funktionen werden in der Regel mithilfe der Standard-C-Schnittstelle aus einer regulären MFC-DLL exportiert. Ein Beispiel zum Schreiben, Erstellen und Verwenden einer regulären MFC-DLL finden Sie unter [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap).

Beachten Sie, dass der Begriff USRDLL in der Visual C++-Dokumentation nicht mehr verwendet wird. Eine reguläre, statisch mit MFC verknüpfte DLL weist dieselben Merkmale wie die frühere USRDLL auf.

Eine reguläre, statisch mit MFC verknüpfte DLL verfügt über folgende Funktionen:

- Die ausführbare Clientdatei kann in jeder Programmiersprache geschrieben sein, die die Verwendung von DLLs unterstützt (C, C++, Pascal, Visual Basic usw.). Es muss sich nicht um eine MFC-Anwendung handeln.

- Die DLL kann mit den gleichen statisch mit MFC verknüpften Bibliotheken verknüpft werden, die von Anwendungen verwendet werden. Es gibt keine separate Version der statischen Verknüpfungsbibliotheken für DLLs mehr.

- Vor Version 4.0 von MFC stellten USRDLLs den gleichen Typ von Funktionen bereit wie reguläre, statisch mit MFC verknüpfte MFC-DLLs. Ab Version 4.0 von Visual C++ gilt der Begriff USRDLL als veraltet.

Für eine reguläre, statisch mit MFC verknüpfte DLL gelten folgende Anforderungen:

- Dieser DLL-Typ muss eine von `CWinApp` abgeleitete Klasse instanziieren.

- Dieser DLL-Typ verwendet die von MFC bereitgestellte Funktion `DllMain`. Legen Sie den gesamten DLL-spezifischen Initialisierungscode wie in einer normalen MFC-Anwendung in der Memberfunktion `InitInstance` und den Terminierungscode in `ExitInstance` ab.

- Obwohl der Begriff USRDLL veraltet ist, müssen Sie **_USRDLL** in der Befehlszeile des Compilers definieren. Diese Definition bestimmt, welche Deklarationen von den MFC-Headerdateien abgerufen werden.

Reguläre MFC-DLLs müssen wie eine MFC-Anwendung über eine von `CWinApp` abgeleitete Klasse und ein einzelnes Objekt dieser Anwendungsklasse verfügen. Das `CWinApp`-Objekt der DLL muss jedoch nicht wie das `CWinApp`-Objekt einer Anwendung über ein Hauptnachrichtensystem verfügen.

Beachten Sie, dass der `CWinApp::Run`-Mechanismus nicht für eine DLL gilt, da die Anwendung das Hauptnachrichtensystem besitzt. Wenn die DLL Dialogfelder ohne Modus öffnet oder über ein eigenes Hauptrahmenfenster verfügt, muss das Hauptnachrichtensystem der Anwendung eine von der DLL exportierte Routine aufrufen, die wiederum die `CWinApp::PreTranslateMessage`-Memberfunktion des Anwendungsobjekts der DLL aufruft.

Ein Beispiel dieser Funktion finden Sie im Beispiel „DLLScreenCap“.

Symbole werden in der Regel mithilfe der Standard-C-Schnittstelle aus einer regulären MFC-DLL exportiert. Die Deklaration einer aus einer regulären MFC-DLL exportierten Funktion würde in etwa wie folgt aussehen:

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Alle Speicherbelegungen innerhalb einer regulären MFC-DLL sollten innerhalb der DLL bleiben. Die DLL sollte Folgendes nicht an die aufrufende ausführbare Datei übergeben oder von dieser empfangen:

- Zeiger auf MFC-Objekte

- Zeiger auf durch MFC belegten Speicher

Wenn Sie eine der oben genannten Aktionen durchführen oder von MFC abgeleitete Objekte zwischen der aufrufenden ausführbaren Datei und der DLL übergeben müssen, müssen Sie eine MFC-Erweiterungs-DLL erstellen.

Es ist nur sicher, Zeiger auf Speicher zu übergeben, die von den C-Laufzeitbibliotheken zwischen einer Anwendung und einer DLL zugeordnet wurden, wenn Sie eine Kopie der Daten erstellen. Sie dürfen diese Zeiger nicht löschen, deren Größe nicht ändern und sie nicht verwenden, ohne eine Kopie des Speichers zu erstellen.

Eine DLL, die statisch mit MFC verknüpft ist, kann nicht auch dynamisch mit den gemeinsam genutzten MFC-DLLs verknüpft sein. Eine DLL, die statisch mit MFC verknüpft ist, ist wie jede andere DLL dynamisch an eine Anwendung gebunden. Anwendungen verknüpfen sich mit dieser DLL wie mit jeder anderen DLL.

Die MFC-Standardbibliotheken für statische Verknüpfungen werden entsprechend der unter [Namenskonventionen für MFC-DLLs](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions) beschriebenen Konvention benannt. Bei Version 3.0 und späteren Versionen von MFC müssen Sie dem Linker jedoch nicht mehr selbst die Version der MFC-Bibliothek angeben, in der Sie eine Verknüpfung wünschen. Stattdessen bestimmen die MFC-Headerdateien basierend auf Präprozessordefinitionen wie **\_DEBUG** oder **_UNICODE** automatisch die richtige Version der MFC-Bibliothek, in der verknüpft werden soll. Die MFC-Headerdateien fügen „/DEFAULTLIB“-Anweisungen hinzu, die den Linker anweisen, in einer bestimmten Version der MFC-Bibliothek zu verknüpfen.

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Initialisieren regulärer MFC-DLLs](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Verwenden von MFC als Teil einer DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [Using Database, OLE, and Sockets MFC extension DLLs in regular MFC DLLs (Verwenden von Datenbank-, OLE- und Sockets-MFC-Erweiterungs-DLLs in regulären MFC-DLLs)](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Erstellen einer MFC-DLL](../mfc/reference/mfc-dll-wizard.md)

- [Regular MFC DLLs Dynamically Linked to MFC (Reguläre, dynamisch mit MFC verknüpfte MFC-DLLs)](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC extension DLLs (MFC-Erweiterungs-DLLs)](extension-dlls-overview.md)

## <a name="see-also"></a>Siehe auch

[Arten von DLLs](kinds-of-dlls.md)
