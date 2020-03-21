---
title: Ausführen von Linux-Programmen unter Windows
ms.date: 07/31/2019
helpviewer_keywords:
- Linux [C++], porting to Win32
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
ms.openlocfilehash: 1c1807cee07db479a91f45e21434b3ba13be2ab6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076900"
---
# <a name="running-linux-programs-on-windows"></a>Ausführen von Linux-Programmen unter Windows

Sie haben folgende Möglichkeiten, wenn Sie ein Linux-Programm unter Windows ausführen möchten:

- Führen Sie das Programm unverändert auf dem Windows-Subsystem für Linux (WSL) aus. Im WSL wird Ihr Programm direkt auf der Computerhardware ausgeführt und nicht auf einem virtuellen Computer. Das WSL ermöglicht auch direkte Dateisystemaufrufe zwischen Windows- und Linux-Systemen, wodurch SSL-Datentransport überflüssig ist. Das WSL ist als Befehlszeilenumgebung konzipiert und wird für grafikintensive Anwendungen nicht empfohlen. Weitere Informationen finden Sie [in der Dokumentation für das Windows-Subsystem für Linux](/windows/wsl/about).
- Führen Sie das Programm wie gewohnt auf einem virtuellen Linux-Computer oder in einem Docker-Container aus, entweder auf Ihrem lokalen Computer oder in Azure. Weitere Informationen finden Sie unter [Virtuelle Computer](https://azure.microsoft.com/services/virtual-machines/) oder [Docker in Azure](https://docs.microsoft.com/azure/docker/).
- Kompilieren Sie das Programm mithilfe von gcc oder clang in den Umgebungen [MinGW](http://MinGW.org/) oder [MinGW-w64](https://MinGW-w64.org/doku.php). Dadurch wird eine Übersetzungsebene von Linux für Windows-Systemaufrufe bereitgestellt.
- Kompilieren Sie das Programm, und führen Sie es mithilfe von gcc oder clang in der [Cygwin](https://www.cygwin.com/)-Umgebung aus. So erhalten Sie im Vergleich zu MinGW oder MinGW-w64 eine vollständigere Linux-Umgebung.
- Portieren Sie Ihren Code manuell von Linux, und kompilieren Sie ihn mithilfe von Microsoft C++ (MSVC) für Windows. Dies umfasst das Umgestalten von plattformunabhängigem Code in separate Bibliotheken und das anschließende Neuschreiben des Linux-spezifischen Codes für die Verwendung des Windows-spezifischen Codes (z. B. Win32- oder DirectX-APIs). Dies ist wahrscheinlich die beste Option für Anwendungen, für die Hochleistungsgrafiken erforderlich sind.
