@echo off
:: ============================================================
:: 名称: ClearSystemJunk.bat
:: 作者: LiBao Feng
:: GitHub: https://github.com/Enthusiasm23/SystemCleanupTool.git
:: 描述: 这个脚本用于清理系统中的临时文件和垃圾文件。
:: 版本: 1.1
:: 最后更新: 2024-02-26
:: 注意: 运行脚本前，请确保关闭可能干扰执行的系统保护软件，如杀毒程序或系统优化工具。
:: ============================================================

chcp 65001 >nul
setlocal enabledelayedexpansion

:: 检查是否以管理员权限运行
net session >nul 2>&1
if not %errorlevel% == 0 (
    echo 请以管理员权限重新运行此脚本。
    pause
    exit
)

:: 定义主清理任务
call :ClearJunk
echo. & pause
exit /b

:ClearJunk
echo 正在清理系统垃圾文件，请稍等......

:: 清理指定文件类型
call :ClearFiles "*.tmp"
call :ClearFiles "*._mp"
call :ClearFiles "*.log"
call :ClearFiles "*.gid"
call :ClearFiles "*.chk"
call :ClearFiles "*.old"
call :ClearRecycled
call :ClearFiles "%windir%\*.bak"
call :ClearPrefetch
call :ClearTemp
call :ClearRecent
call :ClearInternetTemp
call :ClearSystemLogs
call :ClearErrorReports
call :ClearWindowsUpdateCache
call :ClearWindowsTempFiles
call :ClearThumbnailCache

echo 系统垃圾文件清理完成！
exit /b

:ClearFiles
echo 正在清理 %1 文件...
for /r %systemdrive% %%i in (%1) do del /f /s /q "%%i"
exit /b

:ClearRecycled
echo 正在清理回收站文件...
del /f /s /q /a %systemdrive%\$Recycle.Bin\*.*
exit /b

:ClearPrefetch
echo 正在清理预读缓存文件...
del /f /s /q %windir%\prefetch\*.*
exit /b

:ClearTemp
echo 正在清理临时文件夹...
rd /s /q %windir%\temp & md %windir%\temp
exit /b

:ClearRecent
echo 正在清理最近使用的文件列表...
del /f /q %APPDATA%\Microsoft\Windows\Recent\*.*
exit /b

:ClearInternetTemp
echo 正在清理互联网临时文件...
del /f /s /q "%userprofile%\Local Settings\Temporary Internet Files\*.*"
del /f /s /q "%userprofile%\Local Settings\Temp\*.*"
exit /b

:ClearSystemLogs
echo 正在清理系统日志文件...
call :ClearFiles "%windir%\Logs\*.log"
exit /b

:ClearErrorReports
echo 正在清理错误报告文件...
call :ClearFiles "%programdata%\Microsoft\Windows\WER\ReportArchive\*"
call :ClearFiles "%programdata%\Microsoft\Windows\WER\ReportQueue\*"
exit /b

:ClearWindowsUpdateCache
echo 正在清理 Windows 更新缓存...
call :ClearFiles "%windir%\SoftwareDistribution\Download\*"
exit /b

:ClearWindowsTempFiles
echo 正在清理 Windows 安装临时文件...
call :ClearFiles "%windir%\$NtUninstall*\*"
call :ClearFiles "%windir%\$NtServicePackUninstall$\*"
exit /b

:ClearThumbnailCache
echo 正在清理缩略图缓存...
del /f /q /s %userprofile%\AppData\Local\Microsoft\Windows\Explorer\thumbcache_*.db
exit /b
