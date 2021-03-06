---
title: webOS OSE 1.8.0 Release
date: 2019-06-17
slug: webos-ose-1-8-0-release
posttype: release
toc: false
---

We are pleased to announce the new release of webOS Open Source Edition (OSE)! This release includes the following changes:

* [Completion of ACG migration](#completion-of-acg-migration)
* [Change on the application life-cycle management policy](#change-on-the-application-life-cycle-management-policy)
* [Flow Manager](#flow-manager)
* [Base components upgrade](#base-components-upgrade)

Please refer to the [release notes]({{< relref "webos-ose-1-8-0-release-notes" >}}) for more details on changes for this release.

## Completion of ACG migration

**ACG (Access Control Groups)** is a new security model that provides fine-grained access control of security permissions for services running on Luna Bus. This allows developers to define separate security groups with different set of methods based on functionality or security level.

This release marks the completion of migration from the legacy model (public/private) to ACG, which means developers need to set appropriate ACG information when configuring apps or services, as follows:

* **For web apps, QML apps, and native apps**
    * If methods of the external services are used, specify the group information of the external methods in the `requiredPermissions` field of `appinfo.json`.
* **For external JS services**
    * If methods of the external services are used, add the group information of the external methods to the `requiredPermissions` field in `appinfo.json` of the web app used for packaging the JS service.
* **For built-in JS services and native services**
    * If methods of the external services are used, specify the group information of the external methods in the client permission file.
    * Specify relevant group and permission information in the role file and API permission file.

For details, check the updated app/service development guides under the [Tutorials]({{< relref "/docs/tutorials" >}}) section.

## Change on the application life-cycle management policy

Due to improvement in the platform stability, the application life-cycle management policy has been changed from single-app policy to multi-app policy. webOS OSE now allows multiple apps to be launched, with one app running in the foreground while the other apps are suspended in the background. For more information, see [Application Lifecycle]({{< relref "web-app-lifecycle" >}}).

## Flow Manager

This release adds the **Flow Manager** service. Flow Manager allows users to easily plan and perform a series of tasks in the webOS environment. It is implemented based on [Node-RED](https://nodered.org), and its behavior is controlled by a flow consisting of nodes.

webOS custom nodes are provided under the "webos" category. With these custom nodes, users can bring in the functionalities of webOS services. Available custom nodes are as follows:

* ls2
* sam:launch
* tts:start
* tts:stop

To open the Flow Manager editor, access "http://{webOS-device-IP}:8000/red" on a web browser. An example flow, webos intro signage, and examples of using the custom nodes are preloaded in the editor. The webos intro signage uses the mediaviewer app to show the signage content.

Click a node to see the help or double-click to edit. For more details on how to use the editor, visit https://nodered.org/docs/.

## Base components upgrade

With this release, the following base components have been upgraded in order to enhance compatibility.

* Node.js has been upgraded from v6.11.2 to v8.12.0.
* GStreamer has been upgraded from v1.14.0 to v1.14.4.
