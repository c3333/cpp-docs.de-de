---
title: Zu Rohzeichenfolgenliteral konvertieren
ms.date: 11/16/2016
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
ms.openlocfilehash: 5636e00bfe8655d84fb2e4b64e0391324ab35d7d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171813"
---
# <a name="convert-to-raw-string-literal"></a>Zu Rohzeichenfolgenliteral konvertieren

**Zweck:** Umwandeln einer beliebigen Zeichenfolge in ein C++-Rohzeichenfolgenliteral.

**Anwendung:** Wenn Sie über eine Zeichenfolge mit Escapezeichen verfügen, die nicht als Escapezeichen verarbeitet werden sollen.

**Grund:** Sie könnten doppelte Escapezeichen verwenden, dies führt jedoch in den meisten Fällen zu verwirrenden und schwer lesbaren Zeichenfolgen.  Mithilfe von Rohzeichenfolgenliteralen sind Zeichenfolgen viel einfacher zu lesen.

**Anwendung:**

1. Platzieren Sie Ihren Text oder Mauszeiger auf der Escapezeichenfolge, die konvertiert werden soll.

   ![Markierter Code](images/stringliteral_highlight.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen, und klicken Sie im Kontextmenü auf **Zu Rohzeichenfolgenliteral konvertieren**.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**. Klicken Sie anschließend im Kontextmenü auf **Zu Rohzeichenfolgenliteral konvertieren**.
     * Klicken Sie auf das ![Glühbirnensymbol](images/bulb.png), das am linken Rand angezeigt wird, und klicken Sie im Kontextmenü auf **Zu Rohzeichenfolgenliteral konvertieren**.

1. Die Zeichen folge wird sofort in ein Rohzeichenfolgenliteral konvertiert.

   ![Rohzeichenfolgenliteral-Ergebnis](images/stringliteral_result.png)
