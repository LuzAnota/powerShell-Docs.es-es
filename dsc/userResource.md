---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC User
ms.openlocfilehash: f2660933aec43967e3f4082a983ef328a5b93851
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
#<a name="dsc-user-resource"></a>Recurso de DSC User#


>Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0


El recurso __User__ de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar cuentas de usuarios locales en el nodo de destino.


##<a name="syntax"></a>Sintaxis##

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propiedades
|  Propiedad  |  Descripción   |
|---|---|
| UserName| Indica el nombre de la cuenta para la que quiere garantizar un estado específico.|
| Descripción| Indica la descripción que se quiere utilizar para la cuenta de usuario.|
| Deshabilitada| Indica si la cuenta se encuentra habilitada. Establezca esta propiedad en __$true__ para asegurarse de que esta cuenta esté deshabilitada y establézcala como __$false__ para asegurarse de que esté habilitada.|
| Ensure| Indica si existe la cuenta. Establezca esta propiedad en "Present" para asegurarse de que la cuenta exista y establézcala como "Absent" para asegurarse de que la cuenta no exista.|
| FullName| Representa una cadena con el nombre completo que quiere utilizar para la cuenta de usuario.|
| Contraseña| Indica la contraseña que quiere usar para esta cuenta. |
| PasswordChangeNotAllowed| Indica si el usuario puede cambiar la contraseña. Establezca esta propiedad en __$true__ para asegurarse de que el usuario no pueda cambiar la contraseña y establézcala como __$false__ para permitir al usuario cambiar la contraseña. El valor predeterminado es __$false__.|
| PasswordChangeRequired| Indica si el usuario debe cambiar la contraseña en el próximo inicio de sesión. Establezca esta propiedad en __$true__ si el usuario debe cambiar la contraseña. El valor predeterminado es __$true__.|
| PasswordNeverExpires| Indica si la contraseña expirará. Para asegurarse de que la contraseña para esta cuenta no expire nunca, establezca esta propiedad en __$true__; establézcala en __$false__ si la contraseña expirará. El valor predeterminado es __$false__.|
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Ejemplo

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```