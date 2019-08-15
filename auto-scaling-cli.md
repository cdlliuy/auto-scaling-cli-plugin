---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

---


{:codeblock: .codeblock}
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:table: .aria-labeledby="caption"}
{:tip: .tip}
{:deprecated: .deprecated}

# Auto-Scaling CLI
{: #autoscalingcli}

{{site.data.keyword.autoscaling}} is deprecated. As of 1st Augest 2019, you cannot provision new {{site.data.keyword.autoscaling}} instances in public region. Existing service instances are supported until 30th September 2019. <br/>
To continue using the auto-scaling capability for Cloud Foundray application in {{site.data.keyword.Bluemix_notm}}, please migrate to the NEW [built-in Auto-Scaling experience available within the Cloud Foundry application context](https://{DomainName}/docs/cloud-foundry-public?topic=cloud-foundry-public-autoscale_cloud_foundry_apps). 
{:deprecated}

You can configure the {{site.data.keyword.autoscaling}} service by using the {{site.data.keyword.autoscaling}} CLI for {{site.data.keyword.Bluemix_notm}}. The {{site.data.keyword.autoscaling}} CLI supports Linux64, Win64, and OSX, and provides functionality that is similar to the auto-scaling RESTful API provides.
{: shortdesc}

**Prerequisites**

* Before you begin, install the {{site.data.keyword.Bluemix_notm}} CLI. See [Download {{site.data.keyword.Bluemix_notm}} CLI ![External link icon](../icons/launch-glyph.svg)](http://plugins.ng.bluemix.net/ui/home.html){: new_window} for instructions.

* Adding the {{site.data.keyword.Bluemix_notm}} CLI plug-in

To install the {{site.data.keyword.autoscaling}} CLI plugin, run the following command:
```
ibmcloud plugin install auto-scaling -r Bluemix
```
{: codeblock}

* Before running the registry commands, log in to {{site.data.keyword.Bluemix_notm}} with the `ibmcloud login` command to generate an access token and authenticate your session.

<table summary="Manage {{site.data.keyword.autoscaling}} service">
<caption>Table 1. Commands for managing {{site.data.keyword.autoscaling}} service
</caption>
 <thead>
 <th colspan="5">Commands for managing the {{site.data.keyword.autoscaling}} service</th>
 </thead>
 <tbody>
 <tr>
 <td>[ibmcloud as policy-create](#bx_as_policy_create)</td>
 <td>[ibmcloud as policy-attach](#bx_as_policy_attach)</td>
 <td>[ibmcloud as policy-show](#bx_as_policy_show)</td>
 <td>[ibmcloud as policy-detach](#bx_as_policy_detach)</td>
 <td>[ibmcloud as policy-enable](#bx_as_policy_enable)</td>
 </tr>
 <tr>
 <td>[ibmcloud as history-show](#bx_as_history_show)</td>
 </tr>
 </tbody></table>


## Generating an auto-scaling policy
{: #bx_as_policy_create}

You can generate an auto-scaling policy by answering the questions on the command line interface. Depending on your input, a JSON file that contains the definition of the auto-scaling policy is saved with the name that you enter. If you do not enter  the file name, the policy content is printed to the command line directly without saving it to a file. Run the following command:

```
ibmcloud as policy-create
```
{: codeblock}

**Prerequisites**

None

## Attaching an auto-scaling policy
{: #bx_as_policy_attach}

You can attach an auto-scaling policy to a specific app. Run the following command:

```
ibmcloud as policy-attach <APP_NAME> -p <policy_file>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;APP_NAME&gt;</dt>
<dd class="pd">The name of the app to which you want to attach an auto-scaling policy.</dd>
<dt class="pt dlterm">&lt;policy_file&gt;</dt>
<dd class="pd">The name of the JSON file that describes the auto-scaling policy. See the <a href="https://new-console.{DomainName}/apidocs/48" target="_blank">{{site.data.keyword.autoscaling}} RESTful API doc</a><img src="../icons/launch-glyph.svg" alt="External link icon"> for more details.</dd>
</dl>


## Displaying an auto-scaling policy
{: #bx_as_policy_show}

You can show the auto-scaling policy of an app. The content of the policy is printed to the command line directly. Run the following command:

```
ibmcloud as policy-show <APP_NAME> [--json]
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;APP_NAME&gt;</dt>
<dd class="pd">The name of the app for which you want to show the auto-scaling policy. By default, the JSON structure is translated into a series of human readable output.</dd>
</dl>

**Tip:** You can also use the **--json** option to pretty print the original JSON response.


## Detaching an auto-scaling policy
{: #bx_as_policy_detach}

You can remove an auto-scaling policy from an  app. Run the following command:

```
ibmcloud as policy-detach <APP_NAME>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;APP_NAME&gt;</dt>
<dd class="pd">The name of the app for which you want to detach the auto-scaling policy.</dd>
</dl>


## Enabling or disabling an auto-scaling policy
{: #bx_as_policy_enable}

You can enable or disable the auto-scaling policy of a specific  app. Run the following command:

```
ibmcloud as policy-enable|policy-disable <APP_NAME>
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;APP_NAME&gt;</dt>
<dd class="pd">The name of the app for which you want to enable or disable the auto-scaling policy.</dd>
</dl>


## Displaying auto-scaling history of an app
{: #bx_as_history_show}

You can show the history of the auto-scaling activity of a specific app. A table of auto-scaling history records is displayed in the command line interface.

```
ibmcloud as history-show <APP_NAME>  [--start-date=<start_timestamp>]  [--end-date=<end_timestamp>]  [--json]
```
{: codeblock}

<dl class="parml">
<dt class="pt dlterm">&lt;APP_NAME&gt;</dt>
<dd class="pd">The name of the app for which you want to show the history of the auto-scaling policy.
<dt class="pt dlterm">&lt;start_timestamp&gt;</dt>
<dd class="pd">The time stamp of the beginning of the history range. The supported formats are `yyyy-MM-ddTHH:mm:ss+/-hhmm, yyyy-MM-ddTHH:mm:ssZ`. By default, the time stamp is set to 50 hours ahead of the current time. See the <a href="https://www.w3.org/TR/NOTE-datetime" target="_blank">W3C Date and Time Formats standard</a><img src="../icons/launch-glyph.svg" alt="External link icon"> for details about the time stamp format.
<dt class="pt dlterm">&lt;end_timestamp&gt;</dt>
<dd class="pd">The time stamp of the ending of the history range. The supported formats are `yyyy-MM-ddTHH:mm:ss+/-hhmm, yyyy-MM-ddTHH:mm:ssZ`. By default, the time stamp is set to the current time. See the <a href="https://www.w3.org/TR/NOTE-datetime" target="_blank">W3C Date and Time Formats standard</a> <img src="../icons/launch-glyph.svg" alt="External link icon">for details about the time stamp format.
</dl>


You can also use the **--json** option to pretty print the original JSON response.
{:tip}
