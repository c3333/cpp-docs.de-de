---
title: In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen
ms.date: 12/30/2016
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
ms.openlocfilehash: cf67cb9c0a2438ee6ac1bcc7753c0f89b63a356d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214317"
---
# <a name="crt-functions-not-supported-in-universal-windows-platform-apps"></a>In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen

Viele CRT-Funktionen (C-Laufzeit) sind nicht verfügbar, wenn Sie Apps für die universelle Windows-Plattform erstellen. In einigen Fällen sind Problem Umgehungen verfügbar – beispielsweise können Sie Windows-Runtime oder Win32-APIs verwenden. In anderen Fällen wurden die CRT-Funktionen jedoch möglicherweise gesperrt, da die ihnen entsprechenden Features oder die unterstützenden APIs nicht auf Apps für die universelle Windows-Plattform (UWP) angewendet werden können. Eine alternative Methode, die für die Windows-Runtime unterstützt wird, finden Sie unter [Alternativen zu Windows-APIs in UWP-apps](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

In der folgenden Tabelle sind die CRT-Funktionen, die beim Erstellen von Apps für die universelle Windows-Plattform nicht verfügbar sind, sowie mögliche Problemumgehungen aufgeführt.

## <a name="unsupported-crt-functions"></a>Nicht unterstützte CRT-Funktionen

||||
|-|-|-|
|_beep _sleep _seterrormode|Diese Funktionen waren in früheren Versionen der CRT veraltet. Darüber hinaus sind die entsprechenden Win32-APIs für Apps für die universelle Windows-Plattform nicht verfügbar.|Keine Problemumgehung.|
|chdir _chdrive getcwd|Diese Funktionen sind veraltet oder nicht threadsicher.|Verwenden Sie „_chdir“, „_getcwd“ und verwandte Funktionen.|
|_cgets _cgets_s _cgetws _cgetws_s _cprintf _cprintf_l _cprintf_p _cprintf_p_l _cprintf_s _cprintf_s_l _cputs _cputws _cscanf _cscanf_l _cscanf_s _cscanf_s_l _cwait _cwprintf _cwprintf_l _cwprintf_p _cwprintf_p_l _cwprintf_s _cwprintf_s_l _cwscanf _cwscanf_l _cwscanf_s _cwscanf_s_l _vcprintf _vcprintf_l _vcprintf_p _vcprintf_p_l _vcprintf_s _vcprintf_s_l _vcwprintf _vcwprintf_l _vcwprintf_p _vcwprintf_p_l _vcwprintf_s _vcwprintf_s_l _getch _getch_nolock _getche _getche_nolock _getwch _getwch_nolock _getwche _getwche_nolock _putch _putch_nolock _putwch _putwch_nolock _ungetch _ungetch_nolock _ungetwch _ungetwch_nolock _kbhit kbhit putch cgets cprintf cputs cscanf cwait getch getche ungetch|Diese Funktionen werden zum direkten Lesen von der sowie zum direkten Schreiben in die Konsole verwendet. Apps für die universelle Windows-Plattform sind nur für die grafische Benutzeroberfläche (GUI) vorgesehen und unterstützen die Konsole nicht.|Keine Problemumgehung.|
|getpid|Diese Funktion ist veraltet.|Verwenden Sie „_getpid“ oder die Win32-API `GetCurrentProcessId()`.|
|_getdiskfree|Nicht verfügbar.|Verwenden Sie die Win32-API `GetDiskFreeSpaceExW()`.|
|_getdrive _getdrives|Die entsprechende API ist für Apps für die universelle Windows-Plattform nicht verfügbar.|Keine Problemumgehung.|
|_inp _inpd _inpw _outp _outpd _outpw inp inpd inpw outp outpd outpw|Port-E/A wird in Apps für die universelle Windows-Plattform nicht unterstützt.|Keine Problemumgehung.|
|_ismbcalnum _ismbcalnum_l _ismbcalpha _ismbcalpha_l _ismbcdigit _ismbcdigit_l _ismbcgraph _ismbcgraph_l _ismbchira _ismbchira_l _ismbckata _ismbckata_l _ismbcl0 _ismbcl0_l _ismbcl1 _ismbcl1_l _ismbcl2 _ismbcl2_l _ismbclegal _ismbclegal_l _ismbclower _ismbclower_l _ismbcprint _ismbcprint_l _ismbcpunct _ismbcpunct_l _ismbcspace _ismbcspace_l _ismbcsymbol _ismbcsymbol_l _ismbcupper _ismbcupper_l _mbbtombc _mbbtombc_l _mbbtype _mbbtype_l _mbccpy _mbccpy_l _mbccpy_s _mbccpy_s_l _mbcjistojms _mbcjistojms_l _mbcjmstojis _mbcjmstojis_l _mbclen _mbclen_l _mbctohira _mbctohira_l _mbctokata _mbctokata_l _mbctolower _mbctolower_l _mbctombb _mbctombb_l _mbctoupper _mbctoupper_l _mbsbtype _mbsbtype_l _mbscat _mbscat_l _mbscat_s _mbscat_s_l _mbschr _mbschr_l _mbscmp _mbscmp_l _mbscoll _mbscoll_l _mbscpy _mbscpy_l _mbscpy_s _mbscpy_s_l _mbscspn _mbscspn_l _mbsdec _mbsdec_l _mbsicmp _mbsicmp_l _mbsicoll _mbsicoll_l _mbsinc _mbsinc_l _mbslen _mbslen_l _mbslwr _mbslwr_l _mbslwr_s _mbslwr_s_l _mbsnbcat _mbsnbcat_l _mbsnbcat_s _mbsnbcat_s_l _mbsnbcmp _mbsnbcmp_l _mbsnbcnt _mbsnbcnt_l _mbsnbcoll _mbsnbcoll_l _mbsnbcpy _mbsnbcpy_l _mbsnbcpy_s _mbsnbcpy_s_l _mbsnbicmp _mbsnbicmp_l _mbsnbicoll _mbsnbicoll_l _mbsnbset _mbsnbset_l _mbsnbset_s _mbsnbset_s_l _mbsncat _mbsncat_l _mbsncat_s _mbsncat_s_l _mbsnccnt _mbsnccnt_l _mbsncmp _mbsncmp_l _mbsncoll _mbsncoll_l _mbsncpy _mbsncpy_l _mbsncpy_s _mbsncpy_s_l _mbsnextc _mbsnextc_l _mbsnicmp _mbsnicmp_l _mbsnicoll _mbsnicoll_l _mbsninc _mbsninc_l _mbsnlen _mbsnlen_l _mbsnset _mbsnset_l _mbsnset_s _mbsnset_s_l _mbspbrk _mbspbrk_l _mbsrchr _mbsrchr_l _mbsrev _mbsrev_l _mbsset _mbsset_l _mbsset_s _mbsset_s_l _mbsspn _mbsspn_l _mbsspnp _mbsspnp_l _mbsstr _mbsstr_l _mbstok _mbstok_l _mbstok_s _mbstok_s_l _mbsupr _mbsupr_l _mbsupr_s _mbsupr_s_l is_wctype|Multibyte-Zeichenfolgen werden in Apps für die universelle Windows-Plattform nicht unterstützt.|Verwenden Sie stattdessen Unicode-Zeichenfolgen.|
|_pclose _pipe _popen _wpopen|Die Pipe-Funktionalität ist in Apps für die universelle Windows-Plattform nicht verfügbar.|Keine Problemumgehung.|
|_resetstkoflw|Unterstützende Win32-APIs sind für Apps für die universelle Windows-Plattform nicht verfügbar.|Keine Problemumgehung.|
|_getsystime _setsystime|Dies waren veraltete APIs in früheren CRT-Versionen. Darüber hinaus kann ein Benutzer die Systemzeit in einer App für die universelle Windows-Plattform aufgrund fehlender Berechtigungen nicht festlegen.|Um nur die Systemzeit zu erhalten, verwenden Sie die Win32-API `GetSystemTime`. Die Systemzeit kann nicht festgelegt werden.|
|_environ _putenv _putenv_s _searchenv _searchenv_s _dupenv_s _wputenv _wputenv_s _wsearchenv getenv getenv_s putenv _wdupenv_s _wenviron _wgetenv _wgetenv_s _wsearchenv_s tzset|Umgebungsvariablen sind für Apps für die universelle Windows-Plattform nicht verfügbar.|Keine Problemumgehung. Verwenden Sie „_tzset“ zum Festlegen der Zeitzone.|
|_loaddll _getdllprocaddr _unloaddll|Dies waren veraltete Funktionen in früheren CRT-Versionen. Darüber hinaus können Benutzer DLL-Dateien nur in demselben Anwendungspaket laden.|Verwenden Sie die Win32-APIs `LoadPackagedLibrary`, `GetProcAddress`und `FreeLibrary` zum Laden und Verwenden verpackter DLL-Dateien.|
|_wexecl _wexecle _wexeclp _wexeclpe _wexecv _wexecve _wexecvp _wexecvpe _execl _execle _execlp _execlpe _execv _execve _execvp _execvpe _spawnl _spawnle _spawnlp _spawnlpe _spawnv _spawnve _spawnvp _spawnvpe _wspawnl _wspawnle _wspawnlp _wspawnlpe _wspawnv _wspawnve _wspawnvp _wspawnvpe _wsystem execl execle execlp execlpe execv execve execvp execvpe spawnl spawnle spawnlp spawnlpe spawnv spawnve spawnvp spawnvpe system|Die Funktionalität ist in Apps für die universelle Windows-Plattform nicht verfügbar. Eine App für die universelle Windows-Plattform kann keine andere App für die universelle Windows-Plattform oder eine Desktop-App aufrufen.|Keine Problemumgehung.|
|_heapwalk _heapadd _heapchk _heapset _heapused|Diese Funktionen werden in der Regel bei der Arbeit mit dem Heap verwendet. Entsprechende Win32-APIs werden in Apps für die universelle Windows-Plattform jedoch nicht unterstützt. Zudem können Apps keine privaten Heaps mehr erstellen oder verwenden.|Keine Problemumgehung. Allerdings ist `_heapwalk` nur zu Debugzwecken in der DEBUG CRT verfügbar. Diese können nicht in Apps verwendet werden, die in die Microsoft Store hochgeladen werden.|

Die folgenden Funktionen sind in der CRT für UWP-apps verfügbar, sollten aber nur verwendet werden, wenn die entsprechenden Win32-oder Windows-Runtime-APIs nicht verwendet werden können, z. –. Wenn Sie große Codebasen portieren.

|||
|-|-|
|Einzelbyte-Zeichenfolgenfunktionen, z. B. `strcat`, `strcpy`, `strlwr`usw.|Erstellen Sie Ihre UWP-apps strikt in Unicode, weil alle Win32-APIs und Windows-Runtime APIs, die verfügbar gemacht werden, nur Unicode-Zeichensätze verwenden.  Einzelbyte-Funktionen wurden für die Portierung umfangreicher Codebasen beibehalten, sollten aber ansonsten vermieden werden, und es sollten stattdessen nach Möglichkeit die entsprechenden Breitzeichen-Funktionen verwendet werden.|
|Stream-E/A- und Datei-E/A-Funktionen auf niedriger Ebene, z. B. `fopen`, `open`usw.|Diese Funktionen sind synchron, was für Apps für die universelle Windows-Plattform nicht empfohlen wird. Verwenden Sie in Ihren Apps für die universelle Windows-Plattform asynchrone APIs, um Dateien zu öffnen, aus Dateien zu lesen und in Dateien zu schreiben, damit das Sperren des UI-Threads verhindert wird. Beispiele für derartige APIs finden Sie in der `Windows::Storage::FileIO` -Klasse.|

## <a name="windows-8x-store-apps-and-windows-phone-8x-apps"></a>Windows 8.x Store-Apps und Windows Phone 8.x-Apps

Zusätzlich zu den zuvor erwähnten APIs sind die folgenden APIs in Windows 8.x Store-Apps und Windows Phone 8.x-Apps nicht verfügbar.

||||
|-|-|-|
|_beginthread _beginthreadex _endthread _endthreadex|Threading-Win32-APIs sind in Windows 8.x Store-Apps nicht verfügbar.|Verwenden Sie stattdessen `Windows Runtime Windows::System::Threading::ThreadPool` oder `concurrency::task` .|
|_chdir _wchdir _getcwd _getdcwd _wgetcwd _wgetdcwd|Das Konzept des Arbeitsverzeichnisses gilt nicht für Windows 8.x Store-Apps.|Verwenden Sie stattdessen vollständige Pfade.|
|_getpid|Diese Funktion war in früheren Versionen der CRT veraltet.|Verwenden Sie die Win32-API `GetCurrentProcessId()`.|
|_isleadbyte_l _ismbbalnum, _ismbbalnum_l, _ismbbalpha, _ismbbalpha _ismbbalpha_l _ismbbgraph _ismbbgraph_l _ismbbkalnum _ismbbkalnum_l _ismbbkana _ismbbkana_l _ismbbkprint _ismbbkprint_l _ismbbkpunct _ismbbkpunct_l _ismbblead _ismbblead_l _ismbbprint _ismbbprint_l _ismbbpunct _ismbbpunct_l _ismbbtrail _ismbbtrail_l _ismbslead _ismbslead_l _ismbstrail _ismbstrail_l _mbsdup isleadbyte|Multibyte-Zeichenfolgen werden in Windows 8.x Store-Apps nicht unterstützt.|Verwenden Sie stattdessen Unicode-Zeichenfolgen.|
|_tzset|Umgebungsvariablen sind für Windows 8.x Store-Apps nicht verfügbar.|Keine Problemumgehung.|
|_get_heap_handle, _heapmin|Entsprechende Win32-APIs werden in Windows 8.x Store-Apps nicht unterstützt. Zudem können Apps keine privaten Heaps mehr erstellen.|Keine Problemumgehung. Allerdings ist `_get_heap_handle` nur zu Debugzwecken in der DEBUG CRT verfügbar.|
