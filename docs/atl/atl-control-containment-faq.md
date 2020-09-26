---
title: Fragen und Antworten zur ATL-Steuerelementkapselung
ms.date: 11/04/2016
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
- ATL, hosting ActiveX controls
- ActiveX controls [C++], hosting
- controls [ATL]
ms.assetid: d4bdfbe0-82ca-4f2f-bb95-cb89bdcc9b53
ms.openlocfilehash: 693617589f157d352972485396777cec587a5b8f
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352699"
---
# <a name="atl-control-containment-faq"></a>Fragen und Antworten zur ATL-Steuerelementkapselung

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>Welche ATL-Klassen machen die Kapselung von ActiveX-Steuerelementen verfügbar?

Der Steuerelement-Hostingcode von ATL erfordert nicht, dass ATL-Klassen verwendet werden. Sie können einfach ein **"AtlAxWin80"** -Fenster erstellen und ggf. die Control-Hosting-API verwenden (Weitere Informationen finden Sie unter **Was ist die ATL-Steuerelement-Hosting-API**). Die folgenden Klassen machen die Kapselungs Funktionen jedoch einfacher zu verwenden.

|Klasse|BESCHREIBUNG|
|-----------|-----------------|
|[CAxWindow](../atl/reference/caxwindow-class.md)|Umschließt ein **"AtlAxWin80"** -Fenster, das Methoden zum Erstellen des Fensters, zum Erstellen eines Steuer Elements und/oder zum Anfügen eines Steuer Elements an das Fenster sowie zum Abrufen von Schnittstellen Zeigern für das Host Objekt bereitstellt.|
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Umschließt ein **"AtlAxWinLic80"** -Fenster, das Methoden zum Erstellen des Fensters, zum Erstellen eines Steuer Elements und/oder zum Anfügen eines lizenzierten Steuer Elements an das Fenster sowie zum Abrufen von Schnittstellen Zeigern für das Host Objekt bereitstellt.|
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|Fungiert als Basisklasse für ActiveX-Steuerelement Klassen basierend auf einer Dialogfeld Ressource. Solche Steuerelemente können andere ActiveX-Steuerelemente enthalten.|
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|Fungiert als Basisklasse für Dialog Klassen, die auf einer Dialogfeld Ressource basieren. Diese Dialogfelder können ActiveX-Steuerelemente enthalten.|
|[CWindow](../atl/reference/cwindow-class.md)|Stellt eine [getdlgcontrol](../atl/reference/cwindow-class.md#getdlgcontrol)-Methode bereit, die einen Schnittstellen Zeiger auf ein-Steuerelement zurückgibt, wenn die ID des zugehörigen Host Fensters angegeben wird. Außerdem vereinfachen die Windows-API-Wrapper, die von verfügbar gemacht werden, die `CWindow` Fensterverwaltung.|

## <a name="what-is-the-atl-control-hosting-api"></a>Was ist die API des ATL-Steuerelementhostings?

Bei der ATL-Steuerelement-Hosting-API handelt es sich um einen Satz von Funktionen, mit denen jedes Fenster als ActiveX-Steuerelement Container fungieren kann. Diese Funktionen können statisch oder dynamisch mit dem Projekt verknüpft werden, da Sie als Quellcode verfügbar sind und von ATL90.dll verfügbar gemacht werden. Die Funktionen zum Hosten von Steuerelementen sind in der folgenden Tabelle aufgeführt.

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Erstellt ein Host Objekt, verbindet es mit dem angegebenen Fenster und fügt dann ein vorhandenes Steuerelement an.|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Erstellt ein Host Objekt, verbindet es mit dem angegebenen Fenster und lädt dann ein-Steuerelement.|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster, ähnlich wie [atlaxkreatecontrol](reference/composite-control-global-functions.md#atlaxcreatecontrol).|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Erstellt ein Host Objekt, stellt eine Verbindung mit dem angegebenen Fenster her und lädt dann ein Steuerelement (ermöglicht auch das Einrichten von Ereignis senken).|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster (ähnlich wie [atlaxkreatecontrollic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)).|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Erstellt ein nicht modalem Dialogfeld aus einer Dialogfeld Ressource und gibt das Fenster Handle zurück.|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Erstellt ein modales Dialogfeld aus einer Dialogfeld Ressource.|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Gibt den **IUnknown** -Schnittstellen Zeiger des Steuer Elements zurück, das in einem-Fenster gehostet wird.|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Gibt den **IUnknown** -Schnittstellen Zeiger des Host Objekts zurück, das mit einem Fenster verbunden ist.|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Initialisiert den Steuerelement-Hostingcode.|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|Hebt die Initialisierung des Steuerelement-hostingcodes auf.|

Die `HWND` Parameter in den ersten drei Funktionen müssen ein vorhandenes Fenster eines (fast) beliebigen Typs sein. Wenn Sie eine dieser drei Funktionen explizit (in der Regel nicht erforderlich) verwenden, übergeben Sie kein Handle an ein Fenster, das bereits als Host fungiert (wenn dies der Fall ist, wird das vorhandene Host Objekt nicht freigegeben).

Die ersten sieben Funktionen bezeichnen [AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) implizit.

> [!NOTE]
> Die Steuerelement-Hosting-API bildet die Grundlage der ATL-Unterstützung für die Unterstützung des ActiveX-Steuer Elements Es ist jedoch in der Regel nicht erforderlich, diese Funktionen direkt aufzurufen, wenn Sie die Wrapper Klassen von ATL nutzen oder vollständig nutzen. Weitere Informationen finden Sie unter [Welche ATL-Klassen vereinfachen die](#which-atl-classes-facilitate-activex-control-containment)Einschluss von ActiveX-Steuerelementen.

## <a name="what-is-atlaxwin100"></a>Was ist AtlAxWin100?

`AtlAxWin100` der Name einer Fenster Klasse, mit der die Funktionen zum Hosting von ATL bereitgestellt werden können. Wenn Sie eine Instanz dieser Klasse erstellen, verwendet die Fenster Prozedur automatisch die Steuerelement-Hosting-API, um ein dem Fenster zugeordnetes Host Objekt zu erstellen und es mit dem Steuerelement zu laden, das Sie als Titel des Fensters angeben.

## <a name="when-do-i-need-to-call-atlaxwininit"></a>Wann muss ich AtlAxWinInit aufrufen?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) registriert die Fenster Klasse **"AtlAxWin80"** (zuzüglich einiger benutzerdefinierter Fenster Meldungen), damit diese Funktion aufgerufen werden muss, bevor Sie versuchen, ein Host Fenster zu erstellen. Sie müssen diese Funktion jedoch nicht immer explizit aufzurufen, da die Hosting-APIs (und die Klassen, die Sie verwenden) diese Funktion häufig für Sie aufzurufen. Es gibt keinen Schaden, wenn diese Funktion mehrmals aufgerufen wird.

## <a name="what-is-a-host-object"></a>Was ist ein Hostobjekt?

Ein Host Objekt ist ein COM-Objekt, das den ActiveX-Steuerelement Container darstellt, der von ATL für ein bestimmtes Fenster bereitgestellt wird. Das Host Objekt unterteilt das Containerfenster, sodass es Nachrichten an das Steuerelement reflektieren kann. es stellt die erforderlichen Container Schnittstellen zur Verwendung durch das Steuerelement bereit und macht die Schnittstellen [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) und [IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) verfügbar, damit Sie die Umgebung des Steuer Elements konfigurieren können.

Sie können das Host Objekt verwenden, um die Umgebungs Eigenschaften des Containers festzulegen.

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Kann ich in einem Fenster mehrere Steuerelemente hosten?

Es ist nicht möglich, mehr als ein Steuerelement in einem einzelnen ATL-Host Fenster zu hosten. Jedes Host Fenster ist so konzipiert, dass genau ein Steuerelement gleichzeitig enthalten ist (Dies ermöglicht einen einfachen Mechanismus für die Verarbeitung von Nachrichten Reflektion und Umgebungs Eigenschaften pro Steuerung). Wenn Sie jedoch möchten, dass der Benutzer mehrere Steuerelemente in einem einzelnen Fenster sehen kann, ist es eine einfache Sache, mehrere Host Fenster als untergeordnete Elemente dieses Fensters zu erstellen.

## <a name="can-i-reuse-a-host-window"></a>Kann ich ein Hostfenster wiederverwenden?

Es wird nicht empfohlen, Host Fenster wiederzuverwenden. Um die Robustheit des Codes zu gewährleisten, sollten Sie die Lebensdauer des Host Fensters mit der Lebensdauer eines einzelnen Steuer Elements verknüpfen.

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>Wann muss ich AtlAxWinInit aufrufen?

[Atlax WinTerm](reference/composite-control-global-functions.md#atlaxwinterm) hebt die Registrierung der Fenster Klasse **"AtlAxWin80"** auf. Diese Funktion sollte aufgerufen werden (wenn Sie keine Host Fenster mehr erstellen müssen), nachdem alle vorhandenen Host Fenster zerstört wurden. Wenn Sie diese Funktion nicht aufzurufen, wird die Registrierung der Fenster Klasse automatisch aufgehoben, wenn der Prozess beendet wird.

## <a name="hosting-activex-controls-using-atl-axhost"></a>Hosten eines ActiveX-Steuerelement mit ATL-XHost

Im Beispiel in diesem Abschnitt wird gezeigt, wie AxHost erstellt wird und wie ein ActiveX-Steuerelement mithilfe verschiedener ATL-Funktionen gehostet wird. Außerdem wird gezeigt, wie Sie über das gehostete Steuerelement auf das Steuerelement und die Senke Ereignisse zugreifen (mithilfe von [IDispEventImpl](../atl/reference/idispeventimpl-class.md)). Das Beispiel hostet das Calendar-Steuerelement in einem Hauptfenster oder in einem untergeordneten Fenster.

Beachten Sie die Definition des `USE_METHOD` Symbols. Sie können den Wert dieses Symbols ändern, um zwischen 1 und 8 zu variieren. Der Wert des Symbols bestimmt, wie das Steuerelement erstellt wird:

- Bei gerade nummerierten Werten von `USE_METHOD` erstellt der-Vorgang zum Erstellen der Host Unterklassen ein Fenster und konvertiert dieses in einen Steuerelement Host. Für ungerade nummerierte Werte erstellt der Code ein untergeordnetes Fenster, das als Host fungiert.

- Bei Werten `USE_METHOD` zwischen 1 und 4 wird der Zugriff auf das Steuerelement und das senken von Ereignissen in dem-Befehl durchgeführt, der auch den Host erstellt. Werte zwischen 5 und 8 Fragen den Host nach Schnittstellen ab und hosten die Senke.

Hier finden Sie eine Zusammenfassung:

|USE_METHOD|Host|Steuern des Zugriffs und des Ereignisses|Gezeigte Funktion|
|-----------------|----------|--------------------------------------|---------------------------|
|1|Untergeordnetes Fenster|Ein Schritt|"Kreatecontrollicex"|
|2|Hauptfenster|Ein Schritt|AtlAxCreateControlLicEx|
|3|Untergeordnetes Fenster|Ein Schritt|"Kreatecontrolex"|
|4|Hauptfenster|Ein Schritt|AtlAxCreateControlEx|
|5|Untergeordnetes Fenster|Mehrere Schritte|"Kreatecontrollic"|
|6|Hauptfenster|Mehrere Schritte|AtlAxCreateControlLic|
|7|Untergeordnetes Fenster|Mehrere Schritte|CreateControl|
|8|Hauptfenster|Mehrere Schritte|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Fragen und Antworten zur Steuerelementkapselung](../atl/atl-control-containment-faq.md)<br/>
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)<br/>
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)<br/>
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[CAxWindow2T-Klasse](../atl/reference/caxwindow2t-class.md)<br/>
[Iaxwinhostwindowlic-Schnittstelle](../atl/reference/iaxwinhostwindowlic-interface.md)
