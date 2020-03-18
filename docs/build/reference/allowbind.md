---
title: /ALLOWBIND
ms.date: 11/04/2016
f1_keywords:
- /allowbind_bind
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
ms.openlocfilehash: 4f5b662223914cbb4970188595afb52cc2500cd4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440392"
---
# <a name="allowbind"></a>/ALLOWBIND

Gibt an, ob eine DLL gebunden werden kann.

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Bemerkungen

Mit der **/ALLOWBIND** -Option wird ein Bit im Header einer DLL festgelegt, das BIND. exe angibt, dass das Bild gebunden werden darf. Durch die Bindung kann ein Bild schneller geladen werden, wenn das Lade Modul für jede referenzierte DLL keine rebase-und Adress Korrektur durchführen muss. Sie möchten möglicherweise nicht, dass eine DLL gebunden wird, wenn Sie digital signiert wurde – die Bindung macht die Signatur ungültig. Die Bindung hat keine Auswirkung, wenn Address Space Layout Anordnung (ASLR) für das Image mithilfe von **/DynamicBase** auf Windows-Versionen, die ASLR unterstützen, aktiviert ist.

Verwenden Sie **/ALLOWBIND: No** , um zu verhindern, dass BIND. exe die dll bindet.

Weitere Informationen finden Sie unter der [/ALLOWBIND](allowbind-prevent-dll-binding.md) (Linkeroption).

## <a name="see-also"></a>Weitere Informationen

[EDITBIN-Optionen](editbin-options.md)
