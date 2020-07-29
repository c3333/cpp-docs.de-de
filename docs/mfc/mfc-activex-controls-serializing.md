---
title: 'MFC-ActiveX-Steuerelemente: Serialisierung'
ms.date: 09/12/2018
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
helpviewer_keywords:
- MFC ActiveX controls [MFC], version support
- wVerMinor global constant [MFC]
- GetVersion method [MFC]
- ExchangeVersion method [MFC]
- MFC ActiveX controls [MFC], serializing
- DoPropExchange method [MFC]
- versioning ActiveX controls
- wVerMajor global constant
ms.assetid: 9d57c290-dd8c-4853-b552-6f17f15ebedd
ms.openlocfilehash: f5e3b4bdf203f90b3550a2521ba51ba451cf3a46
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225019"
---
# <a name="mfc-activex-controls-serializing"></a>MFC-ActiveX-Steuerelemente: Serialisierung

In diesem Artikel wird erläutert, wie ein ActiveX-Steuerelement serialisiert wird. Bei der Serialisierung wird ein dauerhaftes Speichermedium (z. b. eine Datenträger Datei) aus dem Lese-oder Schreibvorgang geschrieben. Die MFC-Bibliothek (Microsoft Foundation Class) bietet integrierte Unterstützung für die Serialisierung in der-Klasse `CObject` . `COleControl`erweitert diese Unterstützung durch die Verwendung eines Eigenschaften Austauschmechanismus auf ActiveX-Steuerelemente.

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

Die Serialisierung für ActiveX-Steuerelemente wird durch Überschreiben von [COleControl::D opropexchange](reference/colecontrol-class.md#dopropexchange)implementiert. Diese Funktion, die beim Laden und Speichern des Steuerelement Objekts aufgerufen wird, speichert alle Eigenschaften, die mit einer Element Variablen oder einer Element Variablen mit Änderungs Benachrichtigung implementiert werden.

In den folgenden Themen werden die wichtigsten Probleme im Zusammenhang mit der Serialisierung eines ActiveX-Steuer Elements behandelt:

- Implementieren `DoPropExchange` der Funktion zum Serialisieren des Steuerelement Objekts

- [Anpassen des Serialisierungsprozesses](#_core_customizing_the_default_behavior_of_dopropexchange)

- [Implementieren von Versions Unterstützung](#_core_implementing_version_support)

## <a name="implementing-the-dopropexchange-function"></a><a name="_core_implementing_the_dopropexchange_function"></a>Implementieren der DoPropExchange-Funktion

Wenn Sie den ActiveX-Steuerelement-Assistenten verwenden, um das Steuerelement Projekt zu generieren, werden der Steuerelement Klasse automatisch mehrere standardhandlerfunktionen hinzugefügt, einschließlich der Standard Implementierung von [COleControl::D opropexchange](reference/colecontrol-class.md#dopropexchange). Das folgende Beispiel zeigt den Code, der den mit dem ActiveX-Steuerelement-Assistenten erstellten Klassen hinzugefügt wird:

[!code-cpp[NVC_MFC_AxUI#43](codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

Wenn Sie eine Eigenschaft als persistent festlegen möchten, ändern Sie `DoPropExchange` durch Hinzufügen eines Aufrufes der Eigenschaften Austausch Funktion. Im folgenden Beispiel wird die Serialisierung einer benutzerdefinierten booleschen CircleShape-Eigenschaft veranschaulicht, bei der die Eigenschaft "CircleShape" den Standardwert " **true**" aufweist:

[!code-cpp[NVC_MFC_AxSer#1](codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

In der folgenden Tabelle sind die möglichen Eigenschaften Austausch Funktionen aufgelistet, die Sie verwenden können, um die Eigenschaften des Steuer Elements zu serialisieren:

|Eigenschaften Austausch Funktionen|Zweck|
|---------------------------------|-------------|
|**PX_Blob ()**|Serialisiert eine Dateneigenschaft des Typs Binary Large Object (BLOB).|
|**PX_Bool ()**|Serialisiert eine boolesche Eigenschaft des Typs.|
|**PX_Color ()**|Serialisiert eine typfarb Eigenschaft.|
|**PX_Currency ()**|Serialisiert eine Eigenschaft vom Typ **CY** (Currency).|
|**PX_Double ()**|Serialisiert eine **`double`** Typeigenschaft.|
|**PX_Font ()**|Serialisiert eine Eigenschaft des Schriftart Typs.|
|**PX_Float ()**|Serialisiert eine **`float`** Typeigenschaft.|
|**PX_IUnknown ()**|Serialisiert eine Eigenschaft vom Typ `LPUNKNOWN` .|
|**PX_Long ()**|Serialisiert eine **`long`** Typeigenschaft.|
|**PX_Picture ()**|Serialisiert eine Eigenschaft des Typs Bild.|
|**PX_Short ()**|Serialisiert eine **`short`** Typeigenschaft.|
|**Pxstring ()**|Serialisiert eine `CString` Typeigenschaft.|
|**PX_ULong ()**|Serialisiert eine **ulong** -Typ-Eigenschaft.|
|**PX_UShort ()**|Serialisiert eine **UShort** -Eigenschaft des Typs.|

Weitere Informationen zu diesen Eigenschaften Austausch Funktionen finden Sie unter [Persistenz von OLE](reference/persistence-of-ole-controls.md) -Steuerelementen in der *MFC-Referenz*.

## <a name="customizing-the-default-behavior-of-dopropexchange"></a><a name="_core_customizing_the_default_behavior_of_dopropexchange"></a>Anpassen des Standard Verhaltens von "DoPropExchange"

Die Standard Implementierung von `DoPropertyExchange` (wie im vorherigen Thema gezeigt) führt einen-Befehl für die-Basisklasse aus `COleControl` . Dadurch wird die Gruppe von Eigenschaften serialisiert, die von automatisch unterstützt `COleControl` werden. Dadurch wird mehr Speicherplatz verwendet, als nur die benutzerdefinierten Eigenschaften des Steuer Elements zu serialisieren. Wenn Sie diesen-Befehl entfernen, kann Ihr Objekt nur die Eigenschaften serialisieren, die Sie als wichtig bezeichnen. Alle Aktien Eigenschafts Zustände, die das Steuerelement implementiert hat, werden beim Speichern oder Laden des Steuerelement Objekts nicht serialisiert, es sei denn, Sie fügen explizit **PX_** Aufrufe für Sie hinzu.

## <a name="implementing-version-support"></a><a name="_core_implementing_version_support"></a>Implementieren von Versions Unterstützung

Versions Unterstützung ermöglicht einem überarbeiteten ActiveX-Steuerelement, neue persistente Eigenschaften hinzuzufügen, und kann weiterhin den persistenten Zustand erkennen und laden, der von einer früheren Version des-Steuer Elements erstellt wurde. Um die Version eines Steuer Elements als Teil der persistenten Daten verfügbar zu machen, müssen Sie [COleControl:: ExchangeVersion](reference/colecontrol-class.md#exchangeversion) in der-Funktion des-Steuer Elements aufzurufen `DoPropExchange` . Dieser Befehl wird automatisch eingefügt, wenn das ActiveX-Steuerelement mit dem ActiveX-Steuerelement-Assistenten erstellt wurde. Er kann entfernt werden, wenn keine Versions Unterstützung erforderlich ist. Die Kosten für die Größe der Kontrolle sind jedoch sehr gering (4 Bytes), um die von der Versions Unterstützung benötigte Flexibilität zu erhöhen.

Wenn das Steuerelement nicht mit dem ActiveX-Steuerelement-Assistenten erstellt wurde, fügen Sie einen-Befehl hinzu, `COleControl::ExchangeVersion` indem Sie die folgende Zeile am Anfang der `DoPropExchange` Funktion einfügen (vor dem-Befehl `COleControl::DoPropExchange` ):

[!code-cpp[NVC_MFC_AxSer#1](codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Sie können ein beliebiges **DWORD** als Versionsnummer verwenden. Vom ActiveX-Steuerelement-Assistenten generierte Projekte verwenden `_wVerMinor` und `_wVerMajor` als Standard. Dabei handelt es sich um globale Konstanten, die in der Implementierungs Datei der ActiveX-Steuerelement Klasse des Projekts definiert sind. Innerhalb der restlichen `DoPropExchange` Funktion können Sie [CPropExchange:: GetVersion](reference/cpropexchange-class.md#getversion) jederzeit aufrufen, um die Version abzurufen, die Sie speichern oder abrufen.

Im folgenden Beispiel hat Version 1 dieses Beispiel Steuer Elements nur eine "ReleaseDate"-Eigenschaft. In Version 2 wird eine "OriginalDate"-Eigenschaft hinzugefügt. Wenn das Steuerelement angewiesen wird, den persistenten Zustand aus der alten Version zu laden, wird die Element Variable für die neue Eigenschaft mit einem Standardwert initialisiert.

[!code-cpp[NVC_MFC_AxSer#4](codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Standardmäßig konvertiert ein Steuerelement alte Daten in das neueste Format. Wenn z. b. Version 2 eines Steuer Elements Daten lädt, die von Version 1 gespeichert wurden, wird das Format der Version 2 geschrieben, wenn es wieder gespeichert wird. Wenn Sie möchten, dass das Steuerelement Daten im letzten Lese Format speichert, übergeben Sie **false** beim Aufrufen von als dritten Parameter `ExchangeVersion` . Dieser dritte Parameter ist optional und ist standardmäßig " **true** ".

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)
