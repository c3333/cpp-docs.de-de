---
title: Intrinsische ARM64-Funktionen
description: Eine Liste der systeminternen ARM64-Funktionen, die vom Microsoft C++-Compiler unterstützt werden.
f1_keywords:
- __break
- __addx18byte
- __addx18word
- __addx18dword
- __addx18qword
- __cas8
- __cas16
- __cas32
- __cas64
- __casa8
- __casa16
- __casa32
- __casa64
- __casl8
- __casl16
- __casl32
- __casl64
- __casal8
- __casal16
- __casal32
- __casal64
- __crc32b
- __crc32h
- __crc32w
- __crc32d
- __crc32cb
- __crc32ch
- __crc32cw
- __crc32cd
- __getReg
- __getRegFp
- __getCallerReg
- __getCallerRegFp
- __hlt
- __incx18byte
- __incx18word
- __incx18dword
- __incx18qword
- __ldar8
- __ldar16
- __ldar32
- __ldar64
- __ldapr8
- __ldapr16
- __ldapr32
- __ldapr64
- __prefetch2
- __readx18byte
- __readx18word
- __readx18dword
- __readx18qword
- __setReg
- __setRegFp
- __setCallerReg
- __setCallerRegFp
- __stlr8
- __stlr16
- __stlr32
- __stlr64
- __swp8
- __swp16
- __swp32
- __swp64
- __swpa8
- __swpa16
- __swpa32
- __swpa64
- __swpl8
- __swpl16
- __swpl32
- __swpl64
- __swpal8
- __swpal16
- __swpal32
- __swpal64
- __sys
- __svc
- __writex18byte
- __writex18word
- __writex18dword
- __writex18qword
author: sigatrev
ms.author: magardn
ms.date: 11/14/2019
ms.openlocfilehash: 196518439445824ddf5a7a841b30eb816251ba60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368208"
---
# <a name="arm64-intrinsics"></a>Intrinsische ARM64-Funktionen

Der Microsoft C++-Compiler (MSVC) stellt die folgenden Systeminformationen für die ARM64-Architektur zur Verfügung. Weitere Informationen zu ARM finden Sie in den Abschnitten Architektur und Softwareentwicklungstools auf der [ARM Developer Documentation-Website.](https://developer.arm.com/docs)

## <a name="neon"></a><a name="top"></a>Neon

Die NEON-Vektoranweisungssatzerweiterungen für ARM64 bieten SIMD-Funktionen (Single Instruction Multiple Data). Sie ähneln denen in den MMX- und SSE-Vektor-Anweisungssätzen, die x86- und x64-Architekturprozessoren gemeinsam sind.

NEON-Intrinsics werden unterstützt, wie in der Headerdatei *arm64_neon.h*angegeben. Die MSVC-Unterstützung für NEON-Intrinsiden ähnelt der des ARM64-Compilers, der in der [ARM NEON Intrinsic Reference](https://static.docs.arm.com/ihi0073/c/IHI0073C_arm_neon_intrinsics_ref.pdf) auf der ARM Infocenter-Website dokumentiert ist.

## <a name="arm64-specific-intrinsics-listing"></a><a name="A"></a>ARM64-spezifische Intrinsidenliste

|Funktionsname|Anweisung|Funktionsprototyp|
|-------------------|-----------------|------------------------|
|__break|Brk|void __break(int)|
|__addx18byte||void __addx18byte(unsigniert lang, nicht signierter Zeichen)|
|__addx18word||void __addx18word(unsigniert lang, kurz signiert)|
|__addx18dword||void __addx18dword(unsigniert lang, unsigniert lang)|
|__addx18qword||void __addx18qword(nicht signiert lang, nicht signiert __int64)|
|__cas8|CASB|unsignierte __int8 __cas8(unsigniert __int8 flüchtig* _Target, __int8 _Comp ohne signiert, __int8 _Value nicht signiert)|
|__cas16|Geld|nicht signiert__int16 __cas16(unsigniert __int16 flüchtig* _Target, _Comp ohne __int16 signiert, __int16 _Value nicht signiert)|
|__cas32|CAS|unsigniert __int32 __cas32(unsigniert __int32 flüchtig* _Target, nicht signiert __int32 _Comp, nicht signiert __int32 _Value)|
|__cas64|CAS|unsignierte __int64 __cas64 (unsigniert __int64 flüchtig* _Target, unsigniert __int64 _Comp, __int64 _Value ohne signiert)|
|__casa8|CASAB|unsignierte __int8 __casa8(unsigniert __int8 flüchtig* _Target, unsigniert __int8 _Comp, nicht signiert __int8 _Value)|
|__casa16|CASAH|unsignierte __int16 __casa16 (unsigniert __int16 flüchtig* _Target, unsigniert __int16 _Comp, nicht signiert __int16 _Value)|
|__casa32|Casa|unsignierte __int32 __casa32 (unsigniert __int32 flüchtig* _Target, nicht signiert __int32 _Comp, unsigniert __int32 _Value)|
|__casa64|Casa|unsigniert__int64 __casa64 (unsigniert __int64 flüchtig* _Target, __int64 _Comp ohne signiert, nicht signiert __int64 _Value)|
|__casl8|CASLB|unsigniert__int8 __casl8(unsigniert __int8 flüchtig* _Target, __int8 _Comp ohne signiert, __int8 _Value)|
|__casl16|CASLH|unsignierte __int16 __casl16(unsigniert __int16 flüchtig* _Target, __int16 _Comp ohne Unterzeichnet, __int16 _Value nicht signiert)|
|__casl32|CASL|unsignierte __int32 __casl32 (unsigniert __int32 flüchtig* _Target, unsigniert __int32 _Comp, unsigniert __int32 _Value)|
|__casl64|CASL|unsignierte __int64 __casl64(unsigniert __int64 flüchtig* _Target, unsigniert __int64 _Comp, _Value ohne signierte __int64)|
|__casal8|CASALB|unsignierte __int8 __casal8 (unsigniert __int8 flüchtig* _Target, unsigniert __int8 _Comp, unsigniert __int8 _Value)|
|__casal16|CASALH|unsignierte __int16 __casal16(unsigniert __int16 flüchtig* _Target, __int16 _Comp ohne signiert, __int16 _Value nicht signiert)|
|__casal32|Casal|unsigniert__int32 __casal32(unsigniert __int32 flüchtig* _Target, nicht signiert __int32 _Comp, ohne signiert __int32 _Value)|
|__casal64|Casal|unsigniert __int64 __casal64(unsigniert __int64 flüchtig* _Target, unsigniert __int64 _Comp, unsigniert __int64 _Value)|
|__crc32b|CRC32B|nicht signiert__int32 __crc32b (nicht signiertes __int32, __int32 ohne signiert)|
|__crc32h|CRC32H|nicht signierte __int32 __crc32h (nicht signierte __int32, nicht signierte __int32)|
|__crc32w|CRC32W|unsigniert__int32 __crc32w (nicht signierte __int32, __int32 ohne signiert)|
|__crc32d|CRC32X|nicht signiert__int32 __crc32d (nicht signierte __int32, nicht signierte __int64)|
|__crc32cb|CRC32CB|unsigniert__int32 __crc32cb(nicht signierter __int32, __int32 ohne signiert)|
|__crc32ch|CRC32CH|nicht signiert__int32 __crc32ch(nicht signierte __int32, __int32 ohne signiert)|
|__crc32cw|CRC32CW|unsignierte __int32 __crc32cw(nicht signierte __int32, __int32 ohne signiert)|
|__crc32cd|CRC32CX|nicht signiert__int32 __crc32cd (nicht signierte __int32, __int64 nicht signiert)|
|__dmb|DMB|void __dmb(unsigned int `_Type`)<br /><br /> Fügt einen Speicherabgrenzungsvorgang in den Anweisungsstream ein. Der Parameter `_Type` gibt die Art der Einschränkung an, die die Grenze erzwingt.<br /><br /> Weitere Informationen zu den Arten von Einschränkungen, die erzwungen werden können, finden Sie unter [Speicherbarriereeinschränkungen](#BarrierRestrictions).|
|__dsb|DSB|void __dsb(unsigned int _Type)<br /><br /> Fügt einen Speicherabgrenzungsvorgang in den Anweisungsstream ein. Der Parameter `_Type` gibt die Art der Einschränkung an, die die Grenze erzwingt.<br /><br /> Weitere Informationen zu den Arten von Einschränkungen, die erzwungen werden können, finden Sie unter [Speicherbarriereeinschränkungen](#BarrierRestrictions).|
|__isb|ISB|void __isb(unsigned int _Type)<br /><br /> Fügt einen Speicherabgrenzungsvorgang in den Anweisungsstream ein. Der Parameter `_Type` gibt die Art der Einschränkung an, die die Grenze erzwingt.<br /><br /> Weitere Informationen zu den Arten von Einschränkungen, die erzwungen werden können, finden Sie unter [Speicherbarriereeinschränkungen](#BarrierRestrictions).|
|__getReg||unsigniert __int64 __getReg(int)|
|__getRegFp||Doppelte __getRegFp(int)|
|__getCallerReg||unsigniert__int64 __getCallerReg(int)|
|__getCallerRegFp||Doppelte __getCallerRegFp(int)|
|__hvc|HVC|unsigned int __hvc(unsigned int, ...)|
|__hlt|HLT|int __hlt(unsigniert int, ...)|
|__incx18byte||void __incx18byte(unsigniert lang)|
|__incx18word||void __incx18word(unsigniert lang)|
|__incx18dword||void __incx18dword(nicht lange signiert)|
|__incx18qword||void __incx18qword(unsigniert lang)|
|__iso_volatile_load16||__int16 \__iso_volatile_load16(const \_ \*volatile _int16 )<br /><br /> Weitere Informationen finden Sie unter [__iso_volatile_load/Speichern von intrinsischen Daten](#IsoVolatileLoadStore).|
|__iso_volatile_load32||__int32 \__iso_volatile_load32(const \_ \*volatile _int32 )<br /><br /> Weitere Informationen finden Sie unter [__iso_volatile_load/Speichern von intrinsischen Daten](#IsoVolatileLoadStore).|
|__iso_volatile_load64||__int64 \__iso_volatile_load64(const \_ \*volatile _int64 )<br /><br /> Weitere Informationen finden Sie unter [__iso_volatile_load/Speichern von intrinsischen Daten](#IsoVolatileLoadStore).|
|__iso_volatile_load8||__int8 \__iso_volatile_load8(const \_ \*volatile _int8 )<br /><br /> Weitere Informationen finden Sie unter [__iso_volatile_load/Speichern von intrinsischen Daten](#IsoVolatileLoadStore).|
|__iso_volatile_store16||void __iso_volatile_store16(flüchtige \__int16 \*, \__int16)<br /><br /> Weitere Informationen finden Sie unter [__iso_volatile_load/Speichern von intrinsischen Daten](#IsoVolatileLoadStore).|
|__iso_volatile_store32||void __iso_volatile_store32(flüchtige \__int32 \*, \__int32)<br /><br /> Weitere Informationen finden Sie unter [__iso_volatile_load/Speichern von intrinsischen Daten](#IsoVolatileLoadStore).|
|__iso_volatile_store64||void \___iso_volatile_store64(volatile \* \__int64 , _int64)<br /><br /> Weitere Informationen finden Sie unter [__iso_volatile_load/Speichern von intrinsischen Daten](#IsoVolatileLoadStore).|
|__iso_volatile_store8||void __iso_volatile_store8(flüchtige \__int8 \*, \__int8)<br /><br /> Weitere Informationen finden Sie unter [__iso_volatile_load/Speichern von intrinsischen Daten](#IsoVolatileLoadStore).|
|__ldar8|LDARB|nicht signiert__int8 __ldar8(unsigniert __int8 flüchtig* _Target)|
|__ldar16|LDARH|unsignierte __int16 __ldar16 (nicht signiert __int16 flüchtig* _Target)|
|__ldar32|LDAR|nicht signiert__int32 __ldar32 (nicht signiert __int32 flüchtig* _Target)|
|__ldar64|LDAR|unsignierte __int64 __ldar64(nicht signiert __int64 flüchtig* _Target)|
|__ldapr8|LDAPRB|nicht signierte __int8 __ldapr8 (nicht signiert __int8 flüchtig* _Target)|
|__ldapr16|LDAPRH|unsignierte __int16 __ldapr16(nicht signiert __int16 flüchtig* _Target)|
|__ldapr32|LDAPR|unsignierte __int32 __ldapr32(nicht signiert __int32 flüchtig* _Target)|
|__ldapr64|LDAPR|unsignierte __int64 __ldapr64(nicht signiert __int64 flüchtig* _Target)|
|__mulh||\__int64 __mulh(\_ \__int64, _int64)|
|__prefetch|PRFM|void \___cdecl _prefetch(const void \*)<br /><br /> Stellt `PRFM` dem System einen Speicherhinweis mit dem Prefetch-Vorgang `PLDL1KEEP` bereit, auf den der Speicher unter oder in der Nähe der angegebenen Adresse in Kürze zugreifen kann. Einige Systeme führen möglicherweise eine Optimierung für dieses Speicherzugriffsmuster aus, um die Leistung zur Laufzeit zu verbessern. Aus Sicht der C++-Sprache hat die Funktion jedoch keine sichtbaren Auswirkungen und hat möglicherweise gar keinen Nutzen.|
|__prefetch2|PRFM|void \___cdecl _prefetch(const void \*, uint8_t prfop)<br /><br /> Stellt `PRFM` dem System einen Speicherhinweis mit dem bereitgestellten Prefetch-Vorgang bereit, auf den der Speicher unter oder in der Nähe der angegebenen Adresse möglicherweise bald zugegriffen wird. Einige Systeme führen möglicherweise eine Optimierung für dieses Speicherzugriffsmuster aus, um die Leistung zur Laufzeit zu verbessern. Aus Sicht der C++-Sprache hat die Funktion jedoch keine sichtbaren Auswirkungen und hat möglicherweise gar keinen Nutzen.|
|__readx18byte||Unsigned char __readx18byte(unsigned long)|
|__readx18word||unsigniert kurz __readx18word(unsigniert lang)|
|__readx18dword||unsigniert lange __readx18dword(unsigniert lang)|
|__readx18qword||unsigniert__int64 __readx18qword(nicht signiert lang)|
|__setReg||void __setReg(int, __int64 nicht signiert)|
|__setRegFp||void __setRegFp(int, double)|
|__setCallerReg||void __setCallerReg(int, __int64 nicht signiert)|
|__setCallerRegFp||void __setCallerRegFp(int, double)|
|__sev|SEV|void __sev(void)|
|__static_assert||void __static_assert(int, \*const char )|
|__stlr8|STLRB|void __stlr8 (nicht signiert __int8 flüchtig* _Target, nicht signiert __int8 _Value)|
|__stlr16|STLRH|void __stlr16(nicht signiert __int16 flüchtig* _Target, __int16 _Value)|
|__stlr32|STLR|void __stlr32(unsigniert __int32 flüchtig* _Target, nicht signiert __int32 _Value)|
|__stlr64|STLR|void __stlr64(unsigniert __int64 flüchtig* _Target, __int64 _Value nicht signiert)|
|__swp8|SWPB|unsignierte __int8 __swp8 (unsigniert __int8 flüchtig* _Target, nicht signiert __int8 _Value)|
|__swp16|SWPH|unsignierte __int16 __swp16(nicht signiert __int16 flüchtig* _Target, __int16 _Value nicht signiert)|
|__swp32|SWP|unsigniert__int32 __swp32(nicht signiert __int32 flüchtig* _Target, __int32 _Value ohne Signiert)|
|__swp64|SWP|unsigniert__int64 __swp64(nicht signiert __int64 flüchtig* _Target, nicht signiert __int64 _Value)|
|__swpa8|SWPAB|unsignierte __int8 __swpa8(unsigniert __int8 flüchtig* _Target, __int8 _Value nicht signiert)|
|__swpa16|SWPAH|unsignierte __int16 __swpa16(nicht signiert __int16 flüchtig* _Target, nicht signiert __int16 _Value)|
|__swpa32|SWPA|nicht signiert__int32 __swpa32 (nicht signiert __int32 flüchtig* _Target, nicht signiert __int32 _Value)|
|__swpa64|SWPA|unsignierte __int64 __swpa64(nicht signiert __int64 flüchtig* _Target, nicht signiert __int64 _Value)|
|__swpl8|SWPLB|unsignierte __int8 __swpl8(nicht signiert __int8 flüchtig* _Target, nicht signiert __int8 _Value)|
|__swpl16|SWPLH|nicht signiert__int16 __swpl16 (nicht signiert __int16 flüchtig* _Target, nicht signiert __int16 _Value)|
|__swpl32|SWPL|unsigniert__int32 __swpl32(nicht signiert __int32 flüchtig* _Target, unsigniert __int32 _Value)|
|__swpl64|SWPL|unsignierte __int64 __swpl64(unsigniert __int64 flüchtig* _Target, nicht signiert __int64 _Value)|
|__swpal8|SWPALB|unsigniert__int8 __swpal8(unsigniert __int8 flüchtig* _Target, __int8 _Value ohne signiert)|
|__swpal16|SWPALH|nicht signierte __int16 __swpal16 (nicht signiert __int16 flüchtig* _Target, nicht signiert __int16 _Value)|
|__swpal32|SWPAL|nicht signiert__int32 __swpal32(nicht signiert __int32 flüchtig* _Target, nicht signiert __int32 _Value)|
|__swpal64|SWPAL|unsignierte __int64 __swpal64 (nicht signiert __int64 flüchtig* _Target, __int64 _Value ohne signiert)|
|__sys|Sys|unsigniert int __sys(int, __int64)|
|__svc|SVC|unsigniert int __svc(unsigniert int, ...)|
|__wfe|WFE|void __wfe(void)|
|__wfi|WFI|void __wfi(void)|
|__writex18byte||void __writex18byte(unsigniert lang, nicht signierter Zeichen)|
|__writex18word||void __writex18word(unsigniert lang, kurz signiert)|
|__writex18dword||void __writex18dword(unsigniert lang, unsigniert lang)|
|__writex18qword||void __writex18qword(nicht signiert lange, nicht signierte __int64)|
|__umulh||nicht \_signierte _int64 \___umulh (nicht \_signierte _int64, _int64 nicht signiert)|
|_CopyDoubleFromInt64||Doppelte _CopyDoubleFromInt64(\__int64)|
|_CopyFloatFromInt32||float _CopyFloatFromInt32(\__int32)|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat(float)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble(double)|
|_CountLeadingOnes||unsigned int _CountLeadingOnes(unsigned long)|
|_CountLeadingOnes64||nicht signiert int _CountLeadingOnes64 \_(nicht signierte _int64)|
|_CountLeadingSigns||unsigned int _CountLeadingSigns(long)|
|_CountLeadingSigns64||nicht signiert int\__CountLeadingSigns64( _int64)|
|_CountLeadingZeros||unsigned int _CountLeadingZeros(unsigned long)|
|_CountLeadingZeros64||nicht signiert int _CountLeadingZeros64 \_(nicht signiert_int64)|
|_ReadStatusReg|MRS|\__int64 _ReadStatusReg(int)|
|_WriteStatusReg|MSR|void _WriteStatusReg(int, \__int64)|

[[Zurück nach oben](#top)]

### <a name="memory-barrier-restrictions"></a><a name="BarrierRestrictions"></a>Speicherbarriereeinschränkungen

Die intrinsischen `__dmb` `__dsb` Funktionen (Datenspeicherbarriere), (Datensynchronisierungsbarriere) und `__isb` (Anweisungssynchronisierungsbarriere) verwenden die folgenden vordefinierten Werte, um die Speicherbarriereeinschränkung in Bezug auf die Freigabedomäne und die Art des Zugriffs anzugeben, die von dem Vorgang betroffen sind.

|Einschränkungswert|BESCHREIBUNG|
|-----------------------|-----------------|
|_ARM64_BARRIER_SY|Gesamtes System, Lese- und Schreibvorgänge.|
|_ARM64_BARRIER_ST|Gesamtes System, nur Schreibvorgänge.|
|_ARM64_BARRIER_LD|Vollständiges System, schreibgeschützt.|
|_ARM64_BARRIER_ISH|Innen teilbar, Lese- und Schreibvorgänge.|
|_ARM64_BARRIER_ISHST|Innen teilbar, nur Schreibvorgänge.|
|_ARM64_BARRIER_ISHLD|Inner sharable, nur lesen.|
|_ARM64_BARRIER_NSH|Nicht teilbar, Lese- und Schreibvorgänge.|
|_ARM64_BARRIER_NSHST|Nicht teilbar, nur Schreibvorgänge.|
|_ARM64_BARRIER_NSHLD|Nicht sharable, nur lesen.|
|_ARM64_BARRIER_OSH|Außen teilbar, Lese- und Schreibvorgänge.|
|_ARM64_BARRIER_OSHST|Außen teilbar, nur Schreibvorgänge.|
|_ARM64_BARRIER_OSHLD|Äußere sharable, nur lesen.|

Für `__isb` das System ist die einzige Einschränkung, die derzeit gültig ist, _ARM64_BARRIER_SY; Alle anderen Werte werden von der Architektur reserviert.

### <a name="__iso_volatile_loadstore-intrinsics"></a><a name="IsoVolatileLoadStore"></a>__iso_volatile_load/Speichern von Intrinsiden

Diese systeminternen Funktionen führen explizit Lasten und Speicher aus, die keinen Compileroptimierungen unterliegen.

```C
__int16 __iso_volatile_load16(const volatile __int16 * Location);
__int32 __iso_volatile_load32(const volatile __int32 * Location);
__int64 __iso_volatile_load64(const volatile __int64 * Location);
__int8 __iso_volatile_load8(const volatile __int8 * Location);

void __iso_volatile_store16(volatile __int16 * Location, __int16 Value);
void __iso_volatile_store32(volatile __int32 * Location, __int32 Value);
void __iso_volatile_store64(volatile __int64 * Location, __int64 Value);
void __iso_volatile_store8(volatile __int8 * Location, __int8 Value);
```

#### <a name="parameters"></a>Parameter

*Lage*\
Die Adresse eines Speicherbereichs für Lese- oder Schreibvorgänge.

*Wert*\
Der Wert, der in den angegebenen Speicherort geschrieben werden soll (nur systeminterne Speicherfunktionen).

#### <a name="return-value-load-intrinsics-only"></a>Rückgabewert (nur intrinsische Lasten)

Der Wert des Speicherspeicherorts, der durch *Location*angegeben wird.

#### <a name="remarks"></a>Bemerkungen

Sie können `__iso_volatile_load8/16/32/64` die `__iso_volatile_store8/16/32/64` und die systeminternen verwenden, um explizit Speicherzugriffe auszuführen, die nicht Compileroptimierungen unterliegen. Der Compiler kann die relative Reihenfolge dieser Vorgänge nicht entfernen, synthetisieren oder ändern. Es werden jedoch keine impliziten Hardwarespeicherbarrieren generiert. Aus diesem Grund kann die Hardware die sichtbaren Speicherzugriffe möglicherweise immer noch über mehrere Threads hinweg neu anordnen. Genauer gesagt entsprechen diese intrinsischen Komponenten den folgenden Ausdrücken, wie sie unter **/volatile:iso**kompiliert wurden.

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

Beachten Sie, dass die systeminternen Funktionen flüchtige Zeiger verwenden, um flüchtige Variablen zu berücksichtigen. Es gibt jedoch keine Anforderung oder Empfehlung, flüchtige Zeiger als Argumente zu verwenden. Die Semantik dieser Vorgänge ist genau die gleiche, wenn ein regulärer, nicht flüchtiger Typ verwendet wird.

Weitere Informationen zum Befehlszeilenargument **/volatile:iso** finden Sie unter [/volatile (volatile keyword interpretation)](../build/reference/volatile-volatile-keyword-interpretation.md).

## <a name="arm64-support-for-intrinsics-from-other-architectures"></a><a name="I"></a>ARM64-Unterstützung für intrinsische Komponenten aus anderen Architekturen

In der folgenden Tabelle sind systeminterne Komponenten anderer Architekturen aufgeführt, die auf ARM64-Plattformen unterstützt werden. Wenn sich das Verhalten eines intrinsischen AUF ARM64 von seinem Verhalten auf anderen Hardwarearchitekturen unterscheidet, werden zusätzliche Details angegeben.

|Funktionsname|Funktionsprototyp|
|-------------------|------------------------|
|__assume|void __assume(int)|
|__code_seg|void __code_seg(const \*char )|
|__debugbreak|void \___cdecl _debugbreak(void)|
|__fastfail|__declspec(noreturn) \_void _fastfail(unsigned int)|
|__nop|void __nop(void)|
|__yield|void __yield(void) **Hinweis:** Auf ARM64-Plattformen generiert diese Funktion die YIELD-Anweisung. Diese Anweisung gibt an, dass der Thread eine Aufgabe ausführt, die vorübergehend von der Ausführung angehalten werden kann, z. B. ein Spinlock, ohne das Programm zu beeinträchtigen. Es ermöglicht der CPU, andere Aufgaben während Der Ausführungszyklen auszuführen, die andernfalls verschwendet würden.|
|_AddressOfReturnAddress|void \* _AddressOfReturnAddress(void)|
|_BitScanForward|unsignierte _BitScanForward (nicht \* signiert lange _Index, nicht signiert lange _Mask)|
|_BitScanForward64|unsignierte _BitScanForward64 (nicht \* signiert lange _Index, nicht signiert__int64 _Mask)|
|_BitScanReverse|unsignierte _BitScanReverse (nicht \* signiert lange _Index, nicht signiert lange _Mask)|
|_BitScanReverse64|nicht signierte zeichen _BitScanReverse64 \* (nicht signiert lange _Index, unsigniert __int64 _Mask)|
|_bittest|unsignierte zeichen _bittest(long const \*, long)|
|_bittest64|unsignierte _bittest64(__int64 \*const , __int64)|
|_bittestandcomplement|unsignierte zeichen \*_bittestandcomplement(lang , lang)|
|_bittestandcomplement64|unsignierte _bittestandcomplement64(__int64 \*, __int64)|
|_bittestandreset|unsignierte Zeichen \*_bittestandreset(lang , lang)|
|_bittestandreset64|nicht signierte _bittestandreset64(__int64 \*, __int64)|
|_bittestandset|unsignierte Zeichen \*_bittestandset(lang , lang)|
|_bittestandset64|unsignierte zeichen \*_bittestandset64(__int64 , __int64)|
|_byteswap_uint64|unsigniert__int64 \__cdecl _byteswap_uint64 \__byteswap_uint64(nicht signiertes _int64)|
|_byteswap_ulong|unsigned long __cdecl _byteswap_ulong(unsigned long)|
|_byteswap_ushort|unsigned short __cdecl _byteswap_ushort(unsigned short)|
|_disable|void __cdecl _disable(void) **Hinweis:** Auf ARM64-Plattformen `MSR DAIFCLR,#2`generiert diese Funktion die Anweisung ; es ist nur als intrinsisch verfügbar.|
|_enable|void __cdecl _enable(void) **Hinweis:** Auf ARM64-Plattformen `MSR DAIFSET,#2`generiert diese Funktion die Anweisung ; es ist nur als intrinsisch verfügbar.|
|_lrotl|unsigned long __cdecl _lrotl(unsigned long, int)|
|_lrotr|unsigned long __cdecl _lrotr(unsigned long, int)|
|_ReadBarrier|void _ReadBarrier(void)|
|_ReadWriteBarrier|void _ReadWriteBarrier(void)|
|_ReturnAddress|void \* _ReturnAddress(void)|
|_rotl|unsigned int __cdecl _rotl(unsigned int _Value, int _Shift)|
|_rotl16|unsigned short _rotl16(unsigned short _Value, unsigned char _Shift)|
|_rotl64|nicht signiert__int64 \__cdecl _rotl64(nicht signiert_int64 \__Value, int _Shift)|
|_rotl8|unsigned char _rotl8(unsigned char _Value, unsigned char _Shift)|
|_rotr|unsigned int __cdecl _rotr(unsigned int _Value, int _Shift)|
|_rotr16|unsigned short _rotr16(unsigned short _Value, unsigned char _Shift)|
|_rotr64|unsignierte \___int64 _cdecl \__rotr64 (nicht signiert _int64 _Value, int _Shift)|
|_rotr8|unsigned char _rotr8(unsigned char _Value, unsigned char _Shift)|
|_setjmpex|int __cdecl _setjmpex(jmp_buf)|
|_WriteBarrier|void _WriteBarrier(void)|

[[Zurück nach oben](#top)]

## <a name="interlocked-intrinsics"></a>Ineinverriegelte Intrinsiden

Ineinandergreifende systeminterne Funktionen sind eine Reihe von systeminternen Funktionen, die zum Ausführen atomarer Lese-Änderungs-Schreib-Vorgänge verwendet werden. Einige davon sind auf allen Plattformen verfügbar. Sie sind hier separat aufgeführt, da es eine große Anzahl von ihnen gibt. Da ihre Definitionen meist redundant sind, ist es einfacher, darüber allgemein nachzudenken. Die genauen Verhaltensweisen können von den Namen abgeleitet werden.

Die folgende Tabelle fasst die ARM64-Unterstützung der nicht-bittersten ineinandergreifenden intrinsischen Komponenten zusammen. Jede Zelle in der Tabelle entspricht einem Namen, der durch Anhängen des Vorgangsnamens in der am weitesten links befindlichen Zelle der Zeile und des Typnamens in der obersten Zelle der Spalte an `_Interlocked` abgeleitet wird. Beispielsweise entspricht die Zelle am `Xor` Schnittpunkt `8` der Zeile `_InterlockedXor8` und der Spalte und wird vollständig unterstützt. Die meisten unterstützten Funktionen bieten diese optionalen Suffixe: `_acq`, `_rel` und `_nf`. Das `_acq`-Suffix gibt eine „Acquire“-Semantik zum Abrufen an, und das `_rel`-Suffix gibt eine „Release“-Semantik zum Freigeben an. Das `_nf` Suffix "kein Zaun" ist für ARM und ARM64 einzigartig und wird im nächsten Abschnitt erläutert.

||8|16|32|64|128|P|
|-|-------|--------|--------|--------|-------|-------|
|Hinzufügen|Keine|Keine|Vollständig|Vollständig|Keine|Keine|
|And|Vollständig|Vollständig|Vollständig|Vollständig|Keine|Keine|
|CompareExchange|Vollständig|Vollständig|Vollständig|Vollständig|Vollständig|Vollständig|
|Dekrement|Keine|Vollständig|Vollständig|Vollständig|Keine|Keine|
|Exchange|Vollständig|Vollständig|Vollständig|Vollständig|Keine|Vollständig|
|ExchangeAdd|Vollständig|Vollständig|Vollständig|Vollständig|Keine|Keine|
|Increment|Keine|Vollständig|Vollständig|Vollständig|Keine|Keine|
|oder|Vollständig|Vollständig|Vollständig|Vollständig|Keine|Keine|
|Xor|Vollständig|Vollständig|Vollständig|Vollständig|Keine|Keine|

Schlüssel:

- **Vollständig**: unterstützt `_acq` `_rel`einfache, `_nf` , , und Formen.

- **Keine**: Wird nicht unterstützt

### <a name="_nf-no-fence-suffix"></a><a name="nf_suffix"></a>_nf (kein Zaun) Suffix

Das `_nf` Suffix "kein Zaun" gibt an, dass sich der Vorgang nicht als Speicherbarriere verhält, `_acq`im `_rel`Gegensatz zu den anderen drei Formen (einfach, und ), die sich alle als eine Art Barriere verhalten. Eine mögliche Verwendung `_nf` der Formulare besteht darin, einen Statistikzähler beizubehalten, der von mehreren Threads gleichzeitig aktualisiert wird, dessen Wert jedoch andernfalls nicht verwendet wird, während mehrere Threads ausgeführt werden.

### <a name="list-of-interlocked-intrinsics"></a>Liste der ineinandergreifenden Intrinsiden

|Funktionsname|Funktionsprototyp|
|-------------------|------------------------|
|_InterlockedAdd|lange _InterlockedAdd(lang \*_volatile , lang)|
|_InterlockedAdd64|__int64 _InterlockedAdd64(\_ \*_int64 \_flüchtig , _int64)|
|_InterlockedAdd64_acq|__int64 _InterlockedAdd64_acq(\_ \*_int64 \_volatil , _int64)|
|_InterlockedAdd64_nf|__int64 _InterlockedAdd64_nf(\_ \*_int64 \_flüchtig , _int64)|
|_InterlockedAdd64_rel|__int64 _InterlockedAdd64_rel(\_ \*_int64 \_flüchtig , _int64)|
|_InterlockedAdd_acq|lange _InterlockedAdd_acq(lang \*flüchtig, lang)|
|_InterlockedAdd_nf|lange _InterlockedAdd_nf(lang \*flüchtig, lang)|
|_InterlockedAdd_rel|lange _InterlockedAdd_rel(lang \*flüchtig, lang)|
|_InterlockedAnd|lange _InterlockedAnd(lang \*flüchtig, lang)|
|_InterlockedAnd16|kurze _InterlockedAnd16(kurz \*flüchtig, kurz)|
|_InterlockedAnd16_acq|kurze _InterlockedAnd16_acq(kurz \*flüchtig, kurz)|
|_InterlockedAnd16_nf|kurze _InterlockedAnd16_nf(kurz \*flüchtig, kurz)|
|_InterlockedAnd16_rel|kurze _InterlockedAnd16_rel(kurz \*flüchtig, kurz)|
|_InterlockedAnd64|__int64 _InterlockedAnd64(\_ \*_int64 \_flüchtig , _int64)|
|_InterlockedAnd64_acq|__int64 _InterlockedAnd64_acq(\_ \*_int64 \_flüchtig , _int64)|
|_InterlockedAnd64_nf|__int64 _InterlockedAnd64_nf(\_ \*_int64 \_flüchtig , _int64)|
|_InterlockedAnd64_rel|__int64 _InterlockedAnd64_rel(\_ \*_int64 \_flüchtig , _int64)|
|_InterlockedAnd8|char _InterlockedAnd8(char \*volatile , char)|
|_InterlockedAnd8_acq|char _InterlockedAnd8_acq(char \*volatile , char)|
|_InterlockedAnd8_nf|char _InterlockedAnd8_nf(char \*volatile , char)|
|_InterlockedAnd8_rel|char _InterlockedAnd8_rel(char \*volatile , char)|
|_InterlockedAnd_acq|lange _InterlockedAnd_acq(lang \*flüchtig, lang)|
|_InterlockedAnd_nf|lange _InterlockedAnd_nf(lang \*flüchtig, lang)|
|_InterlockedAnd_rel|lange _InterlockedAnd_rel(lang \*flüchtig, lang)|
|_InterlockedCompareExchange|lange __cdecl _InterlockedCompareExchange(lang flüchtig, \*lang, lang)|
|_InterlockedCompareExchange_acq|lange _InterlockedCompareExchange_acq (lang flüchtig, \*lang, lang)|
|_InterlockedCompareExchange_nf|lange _InterlockedCompareExchange_nf (lang flüchtig, \*lang, lang)|
|_InterlockedCompareExchange_rel|lange _InterlockedCompareExchange_rel (lang flüchtig, \*lang, lang)|
|_InterlockedCompareExchange16|kurze _InterlockedCompareExchange16(kurz \*flüchtig, kurz, kurz)|
|_InterlockedCompareExchange16_acq|kurze _InterlockedCompareExchange16_acq(kurz \*flüchtig, kurz, kurz)|
|_InterlockedCompareExchange16_nf|kurze _InterlockedCompareExchange16_nf(kurz \*flüchtig, kurz, kurz)|
|_InterlockedCompareExchange16_rel|kurze _InterlockedCompareExchange16_rel(kurz \*flüchtig, kurz, kurz)|
|_InterlockedCompareExchange64|\___int64 _InterlockedCompareExchange64( \*_int64 \_flüchtig \_, _int64, _int64)|
|_InterlockedCompareExchange64_acq|\___int64 _InterlockedCompareExchange64_acq( \*_int64 \_volatile \_, _int64, _int64)|
|_InterlockedCompareExchange64_nf|\___int64 _InterlockedCompareExchange64_nf( \*_int64 \_flüchtig \_, _int64, _int64)|
|_InterlockedCompareExchange64_rel|\___int64 _InterlockedCompareExchange64_rel( \*_int64 \_flüchtig \_, _int64, _int64)|
|_InterlockedCompareExchange8|char _InterlockedCompareExchange8(char \*volatile , char, char)|
|_InterlockedCompareExchange8_acq|char _InterlockedCompareExchange8_acq(char \*volatile , char, char)|
|_InterlockedCompareExchange8_nf|char _InterlockedCompareExchange8_nf(char \*volatile , char, char)|
|_InterlockedCompareExchange8_rel|char _InterlockedCompareExchange8_rel(char \*volatile , char, char)|
|_InterlockedCompareExchangePointer|void \* \* _InterlockedCompareExchangePointer(void \*volatile \*, \*void , void )|
|_InterlockedCompareExchangePointer_acq|void \* \* _InterlockedCompareExchangePointer_acq(void \*volatile \*, \*void , void )|
|_InterlockedCompareExchangePointer_nf|void \* \* _InterlockedCompareExchangePointer_nf(void \*volatile \*, \*void , void )|
|_InterlockedCompareExchangePointer_rel|void \* \* _InterlockedCompareExchangePointer_rel(void \*volatile \*, \*void , void )|
|_InterlockedCompareExchange128|unsigned char\__InterlockedCompareExchange128( \* _int64 \_flüchtige \__Destination, \_ \* _int64 _ExchangeHigh, _int64 _ExchangeLow, _int64 _ComparandResult)|
|_InterlockedCompareExchange128_acq|unsigned char\__InterlockedCompareExchange128_acq( \* _int64 \_flüchtige \__Destination, \_ \* _int64 _ExchangeHigh, _int64 _int64 _ExchangeLow _int64 _ComparandResult)|
|_InterlockedCompareExchange128_nf|nicht signierte\_zeichen \* _InterlockedCompareExchange128_nf(_int64 \_flüchtige _Destination, _int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_rel|unsigned char\__InterlockedCompareExchange128_rel( \* _int64 \_flüchtige \__Destination, \_ \* _int64 _ExchangeHigh, _ExchangeLow _int64 _int64 _ComparandResult)|
|_InterlockedDecrement|lange __cdecl _InterlockedDecrement(lang flüchtig \*)|
|_InterlockedDecrement16|kurze _InterlockedDecrement16(kurz \*flüchtig )|
|_InterlockedDecrement16_acq|kurze _InterlockedDecrement16_acq(kurz \*flüchtig )|
|_InterlockedDecrement16_nf|kurze _InterlockedDecrement16_nf(kurz \*flüchtig )|
|_InterlockedDecrement16_rel|kurze _InterlockedDecrement16_rel(kurz \*flüchtig )|
|_InterlockedDecrement64|__int64 _InterlockedDecrement64\_( \*_int64 flüchtig )|
|_InterlockedDecrement64_acq|__int64 _InterlockedDecrement64_acq\_( \*_int64 flüchtig )|
|_InterlockedDecrement64_nf|__int64 _InterlockedDecrement64_nf\_( \*_int64 flüchtig )|
|_InterlockedDecrement64_rel|__int64 _InterlockedDecrement64_rel\_( \*_int64 flüchtig )|
|_InterlockedDecrement_acq|lange _InterlockedDecrement_acq(lang \*flüchtig )|
|_InterlockedDecrement_nf|lange _InterlockedDecrement_nf(lang \*flüchtig )|
|_InterlockedDecrement_rel|lange _InterlockedDecrement_rel(lang \*flüchtig )|
|_InterlockedExchange|lange __cdecl _InterlockedExchange(lang flüchtige \* _Target, lang)|
|_InterlockedExchange_acq|lange _InterlockedExchange_acq (lange flüchtige \* _Target, lang)|
|_InterlockedExchange_nf|lange _InterlockedExchange_nf (lange flüchtige \* _Target, lang)|
|_InterlockedExchange_rel|lange _InterlockedExchange_rel (lange flüchtige \* _Target, lang)|
|_InterlockedExchange16|kurze _InterlockedExchange16 (kurze flüchtige \* _Target, kurz)|
|_InterlockedExchange16_acq|kurze _InterlockedExchange16_acq (kurze flüchtige \* _Target, kurz)|
|_InterlockedExchange16_nf|kurze _InterlockedExchange16_nf(kurze \* flüchtige _Target, kurz)|
|_InterlockedExchange16_rel|kurze _InterlockedExchange16_rel (kurze flüchtige \* _Target, kurz)|
|_InterlockedExchange64|__int64 _InterlockedExchange64(\_ \* _int64 \_volatile _Target, _int64)|
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq(\_ \* _int64 \_flüchtige _Target, _int64)|
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf(\_ \* _int64 \_flüchtige _Target, _int64)|
|_InterlockedExchange64_rel|__int64\__InterlockedExchange64_rel(_int64 \* volatile_Target, \__int64)|
|_InterlockedExchange8|char _InterlockedExchange8(char \* volatile _Target, char)|
|_InterlockedExchange8_acq|char _InterlockedExchange8_acq(char \* volatile _Target, char)|
|_InterlockedExchange8_nf|char _InterlockedExchange8_nf(char \* volatile _Target, char)|
|_InterlockedExchange8_rel|char _InterlockedExchange8_rel(char \* volatile _Target, char)|
|_InterlockedExchangeAdd|lange __cdecl _InterlockedExchangeAdd(lang flüchtig, \*lang)|
|_InterlockedExchangeAdd16|kurze _InterlockedExchangeAdd16(kurz \*flüchtig, kurz)|
|_InterlockedExchangeAdd16_acq|kurze _InterlockedExchangeAdd16_acq(kurz \*flüchtig, kurz)|
|_InterlockedExchangeAdd16_nf|kurze _InterlockedExchangeAdd16_nf(kurz \*flüchtig, kurz)|
|_InterlockedExchangeAdd16_rel|kurze _InterlockedExchangeAdd16_rel(kurz \*flüchtig, kurz)|
|_InterlockedExchangeAdd64|__int64 _InterlockedExchangeAdd64(\_ \*_int64 \_flüchtig , _int64)|
|_InterlockedExchangeAdd64_acq|__int64 _InterlockedExchangeAdd64_acq\_( \* \__int64 flüchtig , _int64)|
|_InterlockedExchangeAdd64_nf|__int64 _InterlockedExchangeAdd64_nf(\_ \*_int64 \_volatil , _int64)|
|_InterlockedExchangeAdd64_rel|__int64\__InterlockedExchangeAdd64_rel(_int64 \* \_flüchtig , _int64)|
|_InterlockedExchangeAdd8|char _InterlockedExchangeAdd8(char \*volatile , char)|
|_InterlockedExchangeAdd8_acq|char _InterlockedExchangeAdd8_acq(char \*volatile , char)|
|_InterlockedExchangeAdd8_nf|char _InterlockedExchangeAdd8_nf(char \*volatile , char)|
|_InterlockedExchangeAdd8_rel|char _InterlockedExchangeAdd8_rel(char \*volatile , char)|
|_InterlockedExchangeAdd_acq|lange _InterlockedExchangeAdd_acq(lang \*flüchtig, lang)|
|_InterlockedExchangeAdd_nf|lange _InterlockedExchangeAdd_nf(lang \*flüchtig, lang)|
|_InterlockedExchangeAdd_rel|lange _InterlockedExchangeAdd_rel(lang \*flüchtig, lang)|
|_InterlockedExchangePointer|void \* \* _InterlockedExchangePointer(void \* volatile \*_Target, void )|
|_InterlockedExchangePointer_acq|void \* \* _InterlockedExchangePointer_acq(void \* volatile \*_Target, void )|
|_InterlockedExchangePointer_nf|void \* \* _InterlockedExchangePointer_nf(void \* volatile \*_Target, void )|
|_InterlockedExchangePointer_rel|void \* \* _InterlockedExchangePointer_rel(void \* volatile \*_Target, void )|
|_InterlockedIncrement|lange __cdecl _InterlockedIncrement(lang flüchtig \*)|
|_InterlockedIncrement16|kurze _InterlockedIncrement16(kurz \*flüchtig )|
|_InterlockedIncrement16_acq|kurze _InterlockedIncrement16_acq(kurz \*flüchtig )|
|_InterlockedIncrement16_nf|kurze _InterlockedIncrement16_nf(kurz \*flüchtig )|
|_InterlockedIncrement16_rel|kurze _InterlockedIncrement16_rel(kurz \*flüchtig )|
|_InterlockedIncrement64|__int64 _InterlockedIncrement64\_( \*_int64 flüchtig )|
|_InterlockedIncrement64_acq|__int64 _InterlockedIncrement64_acq(\_ \*_int64 flüchtig )|
|_InterlockedIncrement64_nf|__int64 _InterlockedIncrement64_nf\_( \*_int64 flüchtig )|
|_InterlockedIncrement64_rel|__int64 _InterlockedIncrement64_rel\_( \*_int64 flüchtig )|
|_InterlockedIncrement_acq|lange _InterlockedIncrement_acq(lang \*flüchtig )|
|_InterlockedIncrement_nf|lange _InterlockedIncrement_nf(lang \*flüchtig )|
|_InterlockedIncrement_rel|lange _InterlockedIncrement_rel(lang \*flüchtig )|
|_InterlockedOr|lange _InterlockedOr(lang \*flüchtig, lang)|
|_InterlockedOr16|kurze _InterlockedOr16(kurz \*flüchtig, kurz)|
|_InterlockedOr16_acq|kurze _InterlockedOr16_acq(kurz \*flüchtig, kurz)|
|_InterlockedOr16_nf|kurze _InterlockedOr16_nf(kurz \*flüchtig, kurz)|
|_InterlockedOr16_rel|kurze _InterlockedOr16_rel(kurz \*flüchtig, kurz)|
|_InterlockedOr64|__int64 _InterlockedOr64(\_ \*_int64 \_flüchtig , _int64)|
|_InterlockedOr64_acq|__int64 _InterlockedOr64_acq(\_ \*_int64 \_flüchtig , _int64)|
|_InterlockedOr64_nf|__int64 _InterlockedOr64_nf\_(_int64 flüchtig \*, \__int64)|
|_InterlockedOr64_rel|__int64 _InterlockedOr64_rel\_( \* \__int64 flüchtig , _int64)|
|_InterlockedOr8|char _InterlockedOr8(char \*volatile , char)|
|_InterlockedOr8_acq|char _InterlockedOr8_acq(char \*volatile , char)|
|_InterlockedOr8_nf|char _InterlockedOr8_nf(char \*volatile , char)|
|_InterlockedOr8_rel|char _InterlockedOr8_rel(char \*volatile , char)|
|_InterlockedOr_acq|lange _InterlockedOr_acq(lang \*flüchtig, lang)|
|_InterlockedOr_nf|lange _InterlockedOr_nf(lang \*flüchtig, lang)|
|_InterlockedOr_rel|lange _InterlockedOr_rel(lang \*flüchtig, lang)|
|_InterlockedXor|lange _InterlockedXor(lang \*flüchtig, lang)|
|_InterlockedXor16|kurze _InterlockedXor16(kurz \*flüchtig, kurz)|
|_InterlockedXor16_acq|kurze _InterlockedXor16_acq(kurz \*flüchtig, kurz)|
|_InterlockedXor16_nf|kurze _InterlockedXor16_nf(kurz \*flüchtig, kurz)|
|_InterlockedXor16_rel|kurze _InterlockedXor16_rel(kurz \*flüchtig, kurz)|
|_InterlockedXor64|__int64 _InterlockedXor64\_( \* \__int64 flüchtig , _int64)|
|_InterlockedXor64_acq|__int64 _InterlockedXor64_acq\_( \* \__int64 flüchtig , _int64)|
|_InterlockedXor64_nf|__int64 _InterlockedXor64_nf(\_ \*_int64 \_flüchtig , _int64)|
|_InterlockedXor64_rel|__int64 _InterlockedXor64_rel(\_ \*_int64 \_flüchtig , _int64)|
|_InterlockedXor8|char _InterlockedXor8(char \*volatile , char)|
|_InterlockedXor8_acq|char _InterlockedXor8_acq(char \*volatile , char)|
|_InterlockedXor8_nf|char _InterlockedXor8_nf(char \*volatile , char)|
|_InterlockedXor8_rel|char _InterlockedXor8_rel(char \*volatile , char)|
|_InterlockedXor_acq|lange _InterlockedXor_acq (lang flüchtig, \*lang)|
|_InterlockedXor_nf|lange _InterlockedXor_nf(lang \*flüchtig, lang)|
|_InterlockedXor_rel|lange _InterlockedXor_rel(lang \*flüchtig, lang)|

[[Zurück nach oben](#top)]

### <a name="_interlockedbittest-intrinsics"></a>_interlockedbittest intrinsische Eigenschaften

Die einfachen ineinandergreifenden Bittests sind allen Plattformen gemeinsam. ARM64 `_acq`fügt `_rel`hinzu `_nf` , und Varianten, die nur die Barrieresemantik eines Vorgangs ändern, wie in [_nf (kein Zaun) Suffix](#nf_suffix) weiter oben in diesem Artikel beschrieben.

|Funktionsname|Funktionsprototyp|
|-------------------|------------------------|
|_interlockedbittestandreset|unsignierte Zeichen _interlockedbittestandreset(lang flüchtig \*, lang)|
|_interlockedbittestandreset_acq|unsignierte zeichen _interlockedbittestandreset_acq(lang flüchtig \*, lang)|
|_interlockedbittestandreset_nf|unsignierte _interlockedbittestandreset_nf (lang flüchtig \*, lang)|
|_interlockedbittestandreset_rel|unsignierte zeichen _interlockedbittestandreset_rel(lang flüchtig \*, lang)|
|_interlockedbittestandreset64|nicht signierte _interlockedbittestandreset64(__int64 flüchtig \*, __int64)|
|_interlockedbittestandreset64_acq|nicht signierte _interlockedbittestandreset64_acq(__int64 flüchtig \*, __int64)|
|_interlockedbittestandreset64_nf|unsignierte _interlockedbittestandreset64_nf(__int64 \*flüchtig , __int64)|
|_interlockedbittestandreset64_rel|nicht signierte _interlockedbittestandreset64_rel(__int64 flüchtig \*, __int64)|
|_interlockedbittestandset|unsignierte zeichen _interlockedbittestandset(lang flüchtig \*, lang)|
|_interlockedbittestandset_acq|unsignierte Zeichen _interlockedbittestandset_acq(lang flüchtig \*, lang)|
|_interlockedbittestandset_nf|unsignierte _interlockedbittestandset_nf (lang flüchtig \*, lang)|
|_interlockedbittestandset_rel|unsignierte _interlockedbittestandset_rel(lang \*flüchtig , lang)|
|_interlockedbittestandset64|unsignierte zeichen _interlockedbittestandset64(__int64 flüchtig \*, __int64)|
|_interlockedbittestandset64_acq|unsignierte _interlockedbittestandset64_acq(__int64 \*flüchtig , __int64)|
|_interlockedbittestandset64_nf|nicht signierte _interlockedbittestandset64_nf(__int64 flüchtig \*, __int64)|
|_interlockedbittestandset64_rel|nicht signierte _interlockedbittestandset64_rel(__int64 flüchtig \*, __int64)|

[[Zurück nach oben](#top)]

## <a name="see-also"></a>Siehe auch

[Compiler-Intrinsics](../intrinsics/compiler-intrinsics.md)\
[ARM-Intrinsiden](arm-intrinsics.md)\
[ARM-Assembler-Referenz](../assembler/arm/arm-assembler-reference.md)\
[C++-Sprachreferenz](../cpp/cpp-language-reference.md)
