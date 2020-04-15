---
title: Handler für Windows-Standardmeldungen
ms.date: 11/04/2016
f1_keywords:
- afx_msg
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
ms.openlocfilehash: 9a136caf3a1d22151cb9cfd48e1cd3f999ab51ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370502"
---
# <a name="handlers-for-standard-windows-messages"></a>Handler für Windows-Standardmeldungen

Standardhandler für Standard-Windows-Nachrichten (**WM_** `CWnd`) sind in der Klasse vordefiniert. Die Klassenbibliothek basiert Namen für diese Handler auf dem Nachrichtennamen. Der Handler für die **WM_PAINT** Nachricht `CWnd` wird z. B. in folgenden Angegeben:

`afx_msg void OnPaint();`

Das **Schlüsselwort afx_msg** schlägt die Wirkung des **virtuellen** Schlüsselworts `CWnd` C++ vor, indem die Handler von anderen Memberfunktionen unterschieden werden. Beachten Sie jedoch, dass diese Funktionen nicht tatsächlich virtuell sind; Sie werden stattdessen über Nachrichtenzuordnungen implementiert. Nachrichtenzuordnungen hängen ausschließlich von Standardpräprozessormakros ab, nicht von Erweiterungen der C++-Sprache. Das **Schlüsselwort afx_msg** wird nach der Vorverarbeitung in Leerzeichen aufgelöst.

Um einen in einer Basisklasse definierten Handler zu überschreiben, definieren Sie einfach eine Funktion mit demselben Prototyp in der abgeleiteten Klasse, und erstellen Sie einen Nachrichtenzuordnungseintrag für den Handler. Ihr Handler "überschreibt" jeden Handler mit demselben Namen in einer der Basisklassen Ihrer Klasse.

In einigen Fällen sollte der Handler den überschriebenen Handler in der Basisklasse aufrufen, damit die Basisklasse(en) und Windows mit der Nachricht arbeiten können. Wo Sie den Basisklassenhandler in Ihrer Außerkraftsetzung aufrufen, hängt von den Umständen ab. Manchmal müssen Sie den Basisklassenhandler zuerst und manchmal zuletzt aufrufen. Manchmal rufen Sie den Basisklassenhandler bedingt auf, wenn Sie die Nachricht nicht selbst verarbeiten möchten. Manchmal sollten Sie den Basisklassenhandler aufrufen und dann abhängig vom Wert oder Status, der vom Basisklassenhandler zurückgegeben wird, bedingt ihren eigenen Handlercode ausführen.

> [!CAUTION]
> Es ist nicht sicher, die Argumente zu ändern, die an einen Handler übergeben werden, wenn Sie beabsichtigen, sie an einen Basisklassenhandler zu übergeben. Sie könnten z. B. versucht sein, `OnChar` das *nChar-Argument* des Handlers zu ändern (z. B. um in Großbuchstaben zu konvertieren). Dieses Verhalten ist ziemlich undurchsichtig, aber wenn Sie `CWnd` diesen `SendMessage` Effekt ausführen müssen, verwenden Sie stattdessen die Memberfunktion.

Wie bestimmen Sie die richtige Methode zum Überschreiben einer bestimmten Nachricht Wenn der [Klassen-Assistent](reference/mfc-class-wizard.md) das Skelett der Handlerfunktion für eine bestimmte Nachricht schreibt , z. B. einen `OnCreate` Handler für **WM_CREATE**, skizziert er in Form der empfohlenen überschriebenen Memberfunktion. Im folgenden Beispiel wird empfohlen, dass der Handler zuerst den Basisklassenhandler aufruft und nur unter der Bedingung fortführt, dass er nicht -1 zurückgibt.

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

Gemäß der Konvention beginnen die Namen dieser Handler mit dem Präfix "Ein". Einige dieser Handler verwenden keine Argumente, während andere mehrere verwenden. Einige haben auch einen anderen Rückgabetyp als **void**. Die Standardhandler für alle **WM_** Nachrichten werden in der *MFC-Referenz* als Memberfunktionen der Klasse `CWnd` dokumentiert, deren Namen mit "Ein" beginnen. Den Memberfunktionsdeklarationen in `CWnd` sind **afx_msg**vorangestellt.

## <a name="see-also"></a>Siehe auch

[Deklarieren von Meldungshandlerfunktionen](../mfc/declaring-message-handler-functions.md)
