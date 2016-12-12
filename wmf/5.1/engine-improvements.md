---
title: "Mejoras del motor de PowerShell en WMF 5.1 (versión preliminar)"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 118cb91528824b75e28a1eadaa377a696c67f2dd
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
#<a name="powershell-engine-improvements"></a>Mejoras del motor de PowerShell

En WMF 5.1, se han implementado las siguientes mejoras al motor central de PowerShell:


## <a name="performance"></a>Rendimiento ##

El rendimiento ha mejorado en algunas áreas importantes:

- Inicio
- La canalización en cmdlets como ForEach-Object y Where-Object es aproximadamente un 50 % más rápido 

Algunas mejoras del ejemplo (los resultados pueden variar en función del hardware): 

| Escenario | Tiempo de 5.0 (ms) | Tiempo de 5.1 (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Primera ejecución de PowerShell: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Caché de análisis de comandos integrada: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |
  
> Nota: Un cambio relacionado con el inicio puede afectar a algunos escenarios no admitidos. 
> PowerShell ya no lee los archivos `$pshome\*.ps1xml`: estos archivos se han convertido en C# para evitar la sobrecarga de archivos y de la CPU que supone procesar los archivos XML. 
Los archivos aún existen para proporcionar compatibilidad con V2 en paralelo, por lo que si se cambia el contenido de los archivos, esto no tendrá ningún efecto en V5, solo en V2. 
Tenga en cuenta que el cambio del contenido de estos archivos nunca ha sido un escenario compatible.

Otro cambio visible es la forma en que PowerShell almacena en caché tanto comandos exportados como otra información de los módulos instalados en un sistema. Antes, la memoria caché se almacenaba en el directorio `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`. En WMF 5.1, la memoria caché es un único archivo `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Para obtener más información, vea [Caché de análisis de módulo](scenarios-features.md#module-analysis-cache).
