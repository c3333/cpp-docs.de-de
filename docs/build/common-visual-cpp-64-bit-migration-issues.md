---
title: Häufig auftretende 64-Bit-Migrationsprobleme bei Visual C++
ms.date: 05/06/2019
helpviewer_keywords:
- 64-bit programming [C++], migration
- 64-bit compiler [C++], migration
- porting 32-bit code to 64-bit code
- migration [C++], 64-bit code issues
- 32-bit code porting [C++]
- 64-bit applications [C++]
- 64-bit compiler [C++], porting 32-bit code
- Win64 [C++]
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
ms.openlocfilehash: 68f4dc4276c5cbce687477ca25ec69f0cb544acb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229856"
---
# <a name="common-visual-c-64-bit-migration-issues"></a>Häufig auftretende 64-Bit-Migrationsprobleme bei Visual C++

Wenn Sie mit dem Microsoft Visual C++-Compiler (MSVC) Anwendungen erstellen, die unter einem 64-Bit-Windows-Betriebssystem ausgeführt werden sollen, sollten Sie folgende Probleme berücksichtigen:

- **`int`** und **`long`** sind unter 64-Bit-Windows-Betriebssystemen 32-Bit-Werte. Bei Programmen, die Sie für 64-Bit-Plattformen kompilieren möchten, sollten Sie darauf achten, keine Zeiger auf 32-Bit-Variablen zuzuweisen. Zeiger sind auf 64-Bit-Plattformen 64-Bit-Werte, und der Zeigerwert wird abgeschnitten, wenn Sie sie einer 32-Bit-Variable zuweisen.

- `size_t`, `time_t` und `ptrdiff_t` sind unter 64-Bit-Windows-Betriebssystemen 64-Bit-Werte.

- `time_t` ist ein 32-Bit-Wert unter 32-Bit-Windows-Betriebssystemen in Visual Studio 2005 und früheren Versionen. `time_t` ist jetzt standardmäßig eine 64-Bit-Ganzzahl. Weitere Informationen finden Sie unter [Zeitmanagement](../c-runtime-library/time-management.md).

   Sie müssen wissen, wo der Code einen **`int`** -Wert akzeptiert und als `size_t`- oder `time_t`-Wert verarbeitet. Die Zahl kann unter Umständen größer als eine 32-Bit-Zahl werden, und Daten werden abgeschnitten, wenn sie wieder an den **`int`** -Speicher übergeben werden.

Der %x-Modifzierer ( **`int`** -Hexadezimalformat) `printf` funktioniert unter einem 64-Bit-Windows-Betriebssystem nicht wie erwartet. Er funktioniert nur auf den ersten 32 Bits des Werts, der an ihn übergeben wird.

- Verwenden Sie %I32x, um einen 32-Bit-Ganzzahltyp im Hexadezimalformat anzuzeigen.

- Verwenden Sie %I64x, um einen 64-Bit-Ganzzahltyp im Hexadezimalformat anzuzeigen.

- %p (Hexadezimalformat für einen Zeiger) funktioniert unter einem 64-Bit-Windows-Betriebssystem wie erwartet.

Weitere Informationen finden Sie unter:

- [MSVC-Compileroptionen](reference/compiler-options.md)

- [Tipps zur Migration](/windows/win32/WinProg64/migration-tips)

## <a name="see-also"></a>Siehe auch

[Konfigurieren von C++-Projekten für 64-Bit-x64-Ziele](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Visual C++-Handbuch: Portieren und Aktualisieren](../porting/visual-cpp-porting-and-upgrading-guide.md)
