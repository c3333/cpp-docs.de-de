---
title: C-Laufzeitfehler R6002
ms.date: 11/04/2016
f1_keywords:
- R6002
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
ms.openlocfilehash: b2e617b6f7841f1aa7e6fd2f6962c0e117fab6c8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197417"
---
# <a name="c-runtime-error-r6002"></a>C-Laufzeitfehler R6002

die Gleit Komma Unterstützung wurde nicht geladen.

Die erforderliche Gleit Komma Bibliothek wurde nicht verknüpft.

> [!NOTE]
> Wenn diese Fehlermeldung beim Ausführen einer App angezeigt wird, wurde die APP aufgrund eines internen Problems heruntergefahren. Es gibt mehrere mögliche Ursachen für diesen Fehler, aber häufig wird er durch einen Fehler im App-Code verursacht oder durch den Versuch, eine APP auszuführen, die nicht für den Prozessor des jeweiligen Computers erstellt wurde.
>
> Sie können versuchen, diesen Fehler zu beheben, indem Sie folgende Schritte ausführen:
>
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um das Programm zu reparieren oder neu zu installieren.
> - Überprüfen Sie **Windows Update** in der **Systemsteuerung** auf Software Updates.
> - Überprüfen Sie, ob eine aktualisierte Version der App angezeigt wird. Wenn das Problem weiterhin besteht, wenden Sie sich an den Anbieter der APP

**Informationen für Programmierer**

Dieser Fehler kann in der app auftreten, wenn die Gleit Komma Bibliothek nicht verknüpft war. Überprüfen Sie eine der folgenden Gründe:

- Eine Format Zeichenfolge für eine `printf_s`-oder `scanf_s`-Funktion enthielt eine Gleit Komma Format Spezifikation, und das Programm enthielt keine Gleit Komma Werte oder-Variablen. Um dieses Problem zu beheben, verwenden Sie ein Gleit Komma Argument, um der Gleit Komma Format Spezifikation zu entsprechen, oder führen Sie eine Gleit Komma Zuweisung an anderer Stelle im Programm aus. Dies bewirkt, dass die Gleit Komma Unterstützung geladen wird.

- Der Compiler minimiert die Größe eines Programms, indem die Gleit Komma Unterstützung nur bei Bedarf geladen wird. Der Compiler kann keine Gleit Komma Vorgänge oder Gleit Komma Formatspezifikationen in Format Zeichenfolgen erkennen, sodass er nicht die erforderlichen Gleit Komma Routinen lädt. Um dieses Problem zu beheben, verwenden Sie eine Gleit Komma Format Spezifikation, und geben Sie ein Gleit Komma Argument an, oder führen Sie eine Gleit Komma Zuweisung an anderer Stelle im Programm aus. Dies bewirkt, dass die Gleit Komma Unterstützung geladen wird.

- In einem Programm mit gemischter Sprache wurde eine C-Bibliothek vor einer Fortran-Bibliothek angegeben, als das Programm verknüpft war. Verknüpfen Sie die C-Bibliothek zuletzt, und geben Sie Sie an.
