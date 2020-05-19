---
title: Erstellen isolierter C/C++-Anwendungen
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: fbb553e3514ac3c32ee1e1f276dcb3e43d3a192e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493341"
---
# <a name="building-cc-isolated-applications"></a>Erstellen isolierter C/C++-Anwendungen

Eine isolierte Anwendung ist nur von parallelen Assemblys abhängig und bindet über ein Manifest an ihre Abhängigkeiten. Ihre Anwendung muss nicht vollständig isoliert sein, damit sie unter Windows ordnungsgemäß ausgeführt wird. Wenn Sie jedoch in die vollständige Isolierung Ihrer Anwendung investieren, können Sie Zeit sparen, wenn Sie Ihre Anwendung in Zukunft warten müssen. Weitere Informationen über die Vorteile einer vollständigen Isolierung Ihrer Anwendung finden Sie unter [Isolierte Anwendungen](/windows/win32/SbsCs/isolated-applications).

Wenn Sie Ihre native C/C++-Anwendung mit Visual Studio erstellen, generiert das Visual Studio-Projektsystem standardmäßig eine Manifestdatei, die die Abhängigkeiten Ihrer Anwendung von Visual Studio-Bibliotheken beschreibt. Wenn dies die einzigen Abhängigkeiten der Anwendung sind, wird die Anwendung zu einer isolierten Anwendung, sobald sie mit Visual Studio neu erstellt wird. Wenn Ihre Anwendung zur Laufzeit andere Bibliotheken verwendet, müssen Sie diese Bibliotheken möglicherweise als parallele Assemblys neu erstellen, indem Sie die unter [Erstellen von parallelen C/C++-Assemblys](building-c-cpp-side-by-side-assemblies.md) beschriebenen Schritte ausführen.

## <a name="see-also"></a>Siehe auch

[Konzept der isolierten Anwendungen und der parallelen Assemblys](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Erstellen von isolierten Anwendungen und parallelen Assemblys (C/C++)](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
