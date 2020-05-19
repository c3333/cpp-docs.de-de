---
title: Erweiterungs-DLLs
ms.date: 05/06/2019
helpviewer_keywords:
- memory [C++], DLLs
- MFC extension DLLs [C++]
- AFXDLL library
- shared resources [C++]
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- resource sharing [C++]
- extension DLLs [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: f69ac3d4-e474-4b1c-87a1-6738843a135c
ms.openlocfilehash: 55b1e55a9c7bdf6daaff98a7fe3f1a2a55f68334
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220763"
---
# <a name="mfc-extension-dlls"></a>MFC-Erweiterungs-DLLs

Eine MFC-Erweiterungs-DLL ist eine DLL, die typischerweise wiederverwendbare Klassen implementiert, welche von bestehenden Microsoft Foundation Class Library-Klassen abgeleitet wurden.

Eine MFC-Erweiterungs-DLL hat die folgenden Features und Anforderungen:

- Die clientseitige ausführbare Datei muss eine MFC-Anwendung sein, die mit definiertem `_AFXDLL` kompiliert wurde.

- Eine MFC-Erweiterungs-DLL kann auch von einer regulären, dynamisch mit MFC verknüpften MFC-DLL verwendet werden.

- MFC-Erweiterungs-DLLs sollten mit definiertem `_AFXEXT` kompiliert werden. Dadurch wird ebenfalls die Definition von `_AFXDLL` erzwungen und sichergestellt, dass die korrekten Deklarationen aus den MFC-Headerdateien übernommen werden. Zusätzlich wird gewährleistet, dass `AFX_EXT_CLASS` beim Erstellen der DLL als `__declspec(dllexport)` definiert wird. Das ist erforderlich, wenn Sie dieses Makro zum Deklarieren der Klassen in der MFC-Erweiterungs-DLL verwenden.

- MFC-Erweiterungs-DLLs sollten keine von `CWinApp` abgeleitete Klasse instanziieren, sondern es vielmehr der Clientanwendung (bzw. DLL) überlassen, dieses Objekt bereitzustellen.

- MFC-Erweiterungs-DLLs sollten jedoch eine `DllMain`-Funktion bereitstellen und notwendige Initialisierungen dort vornehmen.

Erweiterungs-DLLs werden über die Dynamic Link Library-Version von MFC (auch als gemeinsam genutzte MFC-Version bekannt) erstellt. Eine MFC-Erweiterungs-DLL kann ausschließlich von ausführbaren MFC-Dateien (entweder Anwendungen oder regulären MFC-DLLs) verwendet werden, die mit der gemeinsam genutzten MFC-Version erstellt wurden. Sowohl die Clientanwendung als auch die MFC-Erweiterungs-DLL müssen dieselbe Version von MFCx0.dll verwenden. Mit einer MFC-Erweiterungs-DLL können Sie neue benutzerdefinierte Klassen von MFC ableiten und diese erweiterte MFC-Version anschließend Anwendungen zur Verfügung stellen, die die DLL aufrufen.

Erweiterungs-DLLs können auch dazu verwendet werden, von MFC abgeleitete Objekte zwischen Anwendung und DLL zu übergeben. Die dem übergebenen Objekt zugeordneten Memberfunktionen befinden sich in dem Modul, in dem das Objekt erstellt wurde. Da diese Funktionen bei Verwendung der gemeinsam genutzten DLL-Version von MFC ordnungsgemäß exportiert werden, können problemlos Zeiger auf MFC-Objekte oder auf von MFC abgeleitete Objekte zwischen einer Anwendung und den von ihr geladenen MFC-Erweiterungs-DLLs übergeben werden.

Eine MFC-Erweiterungs-DLL verwendet die gemeinsam genutzte MFC-Version auf dieselbe Weise, wie eine Anwendung die gemeinsam genutzte MFC-DLL-Version verwendet. Dabei sind jedoch folgende Punkte zu bedenken:

- Sie verfügt über kein von `CWinApp` abgeleitetes Objekt. Sie muss mit dem von `CWinApp` abgeleiteten Objekt der Clientanwendung arbeiten. Das bedeutet, dass sich die Haupt-Meldungsverteilschleife, die Leerlaufschleife usw. im Besitz der Clientanwendung befinden.

- Sie ruft `AfxInitExtensionModule` in ihrer `DllMain`-Funktion auf. Der Rückgabewert dieser Funktion sollte überprüft werden. Wird ein NULL-Wert von `AfxInitExtensionModule` zurückgegeben, muss aus der `DllMain`-Funktion auch 0 zurückgegeben werden.

- Während der Initialisierung wird ein **CDynLinkLibrary**-Objekt erstellt, falls `CRuntimeClass`-Objekte oder -Ressourcen von der MFC-Erweiterungs-DLL in die Anwendung exportiert werden sollen.

Vor MFC, Version 4.0, wurde dieser DLL-Typ AFXDLL genannt. AFXDLL bezieht sich auf das Präprozessorsymbol `_AFXDLL`, das beim Erstellen der DLL definiert wird.

Die Importbibliotheken für die gemeinsam genutzte MFC-Version werden entsprechend der unter [Namenskonventionen für MFC-DLLs](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions) beschriebenen Konvention benannt. Visual Studio bietet vordefinierte Versionen der MFC-DLLs sowie eine Reihe von MFC-fremden DLLs, die Sie mit Ihren Anwendungen verwenden und weitergeben können. Diese sind in der Datei Redist.txt dokumentiert, die im Ordner Programme\Microsoft Visual Studio installiert ist.

Wenn Sie den Export über eine DEF-Datei vornehmen, fügen Sie den folgenden Code am Anfang und am Ende der Headerdatei ein:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Durch diese vier Zeilen wird sichergestellt, dass der Code ordnungsgemäß für eine MFC-Erweiterungs-DLL kompiliert wird. Ohne diese vier Zeilen wird die DLL möglicherweise falsch kompiliert oder verknüpft.

Wenn Sie einen Zeiger auf ein MFC-Objekt oder auf ein von MFC abgeleitetes Objekt an eine MFC-DLL übergeben oder aus ihr übernehmen möchten, sollte es sich bei der DLL um eine MFC-Erweiterungs-DLL handeln. Die dem übergebenen Objekt zugeordneten Memberfunktionen befinden sich in dem Modul, in dem das Objekt erstellt wurde. Da diese Funktionen bei Verwendung der gemeinsam genutzten DLL-Version von MFC ordnungsgemäß exportiert werden, können problemlos Zeiger auf MFC-Objekte oder auf von MFC abgeleitete Objekte zwischen einer Anwendung und den von ihr geladenen MFC-Erweiterungs-DLLs übergeben werden.

Aufgrund von C++-spezifischen Problemen bei der Namenscodierung und dem Export kann die Exportliste einer MFC-Erweiterungs-DLL im Debug- und im Releasebuild derselben DLL bzw. in DLLs für unterschiedliche Plattformen Unterschiede aufweisen. Das Releasebuild von MFCx0.dll hat ca. 2.000 exportierte Einstiegspunkte, das Debugbuild von MFCx0D.dll ca. 3.000 exportierte Einstiegspunkte.

## <a name="memory-management"></a>Speicherverwaltung

MFCx0.dll und alle MFC-Erweiterungs-DLLs, die in den Adressbereich einer Clientanwendung geladen werden, verwenden dieselbe Speicherbelegungsfunktion, dasselbe Ladeverfahren für Ressourcen und weitere globale MFC-Zustände, so als ob sie in derselben Anwendung enthalten wären. Dies ist von Bedeutung, da MFC-fremde DLL-Bibliotheken und reguläre MFC-DLLs genau entgegengesetzt verfahren: Jede DLL belegt Speicher aus ihrem eigenen Bestand.

Wenn eine MFC-Erweiterungs-DLL Speicher belegt, kann dieser Speicherbereich beliebig mit jedem anderen Objekt, für das die Anwendung Speicher belegt hat, kombiniert werden. Auch wenn eine dynamisch mit MFC verknüpfte Anwendung nach einer Fehlfunktion beendet wird, bleibt die Integrität anderer MFC-Anwendungen, die die DLL ebenfalls nutzen, durch die in das Betriebssystem implementierte Schutzfunktion erhalten.

Entsprechend werden andere globale MFC-Zustände, wie die aktuelle ausführbare Datei, aus der Ressourcen geladen werden, auch von der Clientanwendung und allen MFC-Erweiterungs-DLLs sowie von MFCx0.dll selbst gemeinsam genutzt.

## <a name="sharing-resources-and-classes"></a>Gemeinsame Nutzung von Ressourcen und Klassen

Der Export von Ressourcen erfolgt über eine Ressourcenliste. Jede Anwendung enthält eine einfach verknüpfte Liste mit **CDynLinkLibrary**-Objekten. Bei den meisten MFC-Standardimplementierungen, durch die Ressourcen geladen werden, erfolgt die Suche nach einer Ressource zunächst im aktuellen Ressourcenmodul (`AfxGetResourceHandle`). Falls diese Suche erfolglos bleibt, wird der Versuch, die angeforderte Ressource zu laden, auf die Liste der **CDynLinkLibrary**-Objekte ausgeweitet.

Das Durchlaufen der Liste hat jedoch den Nachteil, dass die Suche etwas langsamer ist und dass die Ressourcen-ID-Bereiche verwaltet werden müssen. Der Vorteil liegt darin, dass eine Clientanwendung, die mit mehreren MFC-Erweiterungs-DLLs verknüpft ist, jede durch die DLL zur Verfügung gestellte Ressource nutzen kann, ohne dass das DLL-Instanzenhandle angegeben werden muss. `AfxFindResourceHandle` ist eine API, die bei der Suche nach einer bestimmten Übereinstimmung die Ressourcenliste durchläuft. Sie verwendet den Ressourcennamen und -typ als Parameter und gibt das zuerst ermittelte Ressourcenhandle (oder NULL) zurück.

Wenn Sie die Liste nicht durchsuchen und nur Ressourcen von einer bestimmten Stelle laden möchten, verwenden Sie die Funktionen `AfxGetResourceHandle` und `AfxSetResourceHandle`, um das alte Handle zu speichern und das neue Handle festzulegen. Achten Sie darauf, dass Sie das alte Ressourcenhandle wiederherstellen, bevor Sie zur Clientanwendung zurückkehren. Ein Beispiel für diese Methode zum expliziten Laden eines Menüs finden Sie in der Datei Testdll2.cpp im MFC-Beispiel [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk).

Die dynamische Erstellung von MFC-Objekten, die einen MFC-Namen erhalten, verläuft ähnlich. Der Mechanismus zur Deserialisierung von MFC-Objekten erfordert die Registrierung aller `CRuntimeClass`-Objekte. Auf diese Weise können C++-Objekte des erforderlichen Typs anhand der zuvor gespeicherten Informationen mittels dynamischer Erstellung rekonstruiert werden.

Im Fall des MFC-Beispiels [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk) sieht die Liste etwa folgendermaßen aus:

```
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE
               |                      |
          TESTDLL2.DLL           TESTDLL2.DLL
               |                      |
          TESTDLL1.DLL           TESTDLL1.DLL
               |                      |
           MFCOxxD.DLL                |
               |                      |
           MFCDxxD.DLL                |
               |                      |
            MFCxxD.DLL            MFCxx.DLL
```

wobei *xx* die Versionsnummer ist; so steht 42 für die Version 4.2.

Die MFCxx.dll befindet sich in der Ressourcen- und Klassenliste gewöhnlich an letzter Stelle. Die Datei enthält alle MFC-Standardressourcen, einschließlich der Eingabeaufforderungen aller Standardbefehls-IDs. Durch ihre Position am Ende der Liste können DLLs und die Clientanwendung selbst auf die gemeinsam genutzten Ressourcen in MFCxx.dll zugreifen, ohne dass eine eigene Kopie der MFC-Standardressourcen erforderlich wäre.

Wenn Sie die Ressourcen und Klassennamen aller DLLs im Namespace der Clientanwendung zusammenführen, hat dies den Nachteil, dass Sie bei der Auswahl von IDs und Namen äußerst sorgfältig vorgehen müssen.

Im [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)-Beispiel wird der Namespace für gemeinsam genutzte Ressourcen mithilfe mehrerer Headerdateien verwaltet.

Wenn die MFC-Erweiterungs-DLL spezielle Daten für jede Anwendung verwalten muss, können Sie eine neue Klasse von **CDynLinkLibrary** ableiten und in `DllMain` erstellen. Die DLL kann dann bei ihrer Ausführung die Liste der **CDynLinkLibrary**-Objekte der aktuellen Anwendung überprüfen, um das Objekt für die jeweilige MFC-Erweiterungs-DLL zu suchen.

### <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Initialisieren von MFC-Erweiterungs-DLLs](run-time-library-behavior.md#initializing-extension-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Tipps zur Verwendung von gemeinsam genutzten Ressourcendateien](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

- [DLL-Version der MFC](../mfc/tn033-dll-version-of-mfc.md)

- [Reguläre, statisch mit MFC verknüpfte MFC-DLLs](regular-dlls-statically-linked-to-mfc.md)

- [Reguläre, dynamisch mit MFC verknüpfte MFC-DLLs](regular-dlls-dynamically-linked-to-mfc.md)

- [Using Database, OLE, and Sockets MFC extension DLLs in regular MFC DLLs (Verwenden von Datenbank-, OLE- und Sockets-MFC-Erweiterungs-DLLs in regulären MFC-DLLs)](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)
