---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Configuración de un cliente de extracción mediante un id. de configuración en PowerShell 4.0"
ms.openlocfilehash: 19328018d276cddd0877869b0ec69c14c51e4b85
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a>Configuración de un cliente de extracción mediante un id. de configuración en PowerShell 4.0

>Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Es necesario indicar a cada nodo de destino que debe usar el modo de extracción y se le debe facilitar la dirección URL donde puede establecer contacto con el servidor de extracción para obtener las configuraciones. Para ello, tendrá que configurar el administrador de configuración local (LCM) con la información necesaria. Para configurar el LCM, debe crear un tipo especial de configuración conocida como "metaconfiguración". Para más información sobre cómo configurar el LCM, consulte [Administrador de configuración local de configuración de estado deseado de Windows PowerShell 4.0](metaConfig4.md).

El script siguiente configura el LCM para que extraiga configuraciones de un servidor denominado "PullServer":

```powershell
Configuration SimpleMetaConfigurationForPull 
{ 
    LocalConfigurationManager 
    { 
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30; 
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    } 
} 
SimpleMetaConfigurationForPull -Output "."
```

En el script, **DownloadManagerCustomData** pasa la dirección URL del servidor de incorporación de cambios y (en este ejemplo) permite una conexión no segura. 

Después de que se ejecute este script, se crea una nueva carpeta de salida denominada **SimpleMetaConfigurationForPull** y se coloca un archivo MOF de metaconfiguración en ella.

Para aplicar la configuración, utilice **Set-DscLocalConfigurationManager** con parámetros para **ComputerName** (utilice "localhost") y **Path** (la ruta de acceso a la ubicación del archivo de localhost.meta.mof del nodo de destino). Por ejemplo: 
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a>Id. de configuración
El script establece la propiedad **ConfigurationID** del LCM en un GUID que se había creado anteriormente para este fin (puede crear un GUID mediante el cmdlet **New-Guid**). La propiedad **ConfigurationID** es lo que usa el LCM para buscar la configuración adecuada en el servidor de incorporación de cambios. El archivo MOF de configuración del servidor de incorporación de cambios debe denominarse `ConfigurationID.mof`, donde *ConfigurationID* es el valor de la propiedad **ConfigurationID** del LCM del nodo de destino.

## <a name="pulling-from-an-smb-server"></a>Incorporación de cambios de un servidor SMB

Si el servidor de incorporación de cambios está configurado como un recurso compartido de archivos SMB, en lugar de un servicio web, especifique **DscFileDownloadManager** en lugar de **WebDownLoadManager**.
**DscFileDownloadManager** toma una propiedad **SourcePath** en lugar de **ServerUrl**. El script siguiente configura el LCM para que extraiga configuraciones de un recurso compartido SMB denominado "SmbDscShare" en un servidor denominado "CONTOSO-SERVER":

```powershell
Configuration SimpleMetaConfigurationForPull 
{ 
    LocalConfigurationManager 
    { 
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30; 
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    } 
} 
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a>Véase también

- [Configuración de un servidor de extracción web de DSC](pullServer.md)
- [Configuración de un servidor de extracción SMB de DSC](pullServerSMB.md)

