---
title: Aktive Dokumente
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC]
- active documents [MFC], requirements
- view objects [MFC], requirements
- OLE [MFC], active documents
- views [MFC], active documents
- active documents [MFC], views
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
ms.openlocfilehash: bfe91dcb42b97ddfbb0bf0be36a54b45e6dc0809
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625155"
---
# <a name="active-documents"></a>Aktive Dokumente

Aktive Dokumente erweitern die Verbund Dokumenten Technologie von OLE. Diese Erweiterungen werden in Form zusätzlicher Schnittstellen zur Verwaltung von Sichten bereitgestellt, sodass Objekte innerhalb von Containern funktionieren und die Kontrolle über Ihre Anzeige-und Druckfunktionen behalten können. Dieser Prozess ermöglicht es, Dokumente sowohl in fremd Frames (z. b. in den Microsoft Office Binder oder Microsoft Internet Explorer) als auch in systemeigenen Frames (z. b. den eigenen Ansichts Anschlüssen des Produkts) anzuzeigen.

In diesem Abschnitt werden die funktionalen [Anforderungen für aktive Dokumente](#requirements_for_active_documents)beschrieben. Das aktive Dokument besitzt eine Gruppe von Daten und verfügt über Zugriff auf den Speicher, in dem die Daten gespeichert und abgerufen werden können. Sie kann eine oder mehrere Ansichten für Ihre Daten erstellen und verwalten. Zusätzlich zur Unterstützung der üblichen Einbett enden und direkten Aktivierungs Schnittstellen von OLE-Dokumenten kommuniziert das aktive Dokument damit, dass Sichten über erstellt werden können `IOleDocument` . Über diese Schnittstelle kann der Container die Ansichten erstellen (und ggf. auflisten), die das aktive Dokument anzeigen kann. Über diese Schnittstelle kann das aktive Dokument auch verschiedene Informationen über sich selbst bereitstellen, z. b. ob es mehrere Ansichten oder komplexe Rechtecke unterstützt.

Im folgenden finden Sie die- `IOleDocument` Schnittstelle. Beachten Sie, dass die- `IEnumOleDocumentViews` Schnittstelle ein OLE-Standard Enumerator für- `IOleDocumentView*` Typen ist.

```
interface IOleDocument : IUnknown
    {
    HRESULT CreateView(
        [in] IOleInPlaceSite *pIPSite,
        [in] IStream *pstm,
        [in] DWORD dwReserved,
        [out] IOleDocumentView **ppView);

    HRESULT GetDocMiscStatus([out] DWORD *pdwStatus);

    HRESULT EnumViews(
        [out] IEnumOleDocumentViews **ppEnum,
        [out] IOleDocumentView **ppView);
    }
```

Jedes aktive Dokument muss über einen Ansichts Rahmen Anbieter mit dieser Schnittstelle verfügen. Wenn das Dokument nicht in einen Container eingebettet ist, muss der aktive Dokument Server selbst den Ansichts Rahmen bereitstellen. Wenn das aktive Dokument jedoch in einen aktiven Dokument Container eingebettet ist, stellt der Container den Ansichts Rahmen bereit.

Ein aktives Dokument kann einen oder mehrere Typen von [Sichten](#requirements_for_view_objects) seiner Daten erstellen (z. b. Normal, Gliederung, Seitenlayout usw.). Sichten fungieren wie Filter, mit denen die Daten angezeigt werden können. Auch wenn das Dokument nur über eine Art Ansicht verfügt, können Sie mehrere Ansichten unterstützen, um neue Fenster Funktionen zu unterstützen (z. b. das **neue Fenster** Element im Menü **Fenster** in Office-Anwendungen).

## <a name="requirements-for-active-documents"></a><a name="requirements_for_active_documents"></a>Anforderungen für aktive Dokumente

Ein aktives Dokument, das in einem aktiven Dokument Container angezeigt werden kann, muss folgende Aktionen ausführen:

- Verwenden Sie OLE-Verbund Dateien als Speichermechanismus, indem Sie implementieren `IPersistStorage` .

- Unterstützt die grundlegenden Einbettungs Funktionen von OLE-Dokumenten, einschließlich **Create from file**. Dies erfordert die Schnittstellen `IPersistFile` , `IOleObject` und `IDataObject` .

- Unterstützung für eine oder mehrere Ansichten, von denen jede eine direkte Aktivierung durchgeführt hat. Das heißt, dass die Ansichten sowohl die-Schnittstelle `IOleDocumentView` als auch die-Schnittstellen `IOleInPlaceObject` und `IOleInPlaceActiveObject` (mithilfe der- `IOleInPlaceSite` und- `IOleInPlaceFrame` Schnittstellen des Containers) unterstützen müssen.

- Unterstützen der standardmäßigen aktiven Dokument Schnittstellen `IOleDocument` , `IOleCommandTarget` und `IPrint` .

Die Kenntnisse, wann und wie die Container seitigen Schnittstellen verwendet werden, sind in diesen Anforderungen impliziert.

## <a name="requirements-for-view-objects"></a><a name="requirements_for_view_objects"></a>Anforderungen für Ansichts Objekte

Ein aktives Dokument kann eine oder mehrere Ansichten seiner Daten erstellen. Funktionell ähneln diese Sichten den Ports einer bestimmten Methode zum Anzeigen der Daten. Wenn ein aktives Dokument nur eine einzelne Ansicht unterstützt, können das aktive Dokument und diese einzelne Ansicht mithilfe einer einzelnen Klasse implementiert werden. `IOleDocument::CreateView`Gibt den Schnittstellen Zeiger desselben-Objekts zurück `IOleDocumentView` .

Um in einem aktiven Dokument Container dargestellt zu werden, muss eine Ansichts Komponente `IOleInPlaceObject` und `IOleInPlaceActiveObject` zusätzlich zu folgenden Aktionen unterstützen `IOleDocumentView` :

```
interface IOleDocumentView : IUnknown
    {
    HRESULT SetInPlaceSite([in] IOleInPlaceSite *pIPSite);
    HRESULT GetInPlaceSite([out] IOleInPlaceSite **ppIPSite);
    HRESULT GetDocument([out] IUnknown **ppunk);
    [input_sync] HRESULT SetRect([in] LPRECT prcView);
    HRESULT GetRect([in] LPRECT prcView);
    [input_sync] HRESULT SetRectComplex(
        [in] LPRECT prcView,
        [in] LPRECT prcHScroll,
        [in] LPRECT prcVScroll,
        [in] LPRECT prcSizeBox);
    HRESULT Show([in] BOOL fShow);
    HRESULT UIActivate([in] BOOL fUIActivate);
    HRESULT Open(void);
    HRESULT CloseView([in] DWORD dwReserved);
    HRESULT SaveViewState([in] IStream *pstm);
    HRESULT ApplyViewState([in] IStream *pstm);
    HRESULT Clone(
        [in] IOleInPlaceSite *pIPSiteNew,
        [out] IOleDocumentView **ppViewNew);
    }
```

Jede Ansicht verfügt über eine zugeordnete Ansichts Site, die den Ansichts Rahmen und den Ansichtsport (HWND und einen rechteckigen Bereich in diesem Fenster) kapselt. Diese Funktionalität wird von der Site auch über die Standardschnittstelle verfügbar gemacht `IOleInPlaceSite` . Beachten Sie, dass es möglich ist, mehr als einen Ansichtsport auf einem einzelnen HWND zu haben.

In der Regel hat jeder Ansichtstyp eine andere gedruckte Darstellung. Daher sollten Sichten und die entsprechenden Ansichts Standorte die Druck Schnittstellen implementieren `IPrint` `IContinueCallback` , wenn bzw. Der Ansichts Rahmen muss mit dem Ansichts Anbieter durch verhandelt `IPrint` werden, wenn der Druckvorgang beginnt, sodass Header, Fußzeilen, Ränder und zugehörige Elemente ordnungsgemäß gedruckt werden. Der Ansichts Anbieter benachrichtigt den Rahmen der druckbezogenen Ereignisse über `IContinueCallback` . Weitere Informationen zur Verwendung dieser Schnittstellen finden Sie Unterprogramm gesteuertes [Drucken](programmatic-printing.md).

Beachten Sie Folgendes: Wenn ein aktives Dokument nur eine einzelne Ansicht unterstützt, können das aktive Dokument und diese einzelne Ansicht mithilfe einer einzelnen konkreten Klasse implementiert werden. `IOleDocument::CreateView`gibt einfach den Schnittstellen Zeiger desselben-Objekts zurück `IOleDocumentView` . Kurz gesagt, es ist nicht erforderlich, dass zwei separate Objektinstanzen vorhanden sind, wenn nur eine Sicht erforderlich ist.

Ein Ansichts Objekt kann auch ein Befehls Ziel sein. Durch `IOleCommandTarget` das Implementieren einer Ansicht können Befehle empfangen werden, die aus der Benutzeroberfläche des Containers stammen (z. b. " **neu**", " **Öffnen**", " **Speichern**unter", " **Drucken** " **Edit** im Menü " **Datei** " und " **Kopieren**", " **Einfügen**", " **Rückgängig** Weitere Informationen finden Sie unter [Nachrichten Behandlung und Befehls Ziele](message-handling-and-command-targets.md).

## <a name="see-also"></a>Siehe auch

[Active Document-Container](active-document-containment.md)
