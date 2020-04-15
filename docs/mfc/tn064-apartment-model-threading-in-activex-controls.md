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
ms.openlocfilehash: 0c6a42124b4b2b03ae7cd9277fa14d43eac7a2bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366069"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064: Apartmentmodellthreading in ActiveX-Steuerelementen

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

In diesem technischen Hinweis wird erläutert, wie das Einfädeln von Apartmentmodell in einem ActiveX-Steuerelement aktiviert wird. Beachten Sie, dass das Einfädeln von Apartmentmodell enzwertert nur in Visual C++-Versionen 4.2 oder höher unterstützt wird.

## <a name="what-is-apartment-model-threading"></a>Was ist Apartment-Model Threading

Das Apartmentmodell ist ein Ansatz zur Unterstützung eingebetteter Objekte, z. B. ActiveX-Steuerelemente, innerhalb einer Multithread-Containeranwendung. Obwohl die Anwendung über mehrere Threads verfügt, wird jede Instanz eines eingebetteten Objekts einer "Wohnung" zugewiesen, die nur für einen Thread ausgeführt wird. Mit anderen Worten, alle Aufrufe in eine Instanz eines Steuerelements werden auf demselben Thread erfolgen.

Allerdings können verschiedene Instanzen der gleichen Art von Kontrolle verschiedenen Wohnungen zugewiesen werden. Wenn also mehrere Instanzen eines Steuerelements gemeinsame Daten gemeinsam haben (z. B. statische oder globale Daten), muss der Zugriff auf diese freigegebenen Daten durch ein Synchronisierungsobjekt, z. B. einen kritischen Abschnitt, geschützt werden.

Ausführliche Informationen zum Modell des Apartment-Threadings finden Sie unter [Prozesse und Threads](/windows/win32/ProcThread/processes-and-threads) in der *OLE-Programmierer-Referenz*.

## <a name="why-support-apartment-model-threading"></a>Warum Unterstützung Apartment-Model Threading

Steuerelemente, die das Einfädeln von Apartmentmodell unterstützen, können in Multithreadcontaineranwendungen verwendet werden, die auch das Apartmentmodell unterstützen. Wenn Sie das Einfädeln von Apartmentmodell nicht aktivieren, begrenzen Sie den potenziellen Containersatz, in dem Ihr Steuerelement verwendet werden könnte.

Das Aktivieren des Einfädelns von Apartment-Modell ist für die meisten Steuerelemente einfach, insbesondere wenn sie über wenig oder keine freigegebenen Daten verfügen.

## <a name="protecting-shared-data"></a>Schutz freigegebener Daten

Wenn Das Steuerelement freigegebene Daten verwendet, z. B. eine statische Membervariable, sollte der Zugriff auf diese Daten mit einem kritischen Abschnitt geschützt werden, um zu verhindern, dass mehrere Threads die Daten gleichzeitig ändern. Um einen kritischen Abschnitt für diesen Zweck einzurichten, `CCriticalSection` deklarieren Sie eine statische Membervariable der Klasse in der Klasse des Steuerelements. Verwenden `Lock` Sie `Unlock` die und Memberfunktionen dieses kritischen Abschnittsobjekts überall dort, wo Ihr Code auf die freigegebenen Daten zugreift.

Betrachten Sie beispielsweise eine Steuerelementklasse, die eine Zeichenfolge verwalten muss, die von allen Instanzen gemeinsam genutzt wird. Diese Zeichenfolge kann in einer statischen Membervariablen beibehalten und durch einen kritischen Abschnitt geschützt werden. Die Klassendeklaration des Steuerelements würde Folgendes enthalten:

```cpp
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

Die Implementierung für die Klasse würde Definitionen für diese Variablen enthalten:

```cpp
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

Der Zugriff `_strShared` auf das statische Element kann dann durch den kritischen Abschnitt geschützt werden:

```cpp
void CSampleCtrl::SomeMethod()
{
    _critSect.Lock();
if (_strShared.Empty())
    _strShared = "<text>";
    _critSect.Unlock();

...
}
```

## <a name="registering-an-apartment-model-aware-control"></a>Registrieren eines Apartment-Model-Aware Control

Steuerelemente, die das Threading von Apartmentmodell unterstützen, sollten diese Funktion in der Registrierung angeben, indem der benannte Wert "ThreadingModel" mit dem Wert "Apartment" in ihrem Klassen-ID-Registrierungseintrag unter der *Klassen-ID*\\**InprocServer32-Schlüssel** hinzugefügt wird. Um zu bewirken, dass dieser Schlüssel automatisch für Ihr Steuerelement registriert wird, übergeben Sie das *flag afxRegApartmentThreading* im sechsten Parameter an: `AfxOleRegisterControlClass`

```cpp
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

Wenn Ihr Steuerelementprojekt von ControlWizard in Visual C++-Version 4.1 oder höher generiert wurde, ist dieses Flag bereits im Code vorhanden. Für die Registrierung des Threadingmodells sind keine Änderungen erforderlich.

Wenn Ihr Projekt von einer früheren Version von ControlWizard generiert wurde, hat Ihr vorhandener Code einen booleschen Wert als sechsten Parameter. Wenn der vorhandene Parameter TRUE ist, ändern Sie ihn in *afxRegInsertable | afxRegApartmentThreading*. Wenn der vorhandene Parameter FALSE ist, ändern Sie ihn in *afxRegApartmentThreading*.

Wenn Ihr Steuerelement nicht den Regeln für das Einfädeln von Apartmentmodell entspricht, dürfen Sie in diesem Parameter *nicht afxRegApartmentThreading* übergeben.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
