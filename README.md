# Introduction

PowerShell Universal Dashboard is a web framework for PowerShell developers. Create websites, REST APIs and dashboards with only PowerShell script. The client and server side code for the dashboard is authored completely in PowerShell. Charts, monitors, tables and grids can easily be created with the cmdlets included with the module.The module is cross-platform and will run anywhere Windows PowerShell or PowerShell Core can run.

Want a quick overview of PowerShell Universal Dashboard? Check out this [short video](https://youtu.be/_ckxYyDv4cg).

## Installation

**Premium Edition**

{% hint style="info" %}
Premium Edition enables all the features of Community Edition with added charts, authorization and authentication. You can purchase a license [here](https://ironmansoftware.com/collections/powershell/products/powershell-universal-dashboard).
{% endhint %}

`Install-Module UniversalDashboard -AcceptLicense`

**Community Edition**

{% hint style="info" %}
Universal Dashboard also features a free Community Edition. This edition is [open-source](https://github.com/ironmansoftware/universal-dashboard), [LGPL licensed](https://github.com/ironmansoftware/universal-dashboard/blob/master/LICENSE) and [available for free](https://www.powershellgallery.com/packages/UniversalDashboard.Community). It contains a subset of features of the Enterprise Edition. To install this version, use the following command line.
{% endhint %}

`Install-Module UniversalDashboard.Community -AcceptLicense`

For a full list of the differences between Community and Premium, visit the [Feature Comparison](feature-comparison.md) page.

![Live data from InfluxDB shown in Universal Dashboard](.gitbook/assets/influxdb.gif)

