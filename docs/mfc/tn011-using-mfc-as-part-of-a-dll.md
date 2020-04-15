---
title: 'TN011: Verwenden von MFC als Teil einer DLL'
ms.date: 11/04/2016
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
ms.openlocfilehash: 0f4d4e2ed76a0fa5f8f775345fc672a1df055a39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370437"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011: Verwenden von MFC als Teil einer DLL

In diesem Hinweis werden reguläre MFC-DLLs beschrieben, mit denen Sie die MFC-Bibliothek als Teil einer Windows Dynamic-Link-Bibliothek (DLL) verwenden können. Es wird davon ausgegangen, dass Sie mit Windows-DLLs und deren Erstellung vertraut sind. Informationen zu MFC-Erweiterungs-DLLs, mit denen Sie Erweiterungen für die MFC-Bibliothek erstellen können, finden Sie unter [DLL-Version von MFC](../mfc/tn033-dll-version-of-mfc.md).

## <a name="dll-interfaces"></a>DLL-Schnittstellen

Reguläre MFC-DLLs gehen davon aus, dass Schnittstellen zwischen der Anwendung und der DLL in C-ähnlichen Funktionen oder explizit exportierten Klassen angegeben werden. MFC-Klassenschnittstellen können nicht exportiert werden.

Wenn sowohl eine DLL als auch eine Anwendung MFC verwenden möchten, haben beide die Wahl, entweder die freigegebene Version der MFC-Bibliotheken zu verwenden oder eine statische Verknüpfung mit einer Kopie der Bibliotheken herzustellen. Die Anwendung und dLL können beide eine der Standardversionen der MFC-Bibliothek verwenden.

regelmäßige MFC-DLLs haben mehrere Vorteile:

- Die Anwendung, die die DLL verwendet, muss keine MFC verwenden und muss keine Visual C++-Anwendung sein.

- Bei regulären MFC-DLLs, die statisch mit MFC verknüpft sind, hängt die Größe der DLL nur von den verwendeten und verknüpften MFC- und C-Laufzeitroutinen ab.

- Bei regulären MFC-DLLs, die dynamisch mit MFC verknüpft werden, können die Einsparungen beim Arbeitsspeicher durch die Verwendung der freigegebenen Version von MFC erheblich sein. Sie müssen jedoch die freigegebenen DLLs, die Mfc-Version\<*version* \<>.dll und die Msvvcrt-Version>.dll mit Ihrer DLL verteilen.*version*

- Der DLL-Entwurf ist unabhängig davon, wie Klassen implementiert werden. Ihr DLL-Design exportiert nur in die gewünschten APIs. Wenn sich die Implementierung ändert, sind daher weiterhin reguläre MFC-DLLs gültig.

- Bei regulären MFC-DLLs, die statisch mit MFC verknüpft sind, gibt es bei der Verwendung von DLL und Anwendung mit MFC keine Probleme mit der Anwendung, die eine andere Version von MFC als die DLL wünscht oder umgekehrt. Da die MFC-Bibliothek statisch mit jeder DLL oder EXE verknüpft ist, steht außer Frage, welche Version Sie haben.

## <a name="api-limitations"></a>API-Einschränkungen

Einige MFC-Funktionen gelten nicht für die DLL-Version, entweder aufgrund technischer Einschränkungen oder weil diese Dienste normalerweise von der Anwendung bereitgestellt werden. Bei der aktuellen Version von MFC ist `CWinApp::SetDialogBkColor`die einzige Funktion, die nicht anwendbar ist, .

## <a name="building-your-dll"></a>Erstellen Ihrer DLL

Beim Kompilieren regulärer MFC-DLLs, die statisch `_USRDLL` `_WINDLL` mit MFC verknüpft sind, müssen die Symbole definiert werden. Ihr DLL-Code muss auch mit den folgenden Compiler-Switches kompiliert werden:

- **/D_WINDLL** bedeutet, dass die Kompilierung für eine DLL ist

- **/D_USRDLL** gibt an, dass Sie eine reguläre MFC-DLL erstellen

Sie müssen diese Symbole auch definieren und diese Compiler-Switches verwenden, wenn Sie regelmäßige MFC-DLLs kompilieren, die dynamisch mit MFC verknüpft sind. Darüber hinaus `_AFXDLL` muss das Symbol definiert und Ihr DLL-Code mit folgenden Themen kompiliert werden:

- **/D_AFXDLL** gibt an, dass Sie eine reguläre MFC-DLL erstellen, die dynamisch mit MFC verknüpft ist

Die Schnittstellen (APIs) zwischen der Anwendung und der DLL müssen explizit exportiert werden. Es wird empfohlen, dass Sie Ihre Schnittstellen als eine geringe Bandbreite definieren und wenn möglich nur C-Schnittstellen verwenden. Direkte C-Schnittstellen sind einfacher zu verwalten als komplexere C++-Klassen.

Platzieren Sie Ihre APIs in einem separaten Header, der sowohl von C- als auch von C++-Dateien eingeschlossen werden kann. Ein Beispiel finden Sie unter screenCap.h im MFC Advanced Concepts-Beispiel [DLLScreenCap.](../overview/visual-cpp-samples.md) Um Ihre Funktionen zu exportieren, geben Sie sie in den `EXPORTS` Abschnitt Ihrer Moduldefinitionsdatei ein (. DEF) oder `__declspec(dllexport)` in Ihre Funktionsdefinitionen aufnehmen. Verwenden `__declspec(dllimport)` Sie diese Funktionen, um diese Funktionen in die ausführbare Clientdatei zu importieren.

Sie müssen das AFX_MANAGE_STATE-Makro am Anfang aller exportierten Funktionen in regulären MFC-DLLs hinzufügen, die dynamisch mit MFC verknüpft werden. Dieses Makro legt den aktuellen Modulstatus auf den für die DLL fest. Um dieses Makro zu verwenden, fügen Sie die folgende Codezeile am Anfang von Funktionen hinzu, die aus der DLL exportiert werden:

`AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`

## <a name="winmain---dllmain"></a>WinMain -> DllMain

Die MFC-Bibliothek definiert den `DllMain` standardmäßigen Win32-Einstiegspunkt, der Ihr von [CWinApp](../mfc/reference/cwinapp-class.md) abgeleitetes Objekt wie in einer typischen MFC-Anwendung initialisiert. Platzieren Sie die gesamte DLL-spezifische Initialisierung in der [InitInstance-Methode](../mfc/reference/cwinapp-class.md#initinstance) wie in einer typischen MFC-Anwendung.

Beachten Sie, dass der [CWinApp::Run-Mechanismus](../mfc/reference/cwinapp-class.md#run) nicht für eine DLL gilt, da die Anwendung eigentümer die Hauptnachrichtenpumpe ist. Wenn Ihre DLL moduslose Dialoge anzeigt oder über ein eigenes Hauptbildfenster verfügt, muss die Hauptnachrichtenpumpe Ihrer Anwendung eine DLL-exportierte Routine aufrufen, die [CWinApp::PreTranslateMessage](../mfc/reference/cwinapp-class.md#pretranslatemessage)aufruft.

Die Verwendung dieser Funktion finden Sie im DLLScreenCap-Beispiel.

Die `DllMain` von MFC bereitstelltde Funktion ruft die [CWinApp::ExitInstance-Methode](../mfc/reference/cwinapp-class.md#exitinstance) Ihrer Klasse auf, von `CWinApp` der vor dem Entladen der DLL abgeleitet wird.

## <a name="linking-your-dll"></a>Verknüpfen Ihrer DLL

Bei regulären MFC-DLLs, die statisch mit MFC verknüpft sind, müssen Sie Ihre DLL mit Nafxcwd.lib oder Nafxcw.lib und mit der Version der C-Laufzeiten mit dem Namen Libcmt.lib verknüpfen. Diese Bibliotheken sind vorgefertigt und können installiert werden, indem Sie sie angeben, wenn Sie Visual C++-Setup ausführen.

## <a name="sample-code"></a>Beispielcode

Ein vollständiges Beispiel finden Sie im MFC Advanced Concepts-Beispielprogramm DLLScreenCap. In diesem Beispiel sind einige interessante Dinge zu beachten:

- Die Compilerflags der DLL und die der Anwendung unterscheiden sich.

- Die Verknüpfungslinien und . DEF-Dateien für die DLL und die für die Anwendung sind unterschiedlich.

- Die Anwendung, die die DLL verwendet, muss sich nicht in C++ aufstellen.

- Die Schnittstelle zwischen der Anwendung und der DLL ist eine API, die von C oder C++ verwendet werden kann und mit DLLScreenCap.def exportiert wird.

Das folgende Beispiel veranschaulicht eine API, die in einer regulären MFC-DLL definiert ist, die statisch mit MFC verknüpft ist. In diesem Beispiel wird die Deklaration in einen `extern "C" { }` Block für C++-Benutzer eingeschlossen. Dies hat mehrere Vorteile. Erstens werden Ihre DLL-APIs für Nicht-C++-Clientanwendungen nutzbar. Zweitens reduziert es den DLL-Overhead, da C++-Namensmangling nicht auf den exportierten Namen angewendet wird. Schließlich erleichtert es das explizite Hinzufügen zu einem . DEF-Datei (für den Export durch Ordinal) ohne sich um namensmangling kümmern zu müssen.

```cpp
#ifdef __cplusplus
extern "C" {
#endif  /* __cplusplus */

struct TracerData
{
    BOOL bEnabled;
    UINT flags;
};

BOOL PromptTraceFlags(TracerData FAR* lpData);

#ifdef __cplusplus
}
#endif
```

Die von der API verwendeten Strukturen werden nicht von MFC-Klassen abgeleitet und im API-Header definiert. Dies reduziert die Komplexität der Schnittstelle zwischen der DLL und der Anwendung und macht die DLL für C-Programme nutzbar.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
