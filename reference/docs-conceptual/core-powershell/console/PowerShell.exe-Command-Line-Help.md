---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Ayuda para la línea de comandos de PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 60b6a7e310821a4092b0972b7abbdae0e2d5f738
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952586"
---
# <a name="powershellexe-command-line-help"></a>Ayuda de línea de comandos de PowerShell.exe

Puede usar PowerShell.exe para iniciar una sesión de PowerShell desde la línea de comandos de otra herramienta (como Cmd.exe) o usarlo en la línea de comandos de PowerShell para iniciar una nueva sesión. Use los parámetros para personalizar la sesión.

## <a name="syntax"></a>Sintaxis

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a>Parámetros

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>

Acepta una versión de cadena con codificación Base 64 de un comando. Use este parámetro para enviar comandos a PowerShell que requieran comillas complejas o llaves.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

Establece la directiva de ejecución predeterminada para la sesión actual y la guarda en la variable de entorno $env:PSExecutionPolicyPreference. Este parámetro no modifica la directiva de ejecución de PowerShell establecida en el Registro. Para obtener más información sobre las directivas de ejecución de PowerShell, incluida una lista de los valores válidos, vea [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

### <a name="-file-filepath-parameters"></a>-File <FilePath> \[<Parameters>]

Ejecuta el script especificado en el ámbito local ("origen de puntos"), para que las funciones y variables que crea el script estén disponibles en la sesión actual. Escriba la ruta de acceso del archivo de script y los parámetros. **File** debe ser el último parámetro del comando, puesto que todos los caracteres escritos después del nombre de parámetro **File** se interpretan como la ruta de acceso de archivo de script seguido de los parámetros de los parámetros del script y sus valores.

Puede incluir los parámetros de un script, así como los valores de parámetro, en el valor del parámetro **File**. Por ejemplo: `-File .\Get-Script.ps1 -Domain Central`. Debe tenerse en cuenta que los parámetros que se pasan al script lo hacen como cadenas literales (una vez interpretados por el shell actual).
Por ejemplo, si se está en cmd.exe y se quiere pasar un valor de la variable de entorno, se usará la sintaxis de cmd.exe: `powershell -File .\test.ps1 -Sample %windir%`. En caso de usar la sintaxis de PowerShell, el script en este ejemplo recibirá el literal "$env:windir" en lugar del valor de esa variable de entorno: `powershell -File .\test.ps1 -Sample $env:windir`.

Normalmente, los parámetros de modificador de un script se incluyen o se omiten. Por ejemplo, el siguiente comando usa el parámetro **All** del archivo de script Get-Script.ps1: `-File .\Get-Script.ps1 -All`

### <a name="-inputformat-text--xml"></a>\-InputFormat {Text | XML}

Describe el formato de los datos que se envían a PowerShell. Los valores válidos son "Text" (cadenas de texto) o "XML" (formato CLIXML serializado).

### <a name="-mta"></a>-Mta

Inicia PowerShell con un contenedor multiproceso. Este parámetro se incorporó en PowerShell 3.0. En PowerShell 3.0, el valor predeterminado es el contenedor uniproceso (STA). En PowerShell 2.0, el valor predeterminado es el contenedor multiproceso (MTA).

### <a name="-noexit"></a>-NoExit

No se cierra después de ejecutar comandos de inicio.

### <a name="-nologo"></a>-NoLogo

Oculta la pancarta de copyright al inicio.

### <a name="-noninteractive"></a>-NonInteractive

No presenta un aviso interactivo al usuario.

### <a name="-noprofile"></a>-NoProfile

No carga el perfil de PowerShell.

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}

Determina cómo se formatea la salida de PowerShell. Los valores válidos son "Text" (cadenas de texto) o "XML" (formato CLIXML serializado).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Carga el archivo de consola de PowerShell especificado. Escriba la ruta de acceso y el nombre del archivo de consola. Para crear un archivo de consola, use el cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) de PowerShell.

### <a name="-sta"></a>-Sta

Inicia PowerShell con un contenedor uniproceso. En PowerShell 3.0, el valor predeterminado es el contenedor uniproceso (STA). En PowerShell 2.0, el valor predeterminado es el contenedor multiproceso (MTA).

### <a name="-version-powershell-version"></a>-Version <PowerShell Version>

Inicia la versión especificada de PowerShell. La versión que especifique debe estar instalada en el sistema. Si PowerShell 3.0 está instalado en el equipo, los valores válidos son "2.0" y "3.0". El valor predeterminado es "3.0".

Si PowerShell 3.0 no está instalado, el único valor válido es "2.0". Otros valores se omiten.

Para obtener más información, vea "[Installing Windows PowerShell](../../setup/installing-windows-powershell.md)" (Instalación de Windows PowerShell).

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

Establece el estilo de ventana de la sesión. Los valores válidos son Normal, Minimizada, Maximizada y Oculta.

### <a name="-command"></a>-Command

Ejecuta los comandos especificados (y todos los parámetros) como si se hubiesen escrito en el símbolo del sistema de PowerShell y, después, se cierra, a menos que se especifique el parámetro NoExit.
Básicamente, cualquier texto situado tras `-Command` se envía como una sola línea de comandos a PowerShell (esto es diferente a cómo `-File` controla los parámetros que se envían a un script).

El valor del comando puede ser "-", una cadena. o un bloque de scripts. Si el valor de Command es "-", el texto del comando se lee de la entrada estándar.

Los bloques de scripts deben incluirse entre llaves ({}). Puede especificar un bloque de scripts solo cuando ejecute PowerShell.exe en PowerShell. Los resultados del script se devuelven al shell principal como objetos XML deserializados, no como objetos activos.

Si el valor de Command es una cadena, **Command** debe ser el último parámetro del comando, porque los caracteres escritos después del comando se interpretan como argumentos del comando.

Para escribir una cadena que ejecute un comando de PowerShell, use el siguiente formato:

```powershell
"& {<command>}"
```

donde las comillas indican una cadena y el operador de invocación (&) hace que se ejecute el comando.

### <a name="-help---"></a>-Help, -?, /?

Muestra este mensaje. Si está escribiendo un comando de PowerShell.exe en PowerShell, anteponga a los parámetros del comando un guion (-), no una barra diagonal (/). Puede usar un guion o una barra diagonal en Cmd.exe.

> [!NOTE]
> Nota de solución de problemas: En PowerShell 2.0, al iniciar algunos programas en la consola de Windows PowerShell, se produce un error LastExitCode 0xc0000142.

## <a name="examples"></a>EJEMPLOS

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```