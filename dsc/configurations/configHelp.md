---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Escribir ayuda para configuraciones de DSC
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402890"
---
# <a name="writing-help-for-dsc-configurations"></a>Escribir ayuda para configuraciones de DSC

>Se aplica a: Windows PowerShell 5.0

Puede usar la ayuda basada en comentarios en configuraciones de DSC. Los usuarios pueden acceder a la Ayuda mediante una llamada a la **configuración** con `-?`, o mediante el [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet. Coloque la Ayuda basada en comentarios directamente encima el `Configuration` palabra clave.
Puede colocar la Ayuda de parámetro en línea con el bloque de comentario, justo encima de la declaración de parámetros o ambos, como se muestra en el ejemplo siguiente.

Para obtener más información sobre la ayuda basada en comentarios de PowerShell, vea [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

> [!NOTE]
> Entornos de desarrollo de PowerShell, como VSCode y el ISE, también tienen fragmentos de código para que pueda insertar automáticamente las plantillas de bloque de comentario.

En el ejemplo siguiente se muestran un script que contiene una configuración y ayuda basada en comentarios para dicha configuración. En este ejemplo se muestra una configuración con parámetros. Para más información sobre cómo usar parámetros en las configuraciones, consulte [agregar parámetros a las configuraciones de](add-parameters-to-a-configuration.md).

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
(and their descriptions) appear in help topic. To change the order, change the syntax.

.EXAMPLE
HelpSample -ComputerName localhost

A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.
.EXAMPLE
HelpSample -FilePath "C:\output.txt"

This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>
configuration HelpSample1
{
    param
    (
        [string]$ComputerName = 'localhost',
        # Provide a PARAMETER section for each parameter that your script or function accepts.
        [string]$FilePath = 'C:\Destination.txt'
    )

    Node $ComputerName
    {
        File HelloWorld
        {
            Contents="Hello World"
            DestinationPath = $FilePath
        }
    }
}
```

## <a name="viewing-configuration-help"></a>Ver la ayuda de configuración

Para ver la Ayuda de una configuración, use el `Get-Help` cmdlet con el nombre de la función o escriba el nombre de la función seguido por `-?`. El siguiente es el resultado de la configuración anterior pasa a `Get-Help`.

```powershell
Get-Help HelpSample1 -Detailed
```

```output
NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-PsDscRunAsCredential] <PSCredential>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] <String>] [[-FilePath] <String>] [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


PARAMETERS
    -InstanceName <String>

    -DependsOn <String[]>

    -PsDscRunAsCredential <PSCredential>

    -OutputPath <String>

    -ConfigurationData <Hashtable>

    -ComputerName <String>
        The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

        Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
        Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
        The description can include paragraph breaks.

        The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
        (and their descriptions) appear in help topic. To change the order, change the syntax.

    -FilePath <String>
        Provide a PARAMETER section for each parameter that your script or function accepts.

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).

    -------------------------- EXAMPLE 1 --------------------------

    PS C:\>HelpSample -ComputerName localhost

    A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
    PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

    If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.




    -------------------------- EXAMPLE 2 --------------------------

    PS C:\>HelpSample -FilePath "C:\output.txt"

    This example will be labeled "EXAMPLE 2" when help is displayed to the user.




REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

> [!NOTE]
> Los campos de la sintaxis y los atributos de parámetro se generan automáticamente para usted mediante PowerShell.

## <a name="see-also"></a>Véase también

- [Configuraciones DSC](configurations.md)
- [Escritura, compilación y aplicación de una configuración](write-compile-apply-configuration.md)
- [Adición parámetros a una configuración](add-parameters-to-a-configuration.md)
