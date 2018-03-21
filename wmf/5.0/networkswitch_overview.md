---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4868cf657f678ee43a6c92d5ee286e9ddb490964
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="network-switch-management-with-powershell"></a>Administración de conmutadores de red con PowerShell

El cmdlet **Get-NetworkSwitchEthernetPort** devuelve ahora la siguiente información adicional con las instancias:

- IPAddress: dirección IP asociada con el puerto.
- PortMode: modo de puerto (acceso, ruta o tronco).
- AccessVLAN: identificador de la VLAN asociada con este puerto en el modo de acceso.
- TrunkedVLANList: lista de identificadores de las VLAN asociadas con este puerto en el modo de tronco.

## <a name="fundamental-network-switch-management-with-windows-powershell"></a>Administración de modificadores de red fundamentales con Windows PowerShell

Los cmdlet NetworkSwitch, introducidos en WMF 5.0, permiten aplicar la configuración de modificador, LAN virtual (VLAN) y básica del puerto del modificador de red de capa 2 a los modificadores de red certificados con el logotipo de Windows Server 2012 R2. Microsoft mantiene su compromiso por admitir la visión de la [capa de abstracción del centro de datos](http://technet.microsoft.com/cloud/dal.aspx) (DAL) y para mostrar el valor para nuestros clientes y socios en este espacio. Con estos cmdlets puede hacer lo siguiente:

- Configuración global del modificador, como:
    - Establecer el nombre de host.
    - Establecer el banner del modificador.
    - Mantener la configuración.
    - Habilitar o deshabilitar una característica.

- Configuración de VLAN:
    - Crear o quitar la VLAN.
    - Habilitar o deshabilitar la VLAN.
    - Enumerar la VLAN.
    - Establecer el nombre descriptivo de una VLAN.

- Configuración de puerto de la capa 2:
    - Enumerar los puertos.
    - Habilitar o deshabilitar los puertos.
    - Establecer los modos de puerto y sus propiedades.
    - Agregar o asociar la VLAN al modo de tronco o acceso en el puerto.

Empiece a explorar buscando todos los cmdlets NetworkSwitch.

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

Existe más información disponible en la entrada de blog del anuncio de WMF 5.0 Preview de Jeffrey Snover: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>

