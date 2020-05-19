---
title: Manifestgenerierung für C/C++-Programme
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
ms.openlocfilehash: 16d5efc5c5f7ce81b4b60269b0c666fd5d24266e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492527"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>Manifestgenerierung für C/C++-Programme

Ein [Manifest](/windows/win32/sbscs/manifests) ist ein XML-Dokument, das entweder als externe XML-Datei oder als in eine Anwendung oder Assembly eingebettete Ressource vorliegt. Das Manifest einer [isolierten Anwendung](/windows/win32/SbsCs/isolated-applications) wird zur Verwaltung der Namen und Versionen freigegebener paralleler Assemblys verwendet, an die die Anwendung zur Runtime gebunden werden muss. Das Manifest einer parallelen Assembly gibt deren Abhängigkeiten von Namen, Versionen, Ressourcen und anderen Assemblys an.

Es gibt zwei Möglichkeiten, ein Manifest für eine isolierte Anwendung oder eine parallele Assembly zu erstellen. Zuerst kann der Ersteller der Assembly nach den Regeln und Benennungsanforderungen manuell eine Manifestdatei erstellen. Wenn ein Programm nur von Visual C++-Assemblys wie CRT, MFC, ATL oder anderen abhängig ist, kann ein Manifest alternativ auch automatisch vom Linker generiert werden.

Die Header von Visual C++-Bibliotheken enthalten Assemblyinformationen, und wenn die Bibliotheken im Anwendungscode enthalten sind, werden diese Assemblyinformationen vom Linker verwendet, um ein Manifest für die endgültige Binärdatei zu erstellen. Der Linker bettet die Manifestdatei nicht in die Binärdatei ein und kann das Manifest nur als externe Datei generieren. Die Verwendung eines Manifests als externe Datei funktioniert möglicherweise nicht in allen Szenarios. Es wird z. B. empfohlen, dass private Assemblys eingebettete Manifeste aufweisen. In Befehlszeilenbuilds wie beispielsweise solchen, die NMAKE zum Erstellen von Code verwenden, kann ein Manifest mit dem Manifesttool eingebettet werden. Weitere Informationen finden Sie unter [Manifestgenerierung über die Befehlszeile](manifest-generation-at-the-command-line.md). Beim Erstellen in Visual Studio kann ein Manifest eingebettet werden, indem eine Eigenschaft für das Manifesttool im Dialogfeld **Projekteigenschaften** festgelegt wird. Weitere Informationen finden Sie unter [Manifestgenerierung in Visual Studio](manifest-generation-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch

[Konzept der isolierten Anwendungen und der parallelen Assemblys](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Erstellen von isolierten Anwendungen und parallelen Assemblys (C/C++)](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
