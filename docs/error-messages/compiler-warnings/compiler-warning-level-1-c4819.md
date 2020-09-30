---
title: Compilerwarnung (Stufe 1) C4819
ms.date: 04/08/2019
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: f81a4f44a489e2e4c5bd5c063d922129581819f9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509362"
---
# <a name="compiler-warning-level-1-c4819"></a>Compilerwarnung (Stufe 1) C4819

> Die Datei enthält ein Zeichen, das in der aktuellen Codepage (*Number*) nicht dargestellt werden kann. Speichern Sie die Datei im Unicode-Format, um Datenverluste zu vermeiden.

C4819 tritt auf, wenn Sie eine ANSI-Quelldatei auf einem System mithilfe einer Codepage kompilieren, die nicht alle Zeichen in der Datei darstellen kann.

Es gibt mehrere Möglichkeiten, C4819 aufzulösen. Eine einfache Möglichkeit besteht darin, das angreifende Zeichen zu entfernen, wenn Sie es nicht benötigen, z. b. wenn es in einem Kommentar ist. Sie können die System Codepage in der Systemsteuerung auf eine festlegen, die den von Ihrem Quellcode verwendeten Zeichensatz unterstützt. Sie können Unicode-Escapesequenzen verwenden, um Zeichen oder Zeichen [folgen](../../c-language/escape-sequences.md) zu erstellen, die nur den Basis-ANSI-Zeichensatz in Ihrem Quellcode verwenden. Schließlich können Sie die Datei im Unicode-Format mit einer Signatur speichern, auch als Byte-Reihenfolge Markierung (BOM) bezeichnet.

Um eine Datei im Unicode-Format zu speichern, klicken Sie in Visual Studio auf **Datei**  >  **Speichern**unter. Wählen Sie im Dialogfeld **Datei speichern** unter die Dropdown Schaltfläche auf der Schaltfläche **Speichern** aus, und klicken Sie auf **mit Codierung speichern**. Wenn Sie den gleichen Dateinamen speichern, müssen Sie möglicherweise bestätigen, dass Sie die Datei ersetzen möchten. Wählen Sie im Dialogfeld **Erweiterte Speicheroptionen** eine Codierung aus, die alle Zeichen in der Datei darstellen kann – z. b. **Unicode (UTF-8 mit Signatur)-Codepage 65001**–, und wählen Sie dann **OK**aus.
