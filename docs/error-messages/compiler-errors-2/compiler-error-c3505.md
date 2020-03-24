---
title: Compilerfehler C3505
ms.date: 11/04/2016
f1_keywords:
- C3505
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
ms.openlocfilehash: 0c67eb46208c35c1b11a74898107ad3c0e6e570d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200849"
---
# <a name="compiler-error-c3505"></a>Compilerfehler C3505

> die Typbibliothek "*GUID*" kann nicht geladen werden.

C3505 kann verursacht werden, wenn Sie den 32-Bit-, x86-gehosteten Cross-Compiler für 64-Bit x64-Ziele auf einem 64-Bit-Computer ausführen, da der Compiler unter WOW64 ausgeführt wird und nur aus der 32-Bit-Registrierungs Struktur gelesen werden kann.

Sie können diesen Fehler beheben, indem Sie sowohl 32-Bit-als auch 64-Bit-Versionen der Typbibliothek, die Sie importieren möchten, sowie beide registrieren.  Oder Sie können den systemeigenen 64-Bit-Compiler verwenden, bei dem Sie die Eigenschaft " **VC + +-Verzeichnisse** " in der IDE ändern müssen, um auf den 64-Bit-Compiler zu verweisen.

Weitere Informationen finden Sie unter

- [Vorgehensweise: Aktivieren eines 64-Bit-Visual C++-Toolsets auf der Befehlszeile](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)

- [Vorgehensweise: Konfigurieren von Visual C++-Projekten für 64-Bit-x64-Zielplattformen](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)
