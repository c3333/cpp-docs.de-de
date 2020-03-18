---
title: 'TN064: Apartmentmodellthreading in ActiveX-Steuerelementen'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
ms.openlocfilehash: f490e82e179da4614eea345136a9edfb1d320705
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442116"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064: Apartmentmodellthreading in ActiveX-Steuerelementen

> [!NOTE]
>  Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

Dieser Technische Hinweis erläutert, wie Apartment Modell Threading in einem ActiveX-Steuerelement aktiviert wird. Beachten Sie, dass das Apartment Modell-Threading nur in C++ den Visual-Versionen 4,2 oder höher unterstützt wird.

## <a name="what-is-apartment-model-threading"></a>Was ist Apartment-Modell Threading?

Das Apartment Modell ist ein Ansatz zur Unterstützung von eingebetteten Objekten, wie z. b. ActiveX-Steuerelementen, in einer Multithread-Containeranwendung. Obwohl die Anwendung mehrere Threads aufweisen kann, wird jede Instanz eines eingebetteten Objekts einem "Apartment" zugewiesen, das nur in einem einzigen Thread ausgeführt wird. Das heißt, dass alle Aufrufe einer Instanz eines-Steuer Elements im gleichen Thread ausgeführt werden.

Unterschiedliche Instanzen desselben Steuerelement Typs können jedoch unterschiedlichen-Apartments zugewiesen werden. Wenn also mehrere Instanzen eines Steuer Elements gemeinsame Daten gemeinsam nutzen (z. b. statische oder globale Daten), muss der Zugriff auf diese freigegebenen Daten durch ein Synchronisierungs Objekt (z. b. ein kritischer Abschnitt) geschützt werden.

Ausführliche Informationen zum Apartment Threading Modell finden Sie unter [Prozesse und Threads](/windows/win32/ProcThread/processes-and-threads) in der *OLE-Programmier Referenz*.

## <a name="why-support-apartment-model-threading"></a>Gründe für die Unterstützung von Apartment Modell Threading

Steuerelemente, die das Apartment Modell-Threading unterstützen, können in multithreadcontainer-Anwendungen verwendet werden, die auch das Apartment Modell unterstützen. Wenn Sie das Thread Modell nicht aktivieren, beschränken Sie den möglichen Satz von Containern, in denen das Steuerelement verwendet werden kann.

Das Aktivieren von Apartment Modell Threading ist für die meisten Steuerelemente einfach, insbesondere dann, wenn Sie nur wenige oder gar keine freigegebenen Daten aufweisen.

## <a name="protecting-shared-data"></a>Schützen von freigegebenen Daten

Wenn das Steuerelement freigegebene Daten verwendet, z. b. eine statische Element Variable, sollte der Zugriff auf diese Daten durch einen kritischen Abschnitt geschützt werden, um zu verhindern, dass mehrere Threads gleichzeitig die Daten ändern. Zum Einrichten eines kritischen Abschnitts zu diesem Zweck deklarieren Sie eine statische Element Variable der Klasse `CCriticalSection` in der Klasse des Steuer Elements. Verwenden Sie die Funktionen `Lock` und `Unlock` Member dieses kritischen Abschnitts Objekts, wenn Ihr Code auf die freigegebenen Daten zugreift.

Stellen Sie sich z. b. eine Steuerelement Klasse vor, die eine Zeichenfolge beibehalten muss, die von allen Instanzen gemeinsam verwendet wird. Diese Zeichenfolge kann in einer statischen Element Variablen verwaltet und durch einen kritischen Abschnitt geschützt werden. Die Klassen Deklaration des-Steuer Elements enthält Folgendes:

```
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

Die Implementierung für die-Klasse enthält Definitionen für diese Variablen:

```
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

Der Zugriff auf den `_strShared` statischen Member kann dann durch den kritischen Abschnitt geschützt werden:

```
void CSampleCtrl::SomeMethod()
{
    _critSect.Lock();
if (_strShared.Empty())
    _strShared = "<text>";
    _critSect.Unlock();

...
}
```

## <a name="registering-an-apartment-model-aware-control"></a>Registrieren eines Steuer Elements für das Apartment-Modell

Steuerelemente, die das Apartment-Modell-Threading unterstützen, sollten diese Funktion in der Registrierung angeben, indem Sie den benannten Wert "ThreadingModel" mit dem Wert "Apartment" in Ihrem Klassen-ID-Registrierungs Eintrag unter der *Klassen-ID*\\**InProcServer32** Key hinzufügen. Damit dieser Schlüssel automatisch für das Steuerelement registriert wird, übergeben Sie das *afxRegApartmentThreading* -Flag im sechsten Parameter an `AfxOleRegisterControlClass`:

```
BOOL CSampleCtrl::CSampleCtrlFactory::UpdateRegistry(BOOL bRegister)
{
    if (bRegister)
    return AfxOleRegisterControlClass(
    AfxGetInstanceHandle(),
    m_clsid,
    m_lpszProgID,
    IDS_SAMPLE,
    IDB_SAMPLE,
    afxRegApartmentThreading,
    _dwSampleOleMisc,
    _tlid,
    _wVerMajor,
    _wVerMinor);

else
    return AfxOleUnregisterClass(m_clsid,
    m_lpszProgID);

}
```

Wenn das Steuerelement Projekt von controlwizard in der Visual C++ -Version 4,1 oder höher generiert wurde, ist dieses Flag im Code bereits vorhanden. Zum Registrieren des Threading Modells sind keine Änderungen erforderlich.

Wenn das Projekt mit einer früheren Version von controlwizard generiert wurde, weist der vorhandene Code einen booleschen Wert als sechsten Parameter auf. Wenn der vorhandene Parameter true ist, ändern Sie ihn in *afxRegInsertable | afxRegApartmentThreading*. Wenn der vorhandene Parameter false ist, ändern Sie ihn in *afxRegApartmentThreading*.

Wenn Ihr Steuerelement nicht den Regeln für das Threading von Apartment Modellen folgt, dürfen Sie *afxRegApartmentThreading* in diesem Parameter nicht übergeben.

## <a name="see-also"></a>Weitere Informationen

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
