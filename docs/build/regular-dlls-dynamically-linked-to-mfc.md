---
title: Reguläre, dynamisch mit MFC verknüpfte MFC-DLLs
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
ms.openlocfilehash: 3bfed5f75dab4c501708950fdb99f53c40ec142c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315000"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>Reguläre, dynamisch mit MFC verknüpfte MFC-DLLs

Eine reguläre, dynamisch mit MFC verknüpfte DLL verwendet MFC intern, und die exportierten Funktionen in der DLL können entweder von den ausführbaren MFC- oder Nicht-MFC-Dateien aufgerufen werden. Wie der Name schon sagt, wird diese Art von DLL mithilfe der DLL-Version von MFC erstellt (auch als freigegebene Version von MFC bekannt). Funktionen werden in der Regel aus einer regulären MFC-DLL mithilfe der Standard-C-Schnittstelle exportiert.

Sie müssen das `AFX_MANAGE_STATE`-Makro zu Beginn aller exportierten Funktionen in regulären MFC-DLLs hinzufügen, die eine dynamische Verknüpfung zu MFC herstellen, um den Status des aktuellen Moduls auf den für die DLL festzulegen. Dies erfolgt, indem die folgende Codezeile am Beginn der Funktionen hinzugefügt wird, die aus der DLL exportiert werden:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

Eine reguläre, dynamisch mit MFC verknüpfte DLL verfügt über folgende Features:

- Hierbei handelt es sich um eine neue Art DLL, die von Visual C++ 4.0 eingeführt wurde.

- Die ausführbare Clientdatei kann in jeder Programmiersprache geschrieben sein, die die Verwendung von DLLs unterstützt (C, C++, Pascal, Visual Basic usw.). Es muss sich nicht um eine MFC-Anwendung handeln.

- Im Gegensatz zur statisch verknüpften, regulären MFC-DLL ist diese Art von DLL dynamisch mit der MFC-DLL verknüpft (auch als freigegebene MFC-DLL bekannt).

- Die MFC-Importbibliothek, die mit dieser Art DLL verknüpft ist, ist identisch mit der, die für MFC-Erweiterungs-DLLs oder Anwendungen verwendet wird, die die MFC-DLL verwenden: MFCxx(D).lib.

Für eine reguläre, dynamisch mit MFC verknüpfte DLL gelten folgende Anforderungen:

- **_AFXDLL** ist bei der Kompilierung dieser DLLs definiert, wie bei einer ausführbaren Datei, die dynamisch mit der MFC-DLL verknüpft ist. **_USRDLL** ist jedoch auch definiert, wie bei einer regulären MFC-DLL, die statisch mit MFC verknüpft ist.

- Diese Art von DLL muss eine von `CWinApp` abgeleitete Klasse instanziieren.

- Diese Art von DLL verwendet die von MFC bereitgestellte `DllMain`-Funktion. Platzieren Sie den gesamten DLL-spezifischen Initialisierungscode wie in einer normalen MFC-Anwendung in der Memberfunktion `InitInstance` und den Terminierungscode in `ExitInstance`.

Da bei dieser Art von DLL die DLL-Version von MFC verwendet wird, müssen Sie den aktuellen Modulstatus auf den für die DLL festlegen. Verwenden Sie dazu das [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state)-Makro zu Beginn jeder Funktion, die aus der DLL exportiert wird.

Reguläre MFC-DLLs müssen wie eine MFC-Anwendung über eine von `CWinApp` abgeleitete Klasse und ein einzelnes Objekt dieser Anwendungsklasse verfügen. Das `CWinApp`-Objekt der DLL muss jedoch nicht wie das `CWinApp`-Objekt einer Anwendung über ein Hauptnachrichtensystem verfügen.

Beachten Sie, dass der `CWinApp::Run`-Mechanismus nicht für eine DLL gilt, da die Anwendung das Hauptnachrichtensystem besitzt. Wenn in Ihrer DLL Dialogfelder ohne Modus angezeigt werden oder Ihre DLL ein eigenes Hauptrahmenfenster hat, muss das Hauptnachrichtensystem Ihrer Anwendung eine von der DLL exportierte Routine aufrufen, die `CWinApp::PreTranslateMessage` aufruft.

Platzieren Sie die gesamte DLL-spezifische Initialisierung in die `CWinApp::InitInstance`-Memberfunktion wie bei einer normalen MFC-Anwendung. Die `CWinApp::ExitInstance`-Memberfunktion Ihrer von `CWinApp` abgeleiteten Klasse wird von der von MFC bereitgestellten `DllMain`-Funktion aufgerufen, bevor die DLL entladen wird.

Sie müssen die freigegebenen DLLs „MFCx0.dll“ und „Msvcr*0.dll“ (oder ähnliche Dateien) mit Ihrer Anwendung verteilen.

Eine DLL, die dynamisch mit MFC verknüpft ist, kann keine statische Verknüpfung mit MFC herstellen. Anwendungen stellen Verknüpfungen zu regulären MFC-DLLs, die dynamisch mit MFC verknüpft sind, wie jede andere DLL her.

Symbole werden in der Regel mithilfe der Standard-C-Schnittstelle aus einer regulären MFC-DLL exportiert. Die Deklaration einer aus einer regulären MFC-DLL exportierten Funktion würde in etwa wie folgt aussehen:

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Alle Speicherbelegungen innerhalb einer regulären MFC-DLL sollten innerhalb der DLL bleiben. Die DLL sollte Folgendes nicht an die aufrufende ausführbare Datei übergeben oder von dieser empfangen:

- Zeiger auf MFC-Objekte

- Zeiger auf durch MFC belegten Speicher

Wenn Sie eine der oben genannten Aktionen durchführen oder von MFC abgeleitete Objekte zwischen der aufrufenden ausführbaren Datei und der DLL übergeben müssen, müssen Sie eine MFC-Erweiterungs-DLL erstellen.

Es ist nur sicher, Zeiger auf Speicher zu übergeben, die von den C-Laufzeitbibliotheken zwischen einer Anwendung und einer DLL zugeordnet wurden, wenn Sie eine Kopie der Daten erstellen. Sie dürfen diese Zeiger nicht löschen, deren Größe nicht ändern und sie nicht verwenden, ohne eine Kopie des Speichers zu erstellen.

Bei der Erstellung einer regulären MFC-DLL, die eine dynamische Verknüpfung zu MFC herstellt, müssen Sie das Makro [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) verwenden, um den Status des MFC-Moduls ordnungsgemäß zu ändern. Dies erfolgt, indem die folgende Codezeile am Beginn der Funktionen hinzugefügt wird, die aus der DLL exportiert werden:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

Das **AFX_MANAGE_STATE**-Makro sollte nicht in regulären MFC-DLLs, die eine statische Verknüpfung zu MFC herstellen, oder in MFC-Erweiterungs-DLLs verwendet werden. Weitere Informationen finden Sie unter [Verwalten der Zustandsdaten von MFC-Modulen](../mfc/managing-the-state-data-of-mfc-modules.md).

Ein Beispiel zum Schreiben, Erstellen und Verwenden einer regulären MFC-DLL finden Sie unter [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap). Weitere Informationen zu regulären MFC-DLLs, die eine dynamische Verknüpfung zu MFC herstellen, finden Sie im Abstrakt des Beispiels im Abschnitt, der mit „Converting DLLScreenCap to Dynamically Link with the MFC DLL“ (Konvertieren von DLLScreenCap in eine dynamische Verknüpfung mit der MFC-DLL) beginnt.

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Initialisieren regulärer MFC-DLLs](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Modulzustände einer regulären, dynamisch mit MFC verknüpften MFC-DLL](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [Verwalten der Zustandsdaten von MFC-Modulen](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Using Database, OLE, and Sockets MFC extension DLLs in regular MFC DLLs (Verwenden von Datenbank-, OLE- und Sockets-MFC-Erweiterungs-DLLs in regulären MFC-DLLs)](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [TN011: Verwenden von MFC als Teil einer DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>Siehe auch

[Arten von DLLs](kinds-of-dlls.md)
