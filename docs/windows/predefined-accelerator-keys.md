---
title: Zugriffstasten (C++)
ms.date: 02/14/2019
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: 4f838caa8ca9e4a996fa4cb8018d663c6c7aecea
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504299"
---
# <a name="accelerator-keys-c"></a>Zugriffstasten (C++)

## <a name="predefined-accelerator-keys"></a>Vordefinierte Zugriffstasten

Es gibt eine Anzahl vordefinierter Zugriffstasten, die Teil eines Windows-Anwendungsprojekts sein können. Einige dieser virtuellen Tasten sind für die Windows-Umgebung. Andere unterstützen Browser-oder Unicode-Anwendungen. Dieser Tasten können in beliebigen Zugriffstasten verwendet werden.

|Schlüssel|Beschreibung|
|---------|-----------------|
|VK_ACCEPT|(IME) akzeptieren|
|VK_BROWSER_BACK|Windows Browser, **zurück** -Taste|
|VK_BROWSER_FAVORITES|Windows Browser, **Favoriten** -Taste|
|VK_BROWSER_FORWARD|Windows Browser, **Vorwärts** -Taste|
|VK_BROWSER_HOME|Windows Browser, **Start** und **Home** Key|
|VK_BROWSER_REFRESH|Windows Browser, Schlüssel **Aktualisieren**|
|VK_BROWSER_SEARCH|Windows Browser, Schlüssel **Suchen**|
|VK_BROWSER_STOP|Windows Browser, Tastatur **Abbrechen**|
|VK_CONVERT|(IME) konvertieren|
|VK_FINAL|(IME) abschließender Modus|
|VK_HANGUEL|Anhängen Hanguel-Modus (aus Kompatibilitätsgründen beibehalten, VK_HANGUL verwenden)|
|VK_HANGUL|Anhängen Hangul-Modus|
|VK_HANJA|Anhängen Hanja-Modus|
|VK_JUNJA|Anhängen Junja-Modus|
|VK_KANA|Anhängen Kana-Modus|
|VK_KANJI|Anhängen Kanji-Modus|
|VK_LAUNCH_APP1|Windows Schlüssel für **Anwendung 1 starten**|
|VK_LAUNCH_APP2|Windows Schlüssel für **Anwendung 2 starten**|
|VK_LAUNCH_MAIL|Windows **Mail Schlüssel starten**|
|VK_LAUNCH_MEDIA_SELECT|Windows **Medien Schlüssel auswählen**|
|VK_LCONTROL|**Linke STRG** -Taste|
|VK_LMENU|**Linke Menü** Taste|
|VK_LSHIFT|**Left Shift** -Taste|
|VK_MEDIA_NEXT_TRACK|Windows Taste für den **nächsten Titel**|
|VK_MEDIA_PLAY_PAUSE|Windows **Medien** Taste wiedergeben/anhalten|
|VK_MEDIA_PREV_TRACK|Windows **Vorherige tracktaste**|
|VK_MEDIA_STOP|Windows **Medien Taste abbrechen**|
|VK_MODECHANGE|(IME)-Modus Change Request|
|VK_NONCONVERT|(IME) nicht konvertieren|
|VK_OEM_1|Windows Für die US-Standardtastatur lautet der Schlüssel " **;:".**|
|VK_OEM_102|Windows Entweder die Spitze Klammer Taste oder die Taste für den umgekehrten Schrägstrich auf der RT 102-Key-Tastatur|
|VK_OEM_2|Windows Für die US-Standardtastatur lautet der **/?** Schlüssel|
|VK_OEM_3|Windows Für die US-Standardtastatur der **`~** Schlüssel|
|VK_OEM_4|Windows Für die US-Standardtastatur ist die **[{** -Taste|
|VK_OEM_5|Windows Für die US-Standardtastatur die ** \\&#124;** -Taste|
|VK_OEM_6|Windows Für die US-Standardtastatur die Taste **]}**|
|VK_OEM_7|Windows Für die US-Standardtastatur ist der Schlüssel "einfache Anführungszeichen/doppelte Anführungszeichen".|
|VK_OEM_COMMA|Windows Für ein beliebiges Land/eine Region **, den Schlüssel**|
|VK_OEM_MINUS|Windows Für ein beliebiges Land/eine Region der **-** Schlüssel|
|VK_OEM_PERIOD|Windows Für ein beliebiges Land/eine Region ist der **.** Schlüssel|
|VK_OEM_PLUS|Windows Für ein beliebiges Land/eine Region der **+** Schlüssel|
|VK_PACKET|Windows Wird verwendet, um Unicode-Zeichen so zu übergeben, als wären Sie Tastatureingaben.|
|VK_RCONTROL|**Right Strg** -Taste|
|VK_RMENU|**Rechte Menü** Taste|
|VK_RSHIFT|**Rechte UMSCHALT** Taste|
|VK_SLEEP|**Computer** Standbytaste|
|VK_VOLUME_DOWN|Windows **Nach-unten** -Taste|
|VK_VOLUME_MUTE|Windows Taste zum **stumm schalten**|
|VK_VOLUME_UP|Windows **Lautstärke** Taste|
|VK_XBUTTON1|Windows **X1** -Maustaste|
|VK_XBUTTON2|Windows **X2** -Maustaste|

## <a name="accelerator-key-association"></a>Zugriffstasten Zuordnung

In vielen Fällen möchten Sie über ein Menüelement und eine Tastenkombination verfügen, um denselben Programmbefehl auszugeben. Sie führen diese Aktion aus, indem Sie dem Menü Element denselben Ressourcen Bezeichner (ID) und einen Eintrag in der Zugriffstasten Tabelle Ihrer Anwendung zuweisen. Sie können die Beschriftung des Menüelements ändern, um den Namen der Zugriffstaste anzuzeigen. Weitere Informationen über Menü Elemente und Zugriffstasten finden Sie unter [Menübefehle](./menu-command-properties.md).

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Zugriffstasten-Editor](../windows/accelerator-editor.md)<br/>
