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
ms.openlocfilehash: cbea3e032932477006820c5a71fbbf3e40123bdf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322076"
---
# <a name="active-documents"></a>Aktive Dokumente

Aktive Dokumente erweitern die zusammengesetzte Dokumenttechnologie von OLE. Diese Erweiterungen werden in Form zusätzlicher Schnittstellen bereitgestellt, die Ansichten verwalten, sodass Objekte in Containern funktionieren und dennoch die Kontrolle über ihre Anzeige- und Druckfunktionen behalten können. Dieser Prozess ermöglicht die Anzeige von Dokumenten sowohl in fremden Frames (z. B. Microsoft Office Binder oder Microsoft Internet Explorer) als auch in systemeigenen Frames (z. B. in den produkteigenen Ansichtsports).

In diesem Abschnitt werden die funktionalen [Anforderungen für aktive Dokumente](#requirements_for_active_documents)beschrieben. Das aktive Dokument besitzt einen Datensatz und hat Zugriff auf den Speicher, auf dem die Daten gespeichert und abgerufen werden können. Es kann eine oder mehrere Ansichten für seine Daten erstellen und verwalten. Das aktive Dokument unterstützt nicht nur die üblichen Einbettungs- und direkte Aktivierungsschnittstellen `IOleDocument`von OLE-Dokumenten, sondern auch seine Fähigkeit, Ansichten über zu erstellen. Über diese Schnittstelle kann der Container anfordern, die Ansichten zu erstellen (und möglicherweise aufzuzählen), die das aktive Dokument anzeigen kann. Über diese Schnittstelle kann das aktive Dokument auch verschiedene Informationen über sich selbst bereitstellen, z. B. ob es mehrere Ansichten oder komplexe Rechtecke unterstützt.

Im Folgenden `IOleDocument` finden Sie die Schnittstelle. Beachten Sie, dass die `IEnumOleDocumentViews` Schnittstelle ein Standard-OLE-Enumerator für `IOleDocumentView*` Typen ist.

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

Jedes aktive Dokument muss über einen Ansichtsrahmenanbieter mit dieser Schnittstelle verfügen. Wenn das Dokument nicht in einen Container eingebettet ist, muss der aktive Dokumentserver selbst den Ansichtsrahmen bereitstellen. Wenn das aktive Dokument jedoch in einen aktiven Dokumentcontainer eingebettet ist, stellt der Container den Ansichtsrahmen bereit.

Ein aktives Dokument kann einen oder mehrere Arten von [Ansichten](#requirements_for_view_objects) seiner Daten erstellen (z. B. Normal, Gliederung, Seitenlayout usw.). Ansichten wirken wie Filter, durch die die Daten angezeigt werden können. Auch wenn das Dokument nur über einen Ansichtstyp verfügt, können Sie dennoch mehrere Ansichten unterstützen, um neue Fensterfunktionen zu unterstützen (z. B. das Element **"Neues Fenster"** im Menü **Fenster** in Office-Anwendungen).

## <a name="requirements-for-active-documents"></a><a name="requirements_for_active_documents"></a>Anforderungen an aktive Dokumente

Ein aktives Dokument, das in einem aktiven Dokumentcontainer angezeigt werden kann, muss:

- Verwenden Sie die zusammengesetzten Dateien von `IPersistStorage`OLE als Speichermechanismus, indem Sie .

- Unterstützen Sie die grundlegenden Einbettungsfunktionen von OLE-Dokumenten, einschließlich **Erstellen aus Datei**. Dies erfordert die Schnittstellen `IPersistFile`, `IOleObject`, `IDataObject`und .

- Unterstützen Sie eine oder mehrere Ansichten, von denen jede eine Ortsaktivierung kann. Das heißt, die Ansichten `IOleDocumentView` müssen die Schnittstelle `IOleInPlaceObject` sowie `IOleInPlaceActiveObject` die Schnittstellen und `IOleInPlaceSite` `IOleInPlaceFrame` (mit den Containern und Schnittstellen) unterstützen.

- Unterstützen Sie die `IOleDocument`standardmäßigen `IOleCommandTarget`aktiven `IPrint`Dokumentschnittstellen , und .

In diesen Anforderungen wird bekannt, wann und wie die containerseitigen Schnittstellen verwendet werden.

## <a name="requirements-for-view-objects"></a><a name="requirements_for_view_objects"></a>Anforderungen für Ansichtsobjekte

Ein aktives Dokument kann eine oder mehrere Ansichten seiner Daten erstellen. Funktionell sind diese Ansichten wie Ports auf einer bestimmten Methode zum Anzeigen der Daten. Wenn ein aktives Dokument nur eine einzelne Ansicht unterstützt, können das aktive Dokument und diese einzelne Ansicht mit einer einzelnen Klasse implementiert werden. `IOleDocument::CreateView`gibt den Schnittstellenzeiger `IOleDocumentView` desselben Objekts zurück.

Um in einem aktiven Dokumentcontainer dargestellt zu `IOleInPlaceObject` `IOleInPlaceActiveObject` werden, `IOleDocumentView`muss eine Ansichtskomponente zusätzlich unterstützen und zusätzlich:

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

Jede Ansicht verfügt über eine zugeordnete Ansichtssite, die den Ansichtsrahmen und den Ansichtsport (HWND und einen rechteckigen Bereich in diesem Fenster) kapselt. Die Website macht diese Funktionalität `IOleInPlaceSite` über die Standardschnittstelle verfügbar. Beachten Sie, dass es möglich ist, mehr als einen Ansichtsport auf einem einzelnen HWND zu haben.

In der Regel weist jeder Ansichtstyp eine andere gedruckte Darstellung auf. Daher sollten Ansichten und die entsprechenden Ansichtssites die Druckschnittstellen implementieren, wenn `IPrint` bzw. `IContinueCallback`. Der Ansichtsrahmen muss mit `IPrint` dem Ansichtsanbieter ausgehandelt werden, wenn der Druckvorgang beginnt, sodass Kopfzeilen, Fußzeilen, Ränder und verwandte Elemente korrekt gedruckt werden. Der Ansichtsanbieter benachrichtigt den Rahmen von `IContinueCallback`druckbezogenen Ereignissen über . Weitere Informationen zur Verwendung dieser Schnittstellen finden Sie unter [Programmgesteuertes Drucken](../mfc/programmatic-printing.md).

Beachten Sie, dass, wenn ein aktives Dokument nur eine einzelne Ansicht unterstützt, das aktive Dokument und diese einzelne Ansicht mit einer einzelnen konkreten Klasse implementiert werden können. `IOleDocument::CreateView`gibt einfach den Schnittstellenzeiger desselben Objekts `IOleDocumentView` zurück. Kurz gesagt, es ist nicht notwendig, dass es zwei separate Objektinstanzen gibt, wenn nur eine Ansicht erforderlich ist.

Ein Ansichtsobjekt kann auch ein Befehlsziel sein. Durch `IOleCommandTarget` implementieren einer Ansicht können Befehle empfangen werden, die von der Benutzeroberfläche des Containers stammen (z. B. **Neu**, **Öffnen**, **Speichern unter**, **Drucken** im Menü **Datei;** und **Kopieren**, **Einfügen**, **Rückgängig** machen im Menü **Bearbeiten).** Weitere Informationen finden Sie unter [Nachrichtenverarbeitung und Befehlsziele](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Siehe auch

[Active Document-Container](../mfc/active-document-containment.md)
