---
title: Projektbuildwarnung PRJ0049
ms.date: 11/04/2016
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
ms.openlocfilehash: e857a50215dc7516c0e2ec45a97638c76f40f43b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191747"
---
# <a name="project-build-warning-prj0049"></a>Projektbuildwarnung PRJ0049

Das referenzierte Ziel '\<Reference > ' erfordert .NET Framework \<MinFrameworkVersion > und kann im Ziel Framework des Projekts nicht ausgeführt werden.

Anwendungen, die mit Visual Studio 2008 erstellt wurden, können angeben, welche Version der .NET Framework, die Sie als Ziel verwenden sollten. Wenn Sie einen Verweis auf eine Assembly oder ein Projekt hinzufügen, die von einer Version der .NET Framework abhängig ist, die höher als die Zielversion ist, erhalten Sie diese Warnung zur Kompilierzeit.

### <a name="to-correct-this-warning"></a>So beheben Sie diese Warnung

1. Wählen Sie eine der folgenden Optionen aus:

   - Ändern Sie das Ziel Framework im Dialogfeld **Eigenschaften Seiten** des Projekts, sodass es später oder gleich der minimalen Frameworkversion aller Assemblys und Projekte ist, auf die verwiesen wird. Weitere Informationen finden Sie unter [Hinzufügen von verweisen](../../build/adding-references-in-visual-cpp-projects.md).

   - Entfernen Sie den Verweis auf die Assembly oder das Projekt mit einer minimalen Frameworkversion, die später als das Ziel Framework ist. Diese Elemente werden in den **Eigenschaften Seiten**des Projekts mit einem Warnsymbol gekennzeichnet.

## <a name="see-also"></a>Weitere Informationen

[Projektbuildfehler und -warnungen (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
